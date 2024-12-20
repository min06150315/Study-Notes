
# Java: Overriding vs Overloading

Java에서 **다형성(Polymorphism)** 을 구현하는 중요한 두 가지 개념인 오버라이딩(Overriding)과 오버로딩(Overloading)에 대해 알아봅니다. 각각의 정의와 특징, 예제를 통해 차이를 명확히 이해할 수 있습니다.

---

## 1. 메서드 오버라이딩 (Method Overriding)

메서드 오버라이딩은 상속 관계에 있는 클래스에서 **부모 클래스의 메서드를 자식 클래스에서 재정의**하는 것입니다.

### 특징
- **메서드 이름, 매개변수 목록, 반환 타입**이 부모 클래스와 동일해야 합니다.
- 부모 클래스의 메서드는 `public` 또는 `protected`이어야 오버라이딩할 수 있습니다.
- 반환 타입은 부모 메서드와 동일하거나, 상속 관계에 있는 더 구체적인 타입(코바리언트 타입)을 사용할 수 있습니다.
- 접근 제어자는 부모 메서드보다 넓은 범위로 변경할 수 있습니다. (예: `protected` → `public`)
- `@Override` 어노테이션을 사용하여 오버라이딩을 명확히 표시하고 컴파일러의 검사를 받을 수 있습니다.

### 예제: 메서드 오버라이딩
```java
// 부모 클래스
class Animal {
    public void makeSound() {
        System.out.println("Some generic animal sound");
    }
}

// 자식 클래스
class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        myAnimal.makeSound();  // 출력: Some generic animal sound
        
        Animal myDog = new Dog();  // 다형성: Animal 타입으로 Dog 객체 참조
        myDog.makeSound();  // 출력: Bark
    }
}
```

---

## 2. 메서드 오버로딩 (Method Overloading)

메서드 오버로딩은 **같은 이름의 메서드를 매개변수의 개수, 타입, 순서를 달리하여 여러 번 정의**하는 것입니다.

### 특징
- 메서드 이름은 같지만, **매개변수의 개수, 타입, 순서**가 달라야 합니다.
- 반환 타입은 오버로딩을 식별하는 기준이 될 수 없습니다.
- 같은 클래스 내에서만 사용됩니다.

### 예제: 메서드 오버로딩
```java
class Printer {
    // 문자열을 출력하는 메서드
    public void print(String message) {
        System.out.println("Printing message: " + message);
    }

    // 정수를 출력하는 메서드
    public void print(int number) {
        System.out.println("Printing number: " + number);
    }

    // 두 정수를 출력하는 메서드
    public void print(int number1, int number2) {
        System.out.println("Printing two numbers: " + number1 + " and " + number2);
    }
}

public class Main {
    public static void main(String[] args) {
        Printer printer = new Printer();
        printer.print("Hello World");  // 출력: Printing message: Hello World
        printer.print(123);           // 출력: Printing number: 123
        printer.print(10, 20);        // 출력: Printing two numbers: 10 and 20
    }
}
```

---

## 3. 오버라이딩 vs 오버로딩 비교

| 구분             | 오버라이딩 (Overriding)                        | 오버로딩 (Overloading)                        |
|------------------|-----------------------------------------------|----------------------------------------------|
| **정의**         | 부모 클래스의 메서드를 자식 클래스에서 재정의  | 같은 이름의 메서드를 매개변수 목록을 달리하여 정의 |
| **목적**         | 상속받은 메서드의 기능 변경                   | 같은 기능을 다양한 매개변수로 구현            |
| **메서드 이름**  | 동일                                          | 동일                                         |
| **매개변수**     | 동일 (변경 불가)                              | 다를 수 있음 (개수, 타입, 순서)               |
| **반환 타입**    | 동일하거나 더 구체적인 타입                    | 동일                                         |
| **사용 위치**    | 상속 관계에서 부모-자식 클래스 간              | 같은 클래스 내                               |
| **접근 제어자**  | 부모보다 넓은 범위로 변경 가능                 | 동일                                         |

---

## 결론
- **메서드 오버라이딩**: 상속 관계에서 부모 클래스의 메서드를 자식 클래스에서 재정의하여 다형성을 구현.
- **메서드 오버로딩**: 같은 클래스 내에서 메서드 이름을 재사용하며, 매개변수를 달리하여 다양한 버전의 메서드를 구현.

두 개념 모두 Java에서 다형성을 활용하는 중요한 기술입니다.
