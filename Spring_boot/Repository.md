# Repository
리포지토리는 엔티티에 의해 DB 테이블에 접근하는 메서드들을 사용하기 위한 인터페이스이다.
엔티티를 기반으로 DB와 CRUD 작업을 추상화한 계층이다.

<br>

## Repository 관련 대표적인 Annotation
1. @Repository
- 레포지토리 계층임을 나타내고, Spring 컨테이너에 빈으로 등록한다.

2. @Transactional
- 데이터 접근 시 트랜잭션 설정이다. 읽기 전용/쓰기 작업 등을 명시적으로 구분한다.

3. @Query
- 커스텀 쿼리를 작성하여 JPQL 또는 네이티브 쿼리를 수행한다.

<br>

Spring Data JPA에서 @Repository를 생략해도 되는 이유
- Spring Data JPA 에서는 JpaRepository 나 CurdRepository 를 상속받으면, Spring이 자동으로 레포지토리 빈(Bean) 으로 등록한다.

- 따라서 명시하지않아도 동작을 하긴 한다. 