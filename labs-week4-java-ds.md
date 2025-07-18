# 🧪 실습 기록 - 4주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 21 – Java 배열 심화 & 배열 응용

## 📘 1. 개념 정리
- 배열은 같은 타입의 데이터를 연속적으로 저장하는 참조형 자료구조이다.
- 배열의 크기는 고정되며, 인덱스를 이용해 요소에 접근한다.
- 배열은 `for`, `for-each` 반복문으로 순회할 수 있으며, 메서드의 인자로 전달 가능하다.
- 2차원 배열은 행과 열로 이루어진 표 형태이며, 중첩 반복문으로 순회한다.

---

## 🧪 2. 실습 명령어

```java
// ArrayPractice1.java
public class ArrayPractice1 {
    public static void main(String[] args) {
        int[] scores = {85, 92, 78, 64, 99};

        int sum = 0;
        int max = scores[0];

        for (int score : scores) {
            sum += score;
            if (score > max) {
                max = score;
            }
        }

        double avg = (double) sum / scores.length;

        System.out.println("총합: " + sum);
        System.out.println("최댓값: " + max);
        System.out.println("평균: " + avg);
    }
}
```
```java
// ArrayPractice2.java
public class ArrayPractice2 {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        int total = sumArray(numbers);
        System.out.println("배열의 합: " + total);
    }

    public static int sumArray(int[] arr) {
        int sum = 0;
        for (int n : arr) {
            sum += n;
        }
        return sum;
    }
}
```
```java
// ArrayPractice3.java
public class ArrayPractice3 {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day66-array-summary.png" width="450" height="200"/><br/>
  > 배열의 합계, 최댓값, 평균을 구한 출력 결과 (ArrayPractice1.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day66-array-method.png" width="450" height="200"/><br/>
  > 배열을 메서드에 전달해 합계를 계산한 출력 결과 (ArrayPractice2.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day66-2d-array.png" width="450" height="200"/><br/>
  > 2차원 배열을 출력한 결과 (ArrayPractice3.java)
</p>

---

## 🛠️ Troubleshooting & 기록
- 배열의 평균 계산 시 **정수끼리 나누면 소수점이 날아감** → `double`로 형변환 필요
- 배열을 메서드에 전달하면 **참조값**이 넘어간다는 점 다시 확인
- 2차원 배열 순회 시 `matrix[i].length`를 통해 열 길이를 정확히 계산해야 함

---

## 💭 느낀 점
- 배열 구조를 직접 코드로 구현해보니 개념이 훨씬 명확해졌다.
- 특히 for-each와 2중 for문의 차이를 실습을 통해 완전히 체감함.
- 이제 배열을 활용한 간단한 문제는 스스로 구현할 수 있다는 자신감이 생겼다.

---

# ✅ Day 22 – Java 문자열 수정 & StringBuilder 활용

## 📘 1. 개념 정리
- `String`은 불변(immutable)이라 수정할 수 없고, 문자열을 바꿀 때마다 새 객체가 생성된다.
- `StringBuilder`는 내부에 버퍼를 두고 문자열을 효율적으로 수정할 수 있는 클래스이다.
- 문자열을 반복적으로 수정하는 상황에서는 `StringBuilder`가 훨씬 빠르고 메모리 효율적이다.
- `toCharArray()`를 사용하면 문자열을 문자 배열로 변환해 직접 조작할 수 있다.
- 문자 빈도 계산은 `int[]` 배열을 활용해 a~z를 인덱스로 매핑해 구현할 수 있다.

---

## 🧪 2. 실습 명령어

```java
// StringBuilderExample.java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        sb.append("Java ");
        sb.append("is ");
        sb.append("fun!");
        System.out.println("결과: " + sb.toString());

        sb.reverse();
        System.out.println("뒤집은 결과: " + sb.toString());
    }
}
```
```java
// StringVsBuilder.java
public class StringVsBuilder {
    public static void main(String[] args) {
        long startTime, endTime;

        startTime = System.currentTimeMillis();
        String s = "";
        for (int i = 0; i < 10000; i++) {
            s += i;
        }
        endTime = System.currentTimeMillis();
        System.out.println("String 시간: " + (endTime - startTime) + "ms");

        startTime = System.currentTimeMillis();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 10000; i++) {
            sb.append(i);
        }
        endTime = System.currentTimeMillis();
        System.out.println("StringBuilder 시간: " + (endTime - startTime) + "ms");
    }
}
```
```java
// CharFrequency.java
public class CharFrequency {
    public static void main(String[] args) {
        String input = "hello java";
        int[] count = new int[26];

        for (char ch : input.toCharArray()) {
            if (ch >= 'a' && ch <= 'z') {
                count[ch - 'a']++;
            }
        }

        for (int i = 0; i < 26; i++) {
            if (count[i] > 0) {
                System.out.println((char) ('a' + i) + ": " + count[i]);
            }
        }
    }
}
```
```java
// ReverseWithCharArray.java
public class ReverseWithCharArray {
    public static void main(String[] args) {
        String input = "gptrocks";
        char[] chars = input.toCharArray();

        for (int i = 0; i < chars.length / 2; i++) {
            char temp = chars[i];
            chars[i] = chars[chars.length - 1 - i];
            chars[chars.length - 1 - i] = temp;
        }

        System.out.println("뒤집은 문자열: " + new String(chars));
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day67-stringbuilder-basic.png" width="450" height="200"/><br/>
  > StringBuilder로 문자열을 붙이고 뒤집은 출력 결과 (StringBuilderExample.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day67-string-vs-builder-time.png" width="450" height="200"/><br/>
  > String과 StringBuilder의 반복 연산 시간 비교 결과 (StringVsBuilder.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day67-char-frequency.png" width="450" height="200"/><br/>
  > 문자열 내 알파벳 빈도수를 계산한 결과 (CharFrequency.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day67-reverse-chararray.png" width="450" height="200"/><br/>
  > char 배열을 이용해 문자열을 뒤집은 출력 결과 (ReverseWithCharArray.java)
</p>

---

## 🛠️ Troubleshooting & 기록
- `String +=` 반복문은 실행 시간이 오래 걸림 → 반복 처리에는 반드시 `StringBuilder` 사용 필요
- `char[]`로 뒤집을 때는 인덱스를 정확히 매칭하지 않으면 오류 발생 (i와 length - 1 - i)
- `toCharArray()`를 쓰면 문자열을 직접 조작하기 쉬워짐
- 문자 빈도 계산 시 소문자 범위만 처리하도록 `if (ch >= 'a' && ch <= 'z')` 조건 필수

---

## 💭 느낀 점
- StringBuilder의 구조와 성능을 실제로 체감하며 '문자열 수정'의 개념이 명확해졌다.
- 반복문에서 += 를 쓰면 안 된다는 이론이 실습에서 실제 시간 차이로 확인되니 이해가 훨씬 쉬웠다.
- char 배열로 뒤집는 로직도 단순하지만 직접 구현해보니 반복문 로직 감각이 더 잡혔다.
- 이제 문자열도 읽기뿐 아니라 “수정”하는 감각이 생긴 느낌이다.

---

# ✅ Day 23 – Java 클래스와 인스턴스

## 📘 1. 개념 정리
- 클래스(Class)는 객체(Object)를 만들기 위한 설계도이며, 변수와 메서드의 구조를 정의한다.
- 인스턴스(Instance)는 클래스를 바탕으로 `new` 키워드를 통해 생성된 실제 객체이다.
- 각 인스턴스는 자신만의 변수 값을 가지며, 클래스에서 정의한 변수 구조를 기반으로 생성된다.
- 참조형 변수는 객체의 실제 값을 담는 것이 아니라, 메모리 주소를 담고 있는 변수이다.
- 참조 변수 간 대입은 객체 자체를 복사하는 것이 아니라, 같은 객체를 가리키게 되는 것임에 주의해야 한다.

---

## 🧪 2. 실습 명령어

```java
// Car.java
public class Car {
    String color;
    int speed;
}
```
```java
// Main1.java
public class Main1 {
    public static void main(String[] args) {
        Car car1 = new Car();
        car1.color = "red";
        car1.speed = 100;

        Car car2 = new Car();
        car2.color = "blue";
        car2.speed = 80;

        System.out.println("car1 → " + car1.color + ", " + car1.speed);
        System.out.println("car2 → " + car2.color + ", " + car2.speed);
    }
}
```
```java
// Main2.java
public class Main2 {
    public static void main(String[] args) {
        Car original = new Car();
        original.color = "green";
        original.speed = 120;

        Car copy = original;
        copy.speed = 200;

        System.out.println("original.speed = " + original.speed);
        System.out.println("copy.speed = " + copy.speed);
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day68-car-instances.png" width="450" height="80"/><br/>
  > 서로 다른 인스턴스를 생성하고 각기 다른 속성을 할당한 출력 결과 (Main1.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day68-car-reference-copy.png" width="450" height="80"/><br/>
  > 참조 변수를 복사하여 두 변수가 같은 객체를 가리키는 출력 결과 (Main2.java)
</p>

---

## 🛠️ Troubleshooting & 기록
- `Car copy = original;`은 객체 복사가 아니라 **주소 복사**이므로 두 변수는 동일한 객체를 가리킴
- 인스턴스를 새로 생성하지 않고 기존 객체를 복사하면 내부 상태 변경 시 함께 영향을 받음
- 객체가 메모리에 생성되는 시점과 참조변수가 동작하는 구조를 눈으로 보며 이해할 수 있었음

---

## 💭 느낀 점
- 클래스를 정의하는 것만으로는 아무 일도 일어나지 않으며, 인스턴스를 만들어야 진짜 데이터가 생긴다는 개념이 확실해졌다.
- 참조형 변수의 동작이 생각보다 직관적이지 않아서 직접 실습해보니 개념이 분명히 잡혔다.
- 객체지향의 핵심인 “하나의 설계도로 여러 개의 실체를 만들 수 있다”는 구조가 머릿속에 이미지로 자리잡았다.

---

# ✅ Day 24 – Java 생성자, this, 오버로딩

## 📘 1. 개념 정리
- 생성자(Constructor)는 객체가 생성될 때 자동으로 호출되어 객체의 초기 상태를 설정하는 특수한 메서드이다.
- 생성자는 클래스 이름과 같고, 리턴 타입이 없으며, new 키워드와 함께 호출된다.
- this 키워드는 현재 객체 자신을 가리키며, 매개변수와 인스턴스 변수명이 충돌할 때 구분하기 위해 사용한다.
- 생성자는 오버로딩이 가능하여 다양한 초기화 방식 제공이 가능하다.
- 생성자 내부에서 다른 생성자를 호출할 때는 `this()` 구문을 사용하며, 반드시 생성자 첫 줄에 작성해야 한다.

---

## 🧪 2. 실습 명령어

```java
// Car.java
public class Car {
    String color;
    int speed;

    public Car() {
        color = "black";
        speed = 0;
    }

    public Car(String c, int s) {
        color = c;
        speed = s;
    }

    public void display() {
        System.out.println("색상: " + color + ", 속도: " + speed);
    }
}
// Main1.java
public class Main1 {
    public static void main(String[] args) {
        Car c1 = new Car();
        Car c2 = new Car("red", 120);

        c1.display();
        c2.display();
    }
}
```
```java
// Car2.java
public class Car2 {
    String color;
    int speed;

    public Car2(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }

    public void display() {
        System.out.println("색상: " + color + ", 속도: " + speed);
    }
}
// Main2.java
public class Main2 {
    public static void main(String[] args) {
        Car2 c = new Car2("blue", 150);
        c.display();
    }
}
```
```java
// Car3.java
public class Car3 {
    String color;
    int speed;

    public Car3() {
        this("white", 0);
    }

    public Car3(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }

    public void display() {
        System.out.println("색상: " + color + ", 속도: " + speed);
    }
}
```
```java
// Main3.java
public class Main3 {
    public static void main(String[] args) {
        Car3 defaultCar = new Car3();
        Car3 customCar = new Car3("yellow", 200);

        defaultCar.display();
        customCar.display();
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day69-constructor-basic.png" width="450" height="80"/><br/>
  > 기본 생성자와 매개변수 생성자를 사용한 출력 결과 (Main1.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day69-this-keyword.png" width="450" height="80"/><br/>
  > this 키워드를 사용하여 변수 충돌을 해결한 출력 결과 (Main2.java)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day69-constructor-overloading.png" width="450" height="80"/><br/>
  > 생성자 오버로딩을 통해 기본값/사용자지정값 모두 처리한 출력 결과 (Main3.java)
</p>

---

## 🛠️ Troubleshooting & 기록
- 생성자 이름이 클래스명과 다르면 오류 발생 → 자동 호출되지 않음
- 생성자 오버로딩 시 `this()`는 반드시 생성자 **첫 줄에만** 와야 함. 위치가 틀리면 컴파일 오류
- this 키워드를 생략했을 때, 인스턴스 변수와 매개변수가 이름이 같으면 값이 제대로 할당되지 않음
- 생성자 하나라도 만들면 기본 생성자는 자동 생성되지 않으므로 직접 명시 필요

---

## 💭 느낀 점
- 객체를 만들면서 동시에 초기값을 지정하는 구조가 생각보다 깔끔하고 편하다는 걸 느꼈다
- 생성자 오버로딩을 통해 다양한 상황에서 유연하게 객체를 만들 수 있다는 게 객체지향 설계의 유연함처럼 느껴졌다
- this 키워드가 없으면 이름 충돌이 생길 수 있는데, 이걸 직접 실습으로 확인하니 개념이 머리에 박혔다
- 설계도(클래스)를 제대로 사용하기 위해선 생성자의 활용이 매우 중요하다는 걸 실감했다

---

# ✅ Day 25 – Java 접근 제어자, 캡슐화, getter/setter

## 📘 1. 개념 정리
- 접근 제어자(Access Modifier)는 변수나 메서드의 접근 범위를 설정하는 키워드이며, 주요 제어자는 `public`, `private`, `protected`, `default`가 있다.
- `private`은 클래스 내부에서만 접근 가능하며, 외부에서 직접 접근할 수 없다.
- 캡슐화는 클래스 내부 데이터를 숨기고, 공개된 메서드를 통해서만 접근하도록 하는 객체지향의 핵심 설계 원칙이다.
- 외부 접근을 막은 `private` 필드를 간접적으로 조작하기 위해 `getter`(읽기), `setter`(쓰기) 메서드를 만든다.
- setter에 유효성 검사를 넣으면 잘못된 값 입력을 방지할 수 있어 보안성과 안정성이 높아진다.

---

## 🧪 2. 실습 명령어

```java
// User.java
public class User {
    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        if (age >= 0 && age <= 120) {
            this.age = age;
        } else {
            System.out.println("⚠️ 나이는 0~120 사이만 가능합니다.");
        }
    }

    public int getAge() {
        return age;
    }
}
```
```java
// Main.java
public class Main {
    public static void main(String[] args) {
        User u = new User();

        // u.name = "희성"; ❌ private 접근 불가
        u.setName("희성");
        u.setAge(28);

        System.out.println("이름: " + u.getName());
        System.out.println("나이: " + u.getAge());

        u.setAge(-10); // 유효성 검사 실패 시 경고 출력
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day70-getter-setter-normal.png" width="450" height="80"/><br/>
  > getter/setter를 통한 정상적인 정보 접근 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day70-age-invalid-warning.png" width="450" height="80"/><br/>
  > setAge()에서 유효하지 않은 값(-10) 입력 시 경고 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day70-private-error.png" width="450" height="80"/><br/>
  > private 필드(name)에 직접 접근 시 컴파일 오류 발생
</p>

---

## 🛠️ Troubleshooting & 기록
- `private` 필드에 외부에서 직접 접근하면 IDE가 에러를 발생시킴 (→ 보호 구조가 잘 작동함을 확인)
- setter 내부에 유효성 검사 로직을 넣는 방식으로 잘못된 입력을 방지 가능
- 유효하지 않은 나이 입력 시 출력되는 경고 메시지로, 사용자 피드백 처리 흐름 이해

---

## 💭 느낀 점
- 이제 클래스 내부에서만 데이터를 안전하게 다루는 구조가 뭔지 감이 잡혔다
- 직접 접근이 막히니까, "왜 getter/setter가 필요한가"가 확실하게 와닿았다
- setter 안에서 조건 검사까지 하면 외부로부터 객체 상태를 보호할 수 있다는 점이 인상 깊었다

---

# ✅ Day 26 – Java 포함 관계(has-a)

## 📘 1. 개념 정리
- 클래스 간 포함 관계(has-a)는 한 클래스가 다른 클래스의 인스턴스를 멤버로 **포함**하는 구조다.
- 현실 세계의 구조를 코드로 모델링할 때 자주 사용되며, 예: `사람 has-a 주소`, `주문 has-a 상품`.
- 포함 관계는 독립적인 클래스를 조합하여 **책임 분리**와 **재사용성**을 높이는 데 효과적이다.
- 포함된 객체는 생성자에서 전달받거나, 별도로 생성 후 참조시킬 수 있다.
- 포함 객체의 필드나 메서드는 **점(.) 연산자**로 연결 접근이 가능하다 (`p.address.city` 등).

---

## 🧪 2. 실습 명령어

```java
// Address.java
public class Address {
    String city;
    String street;

    public Address(String city, String street) {
        this.city = city;
        this.street = street;
    }

    public void showAddress() {
        System.out.println(city + " " + street);
    }
}
```
```java
// Main.java
public class Main {
    public static void main(String[] args) {
        Address addr = new Address("서울", "강남대로");
        Person p = new Person("희성", addr);

        p.showInfo();
    }
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day71-has-a-new-address.png" width="450" height="80"/><br/>
  > Address 객체를 생성하고, Person 객체에 포함시켜 연결한 모습
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day71-has-a-showinfo.png" width="450" height="120"/><br/>
  > 포함된 Address 객체의 정보를 Person 내부 메서드에서 출력한 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day71-has-a-access-inside.png" width="450" height="80"/><br/>
  > p.address.city 와 같이 포함된 객체 내부 필드에 직접 접근하는 예시
</p>

---

## 🛠️ Troubleshooting & 기록
- 포함 객체를 먼저 생성하고 생성자에 전달하지 않으면 `NullPointerException` 발생 가능
- 포함 관계를 단순하게 이해하면 "클래스 안에 클래스를 넣는 구조"로 받아들이는 것이 직관적임
- `address.showAddress()` 형태로 메서드까지 위임하는 구조가 중요함

---

## 💭 느낀 점
- 객체를 객체 안에 넣는 구조가 처음엔 생소했지만, "사람은 주소를 가진다"는 개념으로 이해하니 직관적으로 와닿았다
- 생성자에서 다른 객체를 전달받는 방식이 확장성과 코드 재사용에 유리하다는 점을 실감했다
- 이런 포함 구조를 통해 하나의 클래스가 너무 많은 역할을 하지 않도록 분리하는 게 좋다는 객체지향 철학이 조금씩 익숙해졌다

---

# ✅ Day 27 – Java 클래스 간 관계 - 객체를 메서드로 전달하기

## 📘 1. 개념 정리

- 메서드의 매개변수로 **다른 클래스의 객체를 전달**할 수 있다.
- 이는 클래스 간 관계(예: has-a 관계)를 코드에서 연결해주는 대표적인 방법이다.
- 전달받은 객체의 메서드나 필드를 해당 메서드 안에서 자유롭게 사용할 수 있다.

---

## 🧪 2. 실습 명령어

```java
// Address.java
public class Address {
    String city;
    String street;

    public Address(String city, String street) {
        this.city = city;
        this.street = street;
    }

    public void showAddress() {
        System.out.println("City: " + city);
        System.out.println("Street: " + street);
    }
}
```
```java
// Person.java
public class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }

    public void showInfo(Address addr) {
        System.out.println("Name: " + name);
        addr.showAddress();
    }
}
```
```java
// Main.java
public class Main {
    public static void main(String[] args) {
        Address a1 = new Address("Seoul", "Mapo-gu");
        Person p1 = new Person("Heesung");

        p1.showInfo(a1);
    }
}
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day72-showinfo-method-call.png" width="450" height="80"/><br/>
  > showInfo 메서드를 호출하여 Person 이름과 Address 정보를 출력한 결과 화면
</p>

---

## 🛠️ Troubleshooting & 기록

- 처음에는 `Address` 객체를 메서드 인자로 넘기는 방식이 어색했으나, `addr.showAddress()` 호출이 `Address` 클래스 내부 메서드를 실행한다는 구조를 이해하고 명확해짐.
- 클래스 간 연결을 메서드 레벨에서 처리하는 구조는 향후 협업 로직이나 데이터 전달 구조의 핵심이 될 수 있음.

---

## 💭 느낀 점

- `has-a` 관계를 단순한 필드 보유 외에도 **메서드 전달 방식**으로도 표현할 수 있다는 점이 새로웠다.
- 객체 간 협력을 메서드 안에서 처리하니 더 유연한 구조가 가능해 보인다.

---

# ✅ Day 28 – Java static & final 키워드 정복

## 📘 1. 개념 정리

- `static`: 클래스 변수 또는 클래스 메서드 선언 시 사용하며, 객체 생성 없이 사용 가능하고 메모리를 공유함
- `final`: 변수, 메서드, 클래스에 붙여서 더 이상 변경할 수 없도록 제한함
- static 변수: 모든 객체가 공유하며 클래스명으로 접근 가능
- static 메서드: 객체 없이 클래스명으로 호출 가능, 내부에서 this 사용 불가
- final 변수: 한 번만 초기화 가능하며 수정 불가 (상수로 사용)
- final 메서드: 자식 클래스에서 오버라이딩 불가능
- final 클래스: 상속 불가능
- static final: 상수 선언에 자주 사용되는 조합 (예: `PI`, `MAX_VALUE`)

---

## 🧪 2. 실습 명령어

```java
public class StaticFinalDemo {

    // static 변수: 모든 객체가 공유
    static String schoolName = "Green High School";

    // final 변수: 한 번만 초기화 가능
    final int studentId;

    // 인스턴스 변수
    String name;

    // static final 변수: 상수
    static final double PI = 3.14159;

    // 생성자
    public StaticFinalDemo(int studentId, String name) {
        this.studentId = studentId;  // final 변수는 생성자에서만 초기화 가능
        this.name = name;
    }

    // 인스턴스 메서드
    public void printStudentInfo() {
        System.out.println("[" + name + "] 학생은 " + schoolName + "에 재학 중입니다.");
    }

    // static 메서드
    public static void changeSchoolName(String newName) {
        schoolName = newName;
        System.out.println("학교명이 " + schoolName + "(으)로 변경되었습니다.");
    }

    // final 메서드
    public final void cannotOverride() {
        System.out.println("이 메서드는 오버라이딩할 수 없습니다.");
    }
}
```
```java
// final 메서드 오버라이드 시도 (컴파일 에러 발생)
public class ChildDemo extends StaticFinalDemo {

    public ChildDemo(int id, String name) {
        super(id, name);
    }

    // @Override
    // public void cannotOverride() {
    //     System.out.println("오버라이딩 시도 중...");
    // }
}
```
```java
public class Main {
    public static void main(String[] args) {

        // static 메서드 호출
        StaticFinalDemo.changeSchoolName("Blue High School");

        // 객체 생성
        StaticFinalDemo s1 = new StaticFinalDemo(101, "Tom");
        StaticFinalDemo s2 = new StaticFinalDemo(102, "Jerry");

        // 인스턴스 메서드 호출
        s1.printStudentInfo();
        s2.printStudentInfo();

        // static final 상수 출력
        System.out.println("원주율 상수: " + StaticFinalDemo.PI);
    }
}
```

---

<p align="center"> <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day73-static-change.png" width="450" height="80"/><br/> > static 메서드로 학교명이 변경되는 출력 확인 </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day73-static-share.png" width="450" height="80"/><br/>
  > 두 객체가 동일한 schoolName(static 변수)을 공유하는 출력 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day73-final-const.png" width="450" height="80"/><br/>
  > static final 상수 PI 출력 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/backend-java-journey/main/images/day73-final-method-error.png" width="450" height="150"/><br/>
  > final 메서드를 오버라이딩하려 할 때 컴파일 에러 발생 (주석 해제 시)
</p>

---

## 🛠️ Troubleshooting & 기록

- `static` 메서드 안에서는 `this` 키워드 사용 불가 → 객체 정보가 없기 때문
- `final` 변수는 반드시 **생성자 또는 선언 시점에 초기화**되어야 함
- `final` 메서드 오버라이드 시 컴파일 에러 발생 → 실습을 통해 정확히 확인함
- `static final` 상수는 대문자와 언더스코어로 이름 짓는 것이 자바 컨벤션임

---

## 💭 느낀 점

- static과 final은 문법 자체는 간단하지만, 개념적으로는 **메모리 구조와 객체 지향 설계 원칙을 함께 이해해야** 제대로 쓰일 수 있다는 걸 느꼈다.
- static은 공유, final은 고정이라는 원칙을 명확히 체득했으며, 특히 static 메서드 내부에서 this가 막히는 구조를 직접 실습하면서 머리에 각인되었다.
- 실습을 통해 변수와 메서드의 소속(클래스 vs 인스턴스)을 명확히 구분할 수 있게 되었다.



