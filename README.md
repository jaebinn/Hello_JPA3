**#엔티티 설계시 주의점**

**엔티티는 가급적 Setter를 사용하지말자! **<br>
(Setter가 모두 열려있으면 변경 포인트가 너무 많아서 유지보수 어려움)

**모든 연관관계는 지연로딩으로 설정!**<br>
- @XToOne(OneToOne, ManyToOne)관계는 기본이 즉시 로딩이므로 직접 지연로딩으로 설정해야한다.<br>
fetch = FetchType.LAZY

**컬렉션은 필드에서 초기화 하자!**<br>
하이버네이트는 엔티티를 영속화 할때, 컬렉션을 감싸서 하이버네이트가 제공하는 내장 컬렉션으로 변경한다.<br>
만약 getOrder() 처럼 임의의 메서드에서 컬렉션을 잘못 생성하면 하이버네이트 내부 메커니즘 문자게 발생할 수 있다. 따라서 필드레벨에서 생성하는 것이 가장 안전하고, 코드도 간결하다.