## 1. 자바 상속의 특징
- `extends`로 부모 클래스 상속.
- 단일 상속만 가능 (부모는 1개).
- 다중 상속 필요 시 인터페이스로 대체.
- 부모 필드·메서드를 자식이 그대로 사용.
- `private` 멤버는 직접 접근 불가.
- 생성자는 상속 안 됨.
- 모든 클래스는 `Object`의 자식 (최상위 부모).
- 자식 객체 생성 시 부모 객체가 먼저 생성됨.
- 자식 → 부모 타입 변환은 자동.

```java
class Phone { void bell() { } }
class SmartPhone extends Phone { void internet() { } }
```

---

## 2. super 키워드
- 바로 위 부모 객체를 가리키는 참조 변수.
- 용도 3가지:
  - `super.필드` : 부모 필드 접근
  - `super.메서드()` : 부모 메서드 호출
  - `super(...)` : 부모 생성자 호출
- `super(...)`는 자식 생성자 첫 줄에만 위치 가능.
- 생략 시 컴파일러가 `super()` 자동 삽입.
- 부모에 기본 생성자 없으면 `super(매개값)` 필수.
- `this`와 `super(...)`는 한 생성자에서 같이 사용 불가 (둘 다 첫 줄이어야 하므로).

```java
class Child extends Parent {
    Child() {
        super("값");        // 부모 생성자
    }
    void show() {
        super.show();       // 부모 메서드
    }
}
```

---

## 3. 메소드 오버라이딩
- 부모 메서드를 자식에서 재정의.
- 이름·매개변수·리턴 타입 동일.
- 접근 제한자는 부모보다 좁게 변경 불가.
- 부모보다 더 넓은 예외 throws 불가.
- `@Override`로 재정의 여부를 컴파일러가 검사.
- `static`, `private`, `final` 메서드는 재정의 불가.
- 오버로딩 = 같은 이름 + 다른 매개변수 (별개 개념).

```java
class Animal { void sound() { System.out.println("..."); } }
class Dog extends Animal {
    @Override
    void sound() { System.out.println("멍멍"); }
}
```

---

## 4. 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
- 실행 시점에 실제 객체 타입 기준으로 오버라이딩된 메서드를 호출하는 방식.
- 런타임 다형성
- 참조 변수 타입이 아니라 **실제 생성된 객체 타입**으로 결정.
- 부모 타입 변수로는 부모에 선언된 메서드만 호출 가능.
- 필드는 해당 안 됨 (참조 변수 타입 기준).

```java
Animal a = new Dog();
a.sound();   

a = new Cat();
a.sound();   
```

---

## 5. 추상 클래스
- 객체 생성 불가, 상속용으로 정의.
- `abstract class`로 선언.
- 일반 필드·생성자·일반 메서드 보유 가능.
- 자식 생성 시 `super()`로 생성자 호출됨.
- 추상 메서드: 구현부 없이 선언만, 자식이 반드시 재정의.
- 추상 메서드가 있으면 클래스도 반드시 `abstract`.
- 자식이 추상 메서드를 다 구현 안 하면 자식도 추상 클래스.
- 공통 기능은 부모에, 달라지는 부분은 자식에 맡기는 용도.

```java
abstract class Shape {
    abstract double area();
}
class Circle extends Shape {
    @Override
    double area() { return Math.PI * 10 * 10; }
}
// new Shape();  // 컴파일 에러
```

---

## 6. final 키워드
- 변경·확장을 막는 키워드.
- 위치별 의미:

| 위치 | 의미 |
|---|---|
| 변수/필드 | 값 변경 불가 (상수) |
| 메서드 | 오버라이딩 불가 |
| 클래스 | 상속 불가 |

- final 필드는 선언 시 또는 생성자에서 1회 초기화.
- 상수는 `static final` + 대문자 스네이크 표기.
- 대표 final 클래스: `String`, `Integer`.
- `final` 참조 변수는 참조 변경만 불가, 객체 내부 값은 변경 가능.

```java
final int MAX = 100;
final void stop() { }
final class Member { }
```

---

## 7. Object 클래스
- 모든 클래스의 최상위 부모.
- 부모를 명시하지 않으면 자동으로 `extends Object`.
- 모든 객체가 Object의 메서드를 사용 가능.

| 메서드 | 기능 |
|---|---|
| `toString()` | 객체 문자열 표현 반환 (기본: `클래스명@해시코드`) |
| `equals(Object)` | 객체 동등 비교 (기본: 주소 비교 `==`과 동일) |
| `hashCode()` | 객체 해시코드 반환 |
| `getClass()` | 실제 클래스 정보 반환 |
| `clone()` | 객체 복제 |

- `toString()` 재정의로 객체 정보 출력 가능.
- `equals()` 재정의로 내용 비교 가능.
- `equals()`를 재정의하면 `hashCode()`도 같이 재정의 (동등 객체는 해시코드도 동일해야 함).
- `HashMap`, `HashSet`은 `hashCode()` → `equals()` 순으로 비교.

```java
class Member {
    String id;

    @Override
    public String toString() { return "Member:" + id; }

    @Override
    public boolean equals(Object o) {
        return o instanceof Member m && id.equals(m.id);
    }

    @Override
    public int hashCode() { return id.hashCode(); }
}

