## 자바가 제공하는 다양한 연산자에 대해 알아봅시다.


### 산술연산자

우리가 알고 있는 일반적인 연산에 사용됩니다. 

사칙연산을 기본으로 하지만 생소한 연산자도 있습니다.

산술연산자는 +, -, *, /, % 5가지로 구성되어있습니다.

나머지 %는 나머지값을 구하는 연산자입니다. 

**예제코드)**

```jsx
public static void 산술연산자() {
    int var1 = 1;
    int var2 = 2;

    System.out.println("var1 + var2 = " + (var1 + var2));
    System.out.println("var1 - var2 = " + (var1 - var2));
    System.out.println("var1 * var2 = " + (var1 * var2));
    System.out.println("var1 / var2 = " + (var1 / var2));
    System.out.println("var1 % var2 = " + (var1 % var2));

    double var3 = 1;
    double var4 = 2;
    System.out.println("var3 / var4 = " + (var3 / var4));
}
```

**결과 값)**

```jsx
var1 + var2 = 3
var1 - var2 = -1
var1 * var2 = 2
var1 / var2 = 0
var1 % var2 = 1
var3 / var4 = 0.5
```

다른 것들은 이해하기 어렵지 않지만 

%가 좀 햇갈립니다. 

5 % 2 이 연산자는 5를 2로 나누었을 때의 

나머지 값을 구하는 연산자입니다. 

그래서 답은 1!

### **비트 연산자(bitwise operator)**

비트 연산자는 비트(bit) 단위로 논리 연산을 할 때 사용하는 연산자입니다.

또한, 비트 단위로 전체 비트를 왼쪽이나 오른쪽으로 이동시킬 때도 사용합니다.

<img width="1200" height="415" alt="Image" src="https://github.com/user-attachments/assets/f5d8c5ab-588f-4862-a169-05552e744f90" />

**예제코드)**

```jsx
public static void 비트연산자() {
    /**
     * int 자료형은 8 Byte이므로 32비트로 표현된다.
     * 0000 0000 0000 0000
     * 연산 설명을 편의를 위해 앞의 12자리는 제외하고 실제 값이 표현되는 마지막 4자리만 표현하겠습니다.
     */
    int var1 = 3;  // 0011
    int var2 = 5;  // 0101
    System.out.println("var1 & var2 = " + (var1 & var2));
    System.out.println("var1 | var2 = " + (var1 | var2));
    System.out.println("var1 ^ var2 = " + (var1 ^ var2));
    System.out.println("var1>> = " + (var1 >> 1));
    System.out.println("var1<< = " + (var1 << 1));
}
```

**결과 값)**

```jsx
var1 & var2 = 1
var1 | var2 = 7
var1 ^ var2 = 6
var1 >> = 1
var1 << = 6
```

### **AND ( & )**

AND 연산자는 같은 위치의 값 모두 1일 경우에 값이 1이 됩니다.

결과값으로 1 (0001) 이 나옵니다.

<img width="815" height="178" alt="Image" src="https://github.com/user-attachments/assets/25e20df3-8d2b-4f43-90ba-677a4b2031b9" />


### **OR ( | )**

OR 연산자는 같은 위치의 값 중 하나라도 1일 경우 값이 1이 됩니다.

결과값으로 7  (0001)이 나옵니다.

<img width="815" height="178" alt="Image" src="https://github.com/user-attachments/assets/25e20df3-8d2b-4f43-90ba-677a4b2031b9" />


### **XOR ( ^ )**

XOR 연산자는 같은 위치의 값 중 한개만 1이어야 1이 됩니다.

결과값으로 6 ( 0110 )이 나옵니다.

<img width="814" height="186" alt="Image" src="https://github.com/user-attachments/assets/7b7b0fab-7a46-41b7-9262-1ebc6d3a6fdf" />


### **Right Shift ( >> )**

Right Shift 연산자는 값을 오른쪽으로 shift 시킵니다.

결과값으로 1이 나옵니다.

<img width="819" height="152" alt="Image" src="https://github.com/user-attachments/assets/1e34012d-0bcd-4868-9227-37e041c7c8c2" />


### **Left Shift ( << )**

Lift Shift 연산자는 값을 왼쪽으로 shift 시킵니다.

결과값으로 6이 나옵니다.

<img width="831" height="155" alt="Image" src="https://github.com/user-attachments/assets/9251deb2-193b-4384-8446-b83b09b75fee" />

### **관계 연산자**

관계 연산자는 양쪽에 있는 데이터를 비교하는 연산자입니다.

<img width="827" height="393" alt="Image" src="https://github.com/user-attachments/assets/fc050eee-63ca-4268-a0f4-3d288d051b9d" />

**예제코드)**

```jsx
public static void 관계연산자() {
    int var1 = 1;
    int var2 = 4;
    Account a = new Account();
    System.out.println("var1 == var2");
    System.out.println(var1 == var2);
    System.out.println("var1 != var2");
    System.out.println(var1 != var2);
    System.out.println("var1 > var2");
    System.out.println(var1 > var2);
    System.out.println("var1 < var2");
    System.out.println(var1 < var2);
    System.out.println("var1 <= var2");
    System.out.println(var1 <= var2);
    System.out.println("var1 >= var2");
    System.out.println(var1 >= var2);
    System.out.println("a instanceof Account");
    System.out.println(a instanceof Account);
}
```

**결과 값)**

```jsx
var1 == var2
false
var1 != var2 
ture
var1 > var2 
false
var1 < var2 
ture
var1 => var2 
false
var1 <= var2 
ture
```

### **논리연산자**

논리연산자는 비트연산과 매우 흡사합니다. 

차이점은 논리연산자의 피연산자는 boolean 타입입니다.

관계 연산자와 혼합하여 많이 사용 됩니다.

연산의 결과가 true(참), false(거짓)으로 반환됩니다. 

<img width="815" height="146" alt="Image" src="https://github.com/user-attachments/assets/75a29f61-5347-4028-9e50-5f5117c6ef00" />


**예제코드)**

```jsx
private static void 논리연산자() {
    boolean var1 = true;
    boolean var2 = true;
    boolean var3 = false;
    boolean var4 = false;

    System.out.println("var1 && var2");
    System.out.println(var1 && var2);
    System.out.println("var1 && var3");
    System.out.println(var1 && var3);
    System.out.println("var1 || var3");
    System.out.println(var1 || var3);
    System.out.println("var3 || var4");
    System.out.println(var3 || var4);
}
```

**결과 값)**

```jsx
var1 && var2
ture
var1 && var3 
false
var1 || var3 
false
var3 || var4 
ture
```

## instanceof

instanceof는 왼쪽 데이터가 오른쪽 클래스와 일치하면 true입니다.

instanceof 객체타입을 확인하는 연산자입니다. 

형변환 가능 여부를 확인하고 부모객체인지 자식 객체인지 확인하는데 사용됩니다. 

instanceof 기본 사용 방법은 “객체 instanceof클래스”를 선언함으로서 사용합니다. 

**예제코드)**

```jsx
public class Test1 extends TestParent {
}

public class TestInterfaceImpl implements TestInterface {
}

class Parent{}
class Child extends Parent{}

public class InstanceofTest {

    public static void main(String[] args){

        Parent parent = new Parent();
        Child child = new Child();

        System.out.println( parent instanceof Parent );  // true
        System.out.println( child instanceof Parent );   // true
        System.out.println( parent instanceof Child );   // false
        System.out.println( child instanceof Child );   // true
    }

}
출처: https://mine-it-record.tistory.com/120 [나만의 기록들:티스토리]
```

**결과 값)**

```jsx
test1 instanceof Test1 
ture
test1 instanceof TestParent
ture
testInterfaceImpl instanceof TestInterfaceImpl 
ture
testInterfaceImpl instanceof TestInterface 
ture
```

instanceof는 상속을 받은 클래스와 상속을 한 클래스도 true가 됩니다.

마찬가지로 interface와 implements 받은 클래스도 결과는 true가 됩니다.

### **assignment(=) operator**

**대입 연산자로서 오른쪽 피연산자의 값을 좌측 피연산자인 변수에 저장한다.**

**오른쪽 피연산자는 리터럴 및 변수, 그리고 다른 연산식이 올 수 있다.**

단순 값 저장하는 대입 연산자가 있고, 연산 수행 후 결과를 저장하는 복합 대입 연산자도 있다.

**예제코드)**

```jsx
private static void assignmentTest() {
    int a = 8;
    int b = 3;

    System.out.println("a = b -> " + (a = b));      
    System.out.println("a += b -> " + (a += b));    // a = a + b
    System.out.println("a -= b -> " + (a -= b));    // a = a - b
    System.out.println("a *= b -> " + (a *= b));    // a = a * b
    System.out.println("a /= b -> " + (a /= b));    // a = a / b
    System.out.println("a %= b -> " + (a &= b));    // a = a & b
}
```

**결과 값)**

```jsx
a = b -> 3
a += b -> 6
a -= b -> 3
a *= b -> 9
a /= b -> 3
a %= b -> 3

```

### **화살표 (->) 연산자**

람다 표현식(lambda expression)이라고도 한다.

람다 표현식이란 간단히 말해 메소드를 하나의 식으로 표현한 것이다.

**예제코드)**

```jsx
// 메소드
int min(int x, int y) {
    retrun x < y ? x : y;
}
// 람다 표현식
(x, y) -> x < y ? x : y;
```

메소드를 람다 표현식으로 표현하면, 클래스를 작성하고 객체를 생성하지 않아도 메소드를 사용할 수 있습니다

자바에서 <u>람다 표현식은 익명 클래스와 같다</u>고 할 수 있습니다.

### 익명 클래스

일반적인 인스턴스 생성법 (`new`)와 다르게 중괄호가 마지막에 붙어있는 구조입니다. 

익명, 즉, 이름이 없는 클래스입니다

이름이 없다는 건 무슨 의미일까?…요

```arduino
//1번
copy csharp  public class Peseon {
      void whoAmI() {
          System.out.println("나는 Person이다.");
      }
  }
```

```scala
//2번
copy scala  public class Child extends Person {
      @Override
      void whoAmI() {
          System.out.println("I'm Child");
      }
  }
```

위는 익명 클래스가 아닌 일반적인 클래스이다.

이런 보통의 경우, 우리는 부모 클래스를 상속 받아 처리하려면

 부모 클래스(Person)를 상속받는 클래스(Child)를 별도로 만들어서 처리한다.

> 💡 Override??
> 
> 
> **Overloading**
> 

그런데 만약 Person를 상속받아 처리해야하는 클래스가 또 필요한 경우, 

매번 Child2 Child3 ... 등의 클래스를 만드는 것은 낭비입니다.

<u>상속 받은 클래스가 재 사용되면 모를까, 그냥 한번 쓰고 버려진다면</u> 

<u>굳이 클래스 파일을 만들 필요는 없겠죠</u>

이럴 경우 익명 클래스를 사용하세용.

```arduino
copy typescript  public static void main(String[] args) {
      Person p = new Person() {
          String name = "Kim";
          @Override
          void whoAmI() {
              System.out.println("나는 " + name + "이다.");
          }
      };
      p.whoAmI();
  }
```

1번에 익명 클래스의 예를 보세요.

인스턴스 생성시, 일반적인 경우와 다르게 중괄호가 더해져 그 안에 처리구문이 들어갔습니다.

따로 상속 받을 자식 클래스를 생성하지 않고,

 인스턴스 생성 부분에서(`new`) 중괄호 내에 자식 클래스의 내용을 선언하는 것이죠.

```
copy scss// 람다 표현식
(x, y) -> x > y ? x : y;
```

```
copy csharp// 익명 클래스new Object() {
    int min(int x, int y) {
        return x < y ? x : y;
    }
}
```

## 3항 연산자

```
copy scss(조건) ? 참일 때 : 거짓일 때
```

## 연산자 우선 순위

단항→이항→삼항 연산자 순으로 우선순위를 갖는다.

산술→비교→논리→대입 연산자 순으로 우선순위를 갖는다.

<img width="589" height="383" alt="Image" src="https://github.com/user-attachments/assets/b94d5ef8-e8be-44f3-86f3-d8cffddeeb54" />
