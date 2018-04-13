# Maven 如何解决依赖冲突

依赖冲突

比如A->X(1.0)，A->B->X(2.0)。A直接依赖了1.0版本的X，而A依赖的B依赖了2.0版本的X。如果依赖范围合适的话，B中依赖的X也是会传递到A项目中的。而两个X的版本不一致，这就产生了依赖冲突。

在依赖冲突发生时，maven不会直接提示错误，而是用一套规则来进行 依赖调解。规则有两条：

1. 路径最近者优先。
2. 第一声明者优先。

依赖路径指的是项目到依赖的长度，比如A->X(1.0)长度为1，A->B->X(2.0)长度为2，所以最终会使用1.0版本的X。

如果两者的路径一样呢？比如A->B->X(2.0)和A->C->X(3.0)，这两个依赖路径的长度都是2，那用哪个呢？这就需要第二个规则了，也就是哪个先声明就用哪个。

大部分情况下maven这种自动的依赖调解能帮我们解决问题了。但是有时候我们不得不手动处理依赖冲突。这种冲突可能不是同一个依赖的不同版本（这个依赖调解能搞定），而是不能同时出现的两个依赖。比如slf4j-log4j和logback这两个依赖是不能同时出现的，但是因为他们的坐标不一样，所以maven不会对齐进行处理。这个时候我们就需要手动进行 排除依赖 了。

## 检查依赖冲突

第一种是使用mvn dependency:tree -Dverbose来列出项目的所有依赖以及传递性依赖。对于重复和冲突的依赖，会提示omitted for duplicate和omitted for conflict with x.x.x。

第二个方法是使用maven的enforcer插件。在项目POM中加入：

```xml

<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-enforcer-plugin</artifactId>
            <version>1.4.1</version>
            <executions>
                <execution>
                    <id>enforce</id>
                    <configuration>
                        <rules>
                            <dependencyConvergence/>
                        </rules>
                    </configuration>
                    <goals>
                        <goal>enforce</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>

```

这样在用maven编译时，如果存在依赖冲突，就会有错误提示
