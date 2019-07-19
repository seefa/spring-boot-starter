## Building Spring Boot application with Gradle plus Kotlin

1-Make a **Gradle** Project by _Kotlin_ language syntax with IDE

2- Make Project package structure(**ir.seefa.sample.project**) in _src/main/kotlin_ and _src/test/kotlin_

* Hint: Be careful about word spelling for packages because Test classes will not able to run SpringBoot Test Runner if *Packages* or *Classes* are not match names.

3- add below codes to **build.gradle.kts** to get **Spring Boot** dependencies and project features(Project name, Project version, Java plugin, dependencies, Add a task to making JAR file, Java configuration, so on)

```
 import org.jetbrains.kotlin.gradle.tasks.KotlinCompile
 
 plugins {
     id("org.springframework.boot") version "2.1.6.RELEASE"
     id("io.spring.dependency-management") version "1.0.7.RELEASE"
     kotlin("jvm") version "1.2.71"
     kotlin("plugin.spring") version "1.2.71"
 }
 
 group = "ir.seefa.sample.project"
 version = "1.0-SNAPSHOT"
 java.sourceCompatibility = JavaVersion.VERSION_11
 
 repositories {
     mavenCentral()
 }
 
 dependencies {
     implementation("org.springframework.boot:spring-boot-starter-web")
     implementation("com.fasterxml.jackson.module:jackson-module-kotlin")
     implementation("org.jetbrains.kotlin:kotlin-reflect")
     implementation("org.jetbrains.kotlin:kotlin-stdlib-jdk8")
     testImplementation("org.springframework.boot:spring-boot-starter-test")
 }
 
 tasks.withType<KotlinCompile> {
     kotlinOptions {
         freeCompilerArgs = listOf("-Xjsr305=strict")
         jvmTarget = "1.8"
     }
 }
```
 
* Tips: 
    1) import _org.jetbrains.kotlin.gradle.tasks.KotlinCompile_
    2) plugins -> _org.springframework.boot_,_io.spring.dependency-management_,_kotlin("jvm")_,_kotlin("plugin.spring")_
    3) apply plugin -> _io.spring.dependency-management_
    4) Project properties: _Group_,_Version_,_java.sourceCompatibility_
    5) repositories
    6) dependencies implementation -> _org.springframework.boot:spring-boot-starter-web_,implementation -> _com.fasterxml.jackson.module:jackson-module-kotlin_,implementation -> _org.jetbrains.kotlin:kotlin-reflect_,implementation -> _org.jetbrains.kotlin:kotlin-stdlib-jdk8_,testImplementation -> _org.springframework.boot:spring-boot-starter-test_
    7) tasks.withType<KotlinCompile>

4- Add **SpringBootStarterApplication.kt** class to has been made package from Step 2 with following code:

```
package ir.seefa.sample.project

import org.springframework.boot.autoconfigure.SpringBootApplication
import org.springframework.boot.runApplication

@SpringBootApplication
class SpringBootStarterApplication

fun main(args: Array<String>) {
	runApplication<SpringBootStarterApplication>(*args)
}
```

5- Add **application.properties** file to _src/main/resources_ path for apply application configuration before run such server port as follows:

```
server.port=9090
```

6- Add **SpringBootStarterApplicationTests** class to _/src/test/kotlin/[Package_Name]_ with following codes

```
package ir.seefa.sample.project

import org.junit.Test
import org.junit.runner.RunWith
import org.springframework.boot.test.context.SpringBootTest
import org.springframework.test.context.junit4.SpringRunner

@RunWith(SpringRunner::class)
@SpringBootTest
class SpringBootStarterApplicationTests {

	@Test
	fun contextLoads() {
	}

}
```

7- run command **gradle** in command line

8- run command **gradle tasks** in command line

9- Build your project with Gradle Wrapper => Run in command line(gradle wrapper --gradle-version 5.4.1)

10- After passing step No.8, we can only run this command to build project(**./gradlew build**)

11- Run this command will execute our Application(**./gradlew run**)  or Run **SpringBootStarterApplication** directly.
