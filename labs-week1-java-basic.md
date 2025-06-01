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

