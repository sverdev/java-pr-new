## late

late는, 늦게 오는 데이터 (ex. API로 요청했는데 값이 아직 안와서 준비를 한다던지 ...)를 위해 사용할 수 있습니다.

```dart
void main() {
    late final String name; // 먼저 선언해두고 값은 넣지 않는다. 그게 late의 의미이다.
    print(name); // 값이 들어가 있지 않으므로 null-safety 하지 않다. 따라서 에러가 난다.

    name = ApiService.getName(); // 이런식으로 서비스를 통해 값을 받아 변수에 넣어주면 된다.

    name = "지혁"; // late를 사용 하였어도 final이 뒤에 붙어있어서 재할당이 불가능하다.
}
```

위 코드 만으로 이해할 수 있을꺼 같다.
