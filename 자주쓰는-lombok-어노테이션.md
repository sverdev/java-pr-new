```
@Entity
@Getter
@Builder
@NoArgsConstructor
@AllArgsConstructor
```

동아리에서 사용할 백엔드 코드를 작성하는데 해당 코드를 쓸 일이 있었다. 부끄럽게도 나는 어노테이션에 관해 잘 몰랐던거 같아 한번 정리 겸 알아보는 글을 작성 해본다. 사실 이는 자바에 더 가까울지도 모르겠다만 난 자바를 배운지 조금은 오래되기도 하였고 스프링에서 자주 사용하는 개념을 더하여 설명 할 예정이라 해당 문서에 추가 해본다.

우선, Entitiy는 JPA에서 테이블과 매핑되는 엔티티임을 나타낸다. 그러므로 따로 보충적인 설명이 필요하지 않으므로 우선 주제에 맞게 lombok의 어노테이션에 대해서만 다뤄보도록 하겠다.

---

일단 **@Getter와 @Setter에** 대해서 알아보자, 먼저 아래처럼 코드를 작성한다.

```
@Getter @Setter
private String name;
```

이런식으로 작성을 해두면, Getter를 통하여 getName()과 같은 형식으로 쓸 수 있게 해준다. 예시는 아래와 같다. Setter 또한 같이 사용 하였다. 아래처럼 set~ 형태로 쓸 수 있다.

```
user.setName('이지혁') // 변수의 첫 글자를 대문자로 입력 해야 한다.
System.out.println(user.getName())
```

---

그 다음은 **@Builder** 이다. 이는 @Setter와 닮은 듯 다른데,
이유론 객체가 완전하지 않으면 에러를 발생하며 생성이 불가능해진다.
우선 사용법을 알아보도록 하자.

```
@Builder
public class Person {
    private final String name;
    private final int age;
    private final int phone;
}
```

이런식으로 코드를 짜뒀다고 하자, 그럼 아래처럼 Build를 사용하여 객체를 만들 수 있다.

```
Person person = Person.builder() // @Builder로 생성된 빌더클래스 생성자
    .name("seungjin")
    .age(25)
    .phone(1234)
    .build();
```

위의 build와 @Getter, @Setter의 특징을 말해보자면,

```
 - 불필요한 생성자의 제거가 가능하다.
 - 데이터의 순서에 상관없이 객체생성이 가능하다
 - 명시적 선언으로 이해하기가 쉽다.
 - 각 인자가 어떤 의미인지 알기 쉽다.
 - @Setter메서드가 없으므로 변경 불가능한 객체를 만들수있다.
 - 한번에 객체를 생성하므로 객체일관성이 깨지지 않는다.
 - build()함수가 null인지 체크해주므로 검증이 가능한다.
 - 완전하지 않은 객체 빌드시 / @Getter로 null 객체를 가져오려고 할 시 nullPointerException을 발생 시켜준다.
```

문서가 길어지는 관계로 나머지는 다음 편에서..
