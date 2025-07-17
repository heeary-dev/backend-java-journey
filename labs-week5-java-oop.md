# 🧪 실습 기록 - 5주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 29 – Java 상속 기본 구조와 super() 호출

## 📘 1. 개념 정리

- `extends` 키워드를 사용하면 부모 클래스를 상속받을 수 있음
- 자식 클래스는 부모 클래스의 필드와 메서드를 자동으로 사용 가능
- 자식 클래스의 생성자에서 `super()`를 호출하여 부모 생성자를 실행
- 상속을 통해 코드 재사용성과 유지보수성이 향상됨

---

## 🧪 2. 실습 명령어

```java
// 부모 클래스: 공통 필드와 기능 정의
public class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void introduce() {
        System.out.println("안녕하세요, 제 이름은 " + name + "이고 나이는 " + age + "살입니다.");
    }
}
```
```java
// 자식 클래스: Person 상속 + 고유 기능 추가
public class Student extends Person {
    String major;

    public Student(String name, int age, String major) {
        super(name, age); // 부모 생성자 호출
        this.major = major;
    }

    public void study() {
        System.out.println(name + " 전공은 " + major + "이며 열심히 공부 중입니다.");
    }
}
```
```java
// 실행 클래스
public class Main {
    public static void main(String[] args) {
        Student s = new Student("희성", 25, "컴퓨터공학");
        s.introduce(); // 부모 메서드 호출
        s.study();     // 자식 메서드 호출
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day74-super-constructor.png" width="450" height="80"/><br/>
  > Student 생성자에서 super()로 부모(Person) 생성자 호출됨을 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day74-inherited-method.png" width="450" height="80"/><br/>
  > 자식 클래스(Student)에서 부모 메서드(introduce)를 호출하여 출력된 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day74-child-method.png" width="450" height="80"/><br/>
  > 자식 클래스의 고유 메서드(study) 실행 결과 출력 확인
</p>

---

## 🛠️ Troubleshooting & 기록

- 생성자에 `super()` 호출을 빼먹으면 컴파일 에러 발생  
  → 부모 생성자에서 매개변수가 필요한 경우 반드시 명시적으로 `super(값)` 호출 필요
- 부모 클래스의 private 필드는 자식 클래스가 직접 접근할 수 없음  
  → 이 경우 getter/setter를 사용해야 함

---

## 💭 느낀 점

- 상속은 단순히 코드를 복붙하는 것이 아니라, **구조적으로 중복을 줄이고** 기능을 확장하는 핵심 문법이라는 걸 실감함
- 특히 생성자 호출 순서(super → this)의 중요성을 직접 실습하며 이해함
- 자식 클래스가 부모 메서드를 그대로 사용할 수 있어서 **유지보수성과 코드 일관성이 향상된다는 점**이 인상 깊었음

---

# ✅ Day 30 – Java 메서드 오버라이딩과 super 메서드 호출

## 📘 1. 개념 정리

- 오버라이딩(Overriding): 부모 클래스에서 상속받은 메서드를 자식 클래스에서 **같은 이름과 시그니처로 재정의**하는 것
- `@Override`: 오버라이딩임을 명시하고, 실수 방지 기능도 제공함
- `super.메서드()`: 오버라이딩된 상황에서도 부모의 메서드를 명시적으로 호출할 수 있음
- 오버라이딩은 다형성과 확장성을 구현하는 핵심 도구임

---

## 🧪 2. 실습 명령어

```java
// 부모 클래스
public class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }

    public void introduce() {
        System.out.println("안녕하세요, 저는 " + name + "입니다.");
    }
}
```
```java
// 자식 클래스: 오버라이딩 + super 호출
public class Student extends Person {
    String major;

    public Student(String name, String major) {
        super(name);
        this.major = major;
    }

    @Override
    public void introduce() {
        super.introduce(); // 부모 메서드 호출
        System.out.println("저는 " + major + "을 전공하는 학생입니다.");
    }
}
```
```java
// 실행 클래스
public class Main {
    public static void main(String[] args) {
        Student s = new Student("희성", "컴퓨터공학");
        s.introduce(); // 자식 introduce 호출 (부모 + 자식 메서드 순차 실행)
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day75-super-introduce.png" width="450" height="80"/><br/>
  > 부모 클래스의 introduce() 메서드가 먼저 실행된 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day75-child-introduce.png" width="450" height="80"/><br/>
  > 자식 클래스(Student)의 introduce()가 오버라이딩되어 실행된 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day75-override-result.png" width="450" height="80"/><br/>
  > 부모 메서드(super.introduce) + 자식 고유 출력이 함께 실행된 최종 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- `@Override`를 생략하면 오타나 시그니처 불일치 시 오류를 감지하지 못함 → 무조건 사용해야 안전
- 오버라이딩 메서드에서 `super.메서드()`를 사용하면 **부모의 원래 동작을 유지하면서 자식 기능을 덧붙일 수 있음**
- 오버라이딩은 메서드 이름, 매개변수, 리턴타입이 **모두 동일해야 성립**됨 (한 글자라도 다르면 단순 오버로딩으로 인식됨)

---

## 💭 느낀 점

- 오버라이딩은 단순한 재정의가 아니라, **기존 기능을 확장하거나 맞춤형으로 바꿔주는 강력한 도구**라는 것을 실감함
- super 키워드를 통해 부모 기능을 포함할 수 있다는 점에서 객체지향의 계층적 설계 철학이 느껴졌음
- 앞으로 상속을 활용할 때, **기본 동작은 유지하면서 필요한 부분만 덧붙이는 방식**으로 활용해볼 수 있을 것 같음
