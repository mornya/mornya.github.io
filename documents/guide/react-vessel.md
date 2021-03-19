# React Vessel
![npm](https://img.shields.io/npm/v/@mornya/react-vessel)
![node](https://img.shields.io/node/v/@mornya/react-vessel)
![types](https://img.shields.io/npm/types/@mornya/react-vessel)
![downloads](https://img.shields.io/npm/dw/@mornya/react-vessel)
![license](https://img.shields.io/npm/l/@mornya/react-vessel)

Copyright 2021. mornya. All rights reserved.

## About
SPA 형태의 React.js 앱 개발을 위한 TypeScript/ECMAScript 기반 스켈레톤을 생성해 주는 프로젝트.
빠른 애플리케이션 개발/배포를 위해 초기 개발환경을 미리 구성하여 복잡하고 번거로운 개발환경 설정에 대해 신경쓰지 않고 코드에 집중하도록 스케폴딩을 제공한다.

## Features
- [TypeScript](https://www.typescriptlang.org/) and ES6+ is supported by default WITHOUT using Babel.
- You can launch the application right away with pre-configured code templates and preferences.
- Code developed with [React.js](https://reactjs.org/) is bundled via [Webpack](https://webpack.js.org/) and extracts static resources.
- Lint and test all of your codes with [Lintest CLI](https://npmjs.com/@lintest/cli).

## Installation
생성된 프로젝트에서 개발을 위해 필요한 `react-vessel` CLI는 기본적으로 전역 모듈로 설치되어 있어야 한다.<br>
아래와 같이 커맨드 라인에서 실행 가능하도록 한다.
> `npm` 대신 `yarn` 사용시, 프로젝트 루트 경로에 `package-lock.json` 파일이 존재하면 제거하고 `yarn.lock` 파일만 참조되도록 한다.
```bash
$ npm install -g @mornya/react-vessel
or
$ yarn global add @mornya/react-vessel
```
린트와 테스트 수행 관련된 모듈은 react-vessel CLI 패키지에서 분리되었으므로, `@lintest/cli` 모듈을 따로 전역으로 설치한다.
```bash
$ npm install -g @lintest/cli
or
$ yarn global add @lintest/cli
```

## Execution
아래와 같이 커맨드 라인에서 CLI를 실행하며, 출력되는 메시지로 사용 가능한 커맨드를 확인 할 수 있다.
> 아래 "Available commands" 참조.
```bash
$ react-vessel
```

## Create a new project
신규 프로젝트 생성은 터미널 등의 환경에서 아래와 같이 `react-vessel init` 커맨드를 실행하여 기본적인 템플릿을 바탕으로 프로젝트 개발 환경을 구축한다.
> 실행시 `src` 하위 경로에 기본적으로 TypeScript 기반 템플릿 소스코드들이 생성되며, 파일 확장자(*.js)로 변경시 ECMAScript/JavaScript를 이용한 개발이 가능하다.
```bash
$ mkdir <project-name>
$ cd <project-name>
$ react-vessel init
```
혹은 `npm init` 등을 실행하여 `package.json` 파일 등이 존재할 때, `react-vessel init` 커맨드를 실행해도 무방하다. 이 때 기존 `package.json` 파일의 내용과 React Vessel에서 템플릿으로 설정한 내용이 병합되어, 각종 설정 들이 추가/변경 된다.
```bash
$ npm init
$ git init
$ react-vessel init
```
아래와 같이 프로젝트 이름 및 설명을 설정하여 초기화 혹은 기존 데이터와 병합이 가능하다.
> `package.json`의 name과 description이 입력된 값으로 변경되며, 신규 생성시에는 README.md 등 템플릿에도 적용된다.
```bash
$ react-vessel init "@myorg/sample"
or
$ react-vessel init "@myorg/new-awesome-libs" "새로운 프로젝트"
```

## Run project
프로젝트 내 개발된 애플리케이션을 로컬환경에서 실행하기 위해 내부적으로 `webpack-dev-server`를 구동하게 되며, 서비스가 시작되면 콘솔에 표기되는 URL 경로로 브라우저 상에서 페이지를 확인 할 수 있다.
```bash
$ npm start
or
$ npm run [dev|serve]
``` 

## Build project
프로젝트 내 ECMAScript 혹은 TypeScript 등으로 작성된 소스파일들은 `Webpack`을 통해 번들링되어 `dist` 경로(변경 불가)에 `*.js` 파일들로 생성이 되며, 해당 경로의 엔트리포인트가 되는 파일을 기점으로 dev-server를 통해 서비스가 실행된다.
> (빌드시 참고) Heroku 배포시 빌드 오류가 발생하는 것을 막기 위해 노드 환경설정 `process.env.DEPLOY_TARGET` 값을 `heroku`로 지정해주면 빌드 오류가 발생하지 않는다.
```bash
$ npm run build
```

## Available commands
React Vessel에서 사용 가능한 커맨드는 아래와 같다.

### `Initialization`
생성된 프로젝트 초기에 실행하도록 한다. 현재 경로에 미리 구성된 템플릿 파일 복제 과정을 수행하며, 만약 수행시 `package.json` 파일이 존재하는 경우 각 설정들을 병합하게 된다.
> `package.json` 파일 이외에 다른 템플릿 파일과 동일한 파일이 현재 경로 및 하위에 존재할 경우에는 덮어쓰기 되니 주의.
```bash
$ react-vessel init
```

### `Start server`
Hot Module Replacement 적용된 로컬 dev-server를 실행한다. 실행될 서버의 `protocol`, `host`, `port` 등은 프로젝트 루트 경로에 `.env` 파일 내에 설정 할 수 있다.
> 초기에는 `.env` 파일이 없으므로 `.env.development` 파일을 복사한다.
```bash
$ react-vessel start
```

### `Build`
ECMAScript 혹은 TypeScript로 개발된 모듈에 대한 빌드를 실행한다.<br>
TypeScript 컴파일러를 통해 트랜스파일된 `.js` 파일들이 추출되며, 해당 파일들은 `dist` 경로에 생성된다.
```bash
$ react-vessel build
```

### `Clean build`
`dist` 경로에 생성된 산출물 및 캐시 디렉토리 내 모든 파일을 제거한다.<br>
> 해당 명령 실행시에만 캐시 디렉토리가 제거 대상에 포함된다.
```bash
$ react-vessel clean
```

### `Check`
타입스크립트 코드 검증을 위해 컴파일러를 실행한다.<br>
> `lint-stage` 등에서 필요시 사용한다.
```bash
$ vessel check
```

### `Bundle Analyze`
웹팩을 통해 `production mode`로 컴파일된 번들의 용량을 체크한다 (webpack-bundle-analyzer 사용). 커맨드를 실행하면 웹 브라우저에서 확인 할 수 있다.<br>
`file` 파라미터를 추가하면 프로젝트 루트 경로에 `stats.json` 파일을 출력한다.
```bash
# 웹 브라우저에서 확인
$ react-vessel analyze

# 파일로 내용 출력
$ react-vessel analyze file
```

## License
프로젝트 라이센스는 [LICENSE](https://mornya.github.io/documents/LICENSE-ISC) 참조.
