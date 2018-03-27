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
    
4. Production-ready features 

  - 스프링부트는 production-ready 애플리케이션을 만드는 데에 유용한 툴들을 제공한다. 
  - 그중에서도 Spring Boot Actuator의 장점을 살린다. 
  - Actuator는 간단하게 앱을 모니터링할 수 있는 다양한 툴들을 포함한다. 
  - Actuator에 대한 더 자세한 사항은 [이전에 쓰인 글](http://www.baeldung.com/spring-boot-actuators)에서 확인할 수 있다.
  - 스프링부트2에서의 actuator는 커스터마이징을 간단하게 적용할 수 있는데에 초점을 두었다. 이는 새로운 리액티브 모듈을 포함한 다른 웹 기술들도 지원한다.
  - 기술 지원
    - 스프링부트 1.x 버전에서는 Spring-MVC만 acutoator의 End-point를 위해 지원
    - 2.x 버전에서 Spring-MVC는 독립적이고 플러그 가능해짐.
    - WebFlux, Jersey, Spring-MVC에 대해서도 지원 
    - 이전과 마찬가지로 JMX는 옵션으로 남아있고, 설정을 통해 사용할지 안할지를 결정할 수 있다.
    
  - Endpoints 커스터마이징
    - 새로운 actuator 인프라구조는 특정 기술에 의존하지 않기 때문에 개발 모델은 처음부터 다시 디자인되었다. 
    - 이 새로운 모델은 더 큰 확장성과 다양한 표현이 가능해지게 했다.
    - 새로운 Actuator를 이용하여 Fruits endpoint를 어떻게 만드는지 살펴보자
```
@Endpoint(id = "fruits")
public class FruitsEndpoint {
    @ReadOperation
    public Map<String, Fruit> fruits() { ... }
    @WriteOperation
    public void addFruits(@Selector String name, Fruit fruit) { ... }
}
```
   - Fruits Endpoint를 ApplicationContext에 등록하기만 하면, fruits는 우리가 선택한 기술에 통해 웹의 endpoint로 노출된다. 
   - 설정을 통해 JMX를 통해서도 노출시킬 수 있다.
```
      GET /application/fruits:  fruits를 전달
      POST /applications/fruits/{a-fruit}:  payload에 포함된 fruit를 다룸
```
   - 위의 예시 외에도 다양하게 적용할 수 있다. 
   - 더 세분화된 데이터를 불러올 수도 있고, 기반 기술에 따라 구체적인 구현을 정의할 수도 있다. (예를 들어, JMX vs. Web 처럼).
   - 더 깊이 들어가면 이 글의 목적에 어긋나므로, 관련 설명은 이정도로 마치겠다.
    
  -  Actuator의 security
     - 스프링부트 1.x버전의 actuator는 자신만의 security 모델을 정의함. 
     - 이 security 모델은 애플리케이션에서 사용되는 것과는 좀 다르다. 이로 인해, 사용자가 security 모델을 수정할 때마다 큰 부담이 따른다. 
     - 스프링부트 2.x 버전에서 security 설정은 애플리케이션에서 사용하는 설정에 따라 규정된다. 
     - 기본적으로 대부분의 actuator의 endpoint들은 비활성화 되어있다. 
     - classpath에 Spring Security가 있던 없던 상관없다. 
     - status와 info외에 모든 endpoint들은 사용자에 의해 활성화되어야 한다.

  - 이 밖의 변화들
     - 대부분의 설정 속성들은 management.xxx에 들어간다. ex)management.endpoints.jmx
     - 일부 endpoint들은 새로운 포맷을 가진다. ex) flyway, liquidbase 등
     - 미리 정의된 endpoint 경로는 더이상 설정가능하지 않다.

5. 개선된 개발 경험

  - 더 나은 피드백
     - 스프링부트는 devtools를 1.3버전에서 소개했다.
     - devtools는 뷰 키술들을 캐싱하는 것과 같은 일반적인 개발 이슈들을 다루며, 자동 실행과 브라우저에서의 실시간 리로딩을 수행한다. 
     - 또한 remote 디버깅을 할 수 있게 해준다. 
     - 스프링부터 2.x 버전에서 devtools를 통해 애플리케이션이 재시작되면, 'delta' 리포트가 출력된다. 
     - 이 리포트는 애플리케이션에서 어떤 부분이 변경되어 영향을 미쳤는지를 알려준다.
     - 스프링부트에 의해 인식된 하나의 JDBC Datasource를 정의했다고 하자. 
        - devtools는 자동으로 인식된 datasource가 생성되지 않았다고 알려줄 것이다. 
        - 또한, devtools는 javax.sql.DataSource 타입에 대한 @ConditionalOnMissingBean과의 부적절한 연결을 원인으로 지적할 것이다. 
        - devtools는 애플리케이션이 재시작할 때마다 이 리포트를 출력할 것이다.
  - 큰 변화
     - JDK 9 이슈로 인해서, devtools는 HTTP를 통한 원격 디버깅 지원을 중단했다.

6. 요약

  - 이 글에서는 스프링부트2가 가져올 일부 변화들을 살펴봤다. 
  - 우리는 의존성과 어떻게 java8이 최소 요구사항이 되었는지 다루었다. 
  - 다음으로 자동구성에 대해 얘기했고, security에 대해서도 알아봤다. 
  - 또한, actuator와 관련된 다양한 개선점들을 확인했다. 
  - 마지막으로, 개발툴에서의 작은 변화들도 살펴보았다.
