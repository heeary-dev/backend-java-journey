# 🧪 실습 기록 - 1주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

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




