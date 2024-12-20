
# Java 객체지향 프로그래밍 (OOP)

Java의 객체지향 프로그래밍(OOP, Object-Oriented Programming)은 프로그램을 **"객체"** 단위로 구성하여, 복잡한 시스템을 효율적으로 관리하고 확장 가능하게 만드는 프로그래밍 패러다임입니다. Java에서 객체지향의 핵심 개념은 클래스, 객체, 상속, 다형성, 캡슐화, 추상화입니다. 각 개념을 자세히 살펴보겠습니다.

---

## 1. 클래스 (Class)

클래스는 객체를 생성하기 위한 템플릿 또는 설계도입니다. 클래스는 속성(필드)과 동작(메서드)을 정의합니다. 객체는 클래스를 기반으로 생성되며, 클래스의 인스턴스라고도 불립니다.

```java
public class Car {
    // 속성 (필드)
    private String model;
    private int year;

    // 생성자
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
    }

    // 동작 (메서드)
    public void start() {
        System.out.println("The car is starting.");
    }
}
```

---

## 2. 객체 (Object)

객체는 클래스를 기반으로 생성된 실체입니다. 각 객체는 클래스에 정의된 속성과 동작을 가지며, 클래스의 인스턴스라고 합니다.

```java
Car myCar = new Car("Tesla", 2020);
myCar.start();  // 메서드 호출
```

---

## 3. 캡슐화 (Encapsulation)

캡슐화는 객체의 데이터를 보호하고, 외부에서 객체의 상태를 변경하는 방법을 제어하는 개념입니다. 객체의 속성(필드)은 보통 `private`으로 설정하고, 외부에서 접근할 수 있도록 `public` 메서드를 제공하는 방식입니다. 이를 통해 **데이터 은닉(data hiding)** 과 데이터의 무결성을 유지할 수 있습니다.

```java
public class Car {
    private String model;  // private으로 선언하여 외부 접근을 제한

    // getter 메서드
    public String getModel() {
        return model;
    }

    // setter 메서드
    public void setModel(String model) {
        this.model = model;
    }
}
```

---

## 4. 상속 (Inheritance)

상속은 기존 클래스를 기반으로 새로운 클래스를 만들 수 있는 기능을 제공합니다. 상속을 통해 코드 재사용성을 높이고, 공통된 기능을 부모 클래스에서 정의하고, 자식 클래스에서 특화된 기능을 추가할 수 있습니다.

```java
// 부모 클래스
public class Vehicle {
    public void start() {
        System.out.println("Vehicle is starting");
    }
}

// 자식 클래스
public class Car extends Vehicle {
    public void honk() {
        System.out.println("Car is honking");
    }
}

Car myCar = new Car();
myCar.start();  // 부모 클래스의 메서드 호출
myCar.honk();   // 자식 클래스의 메서드 호출
```

---

## 5. 다형성 (Polymorphism)

다형성은 같은 이름의 메서드가 객체의 종류에 따라 다르게 동작할 수 있게 하는 개념입니다. Java에서는 **메서드 오버로딩** 과 **메서드 오버라이딩** 을 통해 다형성을 구현할 수 있습니다.

### 메서드 오버로딩 (Method Overloading)

같은 이름의 메서드를 매개변수의 타입이나 개수에 따라 다르게 정의하는 것입니다.

```java
public class Printer {
    public void print(String message) {
        System.out.println("Printing message: " + message);
    }

    public void print(int number) {
        System.out.println("Printing number: " + number);
    }
}
```

### 메서드 오버라이딩 (Method Overriding)

부모 클래스의 메서드를 자식 클래스에서 재정의하는 것입니다.

```java
public class Animal {
    public void makeSound() {
        System.out.println("Some sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Bark");
    }
}

Animal myDog = new Dog();
myDog.makeSound();  // "Bark" 출력
```

---

## 6. 추상화 (Abstraction)

추상화는 객체의 복잡한 구현 세부사항을 숨기고 중요한 정보만을 노출하는 개념입니다. 추상화는 **추상 클래스** 또는 **인터페이스** 를 사용하여 구현됩니다.

### 추상 클래스 (Abstract Class)

인스턴스를 만들 수 없는 클래스이며, 일부 메서드는 구현되지 않고 자식 클래스에서 구현해야 합니다.

```java
abstract class Animal {
    abstract void makeSound();  // 추상 메서드

    public void sleep() {
        System.out.println("Sleeping...");
    }
}

class Dog extends Animal {
    public void makeSound() {
        System.out.println("Bark");
    }
}
```

### 인터페이스 (Interface)

클래스가 구현해야 하는 메서드의 선언만을 포함하는 객체의 계약을 정의합니다.

```java
interface Animal {
    void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Bark");
    }
}
```

---

## 7. 객체지향의 특징 정리

- **추상화**: 불필요한 세부사항을 숨기고 중요한 기능만 제공
- **캡슐화**: 객체의 상태와 기능을 하나로 묶고, 외부에서 직접 접근을 막음
- **상속**: 부모 클래스의 특성을 자식 클래스가 상속받아 재사용
- **다형성**: 하나의 객체가 여러 형태로 동작할 수 있음

---

## 결론

Java에서 객체지향 프로그래밍은 코드의 재사용성과 유지보수성을 높이고, 시스템을 더 쉽게 확장할 수 있도록 돕는 중요한 개념입니다. 클래스와 객체를 중심으로, 데이터를 은닉하고, 상속과 다형성을 통해 효율적인 프로그램을 설계할 수 있습니다.
