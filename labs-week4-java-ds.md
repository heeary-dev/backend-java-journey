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

