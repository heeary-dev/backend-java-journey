# 🧪 실습 기록 - 1주차 labs.md

> 실습과 결과를 정리하는 공간입니다

---

# ✅ Day 01 – Java 시작하기: HelloWorld 실행

## 📘 1. 개념 정리

- Java는 객체 지향 언어이며 플랫폼 독립성을 갖는다.
- Java는 JDK로 개발하고, JVM을 통해 실행된다.
- JDK > JRE > JVM 구조로 포함 관계를 가진다.
- IntelliJ는 Java 프로젝트 개발을 위한 통합 개발 환경(IDE)이다.
- 프로젝트 구조:
  - `src/`: 소스 코드 저장
  - `out/`: 컴파일된 클래스 파일 저장
  - `.idea/`: 설정 파일 저장

---

## 🧪 2. 실습 명령어

```
// HelloWorld.java

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day46-helloworld-run.png" width="450" /><br/>
  > IntelliJ에서 HelloWorld.java 실행 후 "Hello, Java!"가 출력된 모습
</p>

---

## 🛠️ 4. Troubleshooting & 기록

- IntelliJ에서 JDK가 자동으로 설정되지 않는 경우, `Project Structure` → `SDKs` 메뉴에서 수동으로 추가해야 함
- `Run` 실행 시 콘솔에 아무 것도 출력되지 않는다면 Run Configuration을 확인할 것 (main 메서드가 있는 클래스가 제대로 지정되었는지)

---

## 💭 5. 느낀 점

- 자바 학습을 IntelliJ 기반으로 시작하니 개발 흐름이 직관적이었다.
- 단순한 `Hello, Java!` 출력이지만, JDK → 컴파일 → JVM 실행 과정을 명확히 이해할 수 있었다.
- 앞으로 실습을 진행할 때 **스크립트-출력 결과-스크린샷** 흐름을 더 명확히 유지해야겠다고 다짐했다.

---

# ✅ Day 02 – Java변수와 자료형 기초 다지기

## 📘 1. 개념 정리

- 변수는 이름이 붙은 메모리 공간으로, 데이터를 저장하고 재사용하기 위한 목적을 가진다.
- 자바는 변수를 선언할 때 반드시 자료형을 명시해야 한다.
- 자료형은 크게 기본형(Primitive Type)과 참조형(Reference Type)으로 나뉜다.
  - 기본형: int, double, boolean, char, long, float 등
  - 참조형: String, 배열, 클래스 등
- 형 변환에는 자동 형 변환과 강제 형 변환이 있다.
  - 자동: 작은 타입 → 큰 타입 (int → double)
  - 강제: 큰 타입 → 작은 타입 (double → int, 데이터 손실 발생 가능)

---

## 🧪 2. 실습 명령어

```
// VariablePractice.java

public class VariablePractice {
    public static void main(String[] args) {

        // 정수형 변수 선언 및 초기화
        int age = 25;
        long population = 8000000000L;

        // 실수형 변수
        double pi = 3.14159;
        float temperature = 36.5f;

        // 문자형 변수
        char bloodType = 'O';

        // 논리형 변수
        boolean isStudent = true;

        // 문자열 (참조형)
        String name = "Heesung";

        // 변수 출력
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Population: " + population);
        System.out.println("PI: " + pi);
        System.out.println("Temperature: " + temperature);
        System.out.println("Blood Type: " + bloodType);
        System.out.println("Is Student?: " + isStudent);

        // 형 변환 예제
        int a = 10;
        double b = a; // 자동 형 변환
        System.out.println("Auto cast int → double: " + b);

        double x = 9.99;
        int y = (int)x; // 강제 형 변환
        System.out.println("Forced cast double → int: " + y);
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day47-variable-output.png" width="450" /><br/>
  > 다양한 자료형의 변수 선언 후 출력한 전체 결과 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day47-type-casting.png" width="450" /><br/>
  > 자동 형 변환(int → double)과 강제 형 변환(double → int) 출력 결과
</p>

---

## 🛠️ 4. Troubleshooting & 기록

- `float temperature = 36.5;`로 작성 시 `incompatible types` 에러 발생 → `36.5f`로 수정 필요
- `long population = 8000000000;` 선언 시 `integer number too large` 에러 → `L` 접미사 필요
- `char` 타입은 반드시 `'A'`처럼 **작은따옴표** 사용해야 하며, `"A"`(큰따옴표)는 `String`으로 인식됨

---

## 💭 5. 느낀 점

- 변수마다 자료형이 다르기 때문에, 초기화할 때 정확한 문법을 지켜야 오류가 나지 않는다.
- 자동 형 변환은 자연스럽지만 강제 형 변환(double → int)에서는 소수점이 잘리는 **데이터 손실**이 일어난다는 점이 인상 깊었다.
- `String`은 참조형이라 메모리 구조가 다르다는 개념이 처음엔 어색했지만, 코드를 통해 간접적으로 느껴볼 수 있었다.

---

# ✅ Day 03 – Java연산자 - 산술, 비교, 논리, 대입, 단항 연산자 실습

## 📘 1. 개념 정리

- 연산자는 변수나 값에 계산, 비교, 논리 판단 등을 수행하는 기호다.
- 자바 연산자는 크게 5가지 종류가 있다:
  - 산술 연산자: `+`, `-`, `*`, `/`, `%`
  - 비교 연산자: `==`, `!=`, `>`, `<`, `>=`, `<=`
  - 논리 연산자: `&&`, `||`, `!`
  - 대입 연산자: `=`, `+=`, `-=`, `*=`, `/=`
  - 단항 연산자: `++`, `--`, `!`, `+`, `-`
- 연산자 우선순위가 명확하지 않을 땐 괄호로 묶어서 처리한다.

---

## 🧪 2. 실습 명령어

```
// OperatorPractice.java

public class OperatorPractice {
    public static void main(String[] args) {

        // 1. 산술 연산자
        int a = 10, b = 3;
        System.out.println("[산술 연산자]");
        System.out.println("a + b = " + (a + b));
        System.out.println("a - b = " + (a - b));
        System.out.println("a * b = " + (a * b));
        System.out.println("a / b = " + (a / b));
        System.out.println("a % b = " + (a % b));

        // 2. 비교 연산자
        System.out.println("\n[비교 연산자]");
        System.out.println("a > b: " + (a > b));
        System.out.println("a == b: " + (a == b));
        System.out.println("a != b: " + (a != b));

        // 3. 논리 연산자
        boolean x = true, y = false;
        System.out.println("\n[논리 연산자]");
        System.out.println("x && y: " + (x && y));
        System.out.println("x || y: " + (x || y));
        System.out.println("!x: " + (!x));

        // 4. 대입 연산자
        int c = 5;
        System.out.println("\n[대입 연산자]");
        c += 3;
        System.out.println("c += 3 → " + c);
        c *= 2;
        System.out.println("c *= 2 → " + c);

        // 5. 단항 연산자
        int i = 1;
        System.out.println("\n[단항 연산자]");
        System.out.println("++i: " + (++i));
        System.out.println("i++: " + (i++));
        System.out.println("i: " + i);
    }
}
```

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day48-operators-output.png" width="450"/><br/>
  > 산술, 비교, 논리, 대입, 단항 연산자 각각의 출력 결과를 한 화면에 확인한 모습
</p>

---

## 🛠️ 4. Troubleshooting & 기록

- `System.out.println("\n[구분]");` 코드를 활용해 출력 섹션을 시각적으로 나누는 것이 매우 효과적이었다.
- `int / int` 나눗셈 결과는 소수점 없이 **몫만 출력**되기 때문에, 실수 나눗셈이 필요한 경우에는 `double` 또는 `(double)` 형 변환이 필요함.
- `i++`, `++i` 등 단항 연산자의 **출력 시점 차이**를 콘솔로 확인하며 개념이 더 명확해졌다.
- 논리 연산자에서 `&&`와 `||`의 차이(AND vs OR)를 실제 출력값으로 확실히 이해함.

---

## 💭 5. 느낀 점

- 연산자는 단순한 계산 이상의 역할을 하며, 조건문이나 반복문을 설계할 때 필수적으로 사용된다.
- 특히 비교, 논리 연산자는 실무에서도 매우 자주 쓰이므로 `boolean` 결과를 직접 출력해보며 익히는 것이 큰 도움이 되었다.
- 앞으로는 연산자 사용 시 **우선순위와 자료형의 영향**도 항상 염두에 두어야겠다는 것을 실감했다.

---

# ✅ Day 04 – Java 조건문 – if, else if, else, 중첩 조건문

## 📘 1. 개념 정리

- 조건문은 주어진 조건에 따라 코드 실행 흐름을 분기시키는 구조다.
- 기본 형태는 `if`, `else if`, `else`이며, 위에서 아래로 순차적으로 조건을 평가한다.
- 중첩 조건문은 조건문 내부에 또 다른 조건문을 작성하는 방식으로, 복잡한 분기 구조에 사용된다.
- 조건식은 반드시 boolean 타입이어야 하며, 자바에서는 `if (x)` 같은 단축 조건을 사용할 수 없다.

---

## 🧪 2. 실습 명령어

```
// ConditionPractice.java

public class ConditionPractice {
    public static void main(String[] args) {

        // 1. 나이에 따른 분류
        int age = 15;
        System.out.println("[나이 분류]");
        if (age >= 20) {
            System.out.println("성인입니다.");
        } else if (age >= 13) {
            System.out.println("청소년입니다.");
        } else {
            System.out.println("어린이입니다.");
        }

        // 2. 시험 점수 등급
        int score = 92;
        System.out.println("\n[시험 점수 평가]");
        if (score >= 90) {
            System.out.println("A등급");
        } else if (score >= 80) {
            System.out.println("B등급");
        } else if (score >= 70) {
            System.out.println("C등급");
        } else {
            System.out.println("불합격");
        }

        // 3. 로그인 상태 중첩 조건문
        boolean isLoggedIn = true;
        String username = "Heesung";

        System.out.println("\n[로그인 상태 확인]");
        if (isLoggedIn) {
            if (username.equals("Heesung")) {
                System.out.println("환영합니다, Heesung님!");
            } else {
                System.out.println("사용자 이름이 다릅니다.");
            }
        } else {
            System.out.println("로그인이 필요합니다.");
        }
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day49-condition-output.png" width="450" /><br/>
  > 나이 분류, 점수 평가, 로그인 상태 확인을 조건문으로 출력한 전체 결과 화면
</p>

---

## 🛠️ 4. Troubleshooting & 기록

- `else if` 없이 `if`만 여러 개 쓰면, **여러 조건이 동시에 실행**되어 예상과 다른 결과가 나올 수 있음 → 분기문은 순서를 갖는 구조여야 함
- `==`를 문자열 비교에 쓰면 `false`가 나올 수 있음 → 문자열 비교는 반드시 `.equals()` 사용
- 조건식이 boolean이 아닌 경우 (`if (x)` 같은 표현)에는 **컴파일 오류** 발생 → 항상 명시적인 조건식 필요

---

## 💭 느낀 점

- 자바의 조건문은 단순한 판단이 아니라 **로직의 방향을 결정하는 핵심 도구**라는 걸 다시금 느꼈다.
- 특히 중첩 조건문의 흐름과 순서에 따라 결과가 완전히 달라지므로, **코드를 읽는 순서에 민감해져야 한다**.
- 조건이 많아질수록 switch문이나 메서드 분리를 고려해야겠다는 감각이 생겼다.

---

# ✅ Day 05 – Java 조건문 심화 - 논리 연산자, 중첩 조건 개선, return 흐름 제어

## 📘 1. 개념 정리

- 논리 연산자는 조건을 복합적으로 판단할 때 사용하는 연산자이다.
- 주요 논리 연산자:
  - `&&` (AND): 모든 조건이 true일 때 전체 조건이 true
  - `||` (OR): 하나라도 true면 전체 조건이 true
  - `!` (NOT): true → false, false → true로 반전
- 중첩된 if문은 `&&`나 `||`로 결합하여 가독성 좋게 리팩토링할 수 있다.
- `return`은 조건을 만족할 때 메서드 흐름을 조기 종료할 수 있게 한다.

---

## 🧪 2. 실습 명령어

```
// LogicAnd.java
int score = 85;
if (score >= 60 && score <= 100) {
    System.out.println("합격입니다.");
} else {
    System.out.println("불합격입니다.");
}

// LogicOr.java
int temperature = -5;
if (temperature < 0 || temperature > 35) {
    System.out.println("야외활동 위험");
} else {
    System.out.println("활동 가능");
}

// LogicNot.java
boolean isLoggedIn = false;
if (!isLoggedIn) {
    System.out.println("로그인이 필요합니다.");
}

// NestedIfRefactor.java
int x = 7;
if (x > 0 && x < 10) {
    System.out.println("x는 1 이상 9 이하입니다.");
}

// ReturnInIf.java
int age = -1;
if (age < 0) {
    System.out.println("잘못된 나이입니다.");
    return;
}
System.out.println("나이는 " + age + "세입니다.");
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day50-logic-and.png" width="450" /><br/>
  > score가 85일 때 "합격입니다."가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day50-logic-or.png" width="450" /><br/>
  > 온도가 -5일 때 "야외활동 위험"이 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day50-logic-not.png" width="450" /><br/>
  > 로그인 상태가 false일 때 "로그인이 필요합니다."가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day50-nested-refactor.png" width="450" /><br/>
  > x가 7일 때 중첩 if 대신 "x는 1 이상 9 이하입니다."가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day50-return-early-exit.png" width="450" /><br/>
  > age가 -1일 때 "잘못된 나이입니다."만 출력되고 이후 코드가 실행되지 않음
</p>

---

## 🛠️ Troubleshooting & 기록

- 조건식에서 `if (x && y)` 형태는 사용 불가 → 반드시 boolean 결과를 반환하는 비교식 필요
- 복합 조건식에서 괄호를 생략하면 **우선순위 문제**로 예상과 다른 결과 발생 가능
- 중첩된 if문을 `&&`나 `||`로 정리할 경우 코드 흐름이 훨씬 간결해짐
- `return`은 void 메서드에서도 사용 가능하며, 흐름 제어용으로 활용 가능

---

## 💭 느낀 점

- 단순한 if-else 구조에서 벗어나 논리 연산자 기반의 분기 구조를 익히며 사고가 더 정교해졌다.
- `&&`, `||`, `!` 각각의 성질을 명확히 이해한 후 실습에 적용해보니 혼합 조건을 자신 있게 구성할 수 있었다.
- return을 조건 안에 써서 흐름을 차단하는 방식은 실무에서도 매우 효율적으로 활용될 수 있겠다는 감각을 얻었다.

---

# ✅ Day 06 – Java 문자열(String)

## 📘 1. 개념 정리

- 문자열(String)은 문자의 집합으로, 쌍따옴표 `" "`로 감싼 텍스트 데이터를 의미한다.
- `String`은 참조형 자료형이며, 메서드(`length()`, `toUpperCase()` 등)를 사용할 수 있다.
- 문자열 선언은 `String 변수명 = "문자열";` 형태로 한다.
- `+` 연산자를 이용하여 문자열과 문자열, 문자열과 숫자를 연결할 수 있다.
- 숫자와 문자열을 연결하면 숫자가 자동으로 문자열로 변환되어 결합된다.

---

## 🧪 2. 실습 명령어

```
// StringBasic.java

public class StringBasic {
    public static void main(String[] args) {

        // 문자열 변수 선언
        String name = "Heesung";
        String greeting = "Hello";

        // 문자열 연결
        String message = greeting + ", " + name + "!";
        System.out.println(message);

        // 문자열 + 숫자
        int age = 29;
        String info = name + " is " + age + " years old.";
        System.out.println(info);

        // 문자열 메서드 활용
        System.out.println("Length of name: " + name.length());
        System.out.println("Uppercase name: " + name.toUpperCase());
        System.out.println("Lowercase greeting: " + greeting.toLowerCase());
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day51-string-hello.png" width="450" /><br/>
  > 문자열 연결을 통해 "Hello, Heesung!"가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day51-string-age.png" width="450" /><br/>
  > 문자열 + 숫자 연결로 "Heesung is 29 years old."가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day51-string-length.png" width="450" /><br/>
  > name의 글자 수를 출력: "Length of name: 7"
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day51-string-uppercase.png" width="450" /><br/>
  > name을 대문자로 출력: "Uppercase name: HEESUNG"
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day51-string-lowercase.png" width="450" /><br/>
  > greeting을 소문자로 출력: "Lowercase greeting: hello"
</p>

---

## 🛠️ Troubleshooting & 기록

- `String`은 참조형이므로 `.`을 통해 다양한 문자열 메서드를 호출할 수 있다.
- 숫자와 문자열을 `+`로 연결하면 자동으로 숫자가 문자열로 변환되어 붙는다.
- `" "` 없이 문자열을 선언하려 하면 컴파일 오류 발생 → 반드시 쌍따옴표 사용해야 함

---

## 💭 느낀 점

- 문자열 선언과 출력, 연결 방식은 자바의 기본이자 실무에서도 가장 자주 쓰이는 영역임을 실감했다.
- 숫자와 문자열을 같이 다룰 때 자동 형변환이 일어난다는 점이 흥미로웠고, 잘못 쓰면 결과가 달라질 수도 있어 주의가 필요하다고 느꼈다.
- `String`이 단순한 텍스트 저장 그 이상으로, 메서드를 통해 다양한 조작이 가능하다는 점에서 객체형 자료형의 특징을 다시 확인할 수 있었다.

---

# ✅ Day 07 – Java 문자열 비교와 메서드 활용

## 📘 1. 개념 정리

- 문자열 비교는 반드시 `equals()` 메서드를 사용해야 정확한 비교가 가능하다
- `==`는 문자열 객체의 주소값을 비교하므로 값이 같아도 false가 나올 수 있음
- `contains()`는 문자열에 특정 텍스트가 포함되어 있는지 확인
- `startsWith()` / `endsWith()`는 특정 문자열로 시작/끝나는지 판단
- `substring(start, end)`은 부분 문자열을 추출할 때 사용 (end는 포함하지 않음)
- `isEmpty()`는 문자열이 비어 있는지를 boolean 값으로 반환

---

## 🧪 2. 실습 명령어

```
// StringCompare.java

public class StringCompare {
    public static void main(String[] args) {

        // 문자열 비교 (== vs equals)
        String str1 = new String("hello");
        String str2 = new String("hello");

        System.out.println("== result: " + (str1 == str2));
        System.out.println("equals() result: " + str1.equals(str2));

        // contains
        String sentence = "Java programming is fun";
        System.out.println("Contains 'program': " + sentence.contains("program"));

        // startsWith, endsWith
        String word = "Heesung";
        System.out.println("Starts with 'Hee': " + word.startsWith("Hee"));
        System.out.println("Ends with 'ung': " + word.endsWith("ong"));

        // substring
        String code = "HelloJava";
        String part1 = code.substring(0, 5); // "Hello"
        String part2 = code.substring(5);    // "Java"
        System.out.println("First part: " + part1);
        System.out.println("Second part: " + part2);

        // isEmpty
        String emptyStr = "";
        String nonEmptyStr = "data";
        System.out.println("Is emptyStr empty? " + emptyStr.isEmpty());
        System.out.println("Is nonEmptyStr empty? " + nonEmptyStr.isEmpty());
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day52-equals-compare.png" width="450" /><br/>
  > 주소값 비교(false)와 equals 비교(true) 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day52-contains.png" width="450" /><br/>
  > "program"이 포함되어 있음 → true 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day52-starts-ends.png" width="450" /><br/>
  > Heesung이 "Hee"로 시작, "ung"으로 끝남 → true 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day52-substring.png" width="450" /><br/>
  > 부분 문자열 "Hello", "Java"를 추출해서 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day52-isempty.png" width="450" /><br/>
  > 빈 문자열 여부 확인 → true / false 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- 문자열 비교 시 `==`를 사용하면 false가 나올 수 있음 → 반드시 `.equals()` 사용
- `substring(0, 5)`에서 end 인덱스는 **포함되지 않음**을 주의해야 함
- 빈 문자열 확인 시 `isEmpty()`는 `.length() == 0`과 같은 의미이지만 더 직관적임

---

## 💭 느낀 점

- 문자열 비교 시 `==`를 습관적으로 쓸 경우 논리 오류가 발생할 수 있다는 점을 실습을 통해 체감했다.
- `contains`, `startsWith`, `endsWith`는 실제 사용자 입력 처리나 검색 기능에서 매우 유용하게 쓰일 수 있을 것 같다.
- `substring()`을 쓸 때 자바의 인덱스 규칙(0부터 시작, end는 제외)에 주의해야 한다는 것을 다시 한 번 상기하게 되었다.
