# Spring boot Package Structure
![alt text](/Image/Spring_boot/package1.png)
위 그림은 기본적인 프로젝트 아키텍처이다.

## Controller
> Client 와 Service의 중간자 역할, 비즈니스 로직이 있는 서비스를 호출

Client에서 보낸 요청 URL에 따라서 적절한 응답을 한다. Client (View) 에서 Request Body에 담긴 데이터(DTO) 를 Service에 넘겨주고, Service에서 처리하고 Respose Body에 담견 반환된 데이터(DTO)를 돌려주는 역할을 한다. 

Client --(Request)--> Controller --(Response)-->

## Service
> DAO 혹은 Repository에서 받아온 데이터를 받아 가공

Client의 요청 (request)에 대해 어떤 처리를 할 지 결정하는 부분, 간단히 말해 요청 들어온 부분을 개발자가 어떻게 변환하여 다시 사용자에게 전달할 지 결정하는 역할을 한다.

## DAO (Repository)
> 실제로 데이터 베이스에 접근하는 객체 (Repository와 거의 같지만 동일한 것은 아님)

실제로 DB에 접근하여 데이터를 CRUD 하는 객체이다.
Service와 DB를 연결해주는 역할을 하고 있으며, 인터페이스와 이에 대한 구현체를 만들어서 구현체에 CRUD 관련 기능을 구현하고, 이를 DI (Dependency Injection) 해주는 방식으로 사용된다.

#### DAO 패턴 vs Repository 패턴
DAO 패턴은 영구 데이터 저장소에 가까운 것으로 추정

Repository 패턴은 객체의 상태를 관리하는 저장소로 추정되고, 영구 저장소가 아닌 객체의 상태를 관리하는 저장소

DAO는 Repository를 사용하여 구현할 수 없지만, Repository는 DAO를 사용해 구현할 수 있음.

## Entity (Domain)
> 실제 DB 테이블과 매핑되는 요소

실제 DB의 테이블과 매칭될 핵심 클래스이다.
최대한 외부에서 Entity 클래스의 Setter method를 사용하지 않도록 해당 클래스 안에서 필요한 logic을 구현해야한다. 이 때, Constructor 또는 Builder를 사용한다.

## DTO
> 계층 간 데이터 교환을 도와주는 객체

세부적인 로직을 갖고 있지 않은 순수한 데이터 객체, 계층 간 데이터 교환 시 사용된다.

계층 간 데이터 교환을 할 때 Entity로 통신하는 것은 보안에 좋지 못하기에 DTO를 사용

#### Entity 클래스와 DTO 클래스를 분리하는 이유
DB와 View 사이의 역할 분리를 위해서이고, DTO는 데이터를 담고 있는 점이 Entity와 유사하지만, 목적 자체가 전달이므로 읽고, 쓰는 것이 모두 가능하다.

JPA 사용시 Entity 객체는 단순히 데이터를 담는 객체 이상으로 DB와 중요한 역할을 하며 DTO가 일회성으로 데이터를 주고받는 용도로 사용되는 것과 다르게 Entity의 생명주기도 달라 분리하여 사용한다.