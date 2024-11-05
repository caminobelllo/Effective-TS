# [아이템 4] 구조적 타이핑에 익숙해지기

## 구조적 타이핑과 타입 호환성

_TypeScript의 타입 호환성은 구조적 서브 타이핑(subtyping)을 기반으로 합니다. 구조적 타이핑이란 오직 멤버만으로 타입을 관계시키는 방식입니다._

이때 구조적 서브 타이핑과 구조적 타이핑이란 개념에 익숙하지 않아 좀 더 찾아보았다. 구조적 서브 타이핑은 덕 타이핑이라도 하기도 한다.

- **구조적 서브 타이핑 (덕 타이핑) : 상속 관계를 명확하게 명시하지 않은 경우에도 필요한 프로퍼티를 가지고 있다면 타입 호환을 허용하는 것 (즉, 상속 관계에 상관없이 타입 호환을 허용한다는 의미)**
- 구조적 타이핑 : 오직 멤버만으로 타입을 관계시키는 방식

자바스크립트는 본질적으로 덕 타이핑 기반이며, 만약 어떤 함수의 매개변수 값이 모두 제대로 주어진다면 그 값이 어떻게 만들어졌는지 신경쓰지 않고 사용한다.
자바스크립트의 상위 언어인 타입스크립트는 이를 모델링하기 위해 구조적 타이핑을 사용하는 것이다.

서로 다른 인터페이스여도, 구조가 호환되는 경우에는 다음과 같이 NamedVector를 위한 별도의 함수를 구현하지 않더라도 2D 벡터를 타입으로 받는 calculateLength 함수 호출이 가능하다.

```
interface Vector2D {
    x: number
    y: number
}

function calculateLength(v: Vector2D) {
    return Math.sqrt(v.x * v.x + v.y * v.y)
}

interface NamedVector {     // 이건 extends로도 변경 가능
    name: string
    x: number
    y: number
}

const v: NamedVector = { x: 3, y: 4, name: 'Zee' }
calculateLength(v)  // 이게 가능하다
```
