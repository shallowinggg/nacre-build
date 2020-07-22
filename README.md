# nacre-build

The checkstyle config for the multiple modules project.

Use it in your `pom.xml` like this:

```xml
    <plugin>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <version>3.1.1</version>
        <dependencies>
            <dependency>
                <groupId>io.github.shallowinggg</groupId>
                <artifactId>nacre-build</artifactId>
                <version>${nacre-build.version}</version>
            </dependency>
        </dependencies>
        <executions>
            <execution>
                <id>checkstyle</id>
                <phase>verify</phase>
                <configuration>
                    <configLocation>
                        checkstyle/checkstyle.xml
                    </configLocation>
                </configuration>
                <goals>
                    <goal>check</goal>
                </goals>
            </execution>
        </executions>
    </plugin>
```

There are two configs in `checkstyle` folder and `nacre-checkstyle` folder. They only have slight differences, `nacre-checkstyle/checkstyle.xml` should only be used in groupId `io.github.shallowinggg` for configuration limit:

```xml
    <module name="PackageName">
        <property name="format" value="^io\.github\.shallowinggg(\.[a-z]+)*$"/>
    </module>
```

So, you should use general config in `checkstyle` folder for your own projects.

You can also use `google check` with `google-check/checkstyle.xml` or `sun check` with `sun-check/checkstyle.xml` in version `1.2.0`.
