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
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day61-conditional-return.png" width="500" /><br/>
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

---

# ✅ Day 17– Java for 반복문과 메서드 활용

## 📘 1. 개념 정리

- `for` 반복문은 정해진 횟수만큼 코드를 반복 실행할 때 사용하는 기본 반복문
- 구조: `for (초기식; 조건식; 증감식) { ... }`
- 반복문 안에서 메서드를 사용하면 반복 동작을 더 효율적으로 관리할 수 있음
- 메서드에 매개변수를 전달해 반복 횟수나 메시지를 외부에서 제어 가능

---

## 🧪 2. 실습 명령어

```java
// LoopBasic.java
for (int i = 0; i < 5; i++) {
    System.out.println("안녕하세요!");
}

// RepeatMessage.java
repeatHello(3); // 메서드 호출
public static void repeatHello(int count) {
    for (int i = 0; i < count; i++) {
        System.out.println("Hello!");
    }
}

// NumberedLines.java
printLines(4); // 메서드 호출
public static void printLines(int count) {
    for (int i = 1; i <= count; i++) {
        System.out.println(i + "번째 줄입니다.");
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day62-for-basic.png" width="500" /><br/>
  > 기본 for문을 사용한 반복 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day62-for-method.png" width="500" /><br/>
  > 메서드 내부에서 반복문을 실행하여 Hello 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day62-for-numbered.png" width="500" /><br/>
  > 반복문에서 줄 번호를 붙여 출력하는 메서드 실행 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- 반복문 종료 조건을 `i <= count`로 설정할 때 off-by-one 오류 주의 (원하는 횟수보다 1번 더 실행될 수 있음)
- 반복문 내에서 출력할 때 `i`가 0부터 시작하면 사용자 입장에서 어색할 수 있음 → 1부터 시작하도록 조정
- 메서드 재사용성과 테스트 편의성을 고려해, 반복 횟수는 하드코딩 대신 매개변수로 받도록 설계

---

## 💭 느낀 점

- `for` 반복문은 단순 반복 출력뿐만 아니라 로직 구성에 유용하게 사용된다는 점을 실습으로 체감
- 메서드와 결합하니 코드 구조가 더 읽기 쉽고 재사용성이 높아져 개발자의 효율성이 올라가는 것을 느낌
- 반복문이 추상적이라고 생각했었는데, 실제 예제를 통해 직관적으로 이해되었고 자신감이 붙기 시작함

---

# ✅ Day 18– Java 반복문 실전 패턴

## 📘 1. 개념 정리

- `for` 반복문은 문자열의 각 문자에 순차적으로 접근할 때 유용하다.
- `.length()`는 문자열의 총 글자 수를 반환하며 반복 조건으로 활용된다.
- `.charAt(i)`는 문자열에서 i번째 문자를 반환한다.
- 반복문 안에서 `if (i == 0 || i == str.length() - 1)`로 특정 위치(첫/마지막)만 구분 가능하다.

---

## 🧪 2. 실습 명령어

```java
// CharPrinter.java
for (int i = 0; i < name.length(); i++) {
    System.out.println(name.charAt(i));
}

// NumberedChars.java
for (int i = 0; i < word.length(); i++) {
    System.out.println((i + 1) + ". " + word.charAt(i));
}

// FirstLastHighlighter.java
for (int i = 0; i < word.length(); i++) {
    if (i == 0 || i == word.length() - 1) {
        System.out.println("*" + word.charAt(i) + "*");
    } else {
        System.out.println(word.charAt(i));
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day63-char-printer.png" width="500" height="300"/><br/>
  > 문자열의 각 글자를 한 줄씩 출력한 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day63-numbered-chars.png" width="500" height="300"/><br/>
  > 각 글자 앞에 번호를 붙여 출력한 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day63-firstlast-highlight.png" width="500" height="300"/><br/>
  > 첫 글자와 마지막 글자에 별(*)을 붙여 강조한 출력 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- 문자열의 마지막 글자를 처리할 때 `word.length() - 1`을 정확히 기억해야 오류 방지 가능
- `charAt()`은 인덱스가 유효한 범위를 벗어나면 `StringIndexOutOfBoundsException`이 발생하므로 `i < word.length()` 조건이 매우 중요함
- 반복문과 조건문을 결합하여 위치 기반 출력 제어가 가능하다는 점이 핵심

---

## 💭 느낀 점

- 문자열을 다루는 반복문을 직접 작성하면서 반복 구조가 실무에 어떻게 활용될 수 있는지 감이 잡힘
- 특히 번호 매기기나 특정 문자 강조 같은 기능은 UI 개발에서도 자주 쓰일 수 있는 패턴이라 더 의미 있었음
- 자바의 기본기인 `for + charAt + length` 조합이 얼마나 강력한지를 체감한 하루

---

# ✅ Day 19– Java 문자열 반복과 조건 처리

## 📘 1. 개념 정리

- `for` 반복문을 역방향으로 돌리면 문자열을 거꾸로 출력 가능
- `charAt(i)`를 통해 각 문자를 추출하여 조건 분기 가능
- 모음을 세거나 공백을 제거할 때는 `if` 조건문과 `+=` 연산 활용
- 문자열 누적 시 성능은 낮지만, 기본 로직을 이해하는 데 적합

---

## 🧪 2. 실습 명령어

```java
// ReverseString.java
for (int i = word.length() - 1; i >= 0; i--) {
    System.out.print(word.charAt(i));
}

// CountVowels.java
if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
    count++;
}

// RemoveSpaces.java
if (ch != ' ') {
    result += ch;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day64-reverse-string.png" width="500" height="300/><br/>
  > 문자열을 거꾸로 출력한 결과 ("banana" → "ananab")
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day64-count-vowels.png" width="500" /><br/>
  > 입력한 문자열의 모음 개수를 출력한 결과 ("developer" → 4개)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day64-remove-spaces.png" width="500" /><br/>
  > 공백을 제거한 문자열 출력 결과 ("hello world java" → "helloworldjava")
</p>

---

## 🛠️ Troubleshooting & 기록

- 문자열 누적 시 `+=` 연산은 반복적으로 새로운 문자열을 생성함 → 성능은 떨어지나 초보자 로직 구현엔 적합
- `charAt()` 사용 시 인덱스 초과 주의 (`length - 1`까지 접근 가능)
- `for` 역순 반복은 시작 인덱스를 `length() - 1`로 정확히 설정해야 함

---

## 💭 느낀 점

- 반복문과 조건문, 문자열 조작이 실전에 어떻게 쓰이는지 감이 잡힘
- 단순 출력 이상으로 조건 분기를 통한 데이터 가공 능력이 향상됨
- 점점 실무에서 사용될 만한 로직 구성 능력이 붙는 느낌이 들었음
