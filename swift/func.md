## func

func란? function의 줄임으로 swift에서 함수로 쓰입니다.  
다른 언어와의 차이점으론 -> 이 화살표가 특징이며 예시로 아래와 같이 쓰입니다.

```swift
func saypotato() -> String {
    return "PoTaTo"
}

print(saypotato())
```

`func 함수명(매개변수)` 형태이고, `-> String` 이 부분이 반환값의 타입을 지정 해주는 지점입니다.  
만약 화살표와 리턴값 타입을 지정 해주지 않는다면, `반환값이 없는 함수`를 만들 수 있습니다.

다음으로 매개변수가 있고, 반환값이 없는 함수를 예시로 들겠습니다.

```swift
func sayyogurt(name: String) {
    print("My name is \(name), IlIiKeYoGuRt")
}

sayyogurt(name: "이지혁")
// 예상 출력: My name is 이지혁, IlIiKeYoGuRt
```

위와 같이, 매개변수를 사용해 함수를 더 활용할 수 있을겁니다.  
제네릭등을 활용한다면 더 멋진 함수가 될 수 있을꺼라 생각합니다!
