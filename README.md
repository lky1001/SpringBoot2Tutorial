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