<h1> ๐ฑ ์คํ๋ง ํต์ฌ ์๋ฆฌ - ๊ธฐ๋ณธํธ</h1>

> ๋ด์ฉ ์ ๋ฆฌ

<details>
<summary>Table of Contents</summary>

- [IntelliJ ๋จ์ถํค ์ ๋ฆฌ](#intellij-๋จ์ถํค-์ ๋ฆฌ)
- [1. ํ์ ๋๋ฉ์ธ ๊ฐ๋ฐ](#1-ํ์-๋๋ฉ์ธ-๊ฐ๋ฐ)
  - [`์ฝ๋1`์ ๋ฌธ์ ์  ๐ค](#์ฝ๋1์-๋ฌธ์ ์ -)
  - [TIL ๐ก](#til-)
- [2. ํ์ ๋๋ฉ์ธ ์คํ๊ณผ ํ์คํธ](#2-ํ์-๋๋ฉ์ธ-์คํ๊ณผ-ํ์คํธ)
  - [์ ํ์ผ์ด์ ๋ก์ง์ ๊ตฌํ ํ ํ์คํธ](#์ ํ์ผ์ด์-๋ก์ง์-๊ตฌํ-ํ-ํ์คํธ)
  - [`JUnit`์ ์ด์ฉํด์ ํ์คํธ โ๏ธ](#junit์-์ด์ฉํด์-ํ์คํธ-๏ธ)
- [3. ์ฃผ๋ฌธ๊ณผ ํ ์ธ ๋๋ฉ์ธ ๊ฐ๋ฐ](#3-์ฃผ๋ฌธ๊ณผ-ํ ์ธ-๋๋ฉ์ธ-๊ฐ๋ฐ)
  - [`์ฝ๋2`์ ์ค๊ณ](#์ฝ๋2์-์ค๊ณ)
- [4. ๊ด์ฌ์ฌ ๋ถ๋ฆฌ](#4-๊ด์ฌ์ฌ-๋ถ๋ฆฌ)
  - [์ข์ ๊ฐ์ฒด ์งํฅ ์ค๊ณ์ 5๊ฐ์ง ์์น์ ์ ์ฉ](#์ข์-๊ฐ์ฒด-์งํฅ-์ค๊ณ์-5๊ฐ์ง-์์น์-์ ์ฉ)
    - [SRP(Single Responsibility Principle) ๐](#srpsingle-responsibility-principle-)
    - [DIP(Dependency Inversion Principle) ๐](#dipdependency-inversion-principle-)
    - [OCP(Open-Closed Principle) ๐](#ocpopen-closed-principle-)
  - [IoC(์ ์ด์ ์ญ์ ), DI(์์กด๊ด๊ณ ์ฃผ์), ๊ทธ๋ฆฌ๊ณ  ์ปจํ์ด๋](#ioc์ ์ด์-์ญ์ -di์์กด๊ด๊ณ-์ฃผ์-๊ทธ๋ฆฌ๊ณ -์ปจํ์ด๋)
    - [์ ์ด์ ์ญ์ (Inversion of Control, IoC) ๐](#์ ์ด์-์ญ์ inversion-of-control-ioc-)
    - [์์กด๊ด๊ณ ์ฃผ์(Dependency Injection, DI) ๐](#์์กด๊ด๊ณ-์ฃผ์dependency-injection-di-)
    - [IoC ์ปจํ์ด๋, DI ์ปจํ์ด๋ ๐](#ioc-์ปจํ์ด๋-di-์ปจํ์ด๋-)
- [5. ์คํ๋ง์ผ๋ก ์ ํ](#5-์คํ๋ง์ผ๋ก-์ ํ)
  - [์คํ๋ง ์ปจํ์ด๋](#์คํ๋ง-์ปจํ์ด๋)
  - [BeanFactory์ ApplicationContext](#beanfactory์-applicationcontext)
  - [์คํ๋ง ๋น ์ค์  ๋ฉํ ์ ๋ณด - BeanDefinition](#์คํ๋ง-๋น-์ค์ -๋ฉํ-์ ๋ณด---beandefinition)
- [6. ์ฑ๊ธํค ์ปจํ์ด๋](#6-์ฑ๊ธํค-์ปจํ์ด๋)
  - [์์ํ DI ์ปจํ์ด๋](#์์ํ-di-์ปจํ์ด๋)
  - [์ฑ๊ธํค ํจํด](#์ฑ๊ธํค-ํจํด)
  - [์ฑ๊ธํค ์ปจํ์ด๋](#์ฑ๊ธํค-์ปจํ์ด๋)
  - [์ฑ๊ธํค ๋ฐฉ์์ ์ฃผ์์ ](#์ฑ๊ธํค-๋ฐฉ์์-์ฃผ์์ )
- [8. ์์กด๊ด๊ณ ์๋ ์ฃผ์](#8-์์กด๊ด๊ณ-์๋-์ฃผ์)
  - [๋ค์ํ ์์กด๊ด๊ณ ์ฃผ์ ๋ฐฉ๋ฒ](#๋ค์ํ-์์กด๊ด๊ณ-์ฃผ์-๋ฐฉ๋ฒ)
    - [์์ฑ์ ์ฃผ์](#์์ฑ์-์ฃผ์)
    - [์์ ์ ์ฃผ์(Setter ์ฃผ์)](#์์ ์-์ฃผ์setter-์ฃผ์)
    - [ํ๋ ์ฃผ์](#ํ๋-์ฃผ์)
    - [์ผ๋ฐ ๋ฉ์๋ ์ฃผ์](#์ผ๋ฐ-๋ฉ์๋-์ฃผ์)
  - [์ต์์ฒ๋ฆฌ](#์ต์์ฒ๋ฆฌ)
  - [์กฐํ ๋น์ด 2๊ฐ ์ด์ - ๋ฌธ์ ](#์กฐํ-๋น์ด-2๊ฐ-์ด์---๋ฌธ์ )
  - [์กฐํํ ๋น์ด ๋ชจ๋ ํ์ํ  ๋](#์กฐํํ-๋น์ด-๋ชจ๋-ํ์ํ -๋)
- [9. ๋น ์๋ช์ฃผ๊ธฐ ์ฝ๋ฐฑ](#9-๋น-์๋ช์ฃผ๊ธฐ-์ฝ๋ฐฑ)
- [10. ๋น ์ค์ฝํ](#10-๋น-์ค์ฝํ)
  - [ํ๋กํ ํ์ ์ค์ฝํ](#ํ๋กํ ํ์-์ค์ฝํ)
    - [์ฑ๊ธํค ๋น์์ ํ๋กํ ํ์ ๋น ์ฌ์ฉ](#์ฑ๊ธํค-๋น์์-ํ๋กํ ํ์-๋น-์ฌ์ฉ)
  - [์น ์ค์ฝํ](#์น-์ค์ฝํ)
</details>

---
## IntelliJ ๋จ์ถํค ์ ๋ฆฌ
- `โ + โง + โ`
  - ์๋ ์์ฑ๊ณผ ๋์์ `;`๋ฅผ ์ฐ์ด์ค
- `โ + โง + T` 
  - ํ์คํธ ์ฝ๋ ์๋ ์์ฑ
- `โ + โฅ + V`
  - ๋ณ์ ์ถ์ถ
- `โ + โฅ + M`
  - ๋ฉ์๋ ์ถ์ถ
- `โ + E`
  - ์ต๊ทผ ์ฌ์ฉ๋ ํ์ผ๋ค์ ๋ณผ ์ ์์
- `iter + โฅ`
  - ๋ฆฌ์คํธ์ ๊ฐ์ ๋ฐฐ์ด๋ค์ for ๋ฌธ์ ์๋์ผ๋ก ์์ฑ์์ผ์ค
- `โ + โฅ + N`
  - Refactor
- `โ + โฅ + P`
  - ๋งค๊ฐ๋ณ์ ์ถ์ถ


## 1. ํ์ ๋๋ฉ์ธ ๊ฐ๋ฐ
```java
// ์ฝ๋1
public class MemberServiceImpl implements MemberService{

    private final MemberRepository memberRepository = new MemoryMemberRepository();
}
```
### `์ฝ๋1`์ ๋ฌธ์ ์  ๐ค
- ํ์ ์ ์ฅ์๋ฅผ ํ์ฅํ๋ฉด ํ์ ์๋น์ค ๊ตฌํ์ฒด ์์ ์ด ํ์์ ์ด๋ฏ๋ก **OCP** ์๋ฐ 
- ํ์ ์๋น์ค๋ ์ถ์ํ๋ ์์กดํ๊ณ  ๊ตฌํ์ฒด๋ ์์กดํ๊ธฐ ๋๋ฌธ์ **DIP** ์๋ฐ

### TIL ๐ก
- `enum`์ member entity ์ ๊ตฌํํ์ง ์๊ณ  ์๋ก์ด ํ์ผ์ ๋ง๋ค์ด ๊ตฌํ

## 2. ํ์ ๋๋ฉ์ธ ์คํ๊ณผ ํ์คํธ
### ์ ํ์ผ์ด์ ๋ก์ง์ ๊ตฌํ ํ ํ์คํธ
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
- ์๋น์ค๊ฐ ์์ฃผ ์ปค์ง๋ค๋ฉด ์ ํ๋ฆฌ์ผ์ด์ ๋ก์ง์ ๋ฉ์ธ ๋ฉ์๋๋ก ํ์คํธํ๋๋ฐ ํ๊ณ๊ฐ ์กด์ฌํจ

### `JUnit`์ ์ด์ฉํด์ ํ์คํธ โ๏ธ
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
- **Given-When-Then** Pattern (์ค๋น - ์คํ - ๊ฒ์ฆ)
  - `given`: ์ค๋นํ๋ ๊ณผ์ 
  - `when`: ์ค์ ๋ก ์ก์์ ํ๋ ํ์คํธ๋ฅผ ์คํํ๋ ๊ณผ์ 
  - `then`: ํ์คํธ๋ฅผ ๊ฒ์ฆํ๋ ๊ณผ์ 
- ๊ฒ์ฆ์ `assertj`์ `Assertions`๋ฅผ ์ฌ์ฉ
  - `assertThat`๊ณผ `isEqualTo`๊ฐ ๊ฐ๋ค๋ฉด Run ์ฐฝ์ ์ด๋ก๋ถ์ด ๋ค์ด์จ๋ค
  - `assertThat`๊ณผ `isEqualTo`๊ฐ ๋ค๋ฅด๊ฑฐ๋ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ค๋ฉด Run ์ฐฝ์ ๋นจ๊ฐ๋ถ์ด ๋ค์ด์จ๋ค
  
~~Clean Code ์์ ๋ค๋ฃจ๋ ๋จ์ ํ์คํธ์ ๋ํ ๋ด์ฉ์ ๋ค์ ์ฝ์ด๋ด์ผ๊ฒ ๋ค.~~

## 3. ์ฃผ๋ฌธ๊ณผ ํ ์ธ ๋๋ฉ์ธ ๊ฐ๋ฐ
```java
// ์ฝ๋2
public interface DiscountPolicy {

    /**
     * @return ํ ์ธ ๋์ ๊ธ์ก
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
### `์ฝ๋2`์ ์ค๊ณ
- `DiscountPolicy`๋ ํ ์ธ์ ๊ด๋ จ๋ ์ฑ์๋ง ๊ฐ์ง๊ณ  ์๊ณ , `OrderService`๋ ์ฃผ๋ฌธ๊ณผ ๊ด๋ จ๋ ์ฑ์๋ง ๊ฐ์ง๊ณ  ์๋ค.   
  โ ๊ฐ ํด๋์ค๋ ํ ๊ฐ์ง ์ฑ์๋ง ๊ฐ์ง๊ณ  ์๊ธฐ์ **SRP**๋ฅผ ์งํค๊ณ  ์๋ค.
- ํ์ง๋ง `์ฝ๋1`์ ๊ฐ์ด ํ์ฅ ๋๋ค๋ฉด **OCP**, **DIP**๋ฅผ ์๋ฐํ๋ค.

## 4. ๊ด์ฌ์ฌ ๋ถ๋ฆฌ
- ๊ธฐ์กด ์ฝ๋
```java
public class MemberServiceImpl implements MemberService {

  private final MemberRepository memberRepository = new MemboryMemberRespository();
}

public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();
    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
}
```
- ๊ด์ฌ์ฌ๋ฅผ ๋ถ๋ฆฌํ ์ฝ๋
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
- ์์ ๊ฐ์ด ๊ด์ฌ์ฌ๋ฅผ ๋ถ๋ฆฌํ๋ฉด ์ธํฐํ์ด์ค๋ ์ถ์ํ๋ง ์์กดํ๊ธฐ ๋๋ฌธ์ **DIP**๋ฅผ ๋ง์กฑํ๋ค.
- ๋ง์ฝ ํ์ฅ์ ํ๋๋ผ๋ ์์กด์ฑ ์ฃผ์์ผ๋ก ์ธํด **์ฌ์ฉ ์์ญ**(ํด๋ผ์ด์ธํธ ์ฝ๋)์ ๋ณ๊ฒฝ์์ด **๊ตฌ์ฑ ์ญ์ญ**(`AppConfig`)๋ง ์์ ํ๋ฉด ๋๋ฏ๋ก **OCP**๋ฅผ ๋ง์กฑํ๋ค.
- ํด๋ผ์ด์ธํธ ์ฝ๋๋ ์์กด๊ด๊ณ์ ๋ํ ์ฑ์์ ๋๊ณ  ๊ธฐ๋ฅ์๋ง ์ฑ์์ ๊ฐ์ง๋ค.

~~์์กด์ฑ ์ฃผ์์ ๊ณต๋ถํ ํ ์ ๋ฆฌ ํ์~~

### ์ข์ ๊ฐ์ฒด ์งํฅ ์ค๊ณ์ 5๊ฐ์ง ์์น์ ์ ์ฉ
ํ์ฌ๊น์ง **SRP**, **DIP**, **OCP** ์ ์ฉ

#### SRP(Single Responsibility Principle) ๐
**ํ ํด๋์ค๋ ํ๋์ ์ฑ์๋ง ๊ฐ์ ธ์ผ ํ๋ค.**
- ํด๋ผ์ด์ธํธ ๊ฐ์ฒด๋ ์ง์  ๊ตฌํ ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ , ์ฐ๊ฒฐํ๊ณ , ์คํํ๋ ๋ค์ํ ์ฑ์์ ๊ฐ์ง๊ณ  ์์
- SRP๋ฅผ ๋ฐ๋ฅด๋ฉด์ ๊ด์ฌ์ฌ๋ฅผ ๋ถ๋ฆฌ
- ๊ตฌํ ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ  ์ฐ๊ฒฐํ๋ ์ฑ์์ `AppConfig`๊ฐ ๋ด๋น
- ํด๋ผ์ด์ธํธ ๊ฐ์ฒด๋ ์คํํ๋ ์ฑ์๋ง ๋ด๋น

#### DIP(Dependency Inversion Principle) ๐
**ํ๋ก๊ทธ๋๋จธ๋ "์ถ์ํ์ ์์กดํด์ผ์ง, ๊ตฌ์ฒดํ์ ์์กดํ๋ฉด ์๋๋ค." ์์กด์ฑ ์ฃผ์์ ์ด ์์น์ ๋ฐ๋ฅด๋ ๋ฐฉ๋ฒ ์ค ํ๋๋ค.**
- ๊ธฐ์กด ํด๋ผ์ด์ธํธ ์ฝ๋๋ ์ถ์ํ ์ธํฐํ์ด์ค์ ์์กดํ์ง๋ง, ๊ตฌ์ฒดํ ๊ตฌํ ํด๋์ค๋ ํจ๊ป ์์กดํ์
- ๊ด์ฌ์ฌ ๋ถ๋ฆฌ ํ ํด๋ผ์ด์ธํธ ์ฝ๋๋ ์ถ์ํ ์ธํฐํ์ด์ค์๋ง ์์กด

#### OCP(Open-Closed Principle) ๐
**์ํํธ์จ์ด ์์๋ ํ์ฅ์ ์ด๋ ค์๊ณ  ๋ณ๊ฒฝ์๋ ๋ซํ ์์ด์ผ ํ๋ค.**
- ๋คํ์ฑ์ ์ฌ์ฉํ๊ณ  ํด๋ผ์ด์ธํธ๊ฐ DIP๋ฅผ ์งํด
- ์ ํ๋ฆฌ์ผ์ด์์ ์ฌ์ฉ ์์ญ๊ณผ ๊ตฌ์ฑ ์์ญ์ผ๋ก ๋๋
- `AppConfig`๊ฐ ์์กด ๊ด๊ณ๋ฅผ ํด๋ผ์ด์ธํธ ์ฝ๋์ ์ฃผ์ํ๋ฏ๋ก ํด๋ผ์ด์ธํธ ์ฝ๋๋ ๋ณ๊ฒฝํ์ง ์์๋ ๋จ
- ๋ฐ๋ผ์ **์ํํธ์จ์ด ์์๋ฅผ ์๋กญ๊ฒ ํ์ฅํด๋ ์ฌ์ฉ ์ญ์์ ๋ณ๊ฒฝ์ ๋ซํ์๋ค.**

### IoC(์ ์ด์ ์ญ์ ), DI(์์กด๊ด๊ณ ์ฃผ์), ๊ทธ๋ฆฌ๊ณ  ์ปจํ์ด๋
#### ์ ์ด์ ์ญ์ (Inversion of Control, IoC) ๐
- ๋ฆฌํฉํ ๋ฆฌ์  ํ๋ก๊ทธ๋จ์ ํด๋ผ์ด์ธํธ ๊ตฌํ ๊ฐ์ฒด๊ฐ ์ค์ค๋ก ํ์ํ ์๋ฒ ๊ตฌํ ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ , ์ฐ๊ฒฐํ๊ณ  ์คํํ๋ค. ์ฆ, ๊ตฌํ ๊ฐ์ฒด๊ฐ ํ๋ก๊ทธ๋จ์ ์ ์ด ํ๋ฆ์ ์ค์ค๋ก ์กฐ์ขํ๋ค.
- ๊ด์ฌ์ฌ ๋ถ๋ฆฌ ํ ๊ตฌํ ๊ฐ์ฒด๋ ์์ ์ ๋ก์ง๋ง ์ํํ๋ ์ญํ ๋ง ๋ด๋นํ๊ณ , ํ๋ก๊ทธ๋จ์ ์ ์ด ํ๋ฆ์ `AppConfig`๊ฐ ๊ฐ์ ธ๊ฐ๋ค.
- ์ด๋ ๋ฏ ํ๋ก๊ทธ๋จ์ ์ ์ด ํ๋ฆ์ ์ง์  ์ ์ดํ๋ ๊ฒ์ด ์๋๋ผ ์ธ๋ถ์์ ๊ด๋ฆฌํ๋ ๊ฒ์ ์ ์ด์ ์ญ์ (IoC)๋ผ ํ๋ค.

**ํ๋ ์์ํฌ vs ๋ผ์ด๋ธ๋ฌ๋ฆฌ**
- ํ๋ ์์ํฌ๊ฐ ํ๋ก๊ทธ๋๋จธ๊ฐ ์์ฑํ ์ฝ๋๋ฅผ ์ ์ดํ๊ณ , ๋์  ์คํํ๋ฉด ๊ทธ๊ฒ์ ํ๋ ์์ํฌ๋ค. ex) JUnit
- ํ๋ก๊ทธ๋๋จธ๊ฐ ์์ฑํ ์ฝ๋๋ฅผ ์ง์  ์ ์ด์ ํ๋ฆ์ ๋ด๋นํ๋ค๋ฉด, ๊ทธ๊ฒ์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ค.

#### ์์กด๊ด๊ณ ์ฃผ์(Dependency Injection, DI) ๐
- `OrderServiceImpl`์ `DiscountPolicy` ์ธํฐํ์ด์ค์ ์์กดํ๋ค. ์ค์  ์ด๋ค ๊ตฌํ ๊ฐ์ฒด๊ฐ ์ฌ์ฉ๋ ์ง๋ ๋ชจ๋ฆ
- ์์กด๊ด๊ณ๋ **์ ์ ์ธ ํด๋์ค ์์กด ๊ด๊ณ์ ์คํ ์์ ์๋ ๊ฒฐ์ ๋๋ ๋์ ์ธ ์ธ์คํด์ค ์์กด ๊ด๊ณ** ๋์ ๋ถ๋ฆฌํด์ ์๊ฐํด์ผ ํจ

**์ ์ ์ธ ํด๋์ค ์์กด ๊ด๊ณ**   
ํด๋์ค๊ฐ ์ฌ์ฉํ๋ `import` ์ฝ๋๋ง ๋ณด๊ณ  ์์กด ๊ด๊ณ๋ฅผ ์ฝ๊ฒ ํ๋จํ  ์ ์๋ค. ์ ์ ์ธ ์์กด ๊ด๊ณ๋ ์ ํ๋ฆฌ์ผ์ด์์ ์คํํ์ง ์์๋ ๋ถ์ํ  ์ ์๋ค.

ํด๋์ค ๋ค์ด์ด๊ทธ๋จ

<img width="530" alt="image" src="https://user-images.githubusercontent.com/45463495/156312530-35a6faef-4fd8-4d86-9e67-1cc8e1d21483.png">

- `OrderServiceImpl`์ `MemberRepository`, `DiscountPolicy`์ ์์กดํ๋ค๋ ๊ฒ์ ์ ์ ์์
- ํ์ง๋ง ์ด๋ฌํ ํด๋์ค ์์กด ๊ด๊ณ๋ง์ผ๋ก๋ ์ค์  ์ด๋ค ๊ฐ์ฒด๊ฐ `OrderServiceImpl`์ ์ฃผ์๋ ์ง ์ ์ ์์

**๋์ ์ธ ๊ฐ์ฒด ์ธ์คํด์ค ์์กด ๊ด๊ณ**   
์ ํ๋ฆฌ์ผ์ด์ ์คํ ์์ ์ ์ค์  ์์ฑ๋ ๊ฐ์ฒด ์ธ์คํด์ค์ ์ฐธ์กฐ๊ฐ ์ฐ๊ฒฐ๋ ์์กด ๊ด๊ณ

๊ฐ์ฒด ๋ค์ด์ด๊ทธ๋จ

<img width="530" alt="image" src="https://user-images.githubusercontent.com/45463495/156313379-20e8c597-42dd-45e6-990a-f1fec811827e.png">

- ์ ํ๋ฆฌ์ผ์ด์ ์คํ ์์ ์ ์ธ๋ถ์์ ์ค์  ๊ตฌํ ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ  ํด๋ผ์ด์ธํธ์ ์ ๋ฌํด์ ํด๋ผ์ด์ธํธ์ ์๋ฒ์ ์ค์  ์์กด ๊ด๊ณ๊ฐ ์ฐ๊ฒฐ๋๋ ๊ฒ์ **์์กด๊ด๊ณ ์ฃผ์**์ด๋ผ ํ๋ค.
- ์์กด๊ด๊ณ ์ฃผ์์ ์ฌ์ฉํ๋ฉด ํด๋ผ์ด์ธํธ ์ฝ๋๋ฅผ ๋ณ๊ฒฝํ์ง ์๊ณ , ํด๋ผ์ด์ธํธ๊ฐ ํธ์ถํ๋ ๋์์ ํ์ ์ธ์คํด์ค๋ฅผ ๋ณ๊ฒฝ ๊ฐ๋ฅ
- ์์กด๊ด๊ณ ์ฃผ์์ ์ฌ์ฉํ๋ฉด **์ ์ ์ธ ํด๋์ค ์์กด๊ด๊ณ๋ฅผ ๋ณ๊ฒฝํ์ง ์๊ณ , ๋์ ์ธ ๊ฐ์ฒด ์ธ์คํด์ค ์์กด๊ด๊ณ๋ฅผ ์ฝ๊ฒ ๋ณ๊ฒฝ ๊ฐ๋ฅ**

#### IoC ์ปจํ์ด๋, DI ์ปจํ์ด๋ ๐
- `AppConfig`์ฒ๋ผ ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ  ๊ด๋ฆฌํ๋ฉด์ ์์กด๊ด๊ณ๋ฅผ ์ฐ๊ฒฐํด์ฃผ๋ ๊ฒ์ IoC ์ปจํ์ด๋, **DI ์ปจํ์ด๋**๋ผ ํ๋ค.
- ์์กด๊ด๊ณ ์ฃผ์์ ์ด์ ์ ๋ง์ถฐ ์ต๊ทผ์๋ ์ฃผ๋ก DI ์ปจํ์ด๋๋ผ ํ๋ค.

## 5. ์คํ๋ง์ผ๋ก ์ ํ
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
- `AppConfig`์ ์ค์ ์ ๊ตฌ์ฑํ๋ค๋ ๋ป์ `@Configuration`์ ๋ถ์ฌ์ค
- ๊ฐ ๋ฉ์๋์ `@Bean`์ ๋ถ์ฌ์ค -> ์คํ๋ง ์ปจํ์ด๋์ ์คํ๋ง ๋น์ผ๋ก ๋ฑ๋ก

### ์คํ๋ง ์ปจํ์ด๋
- `ApplicationContext`๋ฅผ ์คํ๋ง ์ปจํ์ด๋๋ผ ํ๋ค.
- ๊ธฐ์กด์๋ ๊ฐ๋ฐ์๊ฐ `AppConfig`๋ฅผ ์ง์  ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ , ์์กด์ฑ์ ์ฃผ์ํ์ง๋ง, ์ด์ ๋ถํฐ ์คํ๋ง ์ปจํ์ด๋๋ฅผ ํตํด์ ์ฌ์ฉํ๋ค.
- ์คํ๋ง ์ปจํ์ด๋๋ `@Configuration`์ด ๋ถ์ `AppConfig`๋ฅผ ๊ตฌ์ฑ ์ ๋ณด๋ก ์ฌ์ฉ
- `@Bean`์ด๋ผ ์ ํ ๋ฉ์๋๋ฅผ ๋ชจ๋ ํธ์ถํ์ฌ ๋ฐํ๋ ๊ฐ์ฒด๋ฅผ ์คํ๋ง ์ปจํ์ด๋๋ฅผ ๋ฑ๋กํ๋ค. ์ด๋ ๊ฒ ์คํ๋ง ์ปจํ์ด๋์ ๋ฑ๋ก๋ ๊ฐ์ฒด๋ฅผ ์คํ๋ง ๋น์ด๋ผ ํจ

**์คํ๋ง ์ปจํ์ด๋์ ์์ฑ ๊ณผ์ **

1. ์คํ๋ง ์ปจํ์ด๋ ์์ฑ
```
ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
```
- ์คํ๋ง ์ปจํ์ด๋๋ฅผ ์์ฑํ  ๋๋ ๊ตฌ์ฑ ์ ๋ณด๋ฅผ ์ง์ ํด์ฃผ์ด์ผ ํจ

2. ์คํ๋ง ๋น ๋ฑ๋ก
![](https://user-images.githubusercontent.com/45463495/156500577-f15e775b-b7e5-46b6-8181-9213b88b303b.png)   
- ์คํ๋ง ์ปจํ์ด๋๋ ํ๋ผ๋ฏธ๋๋ก ๋์ด์จ ์ค์  ํด๋์ค ์ ๋ณด๋ฅผ ์ฌ์ฉํด์ ์คํ๋ง ๋น์ ๋ฑ๋ก

๐ก ๋น ์ด๋ฆ
- ๋ฉ์๋ ์ด๋ฆ์ ์ฌ์ฉ
- ์ง์  ๋ถ์ฌ ๊ฐ๋ฅ
  - `@Bean(name="ms")`
- ๋น ์ด๋ฆ์ ํญ์ ๋ค๋ฅธ ์ด๋ฆ์ ๋ถ์ฌํด์ผ ํจ

3. ์คํ๋ง ๋น ์์กด๊ด๊ณ ์ค์ 

์ค๋น|์๋ฃ
:--:|:--:
![image](https://user-images.githubusercontent.com/45463495/156500909-a5ff20f2-1d0f-456c-a1cb-d07b39549737.png)|![image](https://user-images.githubusercontent.com/45463495/156500969-981c546e-330b-47e1-8fa7-b6a7465a78cd.png)
- ์คํ๋ง ์ปจํ์ด๋๋ ์ค์  ์ ๋ณด๋ฅผ ์ฐธ๊ณ ํด์ ์์กด๊ด๊ณ๋ฅผ ์ฃผ์

**์ปจํ์ด๋์ ๋ฑ๋ก๋ ๋ชจ๋  ๋น ์กฐํ**
```java
public class BeanFind {

  AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);

  @Test
  @DisplayName("๋ชจ๋  ๋น ์ถ๋ ฅ")
  void findAllBean() {
    String[] beanDefinitionNames = ac.getBeanDefinitionNames();
    for (String beanDefinitionName : beanDefinitionNames) {
      Object bean = ac.getBean(beanDefinitionName);
      System.out.println("name = " + beanDefinitionName + " Object = " + bean);
    }
  }

  @Test
  @DisplayName("์ ํ๋ฆฌ์ผ์ด์ ๋น ์ถ๋ ฅ")
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
  @DisplayName("๋น ์ด๋ฆ์ ์กฐํ")
  void findBeanByName() {
    MemberService memberService = ac.getBean("memberService", MemberService.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
  }

  @Test
  @DisplayName("ํ์์ผ๋ก๋ง ์กฐํ")
  void findBeanByType() {
    MemberService memberService = ac.getBean(MemberService.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
  }

  @Test
  @DisplayName("๊ตฌ์ฒด ํ์์ผ๋ก ์กฐํ")
  void findBeanByName2() {
    MemberService memberService = ac.getBean("memberService", MemberServiceImpl.class);
    assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
  }

  @Test
  @DisplayName("๋น ์ด๋ฆ์ผ๋ก ์กฐํX")
  void findBeanByNameX() {
    // MemberService xxx = ac.getBean("xxx", MemberService.class);
    assertThrows(NoSuchBeanDefinitionException.class,
            () -> ac.getBean("xxx", MemberService.class));
  }

  @Test
  @DisplayName("ํ์์ผ๋ก ์กฐํ ์ ๊ฐ์ ํ์์ด ๋ ์ด์ ์์ผ๋ฉด, ์ค๋ณต ์ค๋ฅ ๋ฐ์")
  void findBeanByTypeDuplicate() {
//        ac.getBean(MemberRepository.class);
    assertThrows(NoUniqueBeanDefinitionException.class, () -> ac.getBean(MemberRepository.class));
  }

  @Test
  @DisplayName("ํ์์ผ๋ก ์กฐํ ์ ๊ฐ์ ํ์์ด ๋ ์ด์ ์์ผ๋ฉด, ๋น ์ด๋ฆ์ ์ง์ ํ๋ฉด ๋๋ค")
  void findBeanByName() {
    MemberRepository memberRepository = ac.getBean("memberRepository1",
            MemberRepository.class);
    assertThat(memberRepository).isInstanceOf(MemberRepository.class);
  }

  @Test
  @DisplayName("ํน์  ํ์ ๋ชจ๋ ์กฐํํ๊ธฐ")
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
}
```
- ๋ชจ๋  ๋น ์ถ๋ ฅ
  - ์คํ๋ง์ ๋ฑ๋ก๋ ๋ชจ๋  ๋น ์ ๋ณด๋ฅผ ์ถ๋ ฅ
  - `getBeanDefinitionNames()` : ์คํ๋ง์ ๋ฑ๋ก๋ ๋ชจ๋  ๋น ์ด๋ฆ ์กฐํ
  - `getBean()` : ๋น ์ด๋ฆ์ผ๋ก ๋น ๊ฐ์ฒด(์ธ์คํด์ค) ์กฐํ
- ์ ํ๋ฆฌ์ผ์ด์ ๋น ์ถ๋ ฅ
  - `getRole()` : ์คํ๋ง์ด ๋ด๋ถ์์ ์ฌ์ฉํ๋ ๋น์ ๊ตฌ๋ถ
    - `ROLE_APPLICATION` : ์ฌ์ฉ์๊ฐ ์ ์ํ ๋น
    - `ROLE_INFRASTRUCTURE` : ์คํ๋ง ๋ด๋ถ์์ ์ฌ์ฉํ๋ ๋น
- ๋์ผํ ํ์์ด ๋ ๊ฐ์ด์์ผ ๊ฒฝ์ฐ
  - `getBeansOfType()` ์ฌ์ฉ
    - ํด๋น ํ์์ ๋ชจ๋  ๋น์ ์กฐํํ  ์ ์์

### BeanFactory์ ApplicationContext
![](https://user-images.githubusercontent.com/45463495/156716543-dc4f4b08-2668-4bea-8be8-a0a6233f7408.png)

**BeanFactory**
- ์คํ๋ง ์ปจํ์ด๋์ ์ต์์ ์ธํฐํ์ด์ค
- ์คํ๋ง ๋น์ ๊ด๋ฆฌํ๊ณ  ์กฐํํ๋ ์ญํ  ๋ด๋น
- `getBean()` ์ ๊ณต

**ApplicationContext**
- BeanFactory ๊ธฐ๋ฅ์ ๋ชจ๋ ์์๋ฐ์์ ์ ๊ณต
- ์ ํ๋ฆฌ์ผ์ด์์ ๊ฐ๋ฐํ  ๋๋ ๋น์ ๊ด๋ฆฌํ๊ณ  ์กฐํํ๋ ๊ธฐ๋ฅ์ ๋ฌผ๋ก ์ด๊ณ , ์ ๋ง์ ๋ถ๊ฐ๊ธฐ๋ฅ์ด ํ์
- ApplicationContext๊ฐ ์ ๊ณตํ๋ ๋ถ๊ฐ๊ธฐ๋ฅ
  - ๋ฉ์์ง์์ค๋ฅผ ํ์ํ ๊ตญ์ ํ ๊ธฐ๋ฅ
    - ex) ํ๊ตญ์์ ๋ค์ด์ค๋ฉด ํ๊ตญ์ด, ์์ด๊ถ์์ ๋ค์ด์ค๋ฉด ์์ด๋ก ์ถ๋ ฅ
  - ํ๊ฒฝ๋ณ์
    - ๋ก์ปฌ, ๊ฐ๋ฐ, ์ด์๋ค์ ๊ตฌ๋ถํด์ ์ฒ๋ฆฌ
  - ์ ํ๋ฆฌ์ผ์ด์ ์ด๋ฒคํธ
    - ์ด๋ฒคํธ๋ฅผ ๋ฐํํ๊ณ  ๊ตฌ๋ํ๋ ๋ชจ๋ธ์ ํธ๋ฆฌํ๊ฒ ์ง์
  - ํธ๋ฆฌํ ๋ฆฌ์์ค ์กฐํ
    - ํ์ผ, ํด๋์คํจ์ค, ์ธ๋ถ ๋ฑ์์ ๋ฆฌ์์ค๋ฅผ ํธ๋ฆฌํ๊ฒ ์กฐํ

### ์คํ๋ง ๋น ์ค์  ๋ฉํ ์ ๋ณด - BeanDefinition
**BeanDefinition** ์ ๋ณด
- BeanClassName : ์์ฑํ  ๋น์ ํด๋์ค ๋ช
- factoryBeanName : ํฉํ ๋ฆฌ ์ญํ ์ ๋น์ ์ฌ์ฉํ  ๊ฒฝ์ฐ ์ด๋ฆ
- factoryMethodName: ๋น์ ์์ฑํ  ํฉํ ๋ฆฌ ๋ฉ์๋ ์ง์ 
- Scope : ์ฑ๊ธํค(๊ธฐ๋ณธ ๊ฐ)
- lazyInt : ์คํ๋ง ์ปจํ์ด๋๋ฅผ ์์ฑํ  ๋ ๋น์ ์์ฑํ๋ ๊ฒ์ด ์๋๋ผ, ์ค์  ๋น์ ์ฌ์ฉํ  ๋๊น์ง ์ต๋ํ ์์ฑ์ ์ง์ฐ์ฒ๋ฆฌ ํ๋ ์ง ์ฌ๋ถ
- InitMethodName : ๋น์ ์์ฑํ๊ณ , ์์กด๊ด๊ณ๋ฅผ ์ ์ฉํ ๋ค์ ํธ์ถ๋๋ ์ด๊ธฐํ ๋ฉ์๋ ๋ช
- DestroyMethodName : ๋น์ ์๋ช์ฃผ๊ธฐ๊ฐ ๋๋์ ์ ๊ฑฐํ๊ธฐ ์ง์ ์ ํธ์ถ๋๋ ๋ฉ์๋ ๋ช
- Constructor arguments, Properties : ์์กด๊ด๊ณ ์ฃผ์์์ ์ฌ์ฉ

## 6. ์ฑ๊ธํค ์ปจํ์ด๋
### ์์ํ DI ์ปจํ์ด๋
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/156974101-08e832ed-cfda-421c-8919-3d151fd8bf3f.png">

- ๊ณ ๊ฐ์ด ์์ฒญ์ ํ  ๋๋ง๋ค ๊ฐ์ฒด๋ฅผ ์๋ก ์์ฑํจ -> ๋ฉ๋ชจ๋ฆฌ ๋ญ๋น๊ฐ ์ฌํจ

### ์ฑ๊ธํค ํจํด
- ํด๋์ค์ ์ธ์คํด์ค๊ฐ ๋ฑ 1๊ฐ๋ง ์์ฑ๋๋ ๊ฒ์ ๋ณด์ฅํ๋ ๋์์ธ ํจํด
- ์ฑ๊ธํค ํจํด์ ๋จ์ 
  - ๊ตฌํํ๋ ์ฝ๋ ์์ฒด๊ฐ ๋ง์ด ๋ค์ด๊ฐ
  - ์์กด๊ด๊ณ์ ํด๋ผ์ด์ธํธ๊ฐ ๊ตฌ์ฒด ํด๋์ค์ ์์กด -> DIP ์๋ฐ, OCP ์๋ฐํ  ๊ฐ๋ฅ์ฑ์ด ๋์
  - ํ์คํธ๊ฐ ์ด๋ ค์
  - ๋ด๋ถ ์์ฑ์ ๋ณ๊ฒฝํ๊ฑฐ๋ ์ด๊ธฐํ๊ฐ ์ด๋ ค์
  - private ์์ฑ์๋ก ์์ ํด๋์ค๋ฅผ ๋ง๋ค๊ธฐ ์ด๋ ค์
  - ์ ์ฐ์ฑ์ด ๋จ์ด์ง

### ์ฑ๊ธํค ์ปจํ์ด๋
- ์ฑ๊ธํค ํจํด์ ์ ์ฉํ์ง ์์๋ ๊ฐ์ฒด ์ธ์คํด์ค๋ฅผ ์ฑ๊ธํค์ผ๋ก ๊ด๋ฆฌ

**์ฑ๊ธํค ์ปจํ์ด๋ ์ ์ฉ ํ**   
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/156974175-b450142e-6803-4a1b-974c-74d2292fa69f.png">

- ์คํ๋ง ์ปจํ์ด๋ ๋๋ถ์ ๊ณ ๊ฐ์ด ์์ฒญ์ด ์ฌ ๋ ๋ง๋ค ๊ฐ์ฒด๋ฅผ ์์ฑํ๋ ๊ฒ์ด ์๋๋ผ, ์ด๋ฏธ ๋ง๋ค์ด์ง ๊ฐ์ฒด๋ฅผ ๊ณต์ ํด์ ํจ์จ์ ์ผ๋ก ์ฌ์ฌ์ฉํ  ์ ์์

### ์ฑ๊ธํค ๋ฐฉ์์ ์ฃผ์์ 
- ๊ฐ์ฒด ์ธ์คํด์ค๋ฅผ ํ๋๋ง ์์ฑํด์ ๊ณต์ ํ๋ ์ฑ๊ธํค ๋ฐฉ์์ ์ฌ๋ฌ ํด๋ผ์ด์ธํธ๊ฐ ํ๋์ ๊ฐ์ ๊ฐ์ฒด ์ธ์คํด์ค๋ฅผ ๊ณต์ ํ๊ธฐ ๋๋ฌธ์ ์ฑ๊ธํค ๊ฐ์ฒด๋ ์ํ๋ฅผ ์ ์งํ๊ฒ ์ค๊ณํ๋ฉด ์๋๋ค.
- ๋ฌด์ํ๋ก ์ค๊ณํด์ผ ํ๋ค.
  - ํน์  ํด๋ผ์ด์ธํธ์ ์์กด์ ์ธ ํ๋๊ฐ ์์ผ๋ฉด ์๋จ
  - ํน์  ํด๋ผ์ด์ธํธ๊ฐ ๊ฐ์ ๋ณ๊ฒฝํ  ์ ์๋ ํ๋๊ฐ ์์ผ๋ฉด ์๋จ
  - ๊ฐ๊ธ์  ์ฝ๊ธฐ๋ง ๊ฐ๋ฅํด์ผ ํจ
  - ํ๋ ๋์  ์๋ฐ์์ ๊ณต์ ๋์ง ์๋ ์ง์ญ๋ณ์, ํ๋ผ๋ฏธํฐ, ThreadLocal ๋ฑ์ ์ฌ์ฉ
- ์คํ๋ง ๋น์ ํ๋์ ๊ณต์  ๊ฐ์ ์ค์ ํ๋ฉด ํฐ ์ฅ์ ๊ฐ ๋ฐ์ํ  ์ ์์

**์์**
```java
package hello.core.singleton;

public class StateFulService {

    private int price; // ์ํ๋ฅผ ์ ์งํ๋ ํ๋

    public void order(String name, int price) {
        System.out.println("name = " + name + " price = " + price);
        this.price = price; // ์ฌ๊ธฐ๊ฐ ๋ฌธ์ 
    }

    public int getPrice() {
        return price;
    }
}
```
```java
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


        // ThreadA: A ์ฌ์ฉ์ 1000์ ์ฃผ๋ฌธ
        stateFulService1.order("userA", 1000);
        // ThreadB: B ์ฌ์ฉ์ 2000์ ์ฃผ๋ฌธ
        stateFulService2.order("userB", 2000);

        // ThreadA: ์ฌ์ฉ์ A ์ฃผ๋ฌธ ๊ธ์ก ์กฐํ
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

## 8. ์์กด๊ด๊ณ ์๋ ์ฃผ์
### ๋ค์ํ ์์กด๊ด๊ณ ์ฃผ์ ๋ฐฉ๋ฒ
- ์์ฑ์ ์ฃผ์
- ์์ ์ ์ฃผ์(setter ์ฃผ์)
- ํ๋ ์ฃผ์
- ์ผ๋ฐ ๋ฉ์๋ ์ฃผ์

#### ์์ฑ์ ์ฃผ์
- ์์ฑ์๋ฅผ ํตํด์ ์์กด ๊ด๊ณ๋ฅผ ์ฃผ์ํ๋ ๋ฐฉ๋ฒ
- ์์ฑ์ ํธ์ถ ์์ ์ ๋ฑ 1๋ฒ๋ง ํธ์ถ๋๋ ๊ฒ์ด ๋ณด์ฅ๋จ
- **๋ถ๋ณ**, **ํ์** ์์กด๊ด๊ณ์ ์ฌ์ฉ
- ์์ฑ์๊ฐ ํ๋๋ง ์๋ค๋ฉด `@Autowired` ์๋ต ๊ฐ๋ฅ
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

#### ์์ ์ ์ฃผ์(Setter ์ฃผ์)
- setter๋ผ ๋ถ๋ฆฌ๋ ํ๋์ ๊ฐ์ ๋ณ๊ฒฝํ๋ ์์ ์ ๋ฉ์๋๋ฅผ ํต์์ ์์กด๊ด๊ณ๋ฅผ ์ฃผ์ํ๋ ๋ฐฉ๋ฒ
- **์ ํ**, **๋ณ๊ฒฝ** ๊ฐ๋ฅ์ฑ์ด ์๋ ์์กด๊ด๊ณ์ ์ฌ์ฉ
- ์๋ฐ๋น ํ๋กํผํฐ ๊ท์ฝ์ ์์ ์ ๋ฉ์๋ ๋ฐฉ์์ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ
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

#### ํ๋ ์ฃผ์
- ํ๋์ ๋ฐ๋ก ์ฃผ์ํ๋ ๋ฐฉ๋ฒ
- ์ธ๋ถ์์ ๋ณ๊ฒฝ์ด ๋ถ๊ฐ๋ฅํ๋ฏ๋ก ํ์คํธ ํ๊ธฐ ํ๋ฆ
- DI ํ๋ ์์ํฌ๊ฐ ์์ผ๋ฉด ์๋ฌด๊ฒ๋ ํ  ์ ์์
- ์ฌ์ฉ ์ฉ๋
  - ์ ํ๋ฆฌ์ผ์ด์์ ์ค์  ์ฝ๋์ ๊ด๊ณ ์๋ ํ์คํธ ์ฝ๋
  - ์คํ๋ง ์ค์ ์ ๋ชฉ์ ์ผ๋ก ํ๋ `@Configuration` ๊ฐ์ ๊ณณ์์๋ง ํน๋ณํ ์ฉ๋๋ก ์ฌ์ฉ

```java
@Component
public class OrderServiceImpl implements OrderService {
    
    @Autowired
    private MemberRepository memberRepository;
    
    @Autowired
    private DiscountPolicy discountPolicy;
  }
```

#### ์ผ๋ฐ ๋ฉ์๋ ์ฃผ์
- ์ผ๋ฐ ๋ฉ์๋๋ฅผ ํตํด์ ์ฃผ์
- ํ๋ฒ์ ์ฌ๋ฌ ํ๋๋ฅผ ์ฃผ์ ๋ฐ์ ์ ์์
- ์ผ๋ฐ์ ์ผ๋ก ์ ์ฌ์ฉํ์ง ์์

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

### ์ต์์ฒ๋ฆฌ
์ฃผ์ํ  ์คํ๋ง ๋น์ด ์์ด๋ ๋์ํด์ผ ํ  ๋๊ฐ ์์ ๋ `@Autowired`๋ง ์ฌ์ฉํ๋ฉด `required` ์ต์์ ๊ธฐ๋ณธ ๊ฐ์ด `true`๋ก ๋์ด ์์ด ์๋ ์ฃผ์ ๋์์ด ์์ผ๋ฉด ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ค.

์๋ ์ฃผ์ ๋์์ ์ต์์ผ๋ก ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ
- `@Autowired(required=false)`: ์๋ ์ฃผ์ํ  ๋์์ด ์์ผ๋ฉด ์์ ์ ๋ฉ์๋ ์์ฒด๊ฐ ํธ์ถ ์๋จ
- `@Nullable`: ์๋ ์ฃผ์ํ  ๋์์ด ์์ผ๋ฉด null์ด ์๋ ฅ๋จ
- `Optional<>`: ์๋ ์ฃผ์ํ  ๋์์ด ์์ผ๋ฉด `Optional.empty`๊ฐ ์๋ ฅ๋จ

**์ ๋ฆฌ**
- ์์ฑ์ ์ฃผ์ ๋ฐฉ์์ ์ ํํ๋ ์ด์ ๋ ์ฌ๋ฌ๊ฐ์ง๊ฐ ์์ง๋ง, ํ๋ ์์ํฌ์ ์์กดํ์ง ์๊ณ , ์์ํ ์๋ฐ ์ธ์ด์ ํน์ง์ ์ ์ด๋ฆฌ๋ ๋ฐฉ๋ฒ
- ๊ธฐ๋ณธ์ผ๋ก ์์ฑ์ ์ฃผ์์ ์ฌ์ฉํ๊ณ , ํ์ ๊ฐ์ด ์๋ ๊ฒฝ์ฐ๋ ์์ ์ ์ฃผ์ ๋ฐฉ์์ ์ต์์ผ๋ก ๋ถ์ฌ
  - ์์ฑ์ ์ฃผ์๊ณผ ์์ ์ ์ฃผ์ ๋์ ์ฌ์ฉ ๊ฐ๋ฅ
- ํญ์ ์์ฑ์ ์ฃผ์์ ์ ํ

**Lombok**
```gradle
//lombok ์ค์  ์ถ๊ฐ ์์
configurations {
	compileOnly {
		extendsFrom annotationProcessor
	}
}
//lombok ์ค์  ์ถ๊ฐ ๋

//lombok ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ถ๊ฐ ์์
compileOnly 'org.projectlombok:lombok'
annotationProcessor 'org.projectlombok:lombok'

testCompileOnly 'org.projectlombok:lombok'
testAnnotationProcessor 'org.projectlombok:lombok'
//lombok ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ถ๊ฐ ๋
```
๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ ์ฉ ๋ฐฉ๋ฒ
1. Preferences -> plugin -> lombok ๊ฒ์ ์ค์น ์คํ
2. Preferences -> Annotation Processors ๊ฒ์ -> Enable annotation processing ์ฒดํฌ

**Lombok์ ์ ์ฉํ ์ฝ๋**
```java
@Component
@RequiredArgsConstructor
public class OrderServiceImpl implements OrderService{

    private final MemberRepository memberRepository;
    private final DiscountPolicy discountPolicy;
}
```

### ์กฐํ ๋น์ด 2๊ฐ ์ด์ - ๋ฌธ์ 
`@Autowired`๋ ํ์์ผ๋ก ์กฐํํ๋ค. ํ์์ผ๋ก ์กฐํํ๋ฉด ์ ํ๋ ๋น์ด 2๊ฐ ์ด์์ผ ๋ ๋ฌธ์ ๊ฐ ๋ฐ์ํ๋ค.   
`DiscountPolicy`์ ํ์ ํ์์ธ `FixDiscountPolicy`, `RateDiscountPolicy` ๋ ๋ค ์คํ๋ง ๋น์ผ๋ก ์ ์ธํ๋ฉด `NoUniqueBeanDefinitionException` ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ค.

**ํด๊ฒฐ ๋ฐฉ๋ฒ**
- `@Autowired` ํ๋ ๋ช ๋งค์นญ
  - `@Autowired`๋ ํ์ ๋งค์นญ์ ์๋ํ๊ณ , ์ด๋ ์ฌ๋ฌ ๋น์ด ์์ผ๋ฉด ํ๋ ์ด๋ฆ, ํ๋ผ๋ฏธํฐ ์ด๋ฆ์ผ๋ก ๋น ์ด๋ฆ์ ์ถ๊ฐ ๋งค์นญํ๋ค.
- `@Qualifier` ์ฌ์ฉ
  - ์ถ๊ฐ ๊ตฌ๋ถ์๋ฅผ ๋ถ์ฌ์ฃผ๋ ๋ฐฉ๋ฒ
- `@Primary`
  - ์ฐ์ ์์๋ฅผ ์ ํ๋ ๋ฐฉ๋ฒ

### ์กฐํํ ๋น์ด ๋ชจ๋ ํ์ํ  ๋
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

## 9. ๋น ์๋ช์ฃผ๊ธฐ ์ฝ๋ฐฑ
**์คํ๋ง ๋น์ lifecycle**
1. ๊ฐ์ฒด ์์ฑ
2. ์์กด๊ด๊ณ ์ฃผ์

**์คํ๋ง ๋น์ ์ด๋ฒคํธ lifecycle**
1. ์คํ๋ง ์ปจํ์ด๋ ์์ฑ
2. ์คํ๋ง ๋น ์์ฑ
3. ์์กด๊ด๊ณ ์ฃผ์
4. ์ด๊ธฐํ ์ฝ๋ฐฑ
5. ์ฌ์ฉ
6. ์๋ฉธ์  ์ฝ๋ฐฑ
7. ์คํ๋ง ์ข๋ฃ

- **์ด๊ธฐํ ์ฝ๋ฐฑ**: ๋น์ด ์์ฑ๋๊ณ , ๋น์ ์์กด๊ด๊ณ ์ฃผ์์ด ์๋ฃ๋ ํ ํธ์ถ
- **์๋ฉธ์  ์ฝ๋ฐฑ**: ๋น์ด ์๋ฉธ๋๊ธฐ ์ง์ ์ ํธ์ถ

> ๐ก **๊ฐ์ฒด์ ์์ฑ๊ณผ ์ด๊ธฐํ๋ฅผ ๋ถ๋ฆฌํ์**   
> ์์ฑ์๋ ํ์ ์ ๋ณด(ํ๋ผ๋ฏธํฐ)๋ฅผ ๋ฐ๊ณ  ๋ฉ๋ชจ๋ฆฌ๋ฅผ ํ ๋นํด์ ๊ฐ์ฒด๋ฅผ ์์ฑํ๋ ์ฑ์์ ๊ฐ์ง๋ค. ๋ฐ๋ฉด์ ์ด๊ธฐํ๋ ์ด๋ ๊ฒ ์์ฑ๋ ๊ฐ๋ค์ ํ์ฉํด์ ์ธ๋ถ ์ปค๋ฅ์์ ์ฐ๊ฒฐํ๋ ๋ฑ ๋ฌด๊ฑฐ์ด ๋์์ ์ํํ๋ค. ๋ฐ๋ผ์ ์์ฑ์ ์์์ ๋ฌด๊ฑฐ์ด ์ด๊ธฐํ ์์์ ํจ๊ป ํ๋ ๊ฒ๋ณด๋ค ๊ฐ์ฒด๋ฅผ ์์ฑํ๋ ๋ถ๋ถ๊ณผ ์ด๊ธฐํ ํ๋ ๋ถ๋ถ์ ๋ชํํ๊ฒ ๋๋๋ ๊ฒ์ด ์ ์ง๋ณด์์์ ๊ด์ ์์ ์ข๋ค. ๋ฌผ๋ก  ์ด๊ธฐํ ์์์ด ๋ถ ๊ฐ๋ค๋ง ์ฝ๊ฐ ๋ณ๊ฒฝํ๋ ์ ๋๋ก ๋จ์ํ ๊ฒฝ์ฐ์๋ ์์ฑ์์์ ํ๋ฒ์ ๋ค ์ฒ๋ฆฌํ๋๊ฒ ๋ ๋์ ์ ์๋ค.

**์คํ๋ง์ ๋น ์๋ช์ฃผ๊ธฐ ์ฝ๋ฐฑ**
- ์ธํฐํ์ด์ค (`InitializingBean`, `DisposableBean`)
  - ์คํ๋ง ์ ์ฉ ์ธํฐํ์ด์ค
  - ์คํ๋ง ์ ์ฉ ์ธํฐํ์ด์ค์ ์์กด
  - ์ด๊ธฐํ, ์๋ฉธ ๋ฉ์๋์ ์ด๋ฆ์ ๋ณ๊ฒฝํ  ์ ์์
  - ์ธ๋ถ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ ์ ์ฉ์ ํ  ์ ์์
- ์ค์  ์ ๋ณด์ ์ด๊ธฐํ ๋ฉ์๋, ์ข๋ฃ ๋ฉ์๋ ์ง์ 
  - ๋ฉ์๋ ์ด๋ฆ์ ์์ ๋กญ๊ฒ ์ค ์ ์์
  - ์คํ๋ง ์ฝ๋์ ์์กดํ์ง ์์
  - ์ค์  ์ ๋ณด๋ฅผ ์ฌ์ฉํ๊ธฐ ๋๋ฌธ์ ์ธ๋ถ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์๋ ์ด๊ธฐํ, ์ข๋ฃ ๋ฉ์๋๋ฅผ ์ ์ฉ ํ  ์ ์์
- `@PostConstruct`, `@PreDestroy`
  - ์๋ฐ ํ์ค์ด๊ธฐ๋๋ฌธ์ ์คํ๋ง์ ์ข์์ ์ด์ง ์์
  - ์ธ๋ถ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์๋ ์ ์ฉ์ํ์ง ๋ชปํจ

## 10. ๋น ์ค์ฝํ
๋น์ด ์กด์ฌํ  ์ ์๋ ๋ฒ์๋ฅผ ๋ปํจ

**์ค์ฝํ ์ข๋ฅ**
- **์ฑ๊ธํค**: ๊ธฐ๋ณธ ์ค์ฝํ, ์คํ๋ง ์ปจํ์ด๋์ ์์๊ณผ ์ข๋ฃ๊น์ง ์ ์ง๋๋ ๊ฐ์ฅ ๋์ ๋ฒ์์ ์ค์ฝํ
- **ํ๋กํ ํ์**: ์คํ๋ง ์ปจํ์ด๋๋ ํ๋กํ ํ์ ๋น์ ์์ฑ๊ณผ ์์กด๊ด๊ณ ์ฃผ์๊น์ง๋ง ๊ด์ฌํ๊ณ  ๋๋ ๊ด๋ฆฌํ์ง ์๋ ๋งค์ฐ ์งง์ ๋ฒ์์ ์ค์ฝํ
- ์น ๊ด๋ จ ์ค์ฝํ
  - **request**: ์น ์์ฒญ์ด ๋ค์ด์ค๊ณ  ๋๊ฐ ๋๊น์ง ์ ์ง๋๋ ์ค์ฝํ
  - **session**: ์น ์ธ์์ด ์์ฑ๋๊ณ  ์ข๋ฃ๋  ๋๊น์ง ์ ์ง๋๋ ์ค์ฝํ
  - **application**: ์น์ ์๋ธ๋ฆฟ ์ปจํ์คํธ์ ๊ฐ์ ๋ฒ์๋ก ์ ์ง๋๋ ์ค์ฝํ

### ํ๋กํ ํ์ ์ค์ฝํ
์ฑ๊ธํค ์ค์ฝํ์ ๋น์ ์กฐํํ๋ฉด ์คํ๋ง ์ปจํ์ด๋๋ ํญ์ ๊ฐ์ ์ธ์คํด์ค์ ์คํ๋ง ๋น์ ๋ฐํํ๋ค. ๋ฐ๋ฉด์ ํ๋กํ ํ์ ์ค์ฝํ๋ฅผ ์คํ๋ง ์ปจํ์ด๋์ ์กฐํํ๋ฉด ์คํ๋ง ์ปจํ์ด๋๋ ํญ์ ์๋ก์ด ์ธ์คํด์ค๋ฅผ ์์ฑํด์ ๋ฐํํ๋ค.

**์ฑ๊ธํค ๋น ์์ฒญ**   
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158382920-9a58628f-4ab5-497f-a248-89cd7f956bac.png">

1. ์ฑ๊ธํค ์ค์ฝํ์ ๋น์ ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญ
2. ์คํ๋ง ์ปจํ์ด๋๋ ๋ณธ์ธ์ด ๊ด๋ฆฌํ๋ ์คํ๋ง ๋น์ ๋ฐํ
3. ์ดํ ์คํ๋ง ์ปจํ์ด๋์ ๊ฐ์ ์์ฒญ์ด ์๋ ๊ฐ์ ๊ฐ์ฒด ์ธ์คํด์ค์ ์คํ๋ง ๋น์ ๋ฐํ

**ํ๋กํ ํ์ ๋น ์์ฒญ**   
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158383276-0ff845fd-f1ed-4fd9-8962-bad1c3726b25.png">

1. ํ๋กํ ํ์ ์ค์ฝํ์ ๋น์ ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญ
2. ์คํ๋ง ์ปจํ์ด๋๋ ์ด ์์ ์ ํ๋กํ ํ์ ๋น์ ์์ฑํ๊ณ , ํ์ํ ์์กด๊ด๊ณ๋ฅผ ์ฃผ์

<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158383500-0247aab4-76d1-4957-b9e6-74e109d9fbec.png">

3. ์คํ๋ง ์ปจํ์ด๋๋ ์์ฑํ ํ๋กํ ํ์ ๋น์ ํด๋ผ์ด์ธํธ์๊ฒ ๋ฐํ
4. ์ดํ ์คํ๋ง ์ปจํ์ด๋์ ๊ฐ์ ์์ฒญ์ด ์ค๋ฉด ํญ์ ์๋ก์ด ํ๋กํ ํ์ ๋น์ ์์ฑํด์ ๋ฐํ

**ํ๋กํ ํ์ ๋น์ ํน์ง ์ ๋ฆฌ**
- ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญํ  ๋๋ง๋ค ์๋ก ์์ฑ๋จ
- ์คํ๋ง ์ปจํ์ด๋๋ ํ๋กํ ํ์ ๋น์ ์์ฑ๊ณผ ์์กด๊ด๊ณ ์ฃผ์ ๊ทธ๋ฆฌ๊ณ  ์ด๊ธฐํ๊น์ง๋ง ๊ด์ฌํจ
- `@PreDestory`๊ฐ์ ์ข๋ฃ ๋ฉ์๋๊ฐ ํธ์ถ๋์ง ์์
- ํ๋กํ ํ์ ๋น์ ํ๋กํ ํ์ ๋น์ ์กฐํํ ํด๋ผ์ด์ธํธ๊ฐ ๊ด๋ฆฌํด์ผ ํ๊ณ  ์ข๋ฃ ๋ฉ์๋์ ๋ํ ํธ์ถ๋ ํด๋ผ์ด์ธํธ๊ฐ ์ง์  ํด์ผํจ

#### ์ฑ๊ธํค ๋น์์ ํ๋กํ ํ์ ๋น ์ฌ์ฉ
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158385976-c3848b03-2f1a-46be-82ba-6ce542fc5c92.png">

- `clientBean`์ ์ฑ๊ธํค์ด๋ฏ๋ก, ๋ณดํต ์คํ๋ง ์ปจํ์ด๋ ์์ฑ ์์ ์ ํจ๊ป ์์ฑ๋๊ณ , ์์กด๊ด๊ณ ์ฃผ์๋ ๋ฐ์ํ๋ค.
- `clinetBean`์ ํ๋กํ ํ์ ๋น์ ๋ด๋ถ ํ๋์ ๋ณด๊ดํ๋ค.

<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158386665-fd017eb6-7aa3-41f8-ae98-04f69b55b21c.png">

- ํด๋ผ์ด์ธํธ A๋ `clientBean`์ ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญํด์ ๋ฐ๋๋ค. ์ฑ๊ธํค์ด๋ฏ๋ก ํญ์ ๊ฐ์ `clientBean`์ด ๋ฐํ๋๋ค.

<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158387215-ffaaba10-5c2a-4164-a1cf-dac00317713f.png">

- ํด๋ผ์ด์ธํธ B๋ `clientBean`์ ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญํด์ ๋ฐ๋๋ค. ์ฑ๊ธํค์ด๋ฏ๋ก ํญ์ ๊ฐ์ฒด ์ธ์คํด์ค๊ฐ ๋ฐํ๋๋ค.
- `clientBean`์ด ๋ด๋ถ์ ๊ฐ์ง๊ณ  ์๋ ํ๋กํ ํ์ ๋น์ ์ด๋ฏธ ๊ณผ๊ฑฐ์ ์ฃผ์์ด ๋๋ ๋น์ด๊ธฐ ๋๋ฌธ์ ์ฌ์ฉํ  ๋๋ง๋ค ์๋ก ์์ฑ๋์ง ์๋๋ค.

**๋ฌธ์ ์ **  
- ๊ฐ ํด๋ผ์ด์ธํธ๋ ๊ฐ์ ์ธ์คํด์ค๋ฅผ ๋ฐํ๋ฐ๊ธฐ ๋๋ฌธ์ count๋ 1์ด ์๋ 2๊ฐ ๋ฐํ๋๋ค.

**ํด๊ฒฐ ๋ฐฉ๋ฒ**
1. ์คํ๋ง ์ปจํ์ด๋์ ์์ฒญ
```java
@Scope("singleton")
@RequiredArgsConstructor
static class ClientBean {

  @Autowired
  private ApplicationContext ac;

  public int logic() {
    PrototypeBean prototypeBean = ac.getBean(Prototybean.class);
    prototypeBean.addCount();
    return prototypeBean.getCount();
  }
}
```
- ์์กด๊ด๊ณ๋ฅผ ์ธ๋ถ์์ ์ฃผ์ ๋ฐ๋๊ฒ ์๋๋ผ ์ง์  ํ์ํ ์์กด๊ด๊ณ๋ฅผ ์ฐพ์ ๊ฒ์ ์์กด๊ด๊ณ ์กฐํ(Dependency Lookup, DL)๋ผ ํ๋ค.
- ์ ์ฝ๋๊ฐ์ด ์คํ๋ง์ `ApplicationContext` ์ ์ฒด๋ฅผ ์ฃผ์๋ฐ๊ฒ ๋๋ฉด, ์คํ๋ง ์ปจํ์ด๋์ ์ข์์ ์ธ ์ฝ๋๊ฐ ๋๊ณ , ๋จ์ ํ์คํธ๋ ์ด๋ ค์์ง๋ค.

2. ObjectProvider
```java
@Scope("singleton")
@RequiredArgsConstructor 
static class ClientBean {

  private final ObjectProvider<PrototypeBean> prototypeBeanProvider;

  public int logic() {
    PrototypeBean prototypeBean = prototypeBeanProvider.getObject();
    prototypeBean.addCount();
    return prototypeBean.getCount();
  }
}
```
- `prototypeBeanProvider.getObject()`์ ํตํด์ ํญ์ ์๋ก์ด ํ๋กํ ํ์ ๋น์ด ์์ฑ๋จ
- `ObjectProvider`์ `getOjbect()`๋ฅผ ํธ์ถํ๋ฉด ๋ด๋ถ์์ ์คํ๋ง ์ปจํ์ด๋๋ฅผ ํตํด ํด๋น ๋น์ ์ฐพ์์ ๋ฐํํ๋ค.(DL)
- ์คํ๋ง์ด ์ ๊ณตํ๋ ๊ธฐ๋ฅ์ ์ฌ์ฉ
- ๊ธฐ๋ฅ์ด ๋จ์ํ๋ฏ๋ก ๋จ์ํ์คํธ๋ฅผ ๋ง๋ค๊ฑฐ๋ mock ์ฝ๋๋ฅผ ๋ง๋ค๊ธฐ๊ฐ ์ฌ์

**ObjectFactory vs ObjectProvider**
- ObjectFactory: ๊ธฐ๋ฅ์ด ๋จ์, ๋ณ๋์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ ํ์ ์์, ์คํ๋ง์ ์์กด
- ObjectProvider: ObjectFactory ์์, ์ต์๊ณผ ์คํธ๋ฆผ ์ฒ๋ฆฌ๋ฑ ํธ์ ๊ธฐ๋ฅ์ด ๋ง๊ณ  ๋ณ๋์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ ํ์ ์์, ์คํ๋ง์ ์์กด

3. JSR-330 Provider
```java
@Scope("singleton")
@RequiredArgsConstructor 
static class ClientBean {

  private final Provider<PrototypeBean> provider;

  public int logic() {
    PrototypeBean prototypeBean = provider.get();
    prototypeBean.addCount();
    return prototypeBean.getCount();
  }
}
```
- `javax.inject:javax.inject:1` ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ `build.gradle`์ ์ถ๊ฐํด์ผ ํจ
- ์๋ฐ ํ์ค
- ObjectProvider์ ํน์ง๊ณผ๊ฐ์

### ์น ์ค์ฝํ
์น ํ๊ฒฝ์์๋ง ๋์ํ๊ณ  ์คํ๋ง์ด ํด๋น ์ค์ฝํ์ ์ข๋ฃ์์ ๊น์ง ๊ด๋ฆฌํ๋ค. ๋ฐ๋ผ์ ์ข๋ฃ ๋ฉ์๋๊ฐ ํธ์ถ๋จ

**์น ์ค์ฝํ ์ข๋ฅ**
- **request**: HTTP ์์ฒญ ํ๋๊ฐ ๋ค์ด์ด๊ณ  ๋๊ฐ ๋๊น์ง ์ ์ง๋๋ ์ค์ฝํ, ๊ฐ๊ฐ์ HTTP ์์ฒญ๋ง๋ค ๋ณ๋์ ๋น ์ธ์คํด์ค๊ฐ ์์ฑ๋๊ณ , ๊ด๋ฆฌ๋๋ค.
- **session**: HTTP Session๊ณผ ๋์ผํ ์๋ช์ฃผ๊ธฐ๋ฅผ ๊ฐ์ง๋ ์ค์ฝํ
- **application**: ServletContext์ ๋์ผํ ์๋ช์ฃผ๊ธฐ๋ฅผ ๊ฐ์ง๋ ์ค์ฝํ
- **websocket**: ์น ์์ผ๊ณผ ๋์ผํ ์๋ช์ฃผ๊ธฐ๋ฅผ ๊ฐ์ง๋ ์ค์ฝํ

**HTTP request ์์ฒญ ๋น ๊ฐ๊ฐ ํ ๋น๋๋ Request ์ค์ฝํ**   
<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158393438-426777c1-082d-4b1b-b02c-3b2367a690be.png">

**์ค์ฝํ์ ํ๋ก์**
```java
@Component
@Scope(value = "request", proxyMode = ScopedProxyMode.TARGET_CLASS)
public class MyLogger {
    
}
```
- MyLogger์ ๊ฐ์ง ํ๋ก์ ํด๋์ค๋ฅผ ๋ง๋ค๊ณ  HTTP request์ ์๊ด์์ด ๊ฐ์ง ํ๋ก์ ํด๋์ค๋ฅผ ๋ค๋ฅธ ๋น์ ๋ฏธ๋ฆฌ ์ฃผ์ํด๋ ์ ์์

<img width="538" alt="image" src="https://user-images.githubusercontent.com/45463495/158394141-747c65eb-2f27-461b-bc98-4f98f3ed8a9f.png">

- CGLIB๋ผ๋ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ก ๋ด ํด๋์ค๋ฅผ ์์ ๋ฐ์ ๊ฐ์ง ํ๋ก์ ๊ฐ์ฒด๋ฅผ ๋ง๋ค์ด์ ์ฃผ์ํ๋ค.
- ๊ฐ์ง ํ๋ก์ ๊ฐ์ฒด๋ ์ค์  ์์ฒญ์ด ์ค๋ฉด ๊ทธ๋ ๋ด๋ถ์์ ์ค์  ๋น์ ์์ฒญํ๋ ์์ ๋ก์ง์ด ๋ค์ด์๋ค.
- ๊ฐ์ง ํ๋ก์ ๊ฐ์ฒด๋ ์ค์  request scope์๋ ๊ด๊ณ๊ฐ ์๋ค. ๊ทธ๋ฅ ๊ฐ์ง์ด๊ณ , ๋ด๋ถ์ ๋จ์ํ ์์ ๋ก์ง๋ง ์๊ณ , ์ฑ๊ธํค์ฒ๋ผ ๋์ํ๋ค.

**ํ๋ก์ ํน์ง**
- ํ๋ก์ ๊ฐ์ฒด ๋๋ถ์ ํด๋ผ์ด์ธํธ๋ ๋ง์น ์ฑ๊ธํค ๋น์ ์ฌ์ฉํ๋ฏ์ด ํธ๋ฆฌํ๊ฒ request scope๋ฅผ ์ฌ์ฉํ  ์ ์๋ค.
- Provider๋ฅผ ์ฌ์ฉํ๋ , ํ๋ก์๋ฅผ ์ฌ์ฉํ๋  ํต์ฌ ์์ด๋์ด๋ ์ง์ง ๊ฐ์ฒด ์กฐํ๋ฅผ ๊ผญ ํ์ํ ์์ ๊น์ง ์ง์ฐ์ฒ๋ฆฌ ํ๋ค๋ ์ ์ด๋ค.
- ์ ๋ธํ์ด์ ์ค์  ๋ณ๊ฒฝ๋ง์ผ๋ก ์๋ณธ ๊ฐ์ฒด๋ฅผ ํ๋ก์ ๊ฐ์ฒด๋ก ๋์ฒดํ  ์ ์๋ค. ์ด๊ฒ์ด ๋ฐ๋ก ๋คํ์ฑ๊ณผ DI ์ปจํ์ด๋๊ฐ ๊ฐ์ง ํฐ ๊ฐ์ ์ด๋ค.
- ์น ์ค์ฝํ๊ฐ ์๋๋ผ๋ ํ๋ก์๋ ์ฌ์ฉํ  ์ ์๋ค.
