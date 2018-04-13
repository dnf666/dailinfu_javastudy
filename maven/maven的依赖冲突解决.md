 若项目中多个Jar同时引用了相同的Jar时，会产生依赖冲突，但Maven采用了两种避免冲突的策略，因此在Maven中是不存在依赖冲突的。

1. 短路优先
本项目——>A.jar——>B.jar——>X.jar
本项目——>C.jar——>X.jar

若本项目引用了A.jar，A.jar又引用了B.jar，B.jar又引用了X.jar，并且C.jar也引用了X.jar。
在此时，Maven只会引用引用路径最短的Jar。

2. 声明优先 
若引用路径长度相同时，在pom.xml中谁先被声明，就使用谁。
