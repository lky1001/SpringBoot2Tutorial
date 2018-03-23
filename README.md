# SpringBoot2Tutorial

## 이 레포지토리는 스프링 부트 2.0.0.RELEASE 문서를 기반으로 학습용으로 만들어졌습니다.

- [https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle](https://docs.spring.io/spring-boot/docs/2.0.0.RELEASE/reference/htmlsingle)

### 내용

- [Part 1](https://github.com/lky1001/SpringBoot2Tutorial/tree/part1)
- [Part 2](https://github.com/lky1001/SpringBoot2Tutorial/tree/part2)

### What's new in Spring Boot 2? ([http://www.baeldung.com/new-spring-boot-2](http://www.baeldung.com/new-spring-boot-2))

1. 개요

  - 스프링 부트는 스프링 생태계에 독단적으로(opinionated) 접근한다.
  - 2014년 중반에 처음으로 출시됐다.
  - 스프링부트는 많은 개발과 개선이 이루어졌고 2.0 버전은 2018년 초 출시될 준비가 돼었다.(현재는 출시됨)
  - 이 인기있는 라이브러리가 우리를 도우려는 여러가지 분야가 있다.
    - 의존성 관리(Dependency management): 스타터와 다양한 패키지 관리자를 통합하여 관.
    - 자동 설정(Auto Configuration): 스프링 앱이 실행되기 위해 요구하는 설정을 최소화하려하고 설정보다는 관습을 선호(favoring convention over configuration).
    - 제품을 위해 준비된 기능들(Production-ready features): Actuator, 더 나은 로깅, 모니터링, 메트릭, 다양한 PAAS 통합.
    - 향상된 개발 경험(Enhanced development experience): `spring-boot-devtools`를 이용하여 멀티플 테스팅 유틸리티 또는 더 나은 피드백 반복.
  - 이 글은 스프링 부트 2.0에 몇가지 변경되고 계획된 기능을 알아본다. 또한 이러한 변화가 생산성 향상에 어떻게 도움이 되는지 설명할 것이다.

2. 의존성(Dependencies)

  - 자바
    - 스프링부트 2.x는 더이상 자바 7이하는 지원하지 않음. 자바8이 최소 요구사항
    - 또한 자바9를 지원하는 최초의 버전이다.
    - 그들은 1.x 버전에서 자바9을 지원할 계획이 없다.
    - 즉 최신 자바 버전을 이 프레임워크에 이용하려면 스프링 부트 2.x가 유일한 선택이다.

  - 스프링 부트 2 요구사항(Bill of Materials)
    - 스프링 부트가 출시될 때마다 자바 생태계의 다양한 의존성 버전이 업그레이드 된다.
    - 이는 부트 BOM([bill of materials aka BOM](http://www.baeldung.com/spring-maven-bom))으로 정의된다.
    - 2.x도 예외는 없다. 이들을 나열하는 것은 의미가 없지만 [spring-boot-dependencies.pom](https://github.com/spring-projects/spring-boot/blob/master/spring-boot-project/spring-boot-dependencies/pom.xml)을 보면 어떤 시점에서 어떤 버전이 사용되고 있는지 볼 수 있습니다.
  - 최소 요구사항에 대한 몇가지 중요 내용
    - 톰캣 8.5 이상
    - 하이버네이트 5.2 이상
    - 그레이들 3.4 이상

  - 그레이들 플러그인
    - 그레이들 플러그인은 큰 개선과 작은 변경이 있다.
    - jar를 만들기 위한 bootRepackage 그레이들 태스크는 jar와 war를 빌드하기 위한 bootJar와 bootWar로 각각 변경.
    - 우리 앱을 그레이들 플러그인으로 실행하려면, 1.x에서는 bootRun을 실행.
    - 2.x에서 bootRun은 그레이들 JavaExec를 확장.
    - 이는 고전 JavaExec 작업에서 일반적으로 사용하는 것과 동일한 구성을 적용하여 부트 앱을 구성하는 것이 더 쉽다는 것을 의미함.
    - 가끔 스프링 부트 BOM을 이용하길 원함. 하지만 때론 부트앱 전체를 빌드하거나 리패키지하길 원치 않음. 이에 대해 스프링 부트 2.x는 더 이상 의존성 관리를 기본으로 사용하지 않음.
    - 스프링 부트 의존성 관리를 사용하려면 다음을 추가
    - ```apply plugin: 'io.spring.dependency-management'```
    - 이로 인해 위에서 언급한 시나리오의 구성을 줄이고 유연성을 얻을 수 있음.
    
3. 자동 구성(Autoconfiguration)

  - Security
    - 2.x에서 시큐리티 구성이 대폭 간소화 됨.
    - 기본적으로 정적 리소스와 endpoint를 포함하여 모든 것이 안전함.
    - 사용자가 시큐리티를 명시적으로 설정하면, 스프링 부트의 기본값이 영향을 미치지 않음. 사용자는 모든 접근 룰을 한곳에서 설정할 수 있음.
    - 이로써 WebSecurityConfigurerAdapter의 순서 문제로 어려움을 겪지 않게 됨. 이 문제는 Actuator와 앱 시큐리티 룰을 커스텀으로 설정할 때 발생 했음.
    - Actuator와 애플리케이션 룰을 간단히 보면
```
http.authorizeRequests()
  .requestMatchers(EndpointRequest.to("health"))
    .permitAll() // Actuator rules per endpoint
  .requestMatchers(EndpointRequest.toAnyEndpoint())
    .hasRole("admin") // Actuator general rules
  .requestMatchers(StaticResourceRequest.toCommonLocations())
    .permitAll() // Static resource security
  .antMatchers("/**")
    .hasRole("user") // Application security rules
  // ...
```

  - 리액티브 지원(Reactive Support)
    - 스프링 부트 2는 다양한 리액티브 모듈을 위한 새로운 스타터 세트를 제공.
    - 웹플럭스나 몽고디비, 카산드라, 레디스의 리액티브 대응에 대한 몇가지 예제.
    - 웹플럭스를 위한 테스트 유틸리티. @WebFluxTest 사용 가능
    - @WebFluxTest는 1.4에서 다양한 테스트 부분에 포함된 @WebMvcTest와 유사하게 동작함. 
    