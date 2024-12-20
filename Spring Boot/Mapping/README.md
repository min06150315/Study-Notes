
# Spring MVC의 요청 매핑 어노테이션 정리

Spring MVC에서 `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`은 HTTP 요청을 처리하는 데 사용되는 어노테이션입니다. 각 어노테이션의 차이점은 HTTP 메서드와 관련이 있습니다.

## 1. @RequestMapping

- **기능**: 가장 일반적인 요청 매핑 어노테이션으로, 모든 HTTP 메서드(GET, POST, PUT, DELETE 등)에 대해 처리할 수 있습니다.
- **특징**: 
  - 기본적으로 모든 HTTP 메서드에 대해 처리 가능합니다.
  - `method` 속성을 통해 특정 HTTP 메서드를 지정할 수 있습니다.

### 예시
```java
@RequestMapping(value = "/example", method = RequestMethod.GET)
public String handleRequest() {
    return "Handled GET request";
}
```

---

## 2. @GetMapping

- **기능**: GET 요청만 처리합니다.
- **특징**: `@RequestMapping(method = RequestMethod.GET)`의 축약형으로, 주로 데이터를 조회하는 용도로 사용됩니다.

### 예시
```java
@GetMapping("/example")
public String getExample() {
    return "Handled GET request";
}
```

---

## 3. @PostMapping

- **기능**: POST 요청만 처리합니다.
- **특징**: `@RequestMapping(method = RequestMethod.POST)`의 축약형으로, 주로 서버에 데이터를 전송할 때 사용됩니다.

### 예시
```java
@PostMapping("/example")
public String postExample(@RequestBody ExampleRequest request) {
    return "Handled POST request";
}
```

---

## 4. @PutMapping

- **기능**: PUT 요청만 처리합니다.
- **특징**: `@RequestMapping(method = RequestMethod.PUT)`의 축약형으로, 주로 기존 데이터를 수정하는 용도로 사용됩니다.

### 예시
```java
@PutMapping("/example")
public String putExample(@RequestBody ExampleRequest request) {
    return "Handled PUT request";
}
```

---

## 5. @DeleteMapping

- **기능**: DELETE 요청만 처리합니다.
- **특징**: `@RequestMapping(method = RequestMethod.DELETE)`의 축약형으로, 주로 데이터를 삭제하는 용도로 사용됩니다.

### 예시
```java
@DeleteMapping("/example")
public String deleteExample(@PathVariable Long id) {
    return "Handled DELETE request";
}
```

---

## 요약

| 어노테이션               | 처리하는 HTTP 메서드          | 주요 용도                  |
|-----------------------|--------------------------|-----------------------|
| `@RequestMapping`      | 모든 HTTP 메서드           | 범용 요청 매핑             |
| `@GetMapping`          | GET 요청                 | 데이터 조회                |
| `@PostMapping`         | POST 요청                | 데이터 생성/전송            |
| `@PutMapping`          | PUT 요청                 | 데이터 수정                |
| `@DeleteMapping`       | DELETE 요청              | 데이터 삭제                |

`@RequestMapping`은 모든 HTTP 메서드를 처리할 수 있는 범용 어노테이션이며,  
`@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`은 각각 특정 HTTP 메서드에 특화된 어노테이션으로 가독성과 명확성을 높입니다.
