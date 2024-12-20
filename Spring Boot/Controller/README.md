
# Spring Boot에서 @Controller와 @RestController의 차이점

Spring Boot에서 `@Controller`와 `@RestController`는 모두 웹 요청을 처리하는 컨트롤러 클래스를 정의하는 어노테이션이지만, 그 목적과 반환 방식에 차이가 있습니다.

## @Controller

- **목적**: 주로 JSP, HTML, Thymeleaf 등 뷰(View)를 렌더링하는 데 사용됩니다.
- **반환 값**: 메서드에서 반환하는 값은 뷰의 이름(예: `index.html`)이며, 이 뷰를 반환하여 클라이언트에게 HTML 응답을 제공합니다.
- **특징**: HTML 페이지를 렌더링하는 데 주로 사용되며, `@RequestMapping`과 같은 매핑 어노테이션을 통해 요청을 처리합니다.

### 예시
```java
@Controller
public class MyController {
    
    @RequestMapping("/home")
    public String homePage() {
        return "home"; // home.html을 렌더링
    }
}
```

## @RestController

- **목적**: RESTful 웹 서비스 API를 구축하는 데 사용됩니다.
- **반환 값**: 메서드에서 반환하는 객체는 자동으로 JSON 형식으로 변환되어 클라이언트에 전송됩니다.
- **특징**: 기본적으로 `@ResponseBody`가 포함되어 있어 반환 값이 HTTP 응답 본문에 바로 포함됩니다. 주로 JSON/XML 데이터를 반환하는 REST API에서 사용됩니다.

### 예시
```java
@RestController
public class MyRestController {

    @RequestMapping("/api/greet")
    public String greet() {
        return "Hello, World!"; // JSON 응답 "Hello, World!" 반환
    }
}
```

## 주요 차이점

| 특성                 | @Controller                            | @RestController                      |
|----------------------|---------------------------------------|--------------------------------------|
| **뷰 렌더링 여부**    | 뷰를 렌더링 (HTML 페이지 반환)            | JSON/XML 형식의 데이터를 반환          |
| **자동 응답 본문 처리** | 반환값을 뷰 이름으로 사용, HTML 반환      | `@ResponseBody`가 자동 적용, 응답 본문에 포함 |

### 사용 시점
- **@Controller**: 웹 애플리케이션에서 HTML 페이지를 렌더링할 때 사용합니다.
- **@RestController**: RESTful API를 제공할 때 사용합니다.
