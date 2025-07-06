# 🧪 실습 기록 - 3주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 15– Java 메서드의 기초 사용법

## 📘 1. 개념 정리

- 메서드(Method): 특정 기능을 수행하는 코드 블록
- 구성: 반환타입 + 메서드이름 + 매개변수 + 본문
- `void`: 반환값 없이 실행만 하는 메서드
- `return`: 결과값을 반환하는 메서드
- 호출은 반드시 `main()` 메서드 안에서 수행해야 함

---

## 🧪 2. 실습 명령어

```java
public class MethodPractice {

    public static void sayHello() {
        System.out.println("Hello!");
    }

    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        sayHello();                   // void 메서드 호출
        greet("Heeseong");            // 매개변수 있는 void 호출
        int result = add(3, 4);       // return 메서드 호출
        System.out.println("3 + 4 = " + result);
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day60-void-method.png" width="450" /><br/>
  > sayHello() 메서드 호출 결과: Hello!
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day60-void-param.png" width="450"/><br/>
  > greet("Heeseong") 호출 결과: Hello, Heeseong!
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day60-return-method.png" width="450" /><br/>
  > add(3, 4) 호출 결과: 3 + 4 = 7
</p>

---

## 🛠️ Troubleshooting & 기록

- 메서드를 `main()` 외부에 선언하고 호출은 `main()` 내부에서만 해야 함  
- return 메서드의 반환값을 변수에 저장하지 않으면 출력 결과가 안 보임  
- `System.out.println(add(3, 4));`처럼 직접 출력도 가능함

---

## 💭 느낀 점

- 단순 반복되는 코드를 메서드로 나누니 훨씬 깔끔하고 이해하기 쉬움  
- 메서드 이름을 잘 짓는 것이 중요하다는 것을 느꼈고,  
  반복문이나 조건문과 함께 쓰일 때 더 강력할 것 같다는 생각이 듬

---

# ✅ Day 16– Java 메서드 실전 적용과 구조 분리

## 📘 1. 개념 정리

- 메서드는 기능을 독립적으로 분리해주는 코드 블록
- `void` 메서드는 단순 실행, 결과를 반환하지 않음
- `return` 메서드는 결과값을 반환하고, 호출한 곳에서 활용 가능
- 메서드는 클래스 안, main() 밖에 정의하고, main() 안에서 호출함
- 조건문과 return을 결합해 조기 종료, 분기 처리 가능

---

## 🧪 2. 실습 명령어

```java
// VoidMethods.java
sayHello();            // Hello! 출력
greet("Heeseong");     // Hi, Heeseong! 출력
printLine();           // 구분선 출력

// ReturnMethods.java
int result = add(5, 7);                     // 12 반환
System.out.println("합계: " + result);      // 합계: 12 출력

String msg = makeGreeting("Heeseong");     // 문자열 반환
System.out.println(msg);                   // Nice to meet you, Heeseong

// ConditionalMethod.java
System.out.println(checkAge(-1));  // Invalid age
System.out.println(checkAge(15));  // Underage
System.out.println(checkAge(25));  // Adult
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day61-void-method.png" width="500" height="80"/><br/>
  > void 메서드의 정의와 호출 실행 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day61-return-method.png" width="500" height="80"/><br/>
  > 반환값이 있는 메서드 실행 결과 (정수 + 문자열)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day61-conditional-return.png" width="500" height="80"/><br/>
  > 조건문과 return 조합에 따른 분기 실행 결과
</p>

---

## 🛠️ 4. Troubleshooting & 기록

- return이 있는 메서드는 반드시 **반환 타입을 명시**해야 하며, 해당 타입과 **일치하는 값만 return** 가능함
- void 메서드에서 return을 사용할 경우 → `return;`만 허용되고, 값은 줄 수 없음
- 메서드 내 조건 분기는 **if문 + return** 조합으로 깔끔하게 처리 가능

---

## 💭 느낀 점

- 단순 출력이 아닌 **구조적 코드 분리**를 직접 해보면서, 메서드의 진짜 역할을 이해하게 되었다.
- `void`와 `return` 차이를 체감하고, 매개변수를 활용한 코드 재사용에 대한 감각도 잡힘
- 특히 return 조건 분기를 배우며 **유효성 검사, 예외 처리에 활용**될 수 있겠다는 인사이트를 얻음
