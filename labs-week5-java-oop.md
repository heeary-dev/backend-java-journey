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

---

# ✅ Day 31 – Java 다형성 (Polymorphism)

## 📘 1. 개념 정리

- 다형성(Polymorphism): 부모 타입 하나로 여러 자식 객체를 다룰 수 있는 객체지향의 핵심 개념
- 업캐스팅: 자식 객체를 부모 타입 변수에 담는 것 (자동, 안전)
- 오버라이딩된 메서드는 업캐스팅 상태에서도 실제 인스턴스 기준으로 실행됨
- 다운캐스팅: 부모 타입 참조를 자식 타입으로 강제 형변환하여 고유 기능을 사용하는 것 (명시적, 위험 가능성 있음)
- instanceof: 객체의 실제 타입을 검사하는 키워드로, 다운캐스팅 전에 안전성 확인에 사용

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
        System.out.println("저는 사람입니다. 이름은 " + name + "입니다.");
    }
}
```
```java
// 자식 클래스
public class Student extends Person {
    String major;

    public Student(String name, String major) {
        super(name);
        this.major = major;
    }

    @Override
    public void introduce() {
        System.out.println("저는 학생입니다. 이름은 " + name + "이고, 전공은 " + major + "입니다.");
    }

    public void study() {
        System.out.println(name + "은(는) 열심히 공부하고 있습니다.");
    }
}
```
```java
// 실행 클래스
public class Main {
    public static void main(String[] args) {

        Student s1 = new Student("희성", "컴퓨터공학");
        s1.introduce();
        s1.study();

        Person p1 = new Student("철수", "전자공학");
        p1.introduce();

        // p1.study(); // 컴파일 에러 발생

        if (p1 instanceof Student) {
            Student s2 = (Student) p1;
            s2.study();
        }
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day76-direct-student.png" width="450" height="80"/><br/>
  > Student 인스턴스를 직접 생성하여 introduce()와 study()를 실행한 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day76-upcasting-call.png" width="450" height="80"/><br/>
  > 업캐스팅된 상태에서도 오버라이딩된 introduce()가 자식 클래스 기준으로 실행됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day76-downcast-error.png" width="450" height="80"/><br/>
  > 업캐스팅된 객체에서 자식 고유 메서드 study() 호출 시 컴파일 에러 발생
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day76-downcasting-success.png" width="450" height="80"/><br/>
  > instanceof로 실제 타입 확인 후 다운캐스팅하여 study() 호출 성공
</p>

---

## 🛠️ Troubleshooting & 기록

- 업캐스팅은 자식 객체를 부모 타입에 담는 구조로, 컴파일러가 자동 처리하며 안전함  
- 업캐스팅 상태에서는 자식 고유 기능(예: study()) 호출 불가 → 컴파일 에러 발생 확인  
- 다운캐스팅을 통해 자식 타입으로 되돌릴 수 있으나, **객체의 진짜 타입이 맞을 때만 가능**  
- 이를 확인하기 위해 instanceof로 타입 검사 후 다운캐스팅 수행 → 안정성 확보

---

## 💭 느낀 점

- 업캐스팅은 객체를 상위 타입으로 추상화하여 관리하는 강력한 방법이라는 걸 체감함  
- 오버라이딩 메서드가 자식 기준으로 실행되는 구조를 직접 보면서 동적 바인딩의 핵심을 이해하게 됨  
- 다운캐스팅은 반드시 instanceof로 확인 후 진행해야 한다는 점이 명확히 각인되었고,  
  앞으로 다형성을 활용한 코드 설계 시 안전성과 구조적 유연성 모두를 고려할 수 있을 것 같음

---

# ✅ Day 32 – Java 다형성 배열 & 다운캐스팅

## 📘 1. 개념 정리

- 다형성 배열: 부모 타입 배열에 다양한 자식 객체를 담아 처리하는 구조
- 오버라이딩: 업캐스팅 상태에서도 자식의 메서드가 실행되도록 하는 핵심 기능
- instanceof: 객체가 특정 클래스 타입인지 확인하는 키워드
- 다운캐스팅: 부모 타입 객체를 자식 타입으로 강제 형변환하여 고유 기능 사용

---

## 🧪 2. 실습 명령어

```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }

    void introduce() {
        System.out.println("안녕하세요, 저는 " + name + "입니다.");
    }
}
```
```java
class Student extends Person {
    String major;

    Student(String name, String major) {
        super(name);
        this.name = name;
        this.major = major;
    }

    @Override
    void introduce() {
        System.out.println("안녕하세요, 저는 " + name + "이고 전공은 " + major + "입니다.");
    }

    void study() {
        System.out.println(name + "은(는) 열심히 공부 중입니다!");
    }
}
```
```java
public class Main {
    public static void main(String[] args) {
        Person[] people = new Person[3];
        people[0] = new Person("영희");
        people[1] = new Student("철수", "컴퓨터공학");
        people[2] = new Student("민수", "전자공학");

        for (Person p : people) {
            p.introduce(); // 오버라이딩된 메서드 실행
        }

        System.out.println("--------------------");

        for (Person p : people) {
            if (p instanceof Student) {
                Student s = (Student) p; // 다운캐스팅
                s.study(); // 자식 메서드 실행
            }
        }
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day77-polymorphism-array.png" width="500" height="150"/><br/>
  > 다형성 배열에서 오버라이딩 메서드 실행 및 instanceof로 자식 고유 메서드 호출 성공
</p>

---

## 🛠️ Troubleshooting & 기록

- 다형성 배열을 활용하면 다양한 자식 객체를 반복문으로 일괄 처리할 수 있어 코드가 훨씬 유연해짐
- 업캐스팅 상태에서는 자식 메서드 접근 불가 → instanceof로 타입 확인 후 다운캐스팅 필요
- instanceof 없이 다운캐스팅하면 `ClassCastException` 발생 가능 → 반드시 사전 확인이 중요

---

## 💭 느낀 점

- 배열을 활용한 다형성 구조가 실무 코드와 가장 가까운 형태라는 느낌을 받음
- 오버라이딩 메서드가 자식 기준으로 자동 실행된다는 점이 실제 사용에 매우 유용함을 체감
- 부모 타입 배열 + instanceof + 다운캐스팅 조합은 실용적이며, 객체지향의 유연함을 직접 체험한 하루였음

---

# ✅ Day 33 – Java enum 열거형 완전 이해

## 📘 1. 개념 정리

- `enum`은 고정된 상수들을 하나의 타입으로 선언할 수 있는 특별한 클래스
- 내부적으로 각 상수는 **미리 생성된 인스턴스**이며, new 없이 바로 사용 가능
- enum도 클래스처럼 **필드, 생성자, 메서드 포함 가능**
- `switch`, `values()`, `ordinal()`, `name()` 등 다양한 메서드 제공
- 실무에서 **상태값, 타입 구분, 조건 분기** 등에서 매우 자주 활용됨

---

## 🧪 2. 실습 명령어

```java
// 과일 열거형 정의
enum Fruit {
    APPLE("빨강"),
    BANANA("노랑"),
    GRAPE("보라");

    private final String color;

    Fruit(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }
}
```
```java
// 실행 클래스
public class Main {
    public static void main(String[] args) {
        for (Fruit f : Fruit.values()) {
            System.out.println(f.name() + "의 색깔은 " + f.getColor() + "입니다.");
        }

        System.out.println("-----------------");

        Fruit selected = Fruit.BANANA;

        switch (selected) {
            case APPLE:
                System.out.println("사과는 새콤달콤!");
                break;
            case BANANA:
                System.out.println("바나나는 든든해요!");
                break;
            case GRAPE:
                System.out.println("포도는 달콤해요!");
                break;
        }
    }
}
```

---


## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day78-enum-values.png" width="500" height="120"/><br/>
  > Fruit.values()로 모든 열거형 상수와 색상을 반복 출력한 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day78-enum-switch.png" width="500" height="80"/><br/>
  > 선택된 열거형 상수(Fruit.BANANA)에 따라 switch문 분기 처리된 출력 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- enum 생성자에 접근제한자를 지정하지 않으면 기본적으로 private이 적용됨 → 외부에서 new로 생성 불가능  
- switch 문에서 enum 값을 비교할 땐 `enum 상수명`만으로도 매칭됨 → `Fruit.` 없이도 분기 가능  
- enum 내부에 필드와 메서드를 정의하면 일반 클래스처럼 강력한 구조 설계가 가능함

---

## 💭 느낀 점

- enum은 단순 상수 묶음이 아니라 클래스처럼 객체 지향적으로 설계된 구조라는 점이 인상 깊었음  
- 생성자와 필드, 메서드를 포함할 수 있다는 점에서 실무에서 상태나 타입을 정의할 때 훨씬 유용할 것으로 보임  
- switch와 함께 사용할 때 코드가 간결하고 명확해지는 경험을 하며 enum의 실용성을 직접 체감했음
