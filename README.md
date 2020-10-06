# nacre-build

## check style

The checkstyle config for the multiple modules project.

Use it in your `pom.xml` like this:

```xml
    <plugin>
        <artifactId>maven-checkstyle-plugin</artifactId>
        <version>3.1.0</version>
        <dependencies>
            <dependency>
                <groupId>io.github.shallowinggg</groupId>
                <artifactId>nacre-build</artifactId>
                <version>1.3.0</version>
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

There are four configs in `checkstyle` folder, including `checkstyles.xml`, `google-check.xml`, `sun_check.xml` and `nacre-check.xml`. `nacre-check.xml` is only used for shallowinggg's owning projects with configuration limit:

```xml
    <module name="PackageName">
        <property name="format" value="^io\.github\.shallowinggg(\.[a-z]+)*$"/>
    </module>
```

So, you should use other 3 general config in `checkstyle` folder for your projects.

## formatter

Use `formatter-maven-plugin` like this:

```xml
<properites>
    <formatter.config>formatter/formatter.xml</formatter.config>

    <formatter.version>2.12.2</formatter.version>
</properites>

<build>
    <plugins>
        <plugin>
            <groupId>net.revelc.code.formatter</groupId>
            <artifactId>formatter-maven-plugin</artifactId>
            <dependencies>
                <dependency>
                    <groupId>io.github.shallowinggg</groupId>
                    <artifactId>nacre-build</artifactId>
                    <version>${nacre.version}</version>
                </dependency>
            </dependencies>
            <configuration>
                <configFile>${formatter.config}</configFile>
                <skipXmlFormatting>true</skipXmlFormatting>
            </configuration>
            <executions>
                <execution>
                    <goals>
                        <goal>format</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

The formatter config follows google styles but have some slightly modifications in it:

- org.eclipse.jdt.core.formatter.tabulation.char: tab
- org.eclipse.jdt.core.formatter.tabulation.size : 4
- org.eclipse.jdt.core.formatter.insert_new_line_in_empty_block: true

see [eclipse-java-google-style.xml](https://github.com/google/styleguide/blob/gh-pages/eclipse-java-google-style.xml) for more information.
