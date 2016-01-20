## Android 项目中proguard 使用

[proguard简介](proguard.md)

### 开启混淆
- 使用gradle构建方式
    在app下的build.gradle配置 minifyEnabled true
    ``` java
    buildTypes {
       release {
           minifyEnabled true
           proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
       }
   }
   ```    

### 混淆文件
proguardFiles 指定混淆文件，多个混淆文件用‘，’号隔开

getDefaultProguardFile('proguard-android.txt')
这一行指定了[系统默认的混淆文件](proguard-android.txt)，位于<sdk_root>/tools/proguard

proguard-rules.pro文件为额外配置的混淆文件

### 混淆规则
- 需要在AndroidManifest.xml配置的类都不能混淆
- 通过JNI被调用的方法不能混淆
- 动态引用的属性和方法不能混淆
- 某些第三方jar包不能混淆
- js引用的类和方法

### 配置混淆文件
[示例](proguard-rules.pro)

[-keep 使用](keep使用.md)

### 混淆后调试程序
通过mapping.txt文件，可以得到恢复后的Log信息
```
$retrace.sh -verbose app/build/outputs/mapping/release/mapping.txt log.txt
```
>retrace.sh命令位于 Android_sdk/tools/proguard/目录下
