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