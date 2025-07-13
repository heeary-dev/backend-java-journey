# 🧪 실습 기록 - 4주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 21– Java 배열 심화 & 배열 응용

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

# ✅ Day 22– Java 문자열 수정 & StringBuilder 활용

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


