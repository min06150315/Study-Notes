
# Spring Data JPA 자동 구현 메서드

Spring Data JPA는 `JpaRepository`를 상속받으면 기본적인 CRUD 메서드를 자동으로 제공하며, 추가적인 메서드를 정의하지 않아도 데이터베이스와 상호작용할 수 있습니다.

## 기본 CRUD 메서드
`JpaRepository`는 기본적으로 다음과 같은 메서드를 제공합니다:
- `save()`: 엔티티 저장
- `findById()`: ID로 엔티티 조회
- `findAll()`: 모든 엔티티 조회
- `deleteById()`: ID로 엔티티 삭제

## 메서드 이름 규칙
Spring Data JPA에서는 메서드 이름을 분석하여 SQL 쿼리를 자동으로 생성합니다. 메서드 이름을 정의하면, 해당 이름에 맞는 쿼리를 자동으로 생성합니다.

### 예시

```java
List<Post> findByTitle(String title);
```

이 메서드는 `title` 필드를 기준으로 `SELECT * FROM post WHERE title = ?`와 같은 SQL 쿼리를 자동으로 생성합니다.

### 다양한 쿼리 메서드 예시

- `findByTitleAndContent(String title, String content)`: `title`과 `content`를 기준으로 검색
- `findByTitleContaining(String title)`: `title`이 포함된 값을 검색
- `findByCreatedAtBefore(LocalDateTime date)`: 특정 날짜 이전에 생성된 게시글을 검색

Spring Data JPA는 메서드 이름을 기반으로 자동으로 쿼리를 생성하므로, 별도의 쿼리 구현 없이 데이터를 쉽게 조회할 수 있습니다.
