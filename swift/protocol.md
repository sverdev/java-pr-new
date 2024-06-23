## Protocol

프로토콜은? 프로토콜은 인터페이스의 역할과 비슷하게 역할합니다.  
함수와 변수의 타입들을 정의할 수 있습니다. 아래의 예시를 보며 설명 하겠습니다.

```swift
protocol reserve {
    var user: String? { get }
    var hotel: String? { get }

    func start()
}
```

이런식으로 한개의 행동 카테고리 안의 필요한 값(변수)과 행동(함수)를 미리 한번에 정의 해줄 수 있습니다.

이후 미리 타입처럼 정의 해둔 위의 `reserve`를 사용 해보겠습니다.

```swift
struct hotel: reserve {
    var user: String?
    var hotel: String?

    func start()
}
```

위와 같이, 미리 정의 해준 변수와 함수를 모두 구현 해줘야 합니다.
