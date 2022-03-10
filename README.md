<h1> 🌱 스프링 핵심 원리 - 기본편</h1>

> 내용 정리

<details>
<summary>Table of Contents</summary>

- [IntelliJ 단축키 정리](#intellij-단축키-정리)
- [1. 회원 도메인 개발](#1-회원-도메인-개발)
  - [`코드1`의 문제점 🤔](#코드1의-문제점-)
  - [TIL 💡](#til-)
- [2. 회원 도메인 실행과 테스트](#2-회원-도메인-실행과-테스트)
  - [애플케이션 로직을 구현 후 테스트](#애플케이션-로직을-구현-후-테스트)
  - [`JUnit`을 이용해서 테스트 ❗️](#junit을-이용해서-테스트-️)
- [3. 주문과 할인 도메인 개발](#3-주문과-할인-도메인-개발)
  - [`코드2`의 설계](#코드2의-설계)
- [4. 관심사 분리](#4-관심사-분리)
  - [좋은 객체 지향 설계의 5가지 원칙의 적용](#좋은-객체-지향-설계의-5가지-원칙의-적용)
    - [SRP(Single Responsiblilty Principle) 🔗](#srpsingle-responsiblilty-principle-)
    - [DIP(Dependency Inversion Principle) 🔗](#dipdependency-inversion-principle-)
    - [OCP(Open-Closed Prinicple) 🔗](#ocpopen-closed-prinicple-)
  - [IoC(제어의 역전), DI(의존관계 주입), 그리고 컨테이너](#ioc제어의-역전-di의존관계-주입-그리고-컨테이너)
    - [제어의 역전(Inversion of Control, IoC) 🔗](#제어의-역전inversion-of-control-ioc-)
    - [의존관계 주입(Dependency Injection, DI) 🔗](#의존관계-주입dependency-injection-di-)
    - [IoC 컨테이너, DI 컨테이너 🔗](#ioc-컨테이너-di-컨테이너-)
- [5. 스프링으로 전환](#5-스프링으로-전환)
  - [스프링 컨테이너](#스프링-컨테이너)
  - [BeanFactory와 ApplicationContext](#beanfactory와-applicationcontext)
  - [스프링 빈 설정 메타 정보 - BeanDefinition](#스프링-빈-설정-메타-정보---beandefinition)
- [6. 싱글톤 컨테이너](#6-싱글톤-컨테이너)
  - [순수한 DI 컨테이너](#순수한-di-컨테이너)
  - [싱글톤 패턴](#싱글톤-패턴)
  - [싱글톤 컨테이너](#싱글톤-컨테이너)
  - [싱글톤 방식의 주의점](#싱글톤-방식의-주의점)
- [8. 의존관계 자동 주입](#8-의존관계-자동-주입)
  - [다양한 의존관계 주입 방법](#다양한-의존관계-주입-방법)
    - [생성자 주입](#생성자-주입)
    - [수정자 주입(Setter 주입)](#수정자-주입setter-주입)
    - [필드 주입](#필드-주입)
    - [일반 메서드 주입](#일반-메서드-주입)
  - [옵션처리](#옵션처리)
  - [조회 빈이 2개 이상 - 문제](#조회-빈이-2개-이상---문제)
  - [조회한 빈이 모두 필요할 때](#조회한-빈이-모두-필요할-때)
- [9. 빈 생명주기 콜백](#9-빈-생명주기-콜백)
</details>

---
## IntelliJ 단축키 정리
- `⌘ + ⇧ + ⏎`
  - 자동 완성과 동시에 `;`를 찍어줌
- `⌘ + ⇧ + T` 
  - 테스트 코드 자동 생성
- `⌘ + ⌥ + V`
  - 변수 추출
- `⌘ + ⌥ + M`
  - 메소드 추출
- `⌘ + E`
  - 최근 사용된 파일들을 볼 수 있음
- `iter + ⇥`
  - 리스트와 같은 배열들의 for 문을 자동으로 완성시켜줌


## 1. 회원 도메인 개발
```java
// 코드1
public class MemberServiceImpl implements MemberService{

    private final MemberRepository memberRepository = new MemoryMemberRepository();
}
```
### `코드1`의 문제점 🤔
- 회원 저장소를 확장하면 회원 서비스 구현체 수정이 필수적이므로 **OCP** 위반 
- 회원 서비스는 추상화도 의존하고 구현체도 의존하기 때문에 **DIP** 위반

### TIL 💡
- `enum`은 member entity 에 구현하지 않고 새로운 파일을 만들어 구현

## 2. 회원 도메인 실행과 테스트
### 애플케이션 로직을 구현 후 테스트
```java
public class MemberApp {

    public static void main(String[] args) {
        MemberService memberService = new MemberServiceImpl();
        Member member = new Member(1L, "memberA", Grade.VIP);
        memberService.join(member);

        Member findMember = memberService.findMember(1L);
        System.out.println("new member = " + member.getName());
        System.out.println("find Member = " + findMember.getName());
    }
}
```
- 서비스가 아주 커진다면 애플리케이션 로직을 메인 메소드로 테스트하는데 한계가 존재함

### `JUnit`을 이용해서 테스트 ❗️
```java
package hello.core.member;

import org.assertj.core.api.Assertions;
import org.junit.jupiter.api.Test;

public class MemberServiceTest {

    MemberService memberService = new MemberServiceImpl();

    @Test
    void join() {
        // given
        Member member = new Member(1L, "MemberA", Grade.VIP);

        // when
        memberService.join(member);
        Member findMember = memberService.findMember(member.getId());

        // then
        Assertions.assertThat(member).isEqualTo(findMember);
    }
}
```
- **Given-When-Then** Pattern (준비 - 실행 - 검증)
  - `given`: 준비하는 과정
  - `when`: 실제로 액션을 하는 테스트를 실행하는 과정
  - `then`: 테스트를 검증하는 과정
- 검증은 `assertj`의 `Assertions`를 사용
  - `assertThat`과 `isEqualTo`가 같다면 Run 창에 초록불이 들어온다
  - `assertThat`과 `isEqualTo`가 다르거나 오류가 발생한다면 Run 창에 빨간불이 들어온다
  
~~Clean Code 에서 다루는 단위 테스트에 대한 내용을 다시 읽어봐야겠다.~~

## 3. 주문과 할인 도메인 개발
```java
// 코드2
public interface DiscountPolicy {

    /**
     * @return 할인 대상 금액
     */
    int discount(Member member, int price);
}

public class FixDiscountPolicy implements DiscountPolicy {

    private int discountFixAmount = 1000;

    @Override
    public int discount(Member member, int price) {
        if (member.getGrade() == Grade.VIP) {
            return discountFixAmount;
        } else {
            return 0;
        }
    }
}


public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();
    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
}
```
### `코드2`의 설계
- `DiscountPolicy`는 할인에 관련된 책임만 가지고 있고, `OrderService`는 주문과 관련된 책임만 가지고 있다.   
  ⇒ 각 클래스는 한 가지 책임만 가지고 있기에 **SRP**를 지키고 있다.
- 하지만 `코드1`와 같이 확장 된다면 **OCP**, **DIP**를 위반한다.

## 4. 관심사 분리
- 기존 코드
```java
public class MemberServiceImpl implements MemberService {

  private final MemberRepository memeberRepository = new MemboryMemberRespository();
}

public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();
    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
}
```
- 관심사를 분리한 코드
```java
// AppConfig.java
package hello.core;

import hello.core.discount.RateDiscountPolicy;
import hello.core.member.MemberService;
import hello.core.member.MemberServiceImpl;
import hello.core.member.MemoryMemberRepository;
import hello.core.order.OrderService;
import hello.core.order.OrderServiceImpl;

public class AppConfig {

    public MemberService memberService() {
        return new MemberServiceImpl(new MemoryMemberRepository());
    }

    public OrderService orderService() {
        return new OrderServiceImpl(new MemoryMemberRepository(), new RateDiscountPolicy());
    }
}

// MemberServiceImpl.java
public class MemberServiceImpl implements MemberService {

    private final MemberRepository memberRepository;

    public MemberServiceImpl(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }
}

// OrderServiceImpl.java
public class OrderServiceImpl implements OrderService{

    private final MemberRepository memberRepository;
    private final DiscountPolicy discountPolicy;

    public OrderServiceImpl(MemberRepository memberRepository,
        DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
    }
}
```
- 위와 같이 관심사를 분리하면 인터페이스는 추상화만 의존하기 때문에 **DIP**를 만족한다.
- 만약 확장을 하더라도 의존성 주입으로 인해 **사용 영역**(클라이언트 코드)은 변경없이 **구성 역역**(`AppConfig`)만 수정하면 되므로 **OCP**를 만족한다.
- 클라이언트 코드는 의존관계에 대한 책임을 덜고 기능에만 책임을 가진다.

~~의존성 주입을 공부한 후 정리 필요~~

### 좋은 객체 지향 설계의 5가지 원칙의 적용
현재까지 **SRP**, **DIP**, **OCP** 적용

#### SRP(Single Responsiblilty Principle) 🔗
**한 클래스는 하나의 책임만 가져야 한다.**
- 클라이언트 객체는 직접 구현 객체를 생성하고, 연결하고, 실행하는 다양한 책임을 가지고 있음
- SRP를 따르면서 관심사를 분리
- 구현 객체를 생성하고 연결하는 책임은 `AppConfig`가 담당
- 클라이언트 객체는 실행하는 책임만 담당

#### DIP(Dependency Inversion Principle) 🔗
**프로그래머는 "추상화에 의존해야지, 구체화에 의존하면 안된다." 의존성 주입은 이 원칙을 따르는 방법 중 하나다.**
- 기존 클라이언트 코드는 추상화 인터페이스에 의존하지만, 구체화 구현 클래스도 함께 의존했음
- 관심사 분리 후 클라이언트 코드는 추상화 인터페이스에만 의존

#### OCP(Open-Closed Prinicple) 🔗
**소프트웨어 요소는 확장은 열려있고 변경에는 닫혀 있어야 한다.**
- 다형성을 사용하고 클라이언트가 DIP를 지킴
- 애플리케이션을 사용 영역과 구성 영역으로 나눔
- `AppConfig`가 의존 관계를 클라이언트 코드에 주입하므로 클라이언트 코드는 변경하지 않아도 됨
- 따라서 **소프트웨어 요소를 새롭게 확장해도 사용 역영의 변경은 닫혀있다.**

### IoC(제어의 역전), DI(의존관계 주입), 그리고 컨테이너
#### 제어의 역전(Inversion of Control, IoC) 🔗
- 리팩토리전 프로그램은 클라이언트 구현 객체가 스스로 필요한 서버 구현 객체를 생성하고, 연결하고 실행한다. 즉, 구현 객체가 프로그램의 제어 흐름을 스스로 조종했다.
- 관심사 분리 후 구현 객체는 자신의 로직만 수행하는 역할만 담당하고, 프로그램의 제어 흐름은 `AppConfig`가 가져간다.
- 이렇듯 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는 것을 제어의 역전(IoC)라 한다.

**프레임워크 vs 라이브러리**
- 프레임워크가 프로그래머가 작성한 코드를 제어하고, 대신 실행하면 그것은 프레임워크다. ex) JUnit
- 프로그래머가 작성한 코드를 직접 제어의 흐름을 담당한다면, 그것은 라이브러리다.

#### 의존관계 주입(Dependency Injection, DI) 🔗
- `OrderServiceImpl`은 `DiscountPolicy` 인터페이스에 의존한다. 실제 어떤 구현 객체가 사용될지는 모름
- 의존관계는 **정적인 클래스 의존 관계와 실행 시점에는 결정되는 동적인 인스턴스 의존 관계** 둘을 분리해서 생각해야 함

**정적인 클래스 의존 관계**   
클래스가 사용하는 `import` 코드만 보고 의존 관계를 쉽게 판단할 수 있다. 정적인 의존 관계는 애플리케이션을 실행하지 않아도 분석할 수 있다.

클래스 다이어그램

<img width="530" alt="image" src="https://user-images.githubusercontent.com/45463495/156312530-35a6faef-4fd8-4d86-9e67-1cc8e1d21483.png">

- `OrderServiceImpl`은 `MemberRepository`, `DiscountPolicy`에 의존한다는 것을 알 수 있음
- 하지만 이러한 클래스 의존 관계만으로는 실제 어떤 객체가 `OrderServiceImpl`에 주입될지 알 수 없음

**동적인 객체 인스턴스 의존 관계**   
애플리케이션 실행 시점에 실제 생성된 객체 인스턴스의 참조가 연결된 의존 관계

객체 다이어그램

<img width="530" alt="image" src="https://user-images.githubusercontent.com/45463495/156313379-20e8c597-42dd-45e6-990a-f1fec811827e.png">

- 애플리케이션 실행 시점에 외부에서 실제 구현 객체를 생성하고 클라이언트에 전달해서 클라이언트와 서버의 실제 의존 관계가 연결되는 것을 **의존관계 주입**이라 한다.
- 의존관계 주입을 사용하면 클라이언트 코드를 변경하지 않고, 클라이언트가 호출하는 대상의 타입 인스턴스를 변경 가능
- 의존관계 주입을 사용하면 **정적인 클래스 의존관계를 변경하지 않고, 동적인 객체 인스턴스 의존관계를 쉽게 변경 가능**

#### IoC 컨테이너, DI 컨테이너 🔗
- `AppConfig`처럼 객체를 생성하고 관리하면서 의존관계를 연결해주는 것을 IoC 컨테이너, **DI 컨테이너**라 한다.
- 의존관계 주입에 초점을 맞춰 최근에는 주로 DI 컨테이너라 한다.

## 5. 스프링으로 전환
```java
@Configuration
public class AppConfig {

    @Bean
    public MemberService memberService() {
        return new MemberServiceImpl(memberRepository());
    }

    @Bean
    public OrderService orderService() {
        return new OrderServiceImpl(memberRepository(), discountPolicy());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }

    @Bean
    public DiscountPolicy discountPolicy() {
        return new RateDiscountPolicy();
    }
}

```
- `AppConfig`에 설정을 구성한다는 뜻의 `@Configuration`을 붙여줌
- 각 메서드에 `@Bean`을 붙여줌 -> 스프링 컨테이너에 스프링 빈으로 등록

### 스프링 컨테이너
- `ApplicationContext`를 스프링 컨테이너라 한다.
- 기존에는 개발자가 `AppConfig`를 직접 객체를 생성하고, 의존성을 주입했지만, 이제부터 스프링 컨테이너를 통해서 사용한다.
- 스프링 컨테이너는 `@Configuration`이 붙은 `AppConfig`를 구성 정보로 사용
- `@Bean`이라 적힌 메서드를 모두 호출하여 반환된 객체를 스프링 컨테이너를 등록한다. 이렇게 스프링 컨테이너에 등록된 객체를 스프링 빈이라 함

**스프링 컨테이너의 생성 과정**

1. 스프링 컨테이너 생성
```java
ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
```
- 스프링 컨테이너를 생성할 때는 구성 정보를 지정해주어야 함

2. 스프링 빈 등록
![](https://user-images.githubusercontent.com/45463495/156500577-f15e775b-b7e5-46b6-8181-9213b88b303b.png)   
- 스프링 컨테이너는 파라미더로 넘어온 설정 클래스 정보를 사용해서 스프링 빈을 등록

💡 빈 이름
- 메서드 이름을 사용
- 직접 부여 가능
  - `@Bean(name="ms")`
- 빈 이름은 항상 다른 이름을 부여해야 함

3. 스프링 빈 의존관계 설정

준비|완료
:--:|:--:
![image](https://user-images.githubusercontent.com/45463495/156500909-a5ff20f2-1d0f-456c-a1cb-d07b39549737.png)|![image](https://user-images.githubusercontent.com/45463495/156500969-981c546e-330b-47e1-8fa7-b6a7465a78cd.png)
- 스프링 컨테이너는 설정 정보를 참고해서 의존관계를 주입

**컨테이너에 등록된 모든 빈 조회**
```java
AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);

@Test
@DisplayName("모든 빈 출력")
void findAllBean() {
    String[] beanDefinitionNames = ac.getBeanDefinitionNames();
    for (String beanDefinitionName : beanDefinitionNames) {
        Object bean = ac.getBean(beanDefinitionName);
        System.out.println("name = " + beanDefinitionName + " Object = " + bean);
    }
}

@Test
@DisplayName("애플리케이션 빈 출력")
void findApplicationBean() {
    String[] beanDefinitionNames = ac.getBeanDefinitionNames();
    for (String beanDefinitionName : beanDefinitionNames) {
        BeanDefinition beanDefinition = ac.getBeanDefinition(beanDefinitionName);

        if (beanDefinition.getRole() == BeanDefinition.ROLE_APPLICATION) {
            Object bean = ac.getBean(beanDefinitionName);
            System.out.println("name = " + beanDefinitionName + " Object = " + bean);
        }
    }
}

@Test
@DisplayName("빈 이름을 조회")
void findBeanByName() {
    MemberService memberService = ac.getBean("memberService", MemberService.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
}

@Test
@DisplayName("타입으로만 조회")
void findBeanByType() {
    MemberService memberService = ac.getBean(MemberService.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
}

@Test
@DisplayName("구체 타입으로 조회")
void findBeanByName2() {
    MemberService memberService = ac.getBean("memberService", MemberServiceImpl.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
}

@Test
@DisplayName("빈 이름으로 조회X")
void findBeanByNameX() {
    // MemberService xxx = ac.getBean("xxx", MemberService.class);
    assertThrows(NoSuchBeanDefinitionException.class,
        () -> ac.getBean("xxx", MemberService.class));
}

@Test
@DisplayName("타입으로 조회 시 같은 타입이 둘 이상 있으면, 중복 오류 발생")
void findBeanByTypeDuplicate() {
//        ac.getBean(MemberRepository.class);
    assertThrows(NoUniqueBeanDefinitionException.class, () -> ac.getBean(MemberRepository.class));
}

@Test
@DisplayName("타입으로 조회 시 같은 타입이 둘 이상 있으면, 빈 이름을 지정하면 된다")
void findBeanByName() {
    MemberRepository memberRepository = ac.getBean("memberRepository1",
        MemberRepository.class);
    assertThat(memberRepository).isInstanceOf(MemberRepository.class);
}

@Test
@DisplayName("특정 타입 모두 조회하기")
void findAllBeanByType() {
    Map<String, MemberRepository> beansOfType = ac.getBeansOfType(MemberRepository.class);
    for (String key : beansOfType.keySet()) {
        System.out.println("key = " + key + " value = " + beansOfType.get(key));
    }
    System.out.println("beansOfType = " + beansOfType);
    assertThat(beansOfType.size()).isEqualTo(2);
}

@Configuration
static class SameBeanConfig {

    @Bean
    public MemberRepository memberRepository1() {
        return new MemoryMemberRepository();
    }

    @Bean
    public MemberRepository memberRepository2() {
        return new MemoryMemberRepository();
    }

}
```
- 모든 빈 출력
  - 스프링에 등록된 모든 빈 정보를 출력
  - `getBeanDefinitionNames()` : 스프링에 등록된 모든 빈 이름 조회
  - `getBean()` : 빈 이름으로 빈 객체(인스턴스) 조회
- 애플리케이션 빈 출력
  - `getRole()` : 스프링이 내부에서 사용하는 빈을 구분
    - `ROLE_APPLICATION` : 사용자가 정의한 빈
    - `ROLE_INFRASTRUCTURE` : 스프링 내부에서 사용하는 빈
- 동일한 타입이 두 개이상일 경우
  - `getBeansOfType()` 사용
    - 해당 타입에 모든 빈을 조회할 수 있음

### BeanFactory와 ApplicationContext
![](https://user-images.githubusercontent.com/45463495/156716543-dc4f4b08-2668-4bea-8be8-a0a6233f7408.png)

**BeanFactory**
- 스프링 컨테이너의 최상위 인터페이스
- 스프링 빈을 관리하고 조회하는 역할 담당
- `getBean()` 제공

**AppplicationContext**
- BeanFactory 기능을 모두 상속받아서 제공
- 애플리케이션을 개발할 때는 빈을 관리하고 조회하는 기능은 물론이고, 수 많은 부가기능이 필요
- AppplicationContext가 제공하는 부가기능
  - 메시지소스를 활요한 국제화 기능
    - ex) 한국에서 들어오면 한국어, 영어권에서 들어오면 영어로 출력
  - 환경변수
    - 로컬, 개발, 운영들을 구분해서 처리
  - 애플리케이션 이벤트
    - 이벤트를 발행하고 구독하는 모델을 편리하게 지원
  - 편리한 리소스 조회
    - 파일, 클래스패스, 외부 등에서 리소스를 편리하게 조회

### 스프링 빈 설정 메타 정보 - BeanDefinition
**BeanDefinition** 정보
- BeanClassName : 생성할 빈의 클래스 명
- factoryBeanName : 팩토리 역할의 빈을 사용할 경우 이름
- factoryMethodName: 빈을 생성할 팩토리 메서드 지정
- Scope : 싱글톤(기본 값)
- lazyInt : 스프링 컨테이너를 생성할 때 빈을 생성하는 것이 아니라, 실제 빈을 사용할 때까지 최대한 생성을 지연처리 하는 지 여부
- InitMethodName : 빈을 생성하고, 의존관계를 적용한 뒤에 호출되는 초기화 메서드 명
- DestoryMethodName : 빈의 생명주기가 끝나서 제거하기 직전에 호출되는 메서드 명
- Constructor arguments, Properties : 의존관계 주입에서 사용

## 6. 싱글톤 컨테이너
### 순수한 DI 컨테이너
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/156974101-08e832ed-cfda-421c-8919-3d151fd8bf3f.png">

- 고객이 요청을 할 때마다 객체를 새로 생성함 -> 메모리 낭비가 심함

### 싱글톤 패턴
- 클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴
- 싱글톤 패턴의 단점
  - 구현하는 코드 자체가 많이 들어감
  - 의존관계상 클라이언트가 구체 클래스의 의존 -> DIP 위반, OCP 위반할 가능성이 높음
  - 테스트가 어려움
  - 내부 속성을 변경하거나 초기화가 어려움
  - private 생성자로 자식 클래스를 만들기 어려움
  - 유연성이 떨어짐

### 싱글톤 컨테이너
- 싱글톤 패턴을 적용하지 않아도 객체 인스턴스를 싱글톤으로 관리

**싱글톤 컨테이너 적용 후**   
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/156974175-b450142e-6803-4a1b-974c-74d2292fa69f.png">

- 스프링 컨테이너 덕분에 고객이 요청이 올 때 마다 객체를 생성하는 것이 아니라, 이미 만들어진 객체를 공유해서 효율적으로 재사용할 수 있음

### 싱글톤 방식의 주의점
- 객체 인스턴스를 하나만 생성해서 공유하는 싱글톤 방식은 여러 클라이언트가 하나의 같은 객체 인스턴스를 공유하기 때문에 싱글톤 객체는 상태를 유지하게 설계하면 안된다.
- 무상태로 설계해야 한다.
  - 특정 클라이언트에 의존적인 필드가 있으면 안됨
  - 특정 클라이언트가 값을 변경할 수 있는 필드가 있으면 안됨
  - 가급적 읽기만 가능해야 함
  - 필드 대신 자바에서 공유되지 않는 지역변수, 파라미터, ThreadLocal 등을 사용
- 스프링 빈의 필드에 공유 값을 설정하면 큰 장애가 발생할 수 있음

**예시**
```java
package hello.core.singleton;

public class StateFulService {

    private int price; // 상태를 유지하는 필드

    public void order(String name, int price) {
        System.out.println("name = " + name + " price = " + price);
        this.price = price; // 여기가 문제
    }

    public int getPrice() {
        return price;
    }
}


package hello.core.singleton;

import static org.assertj.core.api.Assertions.assertThat;
import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.context.annotation.Bean;

class StateFulServiceTest {

    @Test
    void stateFulServiceSingleton() {
        ApplicationContext ac = new AnnotationConfigApplicationContext(TestConfig.class);

        StateFulService stateFulService1 = ac.getBean(StateFulService.class);
        StateFulService stateFulService2 = ac.getBean(StateFulService.class);


        // ThreadA: A 사용자 1000원 주문
        stateFulService1.order("userA", 1000);
        // ThreadB: B 사용자 2000원 주문
        stateFulService2.order("userB", 2000);

        // ThreadA: 사용자 A 주문 금액 조회
        int price = stateFulService1.getPrice();
        System.out.println("price = " + price);

        assertThat(stateFulService1.getPrice()).isEqualTo(2000);
    }

    static class TestConfig {

        @Bean
        public StateFulService stateFulService() {
            return new StateFulService();
        }
    }
}
```

## 8. 의존관계 자동 주입
### 다양한 의존관계 주입 방법
- 생성자 주입
- 수정자 주입(setter 주입)
- 필드 주입
- 일반 메서드 주입

#### 생성자 주입
- 생성자를 통해서 의존 관계를 주입하는 방법
- 생성자 호출 시점에 딱 1번만 호출되는 것이 보장됨
- **불변**, **필수** 의존관계에 사용
- 생성자가 하나만 있다면 `@Autowired` 생략 가능
```java
@Component
public class OrderServiceImpl implements OrderService {
    private final MemberRepository memberRepository;
    private final DiscountPolicy discountPolicy;
    
    @Autowired
    public OrderServiceImpl(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
    }
}
```

#### 수정자 주입(Setter 주입)
- setter라 불리는 필드의 값을 변경하는 수정자 메서드를 통새서 의존관계를 주입하는 방법
- **선택**, **변경** 가능성이 있는 의존관계에 사용
- 자바빈 프로퍼티 규약의 수정자 메서드 방식을 사용하는 방법
```java
@Component
public class OrderServiceImpl implements OrderService {
  
    private MemberRepository memberRepository;
    private DiscountPolicy discountPolicy;

    @Autowired
    public void setMemberRepository(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }

    @Autowired
    public void setDiscountPolicy(DiscountPolicy discountPolicy) {
        this.discountPolicy = discountPolicy;
    }
}
```

#### 필드 주입
- 필드에 바로 주입하는 방법
- 외부에서 변경이 불가능하므로 테스트 하기 힘듦
- DI 프레임워크가 없으면 아무것도 할 수 없음
- 사용 용도
  - 애플리케이션의 실제 코드와 관계 없는 테스트 코드
  - 스프링 설정을 목적으로 하는 `@Configuration` 같은 곳에서만 특별한 용도로 사용

```java
@Component
public class OrderServiceImpl implements OrderService {
    
    @Autowired
    private MemberRepository memberRepository;
    
    @Autowired
    private DiscountPolicy discountPolicy;
  }
```

#### 일반 메서드 주입
- 일반 메서드를 통해서 주입
- 한번에 여러 필드를 주입 받을 수 있음
- 일반적으로 잘 사용하지 않음

```java
@Component
public class OrderServiceImpl implements OrderService {

    private MemberRepository memberRepository;
    private DiscountPolicy discountPolicy;
    
    @Autowired
    public void init(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
    }
}
```

### 옵션처리
주입할 스프링 빈이 없어도 동작해야 할 때가 있을 때 `@Autowired`만 사용하면 `required` 옵션의 기본 값이 `true`로 되어 있어 자동 주입 대상이 없으면 오류가 발생한다.

자동 주입 대상을 옵션으로 처리하는 방법
- `@Autowired(required=false)`: 자동 주입할 대상이 없으면 수정자 메서드 자체가 호출 안됨
- `@Nullable`: 자동 주입할 대상이 없으면 null이 입력됨
- `Optional<>`: 자동 주입할 대상이 없으면 `Optional.empty`가 입력됨

**정리**
- 생성자 주입 방식을 선택하는 이유는 여러가지가 있지만, 프레임워크에 의존하지 않고, 순수한 자바 언어의 특징을 잘 살리는 방법
- 기본으로 생성자 주입을 사용하고, 필수 값이 아닌 경우는 수정자 주입 방식을 옵션으로 부여
  - 생성자 주입과 수정자 주입 동시 사용 가능
- 항상 생성자 주입을 선택

**Lombok**
```gradle
//lombok 설정 추가 시작
configurations {
	compileOnly {
		extendsFrom annotationProcessor
	}
}
//lombok 설정 추가 끝

//lombok 라이브러리 추가 시작
compileOnly 'org.projectlombok:lombok'
annotationProcessor 'org.projectlombok:lombok'

testCompileOnly 'org.projectlombok:lombok'
testAnnotationProcessor 'org.projectlombok:lombok'
//lombok 라이브러리 추가 끝
```
라이브러리 적용 방법
1. Preferneces -> plugin -> lombok 검색 설치 실행
2. Preferneces -> Annotation Processors 검색 -> Enable annotation processing 체크

**Lombok을 적용한 코드**
```java
@Component
@RequiredArgsConstructor
public class OrderServiceImpl implements OrderService{

    private final MemberRepository memberRepository;
    private final DiscountPolicy discountPolicy;
}
```

### 조회 빈이 2개 이상 - 문제
`@Autowired`는 타입으로 조회한다. 타입으로 조회하면 선택된 빈이 2개 이상일 때 문제가 발생한다.   
`DiscountPolicy`의 하위 타입인 `FixDiscountPolicy`, `RateDiscountPolicy` 둘 다 스프링 빈으로 선언하면 `NoUniqueBeanDefinitionException` 오류가 발생한다.

**해결 방법**
- `@Autowired` 필드 명 매칭
  - `@Autowired`는 타입 매칭을 시도하고, 이때 여러 빈이 있으면 필드 이름, 파라미터 이름으로 빈 이름을 추가 매칭한다.
- `@Qualifier` 사용
  - 추가 구분자를 붙여주는 방법
- `@Primary`
  - 우선순위를 정하는 방법

### 조회한 빈이 모두 필요할 때
```java
package hello.core.autowired;

import static org.assertj.core.api.Assertions.assertThat;

import hello.core.AutoAppConfig;
import hello.core.discount.DiscountPolicy;
import hello.core.member.Grade;
import hello.core.member.Member;
import java.util.List;
import java.util.Map;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class AllBeanTest {

    @Test
    void findAllBean() {
        ApplicationContext ac = new AnnotationConfigApplicationContext(AutoAppConfig.class, DiscountService.class);

        DiscountService discountService = ac.getBean(DiscountService.class);
        Member member = new Member(1L, "userA", Grade.VIP);
        int discountPrice1 = discountService.discount(member, 10000, "fixDiscountPolicy");

        assertThat(discountService).isInstanceOf(DiscountService.class);
        assertThat(discountPrice1).isEqualTo(1000);

        int discountPrice2 = discountService.discount(member, 20000, "rateDiscountPolicy");
        assertThat(discountPrice2).isEqualTo(2000);
    }

    static class DiscountService {
        private final Map<String, DiscountPolicy> policyMap;
        private final List<DiscountPolicy> policies;

        @Autowired
        public DiscountService(
            Map<String, DiscountPolicy> policyMap,
            List<DiscountPolicy> policies) {
            this.policyMap = policyMap;
            this.policies = policies;
            System.out.println("policyMap = " + policyMap);
            System.out.println("policies = " + policies);
        }

        public int discount(Member member, int price, String discountCode) {
            DiscountPolicy discountPolicy = policyMap.get(discountCode);
            return discountPolicy.discount(member, price);
        }
    }
}
```

## 9. 빈 생명주기 콜백
**스프링 빈의 lifecycle**
1. 객체 생성
2. 의존관계 주입

**스프링 빈의 이벤트 lifecycle**
1. 스프링 컨테이너 생성
2. 스프링 빈 생성
3. 의존관계 주입
4. 초기화 콜백
5. 사용
6. 소멸전 콜백
7. 스프링 종료

- **초기화 콜백**: 빈이 생성되고, 빈의 의존관계 주입이 완료된 후 호출
- **소멸전 콜백**: 빈이 소멸되기 직전에 호출

> 💡 **객체의 생성과 초기화를 분리하자**   
> 생성자는 필수 정보(파라미터)를 받고 메모리를 할당해서 객체를 생성하는 책임을 가진다. 반면에 초기화는 이렇게 생성된 값들을 활용해서 외부 커넥션을 연결하는 등 무거운 동작을 수행한다. 따라서 생성자 안에서 무거운 초기화 작업을 함께 하는 것보다 객체를 생성하는 부분과 초기화 하는 부분을 명확하게 나누는 것이 유지보수에서 관점에서 좋다. 물론 초기화 작업이 부 값들만 약간 변경하는 정도로 단순한 경우에는 생성자에서 한번에 다 처리하는게 더 나을 수 있다.

**스프링의 빈 생명주기 콜백**
- 인터페이스 (`InitializingBean`, `DisposableBean`)
  - 스프링 전용 인터페이스
  - 스프링 전용 인터페이스에 의존
  - 초기화, 소멸 메서드의 이름을 변경할 수 없음
  - 외부 라이브러리에 적용을 할 수 없음
- 설정 정보에 초기화 메서드, 종료 메서드 지정
  - 메서드 이름을 자유롭게 줄 수 있음
  - 스프링 코드에 의존하지 않음
  - 설정 정보를 사용하기 때문에 외부 라이브러리에도 초기화, 종료 메서드를 적용 할 수 있음
- `@PostConstruct`, `@PreDestroy`
  - 자바 표준이기때문에 스프링에 종속적이지 않음
  - 외부 라이브러리에는 적용을하지 못함