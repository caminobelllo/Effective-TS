# [아이템 4] 구조적 타이핑에 익숙해지기

서로 다른 인터페이스여도, 구조가 호환되는 경우에는 다음과 같이 NamedVector를 위한 별도의 함수를 구현하지 않더라도 calculateLength 함수 호출이 가능하다.

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
