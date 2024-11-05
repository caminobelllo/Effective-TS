# [아이템 3] 코드 생성과 타입이 관계없음을 이해하기

- 타입스크립트 컴파일러는 두가지 역할을 수행한다.

1. 최신 타입스크립트 (또는 JS)를 브라우저에서 동작하도록 구버전의 자바스크립트로 트랜스파일한다.
2. 코드의 타입 오류를 체크한다.

이 두가지는 서로 완벽히 독립적이다. 따라서, 타입 오류가 있는 코드도 컴파일이 가능하다. (왜냐면 타입체크는 컴파일과 독립적으로 진행되기 때문)
런타임에는 타입 체크가 불가능하다. 런타임 타입은 선언된 타입과 다를 수 있다.

- 클래스는 자바스크립트의 구현되어 있는 실제 값이기도 하면서, 해당 클래스의 인스턴스는 타입스크립트 상의 타입으로도 존재할 수 있다.
  : 타입과 값으로 모두 쓸 수 있다

```
class Square {
    constructor(public width: number) {}
}

class Reactangle extends Square {
    construecor(public width: number, public height: number) {
        super(width)
    }
}

type Shape = Square | Rectangle

funcction calculateArea(shape: Shape) {
    if (shape instanseof Rectangle) {
        shape
        return shape.width * shape.height
    } else {
        shape
        return shape.width * shape.width
    }
}
```
