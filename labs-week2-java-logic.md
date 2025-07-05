# 🧪 실습 기록 - 2주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 08 – Java문자열 조건문 로직 구성

## 📘 1. 개념 정리  
- 문자열 비교는 반드시 `.equals()` 메서드를 사용해야 정확한 비교 가능  
- `contains()` → 특정 문자열 포함 여부 확인  
- `startsWith()` → 접두어로 시작하는지 확인  
- `trim()` + `isEmpty()` → 문자열이 비어 있는지 공백 제거 후 확인

---

## 🧪 2. 실습 명령어  

```
public class StringConditionPractice {
    public static void main(String[] args) {
        // 1. 문자열 내용 비교
        String answer = "yes";
        if (answer.equals("yes")) {
            System.out.println("정답입니다.");
        } else {
            System.out.println("오답입니다.");
        }

        // 2. 포함 여부 확인
        String message = "오늘은 Java 공부를 했습니다.";
        if (message.contains("Java")) {
            System.out.println("자바가 포함되어 있습니다.");
        }

        // 3. 시작하는 단어 확인
        String filename = "report2025.pdf";
        if (filename.startsWith("report")) {
            System.out.println("보고서 파일입니다.");
        }

        // 4. 공백 문자열 검사
        String emptyCheck = "   ";
        if (emptyCheck.trim().isEmpty()) {
            System.out.println("문자열이 비어 있습니다.");
        }
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day53-equals-check.png" width="450" height="80"/><br/>
  > `equals()`로 문자열 내용 비교
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day53-contains-check.png" width="450" height="80"/><br/>
  > "Java" 포함 여부 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day53-startswith-check.png" width="450" height="80"/><br/>
  > "report"로 시작하는 파일명 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day53-empty-check.png" width="450" height="80"/><br/>
  > 공백 제거 후 비어 있는 문자열 확인
</p>

---

## 🛠️ Troubleshooting & 기록  
- 문자열 비교 시 `==`는 주소값 비교이므로 값 비교가 되지 않음 → `.equals()` 필수  
- `trim()`을 쓰지 않으면 `"   "` 같은 입력은 `isEmpty()`로 false 처리됨 → 항상 조합해서 사용  
- `startsWith()`와 `contains()`는 실전 로직 구성에 매우 유용함 → 조건 분기에서 자주 사용됨

---

## 💭 느낀 점  
- 문자열과 조건문을 연결해서 로직을 구성하는 방식이 처음엔 복잡했지만,  
  직접 써보면서 메서드들의 쓰임새가 머릿속에 정리되기 시작했다.  
- 특히 `trim()` + `isEmpty()`는 사용자 입력 검증 시 실수하기 쉬운 부분이라 중요하게 느껴졌고,  
  조건문 안에서 문자열 메서드를 바로 사용하는 구조가 자연스러워졌다.  
- 입력 없이 하드코딩 방식으로 구성해도 로직 흐름은 충분히 연습 가능하다는 걸 느꼈다.

---

# ✅ Day 09 – Java입력과 출력의 기본 구조

## 📘 1. 개념 정리

- `System.out.println()` : 콘솔에 출력하는 메서드 (`PrintStream` 객체의 메서드)
- `Scanner` : 표준 입력(키보드)을 받기 위한 도구 (`java.util` 패키지에서 제공)
- `nextLine()` : 사용자로부터 한 줄 전체를 입력받음 (공백 포함)
- `equals()` : 문자열 비교를 위한 메서드 (`==` 대신 사용해야 정확함)
- `if-else` : 조건 분기문, 특정 조건이 참일 때만 특정 코드 실행

---

## 🧪 2. 실습 명령어

```
import java.util.Scanner;

public class InputPractice {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("이름을 입력하세요: ");
        String name = sc.nextLine();

        System.out.println("안녕하세요, " + name + "님!");

        if (name.equals("admin")) {
            System.out.println("관리자 계정으로 로그인하셨습니다.");
        } else {
            System.out.println("일반 사용자로 로그인하셨습니다.");
        }

        sc.close();
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day54-admin-login.png" width="500" /><br/>
  > admin 입력 시, 관리자 안내 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day54-user-login.png" width="500" /><br/>
  > 일반 사용자 이름 입력 시, 일반 사용자 안내 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- `nextLine()`은 공백 포함 문자열 전체를 받을 수 있어서 `"홍 길동"` 같은 이름도 처리 가능함
- 문자열 비교는 반드시 `==`가 아닌 `equals()`를 써야 정확한 비교가 됨
- `sc.close()`는 메모리 누수 방지를 위한 자바 습관으로, 아직은 크게 티는 안 나지만 항상 포함할 것

---

## 💭 느낀 점

- `Scanner`와 `System.out`의 구조를 명확히 이해하고 나니, 입력-출력 흐름이 눈에 보이기 시작했다.
- 간단한 조건문으로도 로직을 설계할 수 있다는 점에서 자바의 실용적인 문법 구조가 인상적이었다.
- 내 이름을 입력하고 직접 결과가 출력되는 경험이 동기부여가 되었고, 앞으로 조건문과 반복문을 연결해 더 복잡한 로직을 구성하고 싶어졌다.

---

# ✅ Day 10 – Java조건문 심화실습 (scanner)

## 📘 1. 개념 정리

- 조건문은 위에서부터 아래로 순차적으로 실행되며, 한 번이라도 조건을 만족하면 그 아래 조건은 무시된다.
- `if → else if → else` 구조를 통해 여러 분기 처리가 가능하다.
- 숫자 비교는 `>=`, `==` 등으로 가능하며, 점수 등급 분기 로직에서 자주 사용된다.
- `Scanner`를 통해 사용자 입력을 받고, 그 값에 따라 조건문을 통해 결과를 분기한다.

---

## 🧪 2. 실습 명령어

```
import java.util.Scanner;

public class ScoreGrader {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("점수를 입력하세요: ");
        int score = sc.nextInt();

        if (score >= 90) {
            System.out.println("등급: A");
        } else if (score >= 80) {
            System.out.println("등급: B");
        } else if (score >= 70) {
            System.out.println("등급: C");
        } else {
            System.out.println("등급: D");
        }

        sc.close();
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day55-grade-a.png" width="500" /><br/>
  > 95점 입력 시 A등급 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day55-grade-b.png" width="500" /><br/>
  > 85점 입력 시 B등급 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day55-grade-c.png" width="500" /><br/>
  > 75점 입력 시 C등급 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day55-grade-d.png" width="500" /><br/>
  > 60점 입력 시 D등급 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- 조건문 순서를 잘못 배치하면 등급이 잘못 출력될 수 있음 → `score >= 90 → 80 → 70` 순서로 정렬해야 정확하게 분기됨
- `else if`를 사용하지 않고 `if`만 여러 개 쓰면 중복 실행 가능성 있음 → `else if`는 반드시 연결해서 단일 실행 구조로 구성해야 함
- `Scanner` 사용 후 반드시 `sc.close()`로 리소스 정리하는 습관 들이기

---

## 💭 느낀 점

- if문이 단순한 조건 판별을 넘어서 프로그램의 흐름을 나누는 핵심이라는 걸 체감했다.
- 조건 순서를 설계하는 데 있어서 "우선순위" 개념이 명확히 작동한다는 점이 인상 깊었고, 점수 등급처럼 실무적인 조건 로직에도 직접 적용할 수 있을 것 같았다.
- 아직은 짧은 코드지만, 조건 분기를 통해 사용자에게 맞춤형 출력을 해준다는 점에서 실제 프로그램을 만드는 느낌이 들었다.

---

# ✅ Day 11 – Java switch-case 문 기본 구조 학습

## 📘 1. 개념 정리

- `switch` 문은 하나의 값을 기준으로 여러 `case` 중 하나를 실행하는 조건 분기 구조이다.
- `case`는 해당 값이 일치할 때 실행되고, `break`로 종료되지 않으면 아래 case까지 연쇄적으로 실행된다 (fall-through).
- `default`는 어느 case에도 해당하지 않는 경우 실행된다.
- `Scanner`를 통해 사용자에게 학년을 입력받아, 각 학년에 맞는 안내 메시지를 출력하는 프로그램을 작성하였다.

---

## 🧪 2. 실습 명령어

```java
import java.util.Scanner;

public class GradeChecker {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("당신의 학년을 입력하세요 (1~3): ");
        int grade = sc.nextInt();

        switch (grade) {
            case 1:
                System.out.println("1학년입니다.");
                break;
            case 2:
                System.out.println("2학년입니다.");
                break;
            case 3:
                System.out.println("3학년입니다.");
                break;
            default:
                System.out.println("알 수 없는 학년입니다.");
        }

        sc.close();
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day56-grade-1.png" width="500" /><br/>
  > 1 입력 시 "1학년입니다." 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day56-grade-2.png" width="500" /><br/>
  > 2 입력 시 "2학년입니다." 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day56-grade-3.png" width="500" /><br/>
  > 3 입력 시 "3학년입니다." 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day56-grade-unknown.png" width="500" /><br/>
  > 5 입력 시 "알 수 없는 학년입니다." 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- `break`를 빠뜨리면 다음 case까지 연쇄적으로 실행됨 (fall-through 현상 발생)
- `default`는 필수가 아니지만, 사용자 입력값이 예상 범위를 벗어날 수 있으므로 반드시 작성하는 것이 좋음
- `switch`는 `int`, `char`, `String`, `enum` 등에만 사용 가능하며, `boolean`, `double`은 사용할 수 없음

---

## 💭 느낀 점

- `switch` 문이 `if-else`보다 훨씬 **깔끔하게 조건을 나눌 수 있다는 점**이 인상 깊었다.
- 조건이 단순하고 **정해진 값들만 비교할 때는** `switch`가 가독성, 유지보수 면에서 유리하다는 걸 깨달았다.
- 특히 `break`의 역할을 제대로 인식하고 나니 코드 흐름을 훨씬 명확하게 제어할 수 있었다.
