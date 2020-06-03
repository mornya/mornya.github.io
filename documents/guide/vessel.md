# Vessel
![version](https://img.shields.io/npm/v/@mornya/vessel)
![node](https://img.shields.io/node/v/@mornya/vessel)
![types](https://img.shields.io/npm/types/@mornya/vessel)
![downloads](https://img.shields.io/npm/dw/@mornya/vessel)
![license](https://img.shields.io/npm/l/@mornya/vessel)

Copyright 2020. mornya. All rights reserved.

## About
라이브러리 개발을 위한 TypeScript 기반의 코드 템플릿을 생성해 주는 프로젝트.
빠른 개발/배포를 위해 초기 환경을 미리 설정해 두어, 빌드/배포 등 관련 세부 설정에 대해 신경쓰지 않고 코드 개발에 집중하도록 스케폴딩을 제공.

## Features
- TypeScript / ES6+ support with [TypeScript](https://www.typescriptlang.org/).
- No Babel
- Your package can be created with a template, and fewer preferences.
- Created packages can be published in places such as [NPM Registry](https://www.npmjs.com/).
- Linting and testing TypeScript / ECMAScript / JavaScript codes with [Lintest CLI](https://npmjs.com/@lintest/cli).

## Installation
생성된 프로젝트에서 개발을 위해 필요한 `vessel` CLI는 기본적으로 전역 모듈로 설치되어 있어야 한다.<br>
아래와 같이 커맨드 라인에서 실행 가능하도록 한다.
> `npm` 대신 `yarn` 사용시, 프로젝트 루트 경로에 `package-lock.json` 파일이 존재하면 제거하고 `yarn.lock` 파일만 참조되도록 한다.
```bash
$ npm install -g @mornya/vessel
or
$ yarn global add @mornya/vessel
```
린트와 테스트 수행 관련된 모듈은 vessel CLI 패키지에서 분리되었으므로, `@lintest/cli` 모듈을 따로 전역으로 설치한다.
```bash
$ npm install -g @lintest/cli
or
$ yarn global add @lintest/cli
```

## Available scripts
`package.json`에 정의된 "script" 항목 및 기타 실행가능 스크립트는 아래와 같다.

### `clean`
> 빌드 output 디렉토리 경로를 삭제한다.
```bash
$ npm run clean
```

### `build`
> 작성된 모듈은 TypeScript 컴파일러를 거쳐 트랜스파일링 및 minify 되어 `./dist` 디렉토리에 출력된다.<br>
 컴파일은 `tsconfig.json` 설정에 따르며 빌드 완료시 NPM 레지스트리 등에 배포할 수 있다.
```bash
$ npm run build
```

### `watch`
> TypeScript 컴파일러의 watch 기능을 수행한다.
```bash
$ npm run watch
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

### `login`
> package.json의 publishConfig 항목에 설정되거나 기본 NPM Registry로의 퍼블리시를 위해 NPM 로그인 처리를 수행한다.
`npm login`에 scope를 선언하여 처리하는 방식과 동일.
```bash
$ npm run login (not "npm login")
```

### `publish`
> 설정된 registry로 퍼블리시를 수행하기 이전에 로그인/빌드/버전체크 등을 실행한 후 퍼블리시 진행한다.
```bash
$ npm publish
```
