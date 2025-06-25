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

