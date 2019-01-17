# React Introduce

## What is React ?

- Javascript

  자바스크립트 라이브러리이다. 프레임워크를 배울 필요가 없고 자바스크립트와 html 를 알면 된다.

- UI Component

  리액트는 “컴포넌트” 라는 개념에 집중이 되어있는 라이브러리이다.
  UI 컴포넌트를 조합하여 앱을 구성할 수 있으며, 재사용 가능한 컴포넌트로 분리가 가능하다.

  보통의 MVC 모델에서 View 를 담당하고 있으므로, 다른 Model 과 Controller 를 함께 섞어서 사용할 수 있다.

- Virtual DOM
  실제 DOM을 처리하는 것은 비용이 많이 들기 때문에 Virtual DOM 이라는 강력한 방법을 사용한다.

- Data Flow

  리액트는 단방향 데이터 흐름을 지향한다. 데이터 추적이 쉽고 관리하기 용이하다.

  데이터 변화는 UI 에 변화를 준다. 단 UI 의 변화가 데이터에 변화를 주면 안된다.

## 시작 전 준비사항

- [Node.js](https://www.nodejs.org)
- [Yarn](https://yarnpkg.com)
- Editor (VS Code, Atom, Webstorm, etc ...)

## [Webpack](https://webpack.js.org/) (웹팩)

브라우저가 이해할 수 있는 코드로 변환/번들링 해주는 툴 (번들러)

Sass, less, jade, css 등을 js, css, png 로 변환해준다.

## 모듈 설치

creat-react-app 이라는 좋은 도구가 있으니 사용하면 좋을 듯 하나,

하나하나 세팅을 하기 원한다면 귀찮음을 감수해야한다.

Node modules list

- react
- react-dom
- react-router: 클라이언트사이드 라우터
- redux, react-redux : redux 를 통한 데이터 관리
- redux-thunk / redux-saga
- react-addons-update
- ... 공식홈페이지에서 요구하는 것 처럼 그냥 **"_[creat-react-app](https://facebook.github.io/create-react-app/docs/getting-started)_"** 을 사용하자

## Creat React App (CRA)

리액트 앱을 간편하게 만들어주는 도구

프로젝트의 전체적인 구조가 설정되어있고, 웹팩도 세팅되어 있다.

**설치방법**

```
npm install -g create-react-app
```

또는

```
yarn global add create-react-app
```

**사용방법**

```
create-react-app app-name
```

**프로젝트 실행**

```
yarn 대신 npm 을 사용해도 되나 개인적으로 yarn 을 선호합니다.

yarn start
	Starts the development server.
	개발 서버 실행 (우리는 View 만 만들었기 때문에 서버가 필요합니다. 그걸 CRA 가 도와줍니다.)

yarn build
	Bundles the app into static files for production.
	일반적으로 배포를 위한 코드로 빌드(변환) 해줍니다.
	.js .css .html 과 몇개 부스러기가 같이 생성됩니다.

yarn test
	Starts the test runner.
	테스트를 위한건데 이후 테스트코드 작성에 대해 공부하면서 알아봅시다.

yarn eject
	Removes this tool and copies build dependencies, configuration files
	and scripts into the app directory. If you do this, you can’t go back!
	개발환경이 기본적으로 세팅되어 있는데 커스터마이징이 불가능 합니다.
	따라서 개발자는 개발환경을 커스터마이징 하기위해 이 동작을 실행합니다.
	현재 프로젝트의 설정과 스크립트를 우리가 쓸 수 있도록 바꿔줍니다. 이 동작은 되돌릴 수 없습니다.
```
