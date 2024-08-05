## Nil-Coalescing

coalescing은 "하나로 합치다" 라는 뜻입니다. nil-coalescing은 한글로 "nil 병합 연산"이라고 할 수 있습니다.
아래의 예시를 보며 설명을 이어 가겠습니다.

```swift
var myFruit: String? = nil
print(myFruit ?? "nil 아닌데~")
// 출력: nil 아닌데~
```

위 예시로 보면, 원래는 nil이 출력 되어야 하지만, ?? 를 통해 nil에서 **nil 아닌데~**로 바뀐걸 볼 수 있다.

만약 값이 nil이 아닌 경우엔, 정상적으로 값이 들어간다.
