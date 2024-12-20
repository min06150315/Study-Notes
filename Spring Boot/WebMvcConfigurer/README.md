
# WebMvcConfigurer란?

`WebMvcConfigurer`는 Spring MVC에서 웹 애플리케이션의 설정을 커스터마이즈하는 데 사용되는 인터페이스입니다.  
이 인터페이스를 구현하여 다양한 설정을 추가하거나 오버라이드할 수 있습니다.

---

## 주요 역할

### 1. HTTP 요청 처리 방법 설정
- Spring MVC의 요청 처리 방식을 세밀하게 조정할 수 있습니다.
- 예) 인터셉터 설정, 메시지 컨버터 설정, 뷰 리졸버 설정 등.

### 2. 커스텀 필터 및 인터셉터 추가
- `addInterceptors` 메서드를 사용해 애플리케이션에 커스텀 인터셉터를 추가할 수 있습니다.
- **인터셉터**: 요청과 응답을 가로채어 처리할 수 있는 기능.

### 3. CORS 설정
- `addCorsMappings` 메서드를 사용하여 Cross-Origin Resource Sharing (CORS)을 설정합니다.
- 서로 다른 도메인 간 리소스 공유 시 보안 제한을 처리.

### 4. 뷰 리졸버 설정
- `configureViewResolvers` 메서드를 사용하여 뷰 리졸버를 설정합니다.
- `addArgumentResolvers`를 통해 커스텀 인수 해석기를 추가할 수 있습니다.

### 5. 컨버터 및 포맷터 설정
- `addFormatters` 메서드를 사용하여 커스텀 포맷터나 컨버터를 등록합니다.

### 6. 기타 설정
- **정적 리소스 설정**: `addResourceHandlers` 메서드로 정적 리소스 매핑.
- **기본 서블릿 처리 설정**: `configureDefaultServletHandling` 메서드로 기본 서블릿 동작 설정.
- **메시지 컨버터 설정**: `configureMessageConverters` 메서드를 사용하여 메시지 컨버터를 설정.

---

## 예제 코드

```java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    // 1. 인터셉터 설정
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new MyCustomInterceptor())
                .addPathPatterns("/api/**"); // 특정 경로에 인터셉터 적용
    }

    // 2. CORS 설정
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/api/**") // 특정 경로에 대해 CORS 설정 적용
                .allowedOrigins("http://example.com") // 허용할 출처
                .allowedMethods("GET", "POST"); // 허용할 HTTP 메서드
    }
    
    // 3. 정적 리소스 설정
    @Override
    public void addResourceHandlers(ResourceHandlerRegistry registry) {
        registry.addResourceHandler("/static/**") // 요청 경로
                .addResourceLocations("classpath:/static/"); // 리소스 위치
    }
}
```

---

## 요약

- **WebMvcConfigurer의 주요 기능**:
  1. HTTP 요청 처리 방식 커스터마이즈.
  2. 커스텀 인터셉터 추가.
  3. CORS 설정.
  4. 뷰 리졸버 및 인수 해석기 설정.
  5. 컨버터 및 포맷터 추가.

- Spring MVC의 기본 설정을 오버라이드하여 애플리케이션에 맞는 방식으로 동작하도록 설정할 수 있습니다.

`WebMvcConfigurer`는 Spring Boot 애플리케이션의 유연한 설정을 제공하며, CORS, 인터셉터, 정적 리소스 등 다양한 기능을 지원합니다.
