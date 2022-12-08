---
description: gradle build some
---

# Gradle

```
build apk   gradle app:assembleRelease
build aab   gradle app:bundleRelease

print messages during building progress  : —stacktrace —info —debug 

show dependencies conflict : gradle app:dependencies / other module :  gradle ${moduleName}:dependencies
```

## 1&#x20;

本机器没安装gradle 的话 使用 ./gradlew 来执行命令

gradle app:assembleRelease 打包apk,

gradle app:bundleRelease 打包aab &#x20;

后面可以加 —stacktrace —info —debug来打印更多信息

## 2

使用 gradle app:dependencies 来查看所有库的依赖树 &#x20;

若是其他module那就   gradle 模块名:dependencies

gradle -q \[项目名]:dependencies命令查看依赖树&#x20;

## 3

如果有老的android-v4 或者android-combat-v7库与现有的androidX库的冲突，比如一些三方sdk接入

可以用 android.enableJetifier=true  来处理，Jetifier可以将compat-v7之类的库中的转换为androidX对应的类
