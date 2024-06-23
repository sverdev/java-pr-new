## Generic

### 함수

우선 제네릭 프로그래밍은, 데이터 형식에 의존하지 않고 하나의 값이 여러 타입을 가질 수 있는 프로그래밍 방식입니다.
예시로 저희는 아래와 같은 코드를 작성하면서 제네릭 프로그래밍을 하고 있었습니다.

```swift
//배열 선언
var arr: Array<Int> = Array<Int>()
//딕셔너리 선언
var dic: Dictionary<String, Int> = Dictionary<String, Int>()
```

위 예시에서 뭐가 제네릭한거냐 하면, <> 이 꺽쇠 괄호와 Array, Dictionary와 같은 타입 명시가 핵심입니다.  
이를 통하여 제네릭 사용의 시작을 알릴 수 있습니다.

대표적인 특징은 아래와 같습니다.

- 실제 타입명을 써주는 대신, placeholder(임의의 값)을 사용합니다. [예시: T, V, U]
- 타입의 종류는 정해져있지 않은 만큼 추상적인 코드 작성을 지원합니다.
- placeholder의 타입은 함수가 호출될 때 결정됩니다.
- 여러개의 placeholder를 사용하여 여러개의 타입 매개변수를 가질 수 있습니다. [예시: <T, V>]
- 의미 있는 placeholder의 이름 지정을 통해, 코드의 가독성을 높일 수 있습니다. [예시: Dictionary<key, value>, Array[Element]]

---

제네릭의 대표적인 예시를 하나 보겠습니다.

```swift
func swapTwoStrings(_ a: inout String, _ b: inout String) {
    let temporaryA = a
    a = b
    b = temporaryA
}

func swapTwoDoubles(_ a: inout Double, _ b: inout Double) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var someDouble = 3.1
var anotherDouble = 107.1
someDoubles(&someDouble, &anotherDouble)
print("someDouble is now \(someDouble), and anotherDouble is now \(anotherDouble)")
// 출력: "someDouble is now 107.1, and anotherDouble is now 3.1"
```

위의 코드를 보면, 매개변수가 각각 String과 Double인 함수들이 매개변수 서로의 값을 바꿔주는 함수입니다. 만약 실무에서 저런 툴 함수가 필요하고 각 타입마다 값을 바꿔줘야 하는 함수가 필요하다면 코드 길이와 더불어 코드의 길이도 기하급수적으로 늘어날 것입니다.

이때 제네릭이 사용될 수 있습니다.

```swift
func swapTwoParam<T>(_ a: inout T, _b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}


var someDouble = 3.1
var anotherDouble = 107.1
swapTwoParam(&someDouble, &anotherDouble)
print("someDouble is now \(someDouble), and anotherDouble is now \(anotherDouble)")
// 출력: "someDouble is now 107.1, and anotherDouble is now 3.1"

var someInt = 4
var anotherInt = 5
swapTwoParam(&someInt, &anotherInt)
print("someInt is now \(someInt), and anotherInt is now \(anotherInt)")
// 출력: "someInt is now 5, and anotherInt is now 4"
```

이런식으로 코드를 작성 해준다면 T가 제네릭의 placeholder가 되어주고, 각 매개변수의 타입으로 들어가서 여러 매개변수가 되어줄 수 있습니다.

---

### 타입

```swift
struct Stack<Element> {
    var items = [Element]()

    mutating func push(_ item: Element) {
        items.append(item)
    }

    mutating func pop() -> Element {
        return items.removeLast()
    }
}


var stringStack = Stack<String>()
stringStack.push("Hello")
stringStack.push("World")
stringStack.pop() // "World"
```

여기서 위 함수와 헷갈렸는데, 이건 타입 수준에서 정의와 동시에 클래스, 구조체, 열거형 등의 타입을 제네릭하게 만듭니다. 또한 인스턴스 생성 시 실제 타입으로 대체됩니다.

만약 저기서 Elemet가 아닌 Int 등 타입이 지정 되어 있었다면, 스택에서 Int만이 사용 가능 했을겁니다. 다만 제네릭 타입으로 지정했던 만큼, 여러 타입의 자식을 스택 안에 넣어둘 수 있습니다.
