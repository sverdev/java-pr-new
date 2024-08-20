## static

static은, class의 instance를 생성하지 않고도 변수의 값 혹은 메서드를 쓸 수 있게 도와줍니다.  
또한, 해당 객체는 동일 class 내에 한개만 존재하게 됩니다. 그리고 이 객체를 모두가 공유하게 됩니다.

```dart
class profile {
    static String name = "이지혁";
    static sayMyName() {
        print("이지혁");
    }
}

print(profile.name); // "이지혁"
profile.sayMyName; // "이지혁"
```

이런식으로 작성하면, 아래처럼 class의 인스턴스를 생성하지 않고도 사용할 수 있습니다.
