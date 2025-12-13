# JavaScript
자바스크립트는 웹 페이지를 동적으로 만들기 위한 프로그래밍 언어
HTML과 CSS로 구성된 웹페이지에 생동감을 더해 사용자 인터페이스를 구현하며, Node.js와 같은 런타임 환경을 통해 웹 브라우저뿐만 아니라 서버 등 다양한 분야에서도 사용될 수 있다.

## 1. JavaScript의 함수 대표 3가지
함수 = 어떤 코드를 묶어 하나의 기능 단위로 만들고, 필요할 때 실행하는 구조

1. 함수 선언문 (Function Declaration)
2. 함수 표현식 (Function Expression)
3. 화살표 함수 (Arrow Function)

### 1-1. 함수 선언문 (Function Declaration)
예시

```
function greet(name) {
 return '안녕하세요, ${name}님!';
}
console.log(greet("김철수"));
```

- greet 라는 이름을 가진 함수 하나를 메모리에 등록한다
- `console.log` 는 괄호 안의 값을 콘솔에 출력하는 기능

```
function add(a, b) {
 return a + b;
}
console.log(add(2, 3)); // 5
```

- **호이스팅 됨** - 자바스크립트는 코드를 실행하기 전에 함수 선언문과 변수 선언을 먼저 메모리에 등록해둠
> hello()가 먼저 나와 있고 나중에 function hello()가 나오는 상황 - 원래라면 error
> 자바 스크립트에서는 전체 파일을 훑은 뒤에 코드를 읽기 때문에, 코드가 위에서 아래로 실행되기 전에 함수선언을 미리 기억해두고 실행한다. error 아님
> 즉, JavaScript에서 function 선언문은 코드 맨 위로 자동으로 끌어올려진 것처럼 동작한다.

### 1-2. 함수 표현식 (Function Expression)
예시
```
const greet = function(name) {
 return '안녕하세요, ${name}님!';
};


console.log(greet("김뫄뫄"))
;
```
- 함수를 변수에 할당하는 방식 - 함수 자체가 value로 취급되어 변수에 들어간 형태다
- **호이스팅 되지 않는다** - function 선언문과의 차이점

### 1-3. 화살표 함수 (Arrow Function)
예시
```
const greet = (name) => {
 return '안녕하세요, ${name}님!';
};


console.log(greet("박민수"));
```
> 문법적 특징
> function greet(name) { ... }  // 기존 방식
> (name) => { ... }             // 화살표 함수 방식

const add = (a, b) => {
 return a + b;
};
> 기본 형태


const add = (a, b) => a + b;
> 본문이 한줄이면 return과 중괄호 생략 가능


const double = c => x * 2;
> 매개변수가 1개면 괄호 생략 가능


const sayHello = () => "Hello!";
> 매개변수가 없으면 빈 괄호 필수

실행결과
add(3, 5) → 8
double(4) → 8
sayHello() → "Hello!"


### 비교 예시
```
 hi();                                // 호출 가능!


function hi() {                      // 함수 선언문
 console.log("hi");
}
==> error (X)
```


```
hi();                                  // ❌ 오류!


const hi = function() {                 // 함수 '표현식'
 console.log("hi");
};
==> error (O)
```


## 2. this 바인딩

## 3. 구조 분해 할당 (Destructuring)
### 3-1. 객체 구조를 분해할 수 있다
+ 배열도 구조 분해가 가능하다
```
const user = {
        name : "김철수",
        age : 25,
        email : "kim@example.com"
};

const name = user.name; //const는 변수를 만드는 명령어
const age = user.age;
```
기존 방식 = user. 을 계속 반복해야함 (값이 많아질수록 귀찮음)
```
console.log(name);
console.log(age);
console.log(email);
```
위의 식을 구조 분해 할당방식으로 아래처럼 축약 가능함
```
const { name, age, email } = user;
```
const { name } = user; 처럼 필요한 것만 꺼낼 수 있음

### 3-2. 기본값 설정법
존재하지 않는 속성에 기본값을 지정할 수 있다
```
const user = {
    name: "김철수"
};
const { name, hobby = "독서" } = user;  // hobby가 없으면 "독서"를 기본값으로 사용
```

### 3-3. 변수명 변경
추출한 값을 다른 변수명으로 저장할 수 있다
```
const { name: userName, age: userAge } = user;
```
### 3-4. 배열 구조 분해
배열도 구조 분해가 가능하다
```
const colors = ["빨강", "파랑", "초록"];
const [first, second, third] = colors;
```
일부 요소를 건너뛰는 것도 가능함
```
const numbers = [1, 2, 3, 4, 5];
const [first, , third] = numbers; // 두 번째 요소 건너뛰기
```

## 4. 스프레드 연산자 (Spread Operator)
### 4-1. 배열 스프레드 
... 를 사용하여 배열이나 객체를 펼치는 문법
React에서 stat 불변성을 유지할 때 필수적임
```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4, 5, 6]
```
배열이 합쳐짐
```
const copy = [...arr1];
console.log(copy); // [1, 2, 3] 
```
즉, ...을 통해 안에 들어있는 값들을 하나씩 꺼내서 늘어놓는다

```
const withMiddle = [...arr1, 10, 20, ...arr2];
console.log(withMiddle); // [1, 2, 3, 10, 20, 4, 5, 6]
```
중간에 요소 추가하기

### 4-2. 객체 스프레드
```
const user = {
    name: "김철수",
    age: 25
};
```
객체 복사
```
const userCopy = { ...user };
```
속성 추가
```
const userWithEmail = { ...user, email: "kim@example.com" };
console.log(userWithEmail);  // { name: "김철수", age: 25, email: "kim@example.com" }
```
속성 덮어쓰기
```
const olderUser = { ...user, age: 26 };
console.log(olderUser);
```
## 5. 모듈 시스템(Export/Import)
### 5-1. Named Export
여러 개의 값을 내보낼 때 사용함
```
// utils.js
export const PI = 3.14159;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

// 또는 한 번에 내보내기
const multiply = (a, b) => a * b;
const divide = (a, b) => a / b;

export { multiply, divide };
```
출력 예시
```
import { PI, add, subtract } from './utils.js';
console.log(PI);           // 3.14159
console.log(add(2, 3));    // 5
console.log(subtract(5, 2)); // 3
```
> 이 문법은 파일이 다를때만 사용함. 같은 파일일때는 쓸 필요 없다. 

### 5-2. Default Export
파일당 하나의 주요 값을 내보낼 때 사용한다
> 그래서 export/import를 쓰는 이유는, 계산 로직 → Calculator.js / 화면 → App.jsx / 버튼 → Button.jsx 이런식으로
> 한 파일이 한 책임만 갖게 하려고 (웹이든 앱이든 다른 프로젝트던지 같은 로직을 재사용 하기 위해)
예시
```
import Calculator from './Calculator.js';
```

### 5-3. Named와 Default
> 둘의 차이는 이 파일에서 내보내는 게 몇개인지, 그리고 대표가 있는가
Named Export = 여러 개 다 꺼내 쓸 수 있음

# React
## 1. 개념과 특징
### 1-1. 컴포넌트 기반 구조 (Component-Based)
독립적이고 재사용 가능한 컴포넌트로 나누어 개발한다
```
function Button({ text, onClick }) {
  return <button onClick={onClick}>{text}</button>;
}
```
버튼 컴포넌트를 만들었다

```
<Button text="저장" onClick={handleSave} />
<Button text="취소" onClick={handleCancel} />
<Button text="삭제" onClick={handleDelete} />
```
여러 곳에서 재사용 가능

### 1-2. 선언적 프로그래밍 (Declarative)

### 1-3. Virtual DOM (가상 DOM)
### 1-4. 단방향 데이터 흐름 (One-Way Data Flow)
### 1-5. 사용하는 이유
