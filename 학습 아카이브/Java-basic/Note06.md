## 자바 상속의 특징

부모 클래스(상위 클래스)와 자식 클래스(하위 클래스)가 있으며, 

자식 클래스는 부모 클래스를 선택해서,

그 부모의 멤버를 상속받아 그대로 쓸 수 있게 된다.

- 기존 클래스를 재사용해서 새로운 클래스를 작성하는 것

=> 효율적이고 개발시간을 줄일 수 있다.

- 두 클래스를 조상과 자손으로 관계를 맺는 것
- 자손은 조상의 모든 멤버를 상속받는다.
- 자손의 멤버개수는 조상보다 같거나 많다.
- 상속을 받을 때 'extends'키워드를 사용한다.
- 부모 클래스의 private접근 제한을 갖는 필드 및 메소드는 자식이 물려받을 수 없다.

- 부모와 자식 클래스가 서로 다른 패키지에 있다면,

부모의 default접근 제한을 갖는 필드 및 메소드도 물려받을 수 없다. 

( default접근 제한은 같은 패키지에 있는 클래만 접근이 가능)

```java
// 부모 클래스public class Parent {
    String name;
    int age;

    public void nameAndAge(){
        System.out.println("이름: "+ name);
        System.out.println("나이: "+ age);
    }
}

```

```java
// 자식 클래스public class Child extends Parent {
    public Child(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public static void main(String[] args) {
        Child c = new Child("sophie",23);

        c.nameAndAge();

    }
}
// 이름: sophie
// 나이: 23
```

=> 자식클래스에 변수와 메소드를 선언하지 않아도 

부모클래스를 상속받았기 때문에 변수와 메소드를 사용할 수 있다. 

# super?

## 헷갈리는 Super()와 super의 차이

### **super란?**

부모 클래스로부터 상속받은 필드(멤버변수)나 메소드를 자식클래스에서 참조하는데 사용하는 참조 변수.

this를 써서 인스턴스 변수와 지역 변수를 구분하던 것처럼 super를 이용하며

부모 클래스의 변수와 자식 클래스의 변수를 구분하여 사용할 수 있다.

**인스턴스 변수가 선언된 부모 클래스**

```java
class Parents{

	int test_num = 10;

}
```

**부모 클래스의 인스턴스 변수와 이름이 같은 변수를 초기화한 자식 클래스**

```java
class Child extends Parents{

	int test_num = 15;

	public void test_method() {
		System.out.println("부모 클래스가 가진 값: "+super.test_num);
		System.out.println("자식 클래스가 가진 값: "+test_num);
		System.out.println("자식 클래스가 가진 값: "+this.test_num);
	}

}
```

**자식 클래스 객체를 만들어서 메서드를 실행한 코드**

```java
public class Test {
	public static void main(String[] args) {

		Child child = new Child();

		child.test_method();

	}

}

//실행결과
// 부모 클래스가 가진 값: 10;
//자식 클래스가 가진값: 15;
// 자식 클래스가 가진값 :15;
```

super를 통해서 변수가 부모것인지 자식것인지 구분해줄 수 있다.

단, super도 this와 마찬가지로 인스턴스 메서드 안 에서만 사용이 가능하다.

클래스 메서드에선 사용이 불가능하다.

```java
//부모 클래스public class Parent {
    String name;
    int age;

    public Parent(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void nameAndAge(){
        System.out.println("이름: "+ name);
        System.out.println("나이: "+ age);
    }
}

```

```java
//자식 클래스public class Child extends Parent {
    public Child(String name, int age) {
        super(name, age);
    }

    public static void main(String[] args) {
        Child c = new Child("sophie",23);

        c.nameAndAge();

    }
}
// 실행결과
이름: sophie 
나이: 23
```
