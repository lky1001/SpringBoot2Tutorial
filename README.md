# SpringBoot2Tutorial

## part 2 Getting Started

### [레퍼런스](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started)

#### 8. 스프링 부트 소개

- 스프링 부트를 이용하면 실행가능한 독립형, 스프링 기반의 제품을 쉽게 만들 수 있습니다.
- 스프링 플랫폼과 써드파트 라이브러리의 견해를 가지고 당신이 최소한의 고통? 몸부림? (minimum fuss)으로 시작할 수 있게 합니다.
- 대부분의 스프링 부트 애플리케이션은 매우 적은 스프링 설정을 요구합니다.
- 스프링 부트를 사용하여 `java -jar`로 실행할 수 있는 자바 애플리케이션이나 전통적인 war로 배포되는 애플리케이션을 만들 수 있습니다.
- `spring scripts`로 실행되는 CLI도 제공합니다.
- 우리의 주요 목표는 다음과 같다.
  - 모든 스프링 개발을 위한 빠르고 광범위하게 접근할 수 있는 getting-started 경험 제공
  - 요구 사항이 기본에서 벗어나기 시작하면 빠르게 빠져 나올 수 있음(?)
  - 대규모 프로젝트에 공통적으로 non-functional feature 제공(임베디드 서버, 시큐리티, 메트릭, 헬스 체크, 외부화된 구성(externalized configuration))
  - 절대 코드 생성이 없고, XML 설정 요구가 없다.

#### 9. 시스템 요구사항

- 스프링 부트 2.0.0.RELEASE는 [자바8 또는 9](https://www.java.com)와 [스프링 프레임워크 5.0.4.RELEASE](https://docs.spring.io/spring/docs/5.0.4.RELEASE/spring-framework-reference) 이상을 요구.
- 명시적인 빌드 지원은 메이븐 3.2이상과 그레이들4.
- 서블릿 컨테이너: 스프링 부트는 다음의 서블릿 컨테이너를 지원
  - Tomcat 8.5 (서블릿 3.1)
  - Jetty 9.4 (서블릿 3.1)
  - Undertow 1.4 (서블릿 3.1)
  - 아무 서블릿 3.0 이상 호환 컨테이너에 스프링 부트 애플리케이션을 배포할 수 있음.

#### 10. 스프링 부트 설치

- 스프링 부트는 "classic" 자바 개발 도구 또는 커멘드라인 도구를 이용해 설치할 수 있음.
- 어떤 방법이든 자바 1.8이상이 필요.
- 시작하기전 `$ java -version` 명령을 이용해 현재 자바 설치 버전을 확인
- 자바의 첫 개발이거나 스프링 부트를 테스트해보고 싶으면, 스프링 부트 [CLI](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-installing-the-cli)를 먼저 시도해보고, 아니면 "classic" 설치 명령어를 읽으시오.
- 자바 개발자를 위한 설치 명령어
  - 스프링 부트는표준 자바 라이브러리와 같은 방법으로 사용할 수 있음. 그러려먼 spring-boot-*.jar 파일을 classpath에 포함하세요.
  - 스프링 부트는 통합을 위해 어떤 특별한 툴도 필요하지 않으므로 어떤 IDE나 텍스트 에디터도 이용할 수 있음.
  - 또한 스프링 부트 애플리케이션에 특별한 것은 없으며 다른 자바 프로그램처럼 스프링 부트 애플리케이션을 실행하고 디버그 할 수 있다.
  - 스프링 부트의 jar들을 복사할 수도 있지만 일반적으로 Maven이나 그레이들같은 의존성 관리를 지원하는 빌드 도구를 사용하는 것을 추천함.
- 메이븐 설치
  - todo
- 그레이들 설치
  - 스프링 부트는 그레이들4와 호환. 그레이들이 이미 설치되어 있으면, [https://gradle.org](https://gradle.org)의 명령을 따를 수 있음.
  - 스프링 부트의 의존성은 `org.springframework.boot` 그룹을 사용하여 선언할 수 있음.
  - 일반적으로 당신의 프로젝트는 1개 이상의 "[Starters](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-starter)" 의존성을 선언.
  - 스프링 부트는 의존성 선언을 간단히하고 실행 가능한 jar를 만드는데 사용할 수 있는 유용한 [그레이들 플러그인](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#build-tool-plugins-gradle-plugin)을 제공.
```
Gradle Wrapper

그래들 랩퍼는 프로젝트를 빌드할 때 훌륭한(nice) 방법을 제공합니다. 당신의 코드를 빌드 프로세스로 부트스트랩하기 위한 작은 스크립트 및 라이브러리입니다. 자세한 사항은 [https://docs.gradle.org/4.2.1/userguide/gradle_wrapper.html](https://docs.gradle.org/4.2.1/userguide/gradle_wrapper.html) 여기를 보세요.
```

  - `build.gradle` 파일에 다음 예제를 작성하세요
```
plugins {
	id 'org.springframework.boot' version '2.0.0.RELEASE'
	id 'java'
}


jar {
	baseName = 'myproject'
	version =  '0.0.1-SNAPSHOT'
}

repositories {
	jcenter()
}

dependencies {
	compile("org.springframework.boot:spring-boot-starter-web")
	testCompile("org.springframework.boot:spring-boot-starter-test")
}
```

- 스프링 부트 CLI 설치
  - 스프링 부트 CLI는 스프링을 사용하여 빠르게 프로토타입을 작성하는데 사용할 수 있는 커멘드 라인 툴.
  - [그루비](http://groovy-lang.org) 스크립트를 실행할 수 있고, 그러면 보일러플레이트 코드가 없는 자바와 유사한 code를 실행할 수 있음.
  - 스프링 부트로 작업하기 위해서 CLI를 사용할 필요는 없지만 스프링 애플리케이션을 실행해보는 가장 빠른 방법.
  - 수동 설치
    - 스프링 소프트웨어 저장소에서 스프링 ㅊLI 배포판을 다운로드 할 수 있음
    - [spring-boot-cli-2.0.0.RELEASE-bin.zip](https://repo.spring.io/release/org/springframework/boot/spring-boot-cli/2.0.0.RELEASE/spring-boot-cli-2.0.0.RELEASE-bin.zip)
    - [spring-boot-cli-2.0.0.RELEASE-bin.tar.gz](https://repo.spring.io/release/org/springframework/boot/spring-boot-cli/2.0.0.RELEASE/spring-boot-cli-2.0.0.RELEASE-bin.tar.gz)
    - 최신 [스냅샷](https://repo.spring.io/snapshot/org/springframework/boot/spring-boot-cli/)도 사용 가능
    - 다운로드후 압축을 해제하고 [INSTALL.txt](https://raw.github.com/spring-projects/spring-boot/v2.0.0.RELEASE/spring-boot-project/spring-boot-cli/src/main/content/INSTALL.txt) 명령을 따르세요.
    - 요약하면 .zip 파일 안의 /bin 디렉토리에 `spring` 스크립트(윈도우용은 spring.bat)가 있음.
    - 또한 `.jar`파일로 `java -jar`을 이용할 수 있음(스크립트를 사용하면 classpath가 올바르게 설정되었는지 확인할 수 있음)
  - SDKMAN으로 설치
    - SDKMAN(소프트웨어 개발 킷 매니저)는 그루비 및 그루비, 스프링 부트를 포함한 다양한 바이너리 SDK의 여러 버전을 관리하는데 사용할 수 있음.
    - [sdkman.io](http://sdkman.io/)에서 SDKMAN을 받고 다음 명령을 이용해 스프링 부트를 설치하시오.
    
```
$ sdk install springboot
$ spring --version
Spring Boot v2.0.0.RELEASE
```

    - CLI 기능을 개발하거나 작성한 버전을 쉽게 접근하려면 다음 명령을 사용하시오.
    
```
$ sdk install springboot dev /path/to/spring-boot/spring-boot-cli/target/spring-boot-cli-2.0.0.RELEASE-bin/spring-2.0.0.RELEASE/
$ sdk default springboot dev
$ spring --version
Spring CLI v2.0.0.RELEASE
```

    - 앞의 명령어는 dev라 불리는 스프링 로컬 인스턴스를 설치함. 당신의 타겟 빌드 위치를 가르키므로 스프링 부트를 재빌드할때마다 스프링이 최신 버전.
    - 아래 명령을 실행하여 확인할 수 있음.
    
```
$ sdk ls springboot

================================================================================
Available Springboot Versions
================================================================================
> + dev
* 2.0.0.RELEASE

================================================================================
+ - local version
* - installed
> - currently in use
================================================================================
```

  - OSX Homebrew로 설치
    - 맥을 쓰고 Homebrew를 사용하는 경우 다음 명령어로 설치할 수 있음.
    - `/usr/local/bin`에 설치됨.

```
$ brew tap pivotal/tap
$ brew install springboot
```

  - MacPorts로 설치
    - 맥을 쓰고 MacPorts를 사용하는 경우 다음 명령어로 설치할 수 있음.

```
$ sudo port install spring-boot-cli
```

  - 명령행 완료
    - 스프링 부트 CLI에는 BASH및 zsh 쉘에 대한 명령을 제공하는 스크립트가 포함됨.
    - 모든 쉘에서 스크립트(spring라고도 불림)를 만들거나, 개인용 또는 시스템 전체 bash 초기화에 넣을 수 있음.
    - 데비안 시스템에서는 모든 시스템 스크립트가 `/shell-completion/bash`에 있고, 이 디렉토리의 모든 스크립트는 새로운 쉘이 시작될 때 실행됨.
    - 예를 들어, SDKMAN을 사용하여 설치한경우 스크립트를 수동으로 실행하려면 다음 명령을 사용.

```
$ . ~/.sdkman/candidates/springboot/current/shell-completion/bash/spring
$ spring <HIT TAB HERE>
  grab  help  jar  run  test  version
```

  - 스프링 CLI 실행 예제
    - 다음 웹 애플리케이션을 사용하여 CLI 설치를 테스트할 수 있음.
    - 해보려면 `app.groovy` 파일을 다음 내용과 함께 만들고 다음 명령어를 실행.
    
```
@RestController
class ThisWillActuallyRun {

	@RequestMapping("/")
	String home() {
		"Hello World!"
	}

}
```

```
$ spring run app.groovy
```

    - 웹 브라우저에서 `localhost:8080`을 열면, `Hello World!`를 볼 수 있음.

  - 스프링 부트 이전 버전에서 업그레이드
    - 스프링 부트 이전 버전에서 업그레이드 하는 사용자의 경우 자세한 지침을 제공하는 위키의 [마이그레이션](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.0-Migration-Guide)을 참고.
    - 또한 각 릴리즈의 [릴리즈 노트](https://github.com/spring-projects/spring-boot/wiki)에서 "새로 주목할 만한 기능" 목록을 확인하시오.
    - 기존 CLI 설치를 업그레이드하려면 패키지 관리자 명령 (예 : brew upgrade)을 사용하거나 CLI를 수동으로 설치 한 경우 PATH 환경 변수를 업데이트하여 이전 참조를 제거하는 것을 잊지 말고 [표준 지침](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-manual-cli-installation)을 따르시오.

  - 스프링 부트 애플리케이션 개발
    - 이번 섹션에서는 스프링 부트의 주요 기능 중 일부를 강조하는 간단한 "Hello World!" 웹 애플리케이션을 개발하는 방법에 대해 설명.
    - 대부분의 IDE들이 Maven을 지원하기 떄문에 Maven을 사용하여 이 프로젝트를 빌드.
    - 시작전 터미널을 열고 아래 명령을 실행하여 지원 가능한 자바 및 메이븐 버전이 설치되어 있는지 확인.
```
$ java -version
java version "1.8.0_102"
Java(TM) SE Runtime Environment (build 1.8.0_102-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.102-b14, mixed mode)

$ mvn -v
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T16:41:47+00:00)
Maven home: /usr/local/Cellar/maven/3.3.9/libexec
Java version: 1.8.0_102, vendor: Oracle Corporation
```

  - POM 생성
    - 시작하기 위해 Maven의 pom.xml 파일을 만들어야 함. pom.xml은 프로젝트를 빌드하는데 사용되는 recipe임.
    - 좋아하는 텍스트 편집기를 열고 다음을 추가.

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>myproject</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.0.0.RELEASE</version>
	</parent>

	<!-- Additional lines to be added here... -->

</project>
```

    - 앞의 목록은 작업 빌드를 제공. `mvn package`를 실행하여 테스트 가능. (지금은 "jar will be empty - no content was marked for inclusion!" 경고는 무시 가능)
  - classpath 의존성 추가
    - 스프링 부트는 classpath에 jars를 추가할 수 있게 수많은 "Starters"를 제공함.
    - 샘플 애플리케이션은 이전 섹션에서 이미 `parent`에 `spring-boot-starter-parent`를 사용했음.
    - `spring-boot-starter-parent`는 유용한 메이븐 기본값을 제공하는 특별한 starter.
    - 또한 의존성에 대해 `version` 태그를 생략할 수 있도록 dependency-managemt를 제공.
    - 'Starter'는 특별한 종류의 애플리케이션을 개발할때 필요한 종속성을 제공.
    - 우리는 웹 애플리케이션을 개발하고 있기 때문에, `spring-boot-starter-web` 의존성을 추가. 그 전에 아래의 명령어를 수행하여 현재 가지고 있는 의존성을 볼 수 있음.
```
$ mvn dependency:tree

[INFO] com.example:myproject:jar:0.0.1-SNAPSHOT
```

    - `mvn dependency:tree` 명령어는 프로젝트 종석성에 대한 트리를 출력.
    - `spring-boot-starter-parent`는 아무런 의존성도 제공하지 않는다는 것을 알 수 있음.
    - 필요한 의존성을 추가하려면 pom.xml에 parent 섹션 바로 아래 `spring-boot-starter-web` 의존성을 추가.

```
<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>
```

    - `mvn dependency:tree`를 다시 실행하면 톰캣 웹서버와 스프링 부트를 포함하여 많은 의존성이 있음을 알 수 있음.

  - 코드 작성
    - 우리 애플리케이션을 완성하려면, 하나의 자바 파일을 생성해야함. 기본적으로 메이븐은  `src/main/java`의 소스를 컴파일하므로 폴더 구조를 만든 후 `src/main/java/Example.java` 파일을 추가하여 다음 코드를 작성.

```
import org.springframework.boot.*;
import org.springframework.boot.autoconfigure.*;
import org.springframework.web.bind.annotation.*;

@RestController
@EnableAutoConfiguration
public class Example {

	@RequestMapping("/")
	String home() {
		return "Hello World!";
	}

	public static void main(String[] args) throws Exception {
		SpringApplication.run(Example.class, args);
	}

}
```

    - 코드가 많지는 않지만 많은 일이 일어남. 다음 몇 가지 섹션에서 중요한 부분을 단계별로 설명.
    
  - @RestController, @RequestMapping 어노테이션
    - Example 클래스의 첫번째 어노테이션은 `@RestController`. 스테레오타입 어노테이션으로 알려져있음. 코드를 읽는 사람들에게 힌트를 제공하고, 클래스가 특별한 역할을 한다는 것을 스프링에 알려줌.
    - 이 경우 우리의 클래스는 웹 `@Controller` 임. 따라서 스프링이 웹 요청이 들어올때 이를 고려함.
    - `@RequestMapping` 어노테이션은 라우팅 정보를 제공. 이는 `/` 패스로 요청이 들어오면 `home` 메소드에 맵핑되어야 한다는 것을 스프링에 알려줌.
    - `@RestController` 어노테이션은 메소드의 결과 문자를 호출한 곳에 직접 돌려주어 렌더링하게 스프링에 알려줌.
    - 두개는 스프링 MVC의 어노테이션이고, 자세한 내용은 [MVC 섹션](https://docs.spring.io/spring/docs/5.0.4.RELEASE/spring-framework-reference/web.html#mvc) 참고.
    
  - @EnableAutoConfiguration 어노테이션
    - 클래스의 두번째 주석은 `@EnableAutoConfiguration`. 이 어노테이션은 스프링 부트에게 우리가 추가한 jar 의존성을 기반으로 설정 방법을 "추측"하도록 알려줌.
    - `spring-boot-starter-web`은 톰캣과 스프링 MVC를 추가했기 때문에 auto-configuration은 우리가 웹 애플리케이션을 개발하고 그에 따라 스프링을 설정한다고 가정함.
    - Auto-configuration은 "Starters"와 잘 동작하도록 설계되었지만, 두 개념은 직접적으로 연결되지 않음.
    - 자유롭게 starters의 외부에서 jar 디펜던시를 선택하거나 고를수 있음. 스프링 부트는 여전히 당신의 애플리케이션을 위한 자동 설정에 최선을 다함. 
  - "main" 메소드
    - 우리 애플리케이션의 마지막 파트는 `main` 메소드임. 이것은 응용프로그램 시작 지점에 대한 자바 컨벤션을 따르는 표준 방법.
    - `main` 메소드는 `run`을 호출하여 스프링 부트의 `SpringApplication` 클래스에 위임함.
    - `SpringApplication`은 스프링을 시작, 톰캣 웹서버의 자동 설정 시작등으로 애플리케이션을 부트스트랩 함.
    - 스프링 기본 컴포넌트인 `SpringApplication`에 알리기 위해 Example.class를 `run` 메소드의 매개변수로 전달해야 함.
    - `args` 배열도 전달되어 커멘드라인 매개변수를 알려 줌.
  - 예제 실행
    - 이제 애플리케이션이 작동해야 함.
    - 루트 프로젝트 디렉토리에서 `mvn spring-boot:run`을 입력하여 애플리케이션을 실행할 수 있음.
    - 아래와 유사한 출력을 볼 수 있음.

```
$ mvn spring-boot:run

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v2.0.0.RELEASE)
....... . . .
....... . . . (log output here)
....... . . .
........ Started Example in 2.222 seconds (JVM running for 6.514)
```

    - 웹브라우저에서 `localhost:8080`을 열면 `Hello World!`을 볼 수 있음.
  - 실행가능한 Jar 생성
    - 때때로 "fat jars" 라고 부름.
    - 컴파일된 클래스와 코드가 실행하기 위해 필요한 모든 jar 의존성을 포함하는 아카이브
    - 실행가능한 jar를 만들려면 pom.xml에 spring-boot-maven-plugin 추가.

```
<build>
	<plugins>
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
		</plugin>
	</plugins>
</build>
```

    - pom.xml을 저장하고 `mvn package` 실행.

```
$ mvn package

[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building myproject 0.0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO] .... ..
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ myproject ---
[INFO] Building jar: /Users/developer/example/spring-boot-example/target/myproject-0.0.1-SNAPSHOT.jar
[INFO]
[INFO] --- spring-boot-maven-plugin:2.0.0.RELEASE:repackage (default) @ myproject ---
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```

    - target 디렉토리 안에 example-0.0.1-SNAPSHOT.jar를 볼 수 있음. 대략 10MB 용량.
    - jar의 내부를 보려면 `jar tvf` 이용. 
    - `$ jar tvf target/example-0.0.1-SNAPSHOT.jar`