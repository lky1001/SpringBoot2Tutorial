# SpringBoot2Tutorial

## part 1

### [레퍼런스](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-documentation)

#### 1. 문서에 대해

- 스프링부트 레퍼런스 가이드는 [HTML](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/html), [PDF](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/pdf/spring-boot-reference.pdf), [EPUB](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/epub/spring-boot-reference.epub)으로 이용 가능
- 최신 문서는 [docs.spring.io/spring-boot/docs/current/reference](https://docs.spring.io/spring-boot/docs/current/reference)
- 이 문서의 사본은 개인용으로 이용하거나 다른 사람에게 배포할 수 있음. 단 사본에 대해 수수료를 부과하지 않고, 저작권의 고지가 포함되어 있어야 함

#### 2. 도움 받기

- 스트링 부트에 대한 문제가 있다면 우리(스프링 부트팀)가 도움 주고 싶다.
- [How-to documents](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#howto)를 보면 가장 일반적인 답변을 얻을 수 있음
- 스프링을 기본을 익히고, 스프링 부트는 많은 스프링 프로젝트를 기반으로 함. 다양한 레퍼런스 문서를 보려면 [spring.io](https://spring.io/) 사이트를 확인하세요.
- 스프링으로 시작한다면 이 [가이드](https://spring.io/guides) 중 하나에서 시작하세요.
- 질문은 [stackoverflow.com](https://stackoverflow.com/)의 질문 태그 [spring-boot](https://stackoverflow.com/tags/spring-boot)를 우리가 모니터링합니다.
- 스프링 부트의 버그 리포트는 [https://github.com/spring-projects/spring-boot/issues](https://github.com/spring-projects/spring-boot/issues)

#### 3. 첫 단계

- 스프링 부트 또는 스프링을 시작하려면 [다음 토픽(part 2)](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started)으로 시작하세요
- 처음부터 하기: [개요](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-introducing-spring-boot) | [요구사항](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-system-requirements) | [설치](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-installing-spring-boot)
- 튜토리얼: [Part 1](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-first-application) | [Part 2](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-first-application-code)
- 예제 실행: [Part 1](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-first-application-run) | [Part 2](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#getting-started-first-application-executable-jar)

#### 4. 스프링부트로 작업하기

- 스프링부트를 시작할 준비가 진짜 됐는가? 우리는 [다음](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot)과 같이 다루었다.
- 빌드 시스템: [메이븐](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-maven) | [그레이들](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-gradle) | [Ant](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-ant) | [Starters](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-starter)
- 모범 사례: [코드구조](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-structuring-your-code) | [@Configuration](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-configuration-classes) | [@EnableAutoConfiguration](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-auto-configuration) | [빈즈, 의존성 주입](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-spring-beans-and-dependency-injection)
- 코드 실행: [통합개발환경](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-running-from-an-ide) | [앱 패키지](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-running-as-a-packaged-application) | [메이븐](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-running-with-the-maven-plugin) | [그레이들](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-running-with-the-gradle-plugin)
- 앱 패키징: [Production jars](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#using-boot-packaging-for-production)
- 스프링 부트 CLI: [CLI 사용](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#cli)

#### 5. 스프링 부트 기능 학습

- 자세한 스프링 부트의 핵심 기능을 원하는가? [다음 컨텐츠](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features)가 도움이 될 것 이다.
- 핵심 기능들: [SpringApplication](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-spring-application) | [External Configuration](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-external-config) | [Profiles](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-profiles) | [Logging](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-logging)
- 웹 애플리케이션: [MVC](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-spring-mvc) | [내장 컨테이너](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-embedded-container)
- 데이터 작업: [SQL](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-sql) | [NO-SQL](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-nosql)
- 메시징: [개요](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-messaging) | [JMS](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-jms)
- 테스트: [개요](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-testing) | [부트 애플리케이션](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-testing-spring-boot-applications) | [유틸](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-test-utilities)
- 확장(Extending): [Auto-configuration](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-developing-auto-configuration) | [@Conditions](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#boot-features-condition-annotations)

#### 6. 프로덕션

- 스프링 부트 애플리케이션이 제품으로 배포될 준비가 되면, 우리에게 [몇가지 트릭](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready)이 있다.
- Management endpoints: [개요](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-endpoints) | [Customization](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#)
- Connection Options: [HTTP](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-monitoring) | [JMX](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-jmx)
- 모니터링: [Metrics](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-metrics) | [Auditing](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-auditing) | [Tracing](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#) | [Process](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#production-ready-process-monitoring)

#### 7. 고급 주제

- 마지막으로, 고급 사용자를 위한 몇가지 주제가 있음
- 스프링 부트 애플리케이션 배포: [Cloud Deployment](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#cloud-deployment) | [OS Service](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#deployment-service)
- 빌드 툴 플러그인: [메이블](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#build-tool-plugins-maven-plugin) | [그레이들](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#build-tool-plugins-gradle-plugin)
- Appendix: [Application Properties](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#common-application-properties) | [Auto-configuration classes](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#auto-configuration-classes) | [Executable Jars](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle/#executable-jar)