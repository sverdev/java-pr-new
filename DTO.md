# DTO란?

DTO는 Data Transfer Object라는 계층간의 데이터 교환을 위한 객체이며, 주로 Client에 전달되는 데이터를 DTO를 통하여 전달 받습니다.

## 왜 DTO를 사용할까요?

스프링부트에선 주로 SoC라는 관심사의 분리 개념을 많이 사용합니다.
관심사의 수평적인 분리를 통하여 이와 같은 관점에 도달하게 됩니다.

1. 도메인은 비지니스 로직만을 담는 역할을 하는 만큼, 해당 역할에만 충실 해야 합니다. **다른 요소로 인해 방해 받으면 안됩니다.**
2. 만약 두 객체를 혼합한다면... 코드부터가 너무 복잡해져서 아키텍처의 의미가 적어집니다.

또한 한번의 요청을 통해 여러 매개변수를 일괄 처리, 서버의 중복된 요청을 줄임을 통하여 네트워크 비용을 최소화 할 수 있습니다.

그렇기 때문에 null 없이 모든 필드에 값이 있는 공통 DTO 를 사용합니다.
공통 DTO 가 커져서 성능에 이슈가 생기거나, 특수한 경우에만 별도의 DTO 를 사용합니다.