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

```
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

---

# ✅ Day 12 – Java 문자열 심화 (String 메서드 완전정복)

## 📘 1. 개념 정리

- `String`은 참조형 자료형이며 `.equals()`를 통해 값 비교를 수행함
- `.length()`는 문자열 길이를 반환하며, 반환값은 `int`
- `.charAt(index)`는 해당 위치의 **문자 하나 (char)** 를 반환
- `.substring(start, end)`는 특정 구간의 부분 문자열을 잘라 `String` 타입으로 반환
- 사용자 입력을 받아 조건 분기와 문자열 처리를 종합적으로 수행함

---

## 🧪 2. 실습 명령어

```
import java.util.Scanner;

public class NameAnalyzer {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in); // 사용자 입력을 위한 Scanner 객체 생성

        System.out.print("이름을 입력하세요: ");
        String name = sc.nextLine(); // 문자열 입력 받기

        if (name.equals("희성")) { // 문자열 내용 비교
            System.out.println("반가워요, 희성님!");
        } else {
            System.out.println("이름 길이: " + name.length()); // 문자열 길이
            System.out.println("첫 글자: " + name.charAt(0)); // 첫 번째 문자
            System.out.println("마지막 글자: " + name.charAt(name.length() - 1)); // 마지막 문자

            // 이름이 3글자 이상일 경우에만 중간 글자 출력
            if (name.length() >= 3) {
                System.out.println("중간 글자: " + name.substring(1, name.length() - 1)); // 부분 문자열
            } else {
                System.out.println("중간 글자는 없습니다.");
            }
        }

        sc.close(); // Scanner 객체 닫기
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day57-name-match.png" width="500" /><br/>
  > "희성" 입력 시 인사 메시지가 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day57-name-details.png" width="500" /><br/>
  > 일반 이름 입력 시 길이, 첫/마지막 글자, 중간 문자열이 출력됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day57-name-short.png" width="500"/><br/>
  > 이름이 2글자 이하일 경우, 중간 글자가 없다는 메시지가 출력됨
</p>

---

## 🛠️ Troubleshooting & 기록

- `.substring(start, end)`는 **end 인덱스를 포함하지 않는다**는 점 주의  
- `name.length() - 1`은 **마지막 인덱스**를 의미하며, 항상 0부터 시작하는 인덱스 기준으로 계산해야 한다  
- `.charAt()`은 문자(`char`)를 반환하지만 `.substring()`은 문자열(`String`)을 반환한다는 점을 헷갈리지 말 것

---

## 💭 느낀 점

- 문자열을 직접 다뤄보니 이제 단순히 출력하는 것이 아니라, 문자열을 "구성 요소"로 나누어 처리할 수 있게 되었다  
- `length()`, `charAt()`, `substring()`은 앞으로 반복문이나 조건문과 함께 자주 쓰일 핵심 도구라는 걸 실감했다  
- 특히 인덱스를 다룰 때는 항상 **0부터 시작한다는 점과 마지막 인덱스를 정확히 계산**하는 것이 중요함을 다시 한번 체감했다

---

# ✅ Day 13 – Java while 반복문

## 📘 1. 개념 정리
- `while (조건)`은 조건이 참인 동안 계속 반복 실행되는 반복문
- 반복문은 반드시 3요소(초기화, 조건식, 증감 또는 조건 변화)를 포함해야 함
- `while (true)`는 무한 루프를 만들며, 명시적으로 `break` 등으로 탈출해야 함
- 사용자 입력을 기반으로 반복하거나 종료 조건을 설정할 수 있음
- 문자열 비교에는 `.equals()` 사용

---

## 🧪 2. 실습 명령어

```
// 실습 1: 1부터 5까지 출력
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++;
}

// 실습 2: 사용자 입력 반복 받기
Scanner sc = new Scanner(System.in);
String input = "";
while (!input.equals("exit")) {
    System.out.print("입력 (종료하려면 exit): ");
    input = sc.nextLine();
}
System.out.println("프로그램을 종료합니다.");
sc.close();

// 실습 3: 무한 루프 예시
while (true) {
    System.out.println("무한 반복 중...");
}
```

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day58-count-to-five.png" width="500" /><br/>
  > 1부터 5까지 출력 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day58-repeat-input.png" width="500" /><br/>
  > 사용자 입력 반복 → exit 입력 시 종료
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day58-infinite-loop.png" width="500" /><br/>
  > 무한 루프 예시 – "무한 반복 중..." 반복 출력
</p>

---

## 🛠️ Troubleshooting & 기록
- `while (true)`는 조건이 바뀌지 않으면 끝나지 않음 → 실습 중 직접 종료 버튼으로 강제 종료해야 함
- 문자열 비교 시 `==` 대신 `.equals()`를 사용하지 않으면 조건이 작동하지 않음
- 조건 변화 코드(`i++` 등)를 빠뜨리면 무한 루프 발생

---

## 💭 느낀 점
- 반복문은 조건만 설정하면 자동으로 루프가 도는 줄 알았는데, **초기화와 조건 변화 모두 직접 설계해야 한다는 점**이 인상 깊었다
- 무한 루프를 의도적으로 구현해보고 실제로 멈추지 않는 걸 경험하니, **조건 설계의 중요성**을 체감했다
- 사용자 입력 반복 실습이 실전 프로그래밍과 가장 가까운 느낌이어서 흥미로웠고, 앞으로 조건문과 반복문의 조합이 점점 더 익숙해질 것 같다는 자신감이 생겼다

---

# ✅ Day 14 – Java do-while, break, continue

## 📘 1. 개념 정리
- `do-while` 반복문은 **본문을 먼저 실행한 후 조건을 확인**함 → 조건이 false여도 최소 1회 실행됨
- `break`는 반복문 실행 도중 즉시 탈출하는 제어문 → 조건문과 함께 자주 사용됨
- `continue`는 해당 반복만 건너뛰고 다음 반복으로 이동함 → 루프 자체는 유지됨

---

## 🧪 2. 실습 명령어

```
// 실습 1: do-while 구조 이해
int i = 10;
do {
    System.out.println("do-while: " + i);
} while (i < 5);

// 실습 2: break로 반복 중단
for (int i = 1; i <= 5; i++) {
    if (i == 3) break;
    System.out.println("i: " + i);
}

// 실습 3: continue로 회차 건너뛰기
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.println("i: " + i);
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day59-do-while.png" width="500" height="80"/><br/>
  > 조건이 false여도 do-while 본문이 한 번 실행됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day59-break-example.png" width="500" height="80"/><br/>
  > i == 3에서 break 발생 → i: 1, i: 2만 출력되고 반복 종료
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day59-continue-example.png" width="500" height="80"/><br/>
  > i == 3일 때 continue → i: 3만 생략되고 반복 계속됨
</p>

---

## 🛠️ Troubleshooting & 기록

- `do-while` 문 끝에 `;`를 붙이지 않아 컴파일 에러 발생 → `while (조건);` 구조 유지해야 함  
- `break`는 여러 반복문이 중첩될 경우 가장 안쪽 루프만 종료함 → 정확한 위치 확인 필요  
- `continue`는 아래 코드가 무시되고 바로 다음 회차로 넘어감 → 이후 코드가 실행되지 않음  

---

## 💭 느낀 점

- `do-while`은 처음엔 어색했지만, 조건과 순서를 비교해보니 확실히 개념이 잡혔음  
- `break`와 `continue`는 단순 반복을 넘어 **논리적인 흐름 제어**를 할 수 있다는 점에서 흥미로웠음  
- 이론보다 실습을 통해 흐름을 직접 확인하니 확실하게 체화됨  
- 반복문 로직이 훨씬 유연해졌다는 느낌을 받았고, 앞으로 다양한 입력 처리에 잘 쓸 수 있을 것 같음


