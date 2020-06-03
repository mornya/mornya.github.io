# React Vessel
![version](https://img.shields.io/npm/v/@mornya/react-vessel)
![node](https://img.shields.io/node/v/@mornya/react-vessel)
![types](https://img.shields.io/npm/types/@mornya/react-vessel)
![downloads](https://img.shields.io/npm/dw/@mornya/react-vessel)
![license](https://img.shields.io/npm/l/@mornya/react-vessel)

Copyright 2020. mornya. All rights reserved.

## About
SPA 형태의 React.js 앱 개발을 위한 TypeScript 기반의 코드 템플릿을 생성해 주는 프로젝트.<br>
빠른 개발/배포를 위해 초기 환경을 미리 설정해 두어, 컴파일/테스트/앱 개발 등 관련 세부 설정에 대해 신경쓰지 않고 코드 개발에 집중하도록 React.js 앱 스케폴딩을 제공.

## Features
- TypeScript / ES6+ support with [TypeScript](https://www.typescriptlang.org/).
- No Babel
- Your application can be created with a template, and fewer preferences.
- Code developed with [React.js](https://reactjs.org/) is bundled via [Webpack](https://webpack.js.org/) and extracts static resources.
- Linting and testing TypeScript / ECMAScript / JavaScript codes with [Lintest CLI](https://npmjs.com/@lintest/cli).

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

## Available scripts
`package.json`에 정의된 "script" 항목 및 기타 실행가능 스크립트는 아래와 같다.

### `start`
> HMR 및 react-hot-loader 등이 적용된 로컬 개발 서버를 실행한다. 루트 디렉토리의 `.env` 파일이 참조되어 로컬 개발 서버의 호스트명, 접속 포트 등을 설정 할 수 있다.
```bash
$ npm start
$ npm run [serve|dev]
```

### `analyze`
> `production mode`로 컴파일된 번들의 용량을 체크한다. `file` 파라미터를 추가하면 프로젝트 루트 경로에 `stats.json` 파일을 출력한다.
```bash
$ npm run analyze [file]
```

### `clean`
> 빌드 output 디렉토리 경로를 삭제한다.
```bash
$ npm run clean
```

### `build`
> 작성된 애플리케이션은 webpack을 거쳐 컴파일/트랜스파일링 된 후 `./dist` 디렉토리에 출력된다.<br>
 컴파일은 `tsconfig.json` 설정에 따르며 빌드 완료시 웹 서비스가 가능한 환경을 제공한다.
```bash
$ npm run build
```

### `lint`
> Lintest CLI를 실행하여 문법 오류 등을 체크한다.
```bash
$ npm run lint
```

### `lint:fix`
> Lintest CLI를 실행하여 문법 오류 등을 체크하고 자동 교정한다.
```bash
$ npm run lint:fix
```

### `test`
> Lintest CLI를 실행하여 테스트를 수행한다.
```bash
$ npm run test
```

### `test:watch`
> Lintest CLI를 실행하여 watch mode로 테스트케이스를 수행한다.
```bash
$ npm run test:watch
```

### `test:coverage`
> Lintest CLI를 실행하여 테스트 커버리지 데이터를 수집, `/coverage` 디렉토리에 내용을 출력한다.
```bash
$ npm run test:coverage
```
