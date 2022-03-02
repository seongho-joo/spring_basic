<h1> 🌱 스프링 핵심 원리 - 기본편</h1>

> 내용 정리

<details>
<summary>Table of Contents</summary>

- [1. 회원 도메인 개발](#1-회원-도메인-개발)
  - [`코드1`의 문제점 🤔](#코드1의-문제점-)
  - [TIL 💡](#til-)
- [2. 회원 도메인 실행과 테스트](#2-회원-도메인-실행과-테스트)
  - [애플케이션 로직을 구현 후 테스트](#애플케이션-로직을-구현-후-테스트)
  - [`JUnit`을 이용해서 테스트 ❗️](#junit을-이용해서-테스트-️)
- [3. 주문과 할인 도메인 개발](#3-주문과-할인-도메인-개발)
  - [`코드2`의 설계](#코드2의-설계)
</details>

---
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
- 자동 완성을 이용할 경우 `⌘` + `⇧` + `⏎` 단축키를 이용하면 `;`까지 자동으로 찍힘

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

public class FixDiscountPolicy implements DiscountPolicy{

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


public class OrderServiceImpl implements OrderService{

    private final MemberRepository memberRepository = new MemoryMemberRepository();
    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
}
```
### `코드2`의 설계
- `DiscountPolicy`는 할인에 관련된 책임만 가지고 있고, `OrderService`는 주문과 관련된 책임만 가지고 있다.   
  ⇒ 각 클래스는 한 가지 책임만 가지고 있기에 **SRP**를 지키고 있다.
- 하지만 `코드1`와 같이 확장 된다면 **OCP**, **DIP**를 위반한다.
