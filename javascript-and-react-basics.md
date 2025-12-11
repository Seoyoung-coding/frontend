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
