https://doridopi.tistory.com/103
----
# 산술 연산자
산술 연산자는 +, -, *, /, %로 총 5개이다

| 연산식 | 설명 | 샘플 (int num = 10; 일 때) |
| --- | --- | --- |
| `+` | 덧셈 연산 | `int result = num + 1; // = 11` |
| `-` | 뺄셈 연산 | `int result = num - 1; // = 9` |
| `*` | 곱셈 연산 | `int result = num * 2; // = 20` |
| `/` | 나눗셈 연산 | `int result = num / 2; // = 5` |
| `%` | 나눗셈의 나머지 연산 | `int result = num % 3; // = 1` |


* 피연산자 중 범위(크기)가 더 큰 타입으로 자동 형변환 된다
```java
public static void main(String[] args) {
        byte b1 = 10;
        byte b2 = 20;
        int v1 = 10;
        int v2 = 4;
        long v4 = 30L;

        // 1. int보다 작은 타입(byte) 연산 -> int로 자동 형변환
        // byte result1_error = b1 + b2; // 컴파일 에러 발생! (int 타입을 byte에 담을 수 없음)
        int result1 = b1 + b2;
        System.out.println("result1 (byte + byte -> int): " + result1);

        // 2. long 타입이 포함된 연산 -> 모든 피연산자가 long으로 자동 형변환
        long result2 = v1 + v2 - v4; // v1, v2가 모두 long으로 승격되어 연산됨
        System.out.println("result2 (int + int - long -> long): " + result2);

        // 3. 정수 나눗셈 vs double 강제 형변환 나눗셈
        int intDivision = v1 / v2;             // 10 / 4 -> 정수 연산이므로 결과는 2 (소수점 절삭)
        double result3 = (double) v1 / v2;     // (double)10 / 4 -> 10.0 / 4.0 으로 승격되어 결과는 2.5

        System.out.println("정수 나눗셈 결과: " + intDivision);
        System.out.println("result3 (double 강제 변환 후 연산): " + result3);
    }
```
# 비트 연산자
(상식) C언어와 Java등의 서로 다른 언어에서 데이터를 주고 받을 때, 데이터를 다루는 범위가 다르다. 
이걸 맞춰주기 위해서 비트 연산자를 사용하게 된다.
프로그래밍에서는 잘 쓰이지 않는다.



## AND 와 OR
구분	연산식	결과	설명
AND

| 구분 | 연산식 | 결과 | 설명 |
| --- | --- | --- | --- |
| AND (논리곱) | `1 & 1`<br>`1 & 0`<br>`0 & 1`<br>`0 & 0` | `1`<br>`0`<br>`0`<br>`0` | 두 비트 모두 1일 경우에만 연산 결과가 1 |
| OR (논리합) | `1 \| 1`<br>`1 \| 0`<br>`0 \| 1`<br>`0 \| 0` | `1`<br>`1`<br>`1`<br>`0` | 두 비트 중 하나만 1이면 연산 결과는 1 |


예시) 45(00101101)과 25(00011001)을 비트(bit) 단위로 연산해보자. 세로로 보면 됨!

```text
0 0 1 0 1 1 0 1
& (AND 연산)
0 0 0 1 1 0 0 1
↓ (결과)
0 0 0 0 1 0 0 1

0 0 1 0 1 1 0 1
| (OR 연산)
0 0 0 1 1 0 0 1
↓ (결과)
0 0 1 1 1 1 0 1
```
  
## XOR 과 NOT
| 구분 | 연산식 | 결과 | 설명 |
| --- | --- | --- | --- |
| XOR (배타적 논리합) | `1 ^ 1`<br>`1 ^ 0`<br>`0 ^ 1`<br>`0 ^ 0` | `0`<br>`1`<br>`1`<br>`0` | 두 비트 중 하나는 1이고 다른 하나가 0일 경우 연산 결과는 1 |
| NOT (논리 부정) | `~1`<br>`~0` | `0`<br>`1` | 보수 |

# 관계 연산자
관계 연산자는 두 개의 값을 비교하여 그 관계가 참이면 True, 거짓이면 False를 반환한다.

* `>` (초과): 왼쪽 값이 오른쪽 값보다 크면 참
* `<` (미만): 왼쪽 값이 오른쪽 값보다 작으면 참
* `>=` (이상): 왼쪽 값이 오른쪽 값보다 크거나 같으면 참
* `<=` (이하): 왼쪽 값이 오른쪽 값보다 작거나 같으면 참
* `==` (같음): 두 값이 같으면 참
* `!=` (다름): 두 값이 다르면 참

# 논리 연산자
`&`과 `&&`은 결과상 같다.  
하지만 `&&`은 앞의 연산 조건만 봐도 결과가 무조건 나오는 경우, 뒤의 연산 조건은 보지 않기 때문에 조금 더 빠르다.

`|`과 `||`도 마찬가지이다.

=> 결론: `&&`와 `||` 처럼 두 개씩 쓰는 게 좋다(빠르다).

| 구분 | 연산식 | 결과 | 설명 |
| --- | --- | --- | --- |
| AND (논리곱) | `true && true`<br>`true && false`<br>`false && true`<br>`false && false` | `true`<br>`false`<br>`false`<br>`false` | 피연산자 모두가 true일 경우에만 연산 결과가 true |
| OR (논리합) | `true \|\| true`<br>`true \|\| false`<br>`false \|\| true`<br>`false \|\| false` | `true`<br>`true`<br>`true`<br>`false` | 피연산자 중 하나만 true이면 연산 결과가 true |
| XOR (배타적 논리합) | `true ^ true`<br>`true ^ false`<br>`false ^ true`<br>`false ^ false` | `false`<br>`true`<br>`true`<br>`false` | 피연산자가 하나는 true이고 다른 하나가 false일 경우에만 연산 결과가 true |
| NOT (논리 부정) | `!true`<br>`!false` | `false`<br>`true` | 피연산자의 논리값을 바꿈 |

# instanceof

특정 객체가 지정한 클래스의 인스턴스인지, 또는 해당 타입으로 형변환하여 활용 가능한지 상속 관계까지 고려하여 판별하는 연산자입니다.  
검사 결과로 boolean (`true` 또는 `false`)을 반환하며 다형성 기반의 타입 검사에 주로 활용됩니다.

Object 타입으로 전달된 상위 객체나 배열의 실제 타입을 안전하게 확인한 뒤 캐스팅할 때 사용합니다.

```java
Object obj = "Hello Java";

// obj가 String 타입의 인스턴스인지 검사
if (obj instanceof String) {
    System.out.println("obj는 String 타입입니다.");
}

// Object 매개변수로 전달된 배열의 실제 타입 판별
Object arr = new int[]{10, 20, 30};
if (arr instanceof int[]) {
    System.out.println("arr는 int 배열 객체입니다.");
}
// String과 int[] 모두 Object를 상속하고 있으므로, 두 if문은 모두 출력된다!
```

# assignment(=) operator (대입 연산자)

연산자 우측의 값이나 식의 결과를 좌측 변수에 할당/재대입하는 연산자입니다.

* **기본 자료형**: 변수 자체에 실제 값(리터럴)을 직접 저장합니다.
* **참조 자료형**: `new` 연산자로 힙 메모리에 할당된 객체의 시작 주소값(참조값)을 참조 변수에 대입합니다. 다른 참조 변수에 대입 시 동일한 객체의 주소를 공유하게 됩니다.

```java
// 1) 기본 자료형 대입 (실제 값 저장)
int age = 25;
age = 26; // 값 재대입

// 2) 참조 자료형 대입 (객체 주소값 저장)
Score s1 = new Score(); // 생성된 Score 객체의 주소값이 s1에 대입됨
Score s2 = s1;          // s1의 주소값이 s2에 대입되어 두 변수가 동일 객체를 참조함
```

# 화살표(`->`) 연산자

현대 자바 문법에서 switch 표현식과 람다 표현식(Lambda Expression)을 작성할 때 사용되는 구문 연산자입니다.

**주요 용도:**
* **switch 표현식**: 각 case의 분기 결과를 바로 반환하거나 실행할 구문을 지정합니다. 기존 break 문 없이도 fall-through 현상이 발생하지 않아 코드가 간결해집니다.
* **람다 표현식**: `(매개변수) -> { 실행문; }` 형태로 매개변수와 함수 본문(로직)을 연결할 때 사용합니다.

```java
// 1) switch 표현식에서의 화살표 연산자
int day = 1;
String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    default -> "Invalid day";
};

// 2) 람다 표현식에서의 화살표 연산자
List<String> list = List.of("apple", "banana");
list.forEach(item -> System.out.println(item));
```

# 3항 연산자

3항 연산자는 항이 3개다.

이 연산은 두 종류의 결과가 나올 수 있다.  
* 조건식이 만족한다면 (조건식 = `true`) -> 2번째 항이 출력된다.
* 조건식을 만족하지 않는다면 (`false`) -> 3번째 항이 출력된다.

```java
public class ConditionalOperatorTest {
    public static void main(String[] args) {
        int score = 85;

        // 조건식 ? 참일 때 결과 : 거짓일 때 결과
        // score가 80 이상이면 "합격", 80 미만이라면 "불합격"을 문자열 변수에 대입합니다.
        String result = (score >= 80) ? "합격" : "불합격"; // 80 이상이므로 "합격"이 result에 담겨있을 것이다

        System.out.println("점수: " + score);
        System.out.println("판정 결과: " + result); 
    }
}
```

# 연산자 우선 순위

자바 연산자 우선순위 및 연산 방향 정리

| 순위 (위에서 아래 ↓) | 연산자 : 연산 우선 순서는 왼쪽에서 오른쪽 (→)이다 |
| --- | --- |
| 1 | 논리(`!`), 비트(`~`), 부호(`+`, `-`), 증감(`++`, `--`) |
| 2 | 산술(`*`, `/`, `%`) |
| 3 | 산술(`+`, `-`) |
| 4 | 쉬프트(`<<`, `>>`, `>>>`) |
| 5 | 비교(`<`, `>`, `<=`, `>=`, `instanceof`) |
| 6 | 비교(`==`, `!=`) |
| 7 | 논리(`&`) |
| 8 | 논리(`^`) |
| 9 | 논리(`\|`) |
| 10 | 논리(`&&`) |
| 11 | 논리(`\|\|`) |
| 12 | 조건(`?:`) |
| 13 | 대입(`>>>=`, `>>=`, `<<=`, `\|=`, `^=`, `&=`, `%=`, `/=`, `*=`, `-=`, `+=`, `=`) |

# (optional) Java 13. switch 연산자

switch 연산자는 크게 3가지의 형태가 있습니다.  
이는 전통적인 switch문 / 현대적인 switch표현식 / 패턴 매칭방식 입니다.

## 전통적인 switch 문

`case 값:` 형태로 작성하며, 각 케이스의 실행이 끝난 후 switch 블록을 탈출하기 위해 break를 명시해야 합니다.  
break를 작성하지 않으면 다음 케이스의 명령까지 연속으로 실행되는 fall-through 현상이 발생합니다.

```java
int number = 2;

switch (number) {
    case 1:
        System.out.println("ONE");
        break; // break가 없으면 아래 case로 fall-through 발생
    case 2:
        System.out.println("TWO");
        break;
    default:
        System.out.println("기타");
}
```

## 현대적인 switch 표현식 (Switch Expression)

화살표 구문 (`->`)을 이용해 `case 값 ->` 형태로 작성하며, 분기 결과를 바로 반환하므로 break를 작성할 필요가 없고 fall-through가 발생하지 않습니다.

* **결과값 변수 대입**: switch 구문 자체가 하나의 값(표현식)으로 평가되므로, 결과를 변수에 바로 대입할 수 있습니다.
* **default 및 완전성(Exhaustiveness)**: 표현식으로 사용할 때는 모든 가능한 입력 경로에서 결과값이 제공되어야 하므로 일반적으로 default 케이스를 포함해야 합니다.
* **yield 키워드**: 케이스 블록 안에서 여러 문장을 실행한 뒤 최종 결과값을 반환해야 할 때는 `{}` 블록과 함께 `yield` 키워드를 사용합니다.

```java
int number = 2;

// switch 결과를 변수에 바로 대입
String result = switch (number) {
    case 1 -> "ONE";
    case 2 -> {
        System.out.println("추가 작업 수행");
        yield "TWO"; // 블록 내에서 계산된 최종 값을 반환
    }
    default -> "기타";
};
```

## 패턴 매칭 switch (Pattern Matching for switch)

Object와 같은 상위 타입의 변수를 받아 실제 런타임 객체 타입, 타입 변수, 그리고 추가 조건(`when`)을 함께 검사하여 분기할 수 있는 기능입니다.

* 타입 캐스팅 코드를 줄여주며, 더 구체적인 조건을 포괄적인 조건보다 먼저 배치해야 합니다.
* `case null`을 명시적으로 작성하여 안전하게 null 예외 처리를 할 수 있습니다.

```java
Object obj = 42;

switch (obj) {
    case Integer i when i > 10 -> System.out.println("10보다 큰 정수: " + i);
    case Integer i -> System.out.println("정수: " + i);
    case String s when s.isEmpty() -> System.out.println("빈 문자열");
    case String s -> System.out.println("문자열: " + s);
    case null -> System.out.println("null 값 처리");
    default -> System.out.println("기타 타입");
}
```

### switch 방식별 장단점 비교표

| 구분 | 전통적인 switch문 | 현대적인 switch 표현식 (`->`) | 패턴 매칭 switch 방식 |
| --- | --- | --- | --- |
| **핵심 구조** | `case 값:` 콜론 구문 및 break 제어 | `case 값 ->` 화살표 구문 및 yield 활용 | `case 타입 변수 when 조건 ->` 패턴 검사 |
| **반환값 대입** | 불가능 (명령문 구문) | 가능 (결과를 변수에 즉시 대입) | 가능 (결과를 변수에 즉시 대입) |
| **장점** | • 기존 자바 코드 및 하위 버전과의 호환성이 뛰어남.<br>• break를 의도적으로 생략하여 여러 case에 동일한 로직을 적용하는 fall-through 활용 가능. | • break 문이 필요 없어 코드가 간결함.<br>• break 누락으로 인한 의도치 않은 fall-through 버그 방지.<br>• 블록 연산 필요 시 yield를 사용해 결과값을 안전하게 반환. | • Object 등 상위 타입의 런타임 타입 검사 및 캐스팅을 한 번에 처리.<br>• when 절로 세부 조건 추가 검사 가능.<br>• case null을 명시하여 안전한 null 예외 처리 지원. |
| **단점 및 주의사항** | • break 누락 시 다음 case까지 실행되는 fall-through 버그 위험 존재.<br>• 결과 저장을 위해 외부 변수 선언이 필요하여 코드가 길어짐. | • 표현식으로 활용 시 모든 분기에서 결과값이 보장되어야 하므로 default 작성이 필수적임 (완전성 요구). | • 구체적인 조건 패턴을 포괄적 패턴보다 먼저 배치해야 하며, 순서가 어긋나면 컴파일 오류 발생. |
| **주요 활용 상황** | 레거시 코드 유지보수 및 단순 구문 실행 | 입력값에 따른 결과값 반환 및 간결한 변수 초기화 | 객체 다형성 기반의 타입 분기 및 복합 조건 처리 |

---

**참고자료**

[수업 pdf자료] 0820~0828일차  
[자바 기초 강의] 이것이 자바다  
범위 : 26강. 3.1 부호 연산자와 증감 연산자 ~ 38강 4.1 코드 실행 흐름 제어  
https://www.youtube.com/playlist?list=PLVsNizTWUw7EmX1Y-7tB2EmsK6nu6Q10q
