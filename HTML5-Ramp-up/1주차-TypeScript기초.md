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
- `인터페이스(interface)`는 모든 메소드가 개념적으로 추상 메소드이나, 추상 클래스는 단 하나 이상의 추상 메소드만 가지고 있으면 된다. 즉, 추상 클래스는 일반 메소드를 포함할 수 있다.

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
myDog.move();
</code></pre>


<hr><br>
### 참고자료<br>
- [poiemaweb](https://poiemaweb.com/typescript-class)
