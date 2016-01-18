### keep使用

[官方说明](http://proguard.sourceforge.net/manual/usage.html#keepoptionmodifiers)

| Keep | 收缩时不被移出，混淆时不被重命名 | 混淆时不被重命名（选项仅用于混淆阶段） |
| ------------- | ------------- | ------------- |
| 保持类和类的成员  | -keep [,modifier,...] class_spec  | 	-keepnames（等价于-keep,allowshrinking class_spec） |
| 仅保持类的成员，如果在压缩阶段这些类没有被删除  | -keepclassmembers [,modifier,...] class_spec  | -keepclassmembernames class_spec  |
| 保持类和类的成员，如果在压缩阶段这些类没有被删除  | -keepclasseswithmembers [,modifier,...] class_spec  | -keepclasseswithmembernames class_spec |

### modifier取值
| modifier	| 说明 |
| ------------- | ------------- |
| includedescriptorclasses |  方法、字段的类型描述符中的任何类，跟随被keep的方法/字段一并保留，通常用于保留Native方法的名字时，防止Native方法参数的名字被修改，以保证和Native库兼容 |
| allowshrinking | 指定是否入口点可以被压缩 |
| allowoptimization | 指定是否入口点可以被优化 |
| allowobfuscation | 指定是否入口点可以被混淆 |

### class_spec取值
```
[@annotationtype] [[!]public|final|abstract|@ ...] [!]interface|class|enum classname
    [extends|implements [@annotationtype] classname]
[{
    [@annotationtype] [[!]public|private|protected|static|volatile|transient ...] <fields> |
                                                                      (fieldtype fieldname);
    [@annotationtype] [[!]public|private|protected|static|synchronized|native|abstract|strictfp ...] <methods> |
                                                                                           <init>(argumenttype,...) |
                                                                                           classname(argumenttype,...) |
                                                                                           (returntype methodname(argumenttype,...));
    [@annotationtype] [[!]public|private|protected|static ... ] *;
    ...
}]
```

@annotationtype 注解
public|private|protected|static|volatile|transient 修饰符
interface|class|enum 类型
