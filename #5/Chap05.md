
## 1. 클래스 정의
- 객체 생성용 설계도로 정의.
- `class 이름 { 필드; 메서드; }` 형태.
```java
public class Car {
    String model;
    int speed;
}
```
 
## 2. 생성자
- `new` 할 때 호출됨.
- 필드 초기값 설정이 목적.
- 클래스명과 동일한 이름, 리턴 타입 없음.
```java
public Car(String model, int speed) {
    this.model = model;
    this.speed = speed;
}
```
 
## 3. this
- 현재 객체 자기 자신을 가리키는 참조 변수.
- 매개변수와 필드명 같을 때 `this.필드`로 구분.
- `this(...)`는 같은 클래스의 다른 생성자 호출.
## 4. 메서드 정의
- 객체의 기능(동작)을 정의.
- Java: `접근제어자 반환타입 이름(매개변수) { }`
- JS: `이름(매개변수) { }` (`function` 생략)
```java
public void accelerate(int amount) {
    this.speed += amount;
}
```
 
## 5. 객체 생성 (new)
- 힙에 메모리 할당 → 생성자 실행 → 참조값 반환.
- 객체끼리 서로 독립.
```java
Car myCar = new Car("아반떼", 0);
```
 
---
 
# 6. final 필드
- 한 번 초기화되면 변경 불가.
- 선언 시 또는 생성자에서 1회 초기화.
- 미초기화 시 컴파일 에러.
- 상수는 `static final` + 대문자 스네이크 표기.
```java
final String nation = "Korea";
static final double PI = 3.14159;
```
 
---
 
# 7. 접근 제한자
- 접근 범위 제한용 키워드.
| 제한자 | 범위 |
|---|---|
| `public` | 모든 곳 |
| `protected` | 같은 패키지 + 다른 패키지 자식 |
| `default` | 같은 패키지 |
| `private` | 같은 클래스 내부 |
 
- 클래스에는 `public`, `default`만 가능.
- 필드는 보통 `private`으로 정의.
---
 
# 8. Getter / Setter
- `private` 필드 직접 접근 차단용.
- Getter: 값 반환 (`getXxx()`, boolean은 `isXxx()`).
- Setter: 검증 후 저장 (`setXxx()`).
- 핵심 장점은 유효성 검사.
```java
public void setSpeed(int speed) {
    this.speed = (speed < 0) ? 0 : speed;
}
```
 
---
 
# 9. 싱글톤 패턴
- 객체를 단 하나만 생성하는 패턴.
- 생성자 `private` → 외부 `new` 차단.
- `private static` 필드에 유일 객체 저장.
- `public static getInstance()`로 반환.
```java
private static Singleton instance = new Singleton();
private Singleton() {}
public static Singleton getInstance() { return instance; }
```
 
---
 
# 10. 클래스 상속
- 부모 필드·메서드를 자식이 물려받음.
- `extends` 사용.
- 단일 상속만 가능.
- `private` 멤버는 상속 접근 불가.
- 코드 중복 감소가 목적.
```java
class SmartPhone extends Phone { }
```
 
---
 
# 11. 부모 생성자 호출
- 부모 객체가 먼저 생성된 뒤 자식 생성.
- `super(...)`로 부모 생성자 호출.
- 자식 생성자 첫 줄에만 위치 가능.
- 생략 시 `super()` 자동 삽입.
- 부모에 기본 생성자 없으면 `super(매개값)` 필수.
```java
SmartPhone(String model) {
    super(model);
}
```
 
---
 
# 12. 메서드 재정의 (Overriding)
- 부모 메서드를 자식에서 다시 정의.
- 이름·매개변수·리턴 타입 부모와 동일.
- 접근 제한자는 부모보다 좁게 변경 불가.
- `@Override`로 컴파일러 검사.
- 부모 메서드 호출은 `super.메서드()`.
- 오버로딩 = 같은 이름 + 다른 매개변수 (별개 개념).
```java
@Override
void sound() { System.out.println("멍멍"); }
```
 
---
 
# 13. final 클래스 / 메서드
- final 클래스: 상속 불가 (예: `String`).
- final 메서드: 재정의 불가.
```java
public final class Member { }
public final void stop() { }
```
 
---
 
# 14. protected
- 같은 패키지 또는 다른 패키지의 자식 클래스에서 접근 가능.
- 다른 패키지에서는 `new` 부모 객체로 접근 불가.
- 상속받은 자기 자신(`this`/`super`)으로만 접근.
---
 
# 15. 타입 변환
 
## 자동 타입 변환
- 자식 → 부모 타입 대입 시 자동 변환.
- 부모에 선언된 멤버만 사용 가능.
- 재정의된 메서드는 자식 것이 실행.
```java
Animal animal = new Cat();
```
 
## 강제 타입 변환
- 부모 타입 → 자식 타입으로 되돌림.
- 자식 고유 멤버 사용 목적.
```java
Cat cat = (Cat) animal;
```
 
## instanceof
- 실제 객체 타입 확인용 연산자.
- 타입 불일치 캐스팅 시 `ClassCastException`.
- Java 14+ 패턴 매칭으로 확인과 변환 동시 처리.
```java
if (animal instanceof Cat cat) { cat.climb(); }
```
 
---
 
# 16. 다형성
- 같은 타입, 다양한 실행 결과.
- 자동 타입 변환 + 메서드 재정의 기반.
- 객체 교체로 확장성 확보.
- 매개변수를 부모 타입으로 선언하면 모든 자식 전달 가능.
```java
car.tire = new HankookTire();
car.run();  // 한국 타이어 굴러감
```
 
---
 
# 17. 추상 클래스
- 객체 생성 불가, 상속용 클래스로 정의.
- `abstract` 키워드 사용.
- 필드·생성자·일반 메서드 보유 가능.
- 추상 메서드: 구현부 없음, 자식이 반드시 재정의.
- 추상 메서드는 추상 클래스 안에서만 선언.
```java
abstract class Animal {
    abstract void sound();
}
```
 
---
 
# 18. sealed 클래스
- 상속 가능한 자식을 제한하는 클래스 (Java 17 정식).
- `permits`에 허용 클래스 나열.
- 자식은 `final` / `sealed` / `non-sealed` 중 하나 필수.
  - `final`: 상속 종료
  - `sealed`: 허용된 자식만 상속
  - `non-sealed`: 제한 해제
- 같은 패키지(모듈)에 위치해야 함.
- 같은 파일 선언 시 `permits` 생략 가능.

