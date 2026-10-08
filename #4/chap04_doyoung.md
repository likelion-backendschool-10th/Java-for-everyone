https://doridopi.tistory.com/104?category=1360941
----
  자바 프로그래밍에서 프로그램의 실행 흐름을 제어하는 방법 중 하나로 선택문과 반복문이 있습니다.

선택문은 if, switch

반복문은 for, while, do-while 이 있습니다



# 선택문(조건문) - Selection Statements


##  if 문
조건식의 평가 결과가 true인지 false인지 판단하여 실행할 코드 블록을 분기합니다. 조건식의 결과는 반드시 불리언(boolean) 타입이어야 하며, if-else 또는 if-else if-else 구조로 확장하여 다중 조건을 순차적으로 평가할 수 있습니다.

int score = 85;
```java
if (score >= 90) {
    System.out.println("A 학점");
} else if (score >= 80) {
    System.out.println("B 학점");
} else {
    System.out.println("C 학점 이하");
}
```

## switch 문
하나의 식이나 변수 값을 기준으로 준비된 여러 case 중 일치하는 선택지로 이동하여 명령을 실행하는 선택문입니다.
전통적인 콜론(:) 구문 외에도 화살표(->) 구문과 yield를 사용해 결과값을 직접 반환하는 switch 표현식 형태로도 활용됩니다.
```java
int day = 2;

// switch 표현식을 활용한 분기 및 결과 대입
String dayName = switch (day) {
    case 1 -> "월요일";
    case 2 -> "화요일";
    case 3 -> "수요일";
    default -> "기타 요일";
};

System.out.println(dayName); // "화요일"
```

# 반복문- Iteration Statements
## for 문
초기화식, 조건식, 증감식을 하나의 구문에 작성하여 지정된 조건이 참인 동안 블록 내부의 명령을 반복 수행하는 구문입니다. 인덱스 제어가 필요하거나 반복 횟수가 명확할 때 주로 사용됩니다.
```java
// 1부터 5까지 반복 출력
for (int i = 1; i <= 5; i++) {
    System.out.println("for i: " + i);
}
```

## while 문
조건식을 먼저 검사하여 그 결과가 true일 때만 본문 블록을 실행하는 반복문입니다. 최초 검사 시 조건식이 false이면 본문은 단 한 번도 실행되지 않습니다.
```java
int count = 1;

while (count <= 3) {
    System.out.println("while count: " + count);
    count++;
}
```

## do-while 문
본문 블록을 먼저 실행한 후 조건식을 검사하는 반복문입니다. 조건식의 평가 결과와 관계없이 최소 1회 실행이 보장되므로, 사용자 입력 처리 등에 적합합니다.
```java
int number = 10;

do {
    // 최초 1회는 조건 검사 없이 무조건 실행
    System.out.println("do-while 실행: " + number);
    number++;
} while (number < 5); // 조건식이 false이므로 1회 실행 후 종료
```


# (추가) 흐름 제어 키워드 - Jump Statements
## break
실행 중인 가장 가까운 반복문(for, while, do-while)이나 switch 문을 즉시 종료하고 탈출시키는 키워드입니다.
```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // i가 5가 되면 반복문 전체를 탈출
    }
    System.out.println("break 예시: " + i);
}
```

## continue
반복문 내부에서 현재 회차의 남은 실행 명령들을 건너뛰고, 다음 반복(증감식 및 조건 검사)으로 진행하도록 흐름을 변경하는 키워드입니다.
```java
for (int i = 1; i <= 5; i++) {
    if (i % 2 == 0) {
        continue; // 짝수인 경우 아래 출력 구문을 건너뛰고 다음 회차로 이동
    }
    System.out.println("홀수 출력: " + i);
}
```



참고 자료

[수업 pdf 자료] 0827~0901  
[자바 기초 강의] 이것이 자바다 - 범위 : 39강. 4.2 if 문 ~ 45강 4.8 Continue 문
https://www.youtube.com/playlist?list=PLVsNizTWUw7EmX1Y-7tB2EmsK6nu6Q10q
