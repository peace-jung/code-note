# Immutable

## 정의

[사전] Immutable : 불변의, 변경할 수 없는. [반의어] mutable

[프로그래밍] 불변 객체. 생성 후 그 상태를 변경할 수 없는 객체.

객체는 가변객체와 불변객체가 있다.

불변객체는 변경이 불가능하기 때문에 새로운 변수를 할당받아 실행한다.

반면에 값은 불변성을 가지고 있다.



이해를 위해 코드를 확인해본다면

```
const a = "hello";
const b = a + " world";
```

이 과정을 자세히 살펴본다면 **변수 a 에 " world" 라는 문자열을 더하여** b 에 대입하고 있다.

정확히는 **" world"를 만들고(1) 더하고("hello wolrd")(2) 그 변수를 b 에 대입(3)**하는 것이다.

문자열은 불변객체이기 때문에 새로운 변수를 할당하는 과정이 발생하는 것이다.



<image src="heap.png" width="480px" />



### 가변 객체

1. 값을 변경할 수 있다.
2. 값을 변경할 때 인스턴스 자체가 변한다.
3. Array, List, Map …

### 불변 객체

1. 값을 변경할 수 없다.
2. 값을 변경하기 다음과 같은 과정을 거친다.
   - 새로운 인스턴스를 생성한다.
   - 기존의 인스턴스의 포인터를 삭제한다.
   - 포인터에 새로운 인스턴스의 주소를 할당한다.
3. String, Number, Boolean …



## Immutable.js

Immutable.js 는 불변의 데이터 구조를 제공한다.

- List, Stack, Map, Set …

불변의 데이터는 절대 변하지 않기 때문에 위에서 아래로 흐르는 흐름을 가진다.

이 데이터 흐름은 React 의 아키텍쳐와 잘 일치한다.

또한 불변성을 추구하는 Redux 의 요구에도 만족한다.



사용법

```
npm install immutable
```

```
import { Map } from "Immutable"; // Map, Stack, List 다양하게 지원한다.

const map1 = Map({ a: 1, b: 2, c: 3 }); // Map() 으로 감싸고 선언한다.

// immutable.js 의 명령어를 따라야한다.
console.log(map1.a); // undefined
console.log(map1.get("a")); // 1

map1.d = 5 // 실제로 반영되진 않는다.
console.log(map1); // Map { "a": 1, "b": 2, "c": 3 }
map1.set("d", 5); // Map { "a": 1, "b": 2, "c": 3, "d": 5 }
// 기존의 데이터를 수정하는 것이 아니라 새롭게 할당되어 적용된다.
```

```
// 예시
const map1 = Map({ "a": 1, "b": 2, "c": 3 });
const map2 = map1.set("d", 5); // map1 에 d 를 대입한 것 처럼 보이지만
console.log(map1);
> Map { "a": 1, "b": 2, "c": 3 } // 실제로는 map1 이 가리키는 객체는 변화가 없고
console.log(map2);
> Map { "a": 1, "b": 2, "c": 3, "d": 5 } // 재할당이 발생하여 map2 에 적용된다.
```



사용법이 어렵지 않으니 자세한건 사이트에서 직접 확인하면 된다.

[Immutable.js](https://facebook.github.io/immutable-js/)

[github/immutable](https://github.com/facebook/immutable-js/)
