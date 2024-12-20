
# CORS (Cross-Origin Resource Sharing)와 Spring Boot에서의 설정

## CORS란 무엇인가?

CORS는 클라이언트(브라우저)가 서로 다른 출처에서 온 리소스를 안전하게 요청할 수 있도록 허용하는 웹 보안 메커니즘입니다.  
웹 브라우저는 기본적으로 **동일 출처 정책(Same-Origin Policy)**을 따르며, 이는 한 출처에서 로드된 웹 페이지가 다른 출처의 리소스에 접근하는 것을 제한합니다.

### 주요 개념
- **출처(Origin)**: 프로토콜, 호스트, 포트를 조합한 URL 정보입니다.  
  예) `http://localhost:3000`와 `http://localhost:8080`은 서로 다른 출처입니다.
- **CORS 동작 원리**: 클라이언트가 요청을 보낼 때 브라우저는 CORS 정책을 검사하며, 서버가 이를 명시적으로 허용하면 요청이 성공합니다.

---

## CORS를 사용하는 이유

브라우저는 기본적으로 보안상의 이유로 다른 출처에서 오는 요청을 제한합니다.  
그러나 외부 API 호출이나 프론트엔드와 백엔드가 다른 출처에서 실행될 경우, 이를 안전하게 허용하기 위해 CORS 설정이 필요합니다.

### 사용 사례
- React 앱(`http://localhost:3000`)이 Spring Boot API 서버(`http://localhost:8080`)와 통신하는 경우.
- 브라우저가 CORS 정책을 검사하며, 서버가 해당 요청을 허용하지 않으면 요청이 차단됩니다.

---

## Spring Boot에서 CORS 설정

Spring Boot에서 CORS 설정은 프론트엔드와 백엔드가 다른 출처에서 실행될 때 브라우저가 요청을 차단하지 않도록 하기 위해 필요합니다.

### Spring Boot에서의 CORS 설정 방법

#### 1. @CrossOrigin 어노테이션 사용
컨트롤러나 메서드 수준에서 특정 출처를 허용합니다.

```java
@RestController
@CrossOrigin(origins = "http://localhost:3000")
public class MyController {

    @GetMapping("/api/data")
    public String getData() {
        return "Hello, World!";
    }
}
```

#### 2. 전역 CORS 설정

`@Configuration`을 사용하여 애플리케이션 전체에 CORS 정책을 적용합니다.

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class CorsConfig {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**") // 모든 경로에 대해 CORS 설정 적용
                        .allowedOrigins("http://localhost:3000") // 허용할 출처
                        .allowedMethods("GET", "POST", "PUT", "DELETE") // 허용할 HTTP 메서드
                        .allowedHeaders("*") // 모든 헤더 허용
                        .allowCredentials(true); // 자격 증명(쿠키, 인증 헤더) 허용
            }
        };
    }
}
```

### 주요 설정 항목
- `addMapping("/**")`: 모든 경로에 대해 CORS 설정을 적용.
- `allowedOrigins("http://localhost:3000")`: 특정 출처의 요청만 허용.
- `allowedMethods("GET", "POST", "PUT", "DELETE")`: 허용할 HTTP 메서드 지정.
- `allowCredentials(true)`: 자격 증명(쿠키 등) 허용.

---

## 요약

- **CORS란?** 서로 다른 출처 간에 리소스를 안전하게 공유할 수 있도록 허용하는 메커니즘.
- **왜 필요한가?** 보안상의 이유로 기본적으로 차단되는 요청을 허용하기 위해 사용.
- **Spring Boot에서 CORS 설정**:
  - `@CrossOrigin`: 컨트롤러/메서드 단위로 설정.
  - `@Configuration`: 애플리케이션 전체에 전역 설정.

Spring Boot의 CORS 설정은 프론트엔드와 백엔드 간의 원활한 통신을 보장합니다.
