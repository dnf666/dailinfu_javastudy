# Statement 与 PrepareStatement 的区别

## 动态参数

PrepareStatement 支持动态参数的传入，但是 Statement 不支持动态参数的传入

## 编码

PrepareStatement 可以避免如单引号的编码麻烦，Statement 不可以

## 预编译

PrepareStatement 支持预编译，而 Statement 不支持

## 出错是否便查找

PrepareStatement 的高级特性决定如果 Sql 不容易查出来，但是 Statement 容易查

## 安全

PrepareStatement 可以防止 Sql 注入，而 Statement 不可以
