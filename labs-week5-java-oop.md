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


