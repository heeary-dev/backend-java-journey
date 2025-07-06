# 🧪 실습 기록 - 2주차 labs.md

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

