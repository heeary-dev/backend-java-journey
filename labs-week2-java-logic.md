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
