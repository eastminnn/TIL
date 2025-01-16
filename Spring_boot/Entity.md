# Entity
"엔티티" 는 주로 DB의 테이블을 나타내는 클래스를 의미한다.
이 엔티티 클래스는 JPA(Java Persistence API)를 사용해서 DB에 저장되고 관리된다.

<br>

## Entity 관련 대표적인 Annotation
1. @Entity
- 클래스를 엔티티로 선언한다는 뜻이다. JPA가 해당 클래스를 관리하게 된다.

2. @Table
- 엔티티와 매핑할 DB 테이블을 지정한다.

3. @Id
- 테이블의 기본키에 사용할 속성을 지정한다.

4. @GeneratedValue
- 주 키의 값을 위한 자동 생성 전략을 명시하는데 사용된다.
![alt text](/Image/Spring_boot/entity1.PNG)
```
@Data
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY) // DB에서 자동 생성
    private Long id;
```


5. @Column
- 필드와 칼럼을 매핑하는 사용한다.
![alt text](/Image/Spring_boot/entity2.PNG)

6. @CreationTimestamp
- insert시 시간을 자동 저장한다.
```
    @CreationTimestamp // 생성시간 자동기록
    @Column(updatable = false) // 생성시간 수정 불가
    private LocalDateTime created;
```

7. @Enumerated
- enum 타입을 매핑한다.
```
    @Enumerated(EnumType.STRING) // 사용자 관리 (열거형)
    @Column(nullable = false)
    private Role role; // 사용자 권한
```

<br>
결론적으론 엔티티는 단순히 DB에 데이터를 저장하거나 꺼내온다고 생각하면 편하다. 그렇기에 ERD 다이어그램을 작성하고 가장 먼저 작성하는 코드가 엔티티라고 생각하면 된다.