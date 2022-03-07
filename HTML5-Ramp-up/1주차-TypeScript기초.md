## 1주차 - TypeScript 기초
### 개발환경 셋팅 및 ESLint 설치
- <b>개발 환경</b>
  - <img src="https://img.shields.io/badge/Egret%20engine-v5.4.1-blue"/>
  - <img src="https://img.shields.io/badge/Egret%20wing-v3-green"/> 또는 <img src="https://img.shields.io/badge/VScode-1.*-red"/>
  - <img src="https://img.shields.io/badge/node%40latest-%3E%3D%2012.0.0-brightgreen"/>

- <b>ESLint 설치</b>
  1. ESLint 설치를 원하는 프로젝트를 Egret wing3 또는 VSCode로 open
  2. Egret wing3 또는 VSCode에서 `확장` 메뉴 진입 (단축키 `ctrl+shift+x`)
  3. ESLint 검색 -> 설치 -> 다시 로드
  4. [Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started)에 따라 설치 진행 <br><br>
    <img src="https://github.com/choring0989/TIL/blob/master/HTML5-Ramp-up/image/ex_eslint_config.jpg" width="600px"/>
  
  <pre><code>> npm install eslint --save-dev
  > npm init @eslint/config
  
  > # Run file
  > npx eslint yourfilename.js
  
  > # Run on two files
  > npx eslint file1.js file2.js
  
  > # Run on multiple files
  > npx eslint lib/**</code></pre>

### TypeScript 기초 문법
- <b>Class</b> : 객체를 생성하기 위한 템플릿으로, 데이터와 데이터를 조작하는 코드를 하나로 추상화한다.
- 접근 제한자(Access modifier) public, private, protected 를 지원하며, 프로퍼티와 메소드에 접근 제한자를 명시하지 않을 경우에는 암묵적으로 `public`이 된다.
- 클래스 프로퍼티에 `readonly`를 적용할 수 있으며, readonly로 프로퍼티를 선언시 생성자 내부에서만 값을 할당할 수 있다. 그 외에는 오직 읽기만 가능한 상태가 된다. 따라서 상수 선언에 활용이 잦다.
- 클래스 프로퍼티나 메소드에 `static`을 적용할 수 있으며, 정적 메소드로 선언할 경우 클래스의 인스턴스를 생성하지 않아도 `클래스이름.메소드`로 호출할 수 있다.
- `추상 클래스(abstract class)`를 통해 내용 없이 메소드 이름과 타입만 선언할 수 있으며, 이 경우 직접 인스턴스를 생성할 수 없고 상속 목적으로만 사용한다. 추상 클래스를 상속한 클래스는 추상 클래스의 추상 메소드들을 반드시 구현해야 한다.

<pre><code>class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
  }
let greeter = new Greeter("world");

abstract class Animal {
  // 추상 메소드
  abstract makeSound(): void;
  // 일반 메소드
  move(): void {
    console.log('roaming the earth...');
  }
}

// 직접 인스턴스를 생성할 수 없다.
// new Animal();
// error TS2511: Cannot create an instance of the abstract class 'Animal'.

class Dog extends Animal {
  // 추상 클래스를 상속한 클래스는 추상 클래스의 추상 메소드를 반드시 구현하여야 한다
  makeSound() {
    console.log('bowwow~~');
  }
}

const myDog = new Dog();
myDog.makeSound();
myDog.move();</code></pre>


- <b>Interface</b> : 변수, 함수, 클래스에 타입 체크를 위해 강제하는 구현 (일종의 약속을 지정)
- Duck type 언어인 TS에서 인터페이스에 선언된 메소드나 프로퍼티의 구현을 강제하여 구조의 일관성을 유지할 수 있도록 돕는다.
- ES6는 인터페이스를 지원하지 않으나 TS에서는 인터페이스를 지원한다.
- 인터페이스는 직접 인스턴스를 생성할 수 없으며, 인터페이스의 모든 메소드는 개념적으로 추상 메소드이나 `abstract`키워드를 붙이지 않는다.
- 인터페이스는 모든 메소드가 실제 구현부가 없는 메소드이다. 그러나 추상 클래스는 단 하나 이상의 추상 메소드만 가지고 있으면 된다. 즉, 추상 클래스는 실제 구현부가 있는 일반 메소드를 포함할 수 있고, 인터페이스는 실제 구현부가 있는 일반 메소드를 포함할 수 없다.
- 인터페이스의 프로퍼티는 반드시 구현해야 하나, 인터페이스의 프로퍼티 일부가 선택적으로 필요한 경우 프로퍼티 이름 뒤에 `?` 를 붙인다.
- 인터페이스 또한 `extends`키워드를 이용해 다른 인터페이스나 클래스를 상속받을 수 있다. 복수의 상속도 가능하다.
<pre><code>// 인터페이스의 정의
interface Todo {
  id: number;
  content: string;
  completed: boolean;
}

// 변수 todo의 타입으로 Todo 인터페이스를 선언하였다.
let todo: Todo;

// 변수 todo는 Todo 인터페이스를 준수하여야 한다.
todo = { id: 1, content: 'typescript', completed: false };
</code></pre>
<pre><code>// 함수 인터페이스의 정의
interface SquareFunc {
  (num: number): number;
}

// 함수 인테페이스를 구현하는 함수는 인터페이스를 준수하여야 한다.
const squareFunc: SquareFunc = function (num: number) {
  return num * num;
}

console.log(squareFunc(10)); // 100
</code></pre>
<pre><code>// 인터페이스의 정의
interface ITodo {
  id: number;
  content: string;
  completed: boolean;
}

// Todo 클래스는 ITodo 인터페이스를 구현하여야 한다.
class Todo implements ITodo {
  constructor (
    public id: number,
    public content: string,
    public completed: boolean
  ) { }
}

const todo = new Todo(1, 'Typescript', false);

console.log(todo);
</code></pre>
<pre><code>// 선택적 프로퍼티
interface UserInfo {
  username: string;
  password: string;
  age?    : number;
  address?: string;
}

const userInfo: UserInfo = {
  username: 'ungmo2@gmail.com',
  password: '123456'
}

console.log(userInfo);
</code></pre>
- <b>Inheritance</b>: 상속, 부모 클래스(또는 인터페이스)의 프로퍼티와 메소드를 자식 클래스(또는 인터페이스)에서 사용할 수 있도록 하는 것
- 타입스크립트에서는 `extends` 키워드를 이용해 다른 인터페이스나 클래스를 상속받을 수 있으나, 클래스는 단 하나만 상속이 가능하고 인터페이스는 다중 상속이 가능하다.
<pre><code>interface face {
    eye: string;
    mouse: string;
}

interface head {
    hiar: string;
}

interface human extends face, head {
  // 인터페이스끼리는 다중 상속이 가능
}

class me implements human {
    eye = "";
    mouse = "";
    hiar = "";
}
</code></pre>

- <b>Data Types</b>: `Boolean`, `Number`, `String`, `Array`, `Tuple`, `Enum`, `Any`, `Void`, `Null`, `Undefined`, `Object` 타입 등이 있다.
- 자세한 예제와 내용은 [TypeScript-Handbook 한글 문서 - 기본 타입](https://typescript-kr.github.io/pages/basic-types.html) 참고

---
### 참고자료
- [poiemaweb](https://poiemaweb.com/typescript-class)
- [TypeScript-Handbook 한글 문서](https://typescript-kr.github.io/)
