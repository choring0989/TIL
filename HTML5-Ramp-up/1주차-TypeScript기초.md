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
