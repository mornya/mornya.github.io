# Vessel
![npm](https://img.shields.io/npm/v/@mornya/vessel)
![node](https://img.shields.io/node/v/@mornya/vessel)
![types](https://img.shields.io/npm/types/@mornya/vessel)
![downloads](https://img.shields.io/npm/dw/@mornya/vessel)
![license](https://img.shields.io/npm/l/@mornya/vessel)

Copyright 2021. mornya. All rights reserved.

## About
라이브러리(디펜던시 모듈) 개발을 위한 TypeScript/ECMAScript 기반 스켈레톤을 생성해 주는 프로젝트.
빠른 애플리케이션 개발/배포를 위해 초기 개발환경을 미리 구성하여 복잡하고 번거로운 개발환경 설정에 대해 신경쓰지 않고 코드에 집중하도록 스케폴딩을 제공한다.

## Features
- [TypeScript](https://www.typescriptlang.org/) and ES6+ is supported by default WITHOUT using Babel.
- You can make libraries right away with pre-configured code templates and preferences.
- Created packages can be published in places such as [NPM Registry](https://www.npmjs.com/).
- Lint and test all of your codes with [Lintest CLI](https://npmjs.com/@lintest/cli).

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

## Execution
아래와 같이 커맨드 라인에서 CLI를 실행하며, 출력되는 메시지로 사용 가능한 커맨드를 확인 할 수 있다.
> 문서 하단 "Available commands" 참조.
```bash
$ vessel
```

## Create a new project
신규 프로젝트 생성은 터미널 등의 환경에서 아래와 같이 `vessel init` 커맨드를 실행하여 기본적인 템플릿을 바탕으로 프로젝트 개발 환경을 구축한다.
> 실행시 `src` 하위 경로에 포함되는 원본 코드는 기본적으로 TypeScript 파일이며, ECMAScript/VanillaJS 등으로 개발을 위해 확장자를 *.js 및 *.jsx 형태로 변경하면 된다.
```bash
$ mkdir <project-name>
$ cd <project-name>
$ vessel init
```
혹은 `npm init` 등을 실행하여 `package.json` 파일 등이 존재할 때, `vessel init` 커맨드를 실행해도 무방하다. 이 때 기존 `package.json` 파일의 내용과 Vessel에서 템플릿으로 설정한 내용이 병합되어, 각종 설정 들이 추가/변경 된다.
```bash
$ npm init
$ git init
$ vessel init
```
아래와 같이 프로젝트 이름 및 설명을 설정하여 초기화 혹은 기존 데이터와 병합이 가능하다.
> `package.json`의 name과 description이 입력된 값으로 변경되며, 신규 생성시에는 README.md 등 템플릿에도 적용된다.
```bash
$ vessel init "@myorg/sample"
or
$ vessel init "@myorg/new-awesome-libs" "새로운 프로젝트"
```

## Build project
프로젝트 내 ECMAScript 혹은 TypeScript 등으로 작성된 파일들은 트랜스파일을 거쳐 `dist` 경로(변경 불가)에 `*.js` 파일들로 생성이 되며, 해당 경로의 각 모듈들은 라이브러리가 사용될 프로젝트의 디펜던시로 사용되게 된다. `npm publish` 명령을 통해서도 빌드가 먼저 실행되지만, 개발 테스트 등을 위해 아래와 같은 명령을 실행해 볼 수 있다.
> `npm run build` 명령은 빌드만 진행하고 종료하지만 `npm run watch` 명령은 빌드 후 소스코드 변경을 감지하여 빌드를 수행한다 (watch mode).
```bash
$ npm run build
$ npm run watch
```

## Check local project
NPM 레지스트리나 NexusOSS 등에 개발된 모듈을 퍼블리시 하기 전에 실제 사용될 앱에서 해당 라이브러리를 테스트 할 수 있다.<br>
현재 프로젝트의 루트 경로에서 아래와 같은 커맨드를 입력하면 전역 Node 모듈 설치 영역에 심볼릭 링크 형태로 현재 라이브러리가 연계된다.
```bash
$ npm link
```
지속적으로 확인하며 라이브러리를 수정해야 할 경우에는 `npm run watch` 등을 실행하면 된다.<br><br>
그리고 해당 라이브러리를 사용 할 앱에서는 링크된 라이브러리의 패키지명을 연계해주면 된다.
```bash
$ npm link my-awesome-library
```
> 링크된 라이브러리를 사용하게 될 앱의 `package.json` 파일 내용을 확인해보면 디펜던시를 찾을 수 없다는 메시지가 나올 수도 있다. 이 때에는 아래와 같이 디펜던시를 임의로 추가해준다.
```json
{
  "dependency": {
    "my-awesome-library": "latest"
  }
}
```
Webpack을 사용하는 프로젝트에서는 링크된 라이브러리로 인해 빌드가 되지 않을 수도 있다. 링크된 라이브러리는 프로젝트 내 npm install로 설치한 것이 아니라 외부에 위치한 심볼릭 링크이기 때문에 디렉토리를 찾을 수 없을 것이다. 이런 경우 webpack.config.js 설정에 아래 내용을 추가해준다.
```json
{
  "resolve": {
    "symlinks": false
  }
}
```

## Publish project
NPM 레지스트리 등에 퍼블리시 진행을 하기 위해서는 처음 1회 레지스트리에 로그인을 진행해야 하는데, 아래 명령으로 손쉽게 처리 할 수 있다.<br>
기본 [NPM 레지스트리](https://registry.npmjs.org)로의 모듈 퍼블리시라면 `npm login`으로도 가능하지만, 사설 레지스트리 등을 이용할 경우 `package.json` 파일 내 `publishConfig` 항목에 설정된 레지스트리에 퍼블리시를 원한다면 옵션 값을 추가해야 하지만, `npm run login` 명령으로 간단히 로그인 할 수 있다.
```bash
$ npm run login
```
그리고 퍼블리시를 바로 진행해도 된다.<br>
`package.json` 파일의 `prepublishOnly` 항목에 설정된 스크립트가 실행되며, 로그인/빌드/버전체크 등의 처리가 이루어진다.<br>
```bash
$ npm publish
```
단, 그 전에 만약 퍼블리시 명령을 통해 배포될 파일 중 제외할 파일들이 있거나 배포 할 디렉토리나 파일을 선택하고 싶다면 아래 방법 중 하나를 사용한다.
- package.json의 `"files"` 항목은 배포시 포함될 디렉토리나 파일 목록이므로 포함 할 내용을 기재하고, 제외할 항목은 맨 앞에 `!`를 붙여준다 (`vessel init` 명령으로 생성된 package.json 파일 참고)
- 제외될 항목을 `.npmignore` 파일에 기재.
> 배포시 기본적으로 테스트 파일(*.test.{ts|tsx|js|jsx}) 등은 패키징에서 제외된다.<br>
> 정상적으로 빌드가 성공하고 로그인되어 레지스트리 등에 업로드되어 배포가 완료되면 사이트 등에서 확인해보도록 한다. 예를들어 NPM 레지스트리에 배포되었다면 NPM에 로그인해서 패키지 목록에서 확인하거나, 아래와 같이 검색을 통해 확인할 수도 있다.<br>ex) https://www.npmjs.com/search?q=my-awesome-library

## Available commands
Vessel에서 사용 가능한 커맨드는 아래와 같다.

### `Initialization`
생성된 프로젝트 초기에 실행하도록 한다. 현재 경로에 미리 구성된 템플릿 파일 복제 과정을 수행하며, 만약 수행시 `package.json` 파일이 존재하는 경우 각 설정들을 병합하게 된다.
> `package.json` 파일 이외에 다른 템플릿 파일과 동일한 파일이 현재 경로 및 하위에 존재할 경우에는 덮어쓰기 되니 주의.
```bash
$ vessel init
```

### `Build`
ECMAScript 혹은 TypeScript로 개발된 모듈에 대한 빌드를 실행한다.<br>
TypeScript 컴파일러를 통해 트랜스파일된 `.js` 파일들이 추출되며, 해당 파일들은 `dist` 경로에 생성된다.
```bash
# 빌드만 실행
$ vessel build

# 빌드 및 watch 모드 실행
$ vessel build watch
```

### `Clean build`
`dist` 경로에 생성된 산출물 및 캐시 디렉토리 내 모든 파일을 제거한다.<br>
> 해당 명령 실행시에만 캐시 디렉토리가 제거 대상에 포함된다.
```bash
$ vessel clean
```

### `Check`
타입스크립트 코드 검증을 위해 컴파일러를 실행한다.<br>
> `lint-stage` 등에서 필요시 사용한다.
```bash
$ vessel check
```

### `Login registry`
퍼블리시 대상이 되는 레지스트리로의 로그인을 실행한다. [NPM 레지스트리](https://registry.npmjs.org)로 퍼블리시한다면 `npm login` 명령과 동일하게 수행되지만, 사설 레지스트리 등에 퍼블리시를 원한다면 `package.json` 파일 내의 `publishConfig` 항목에 대상 레지스트리 url를 기재하고 `npm run login`을 실행하면 간편하게 로그인을 수행 할 수 있다.
```bash
$ vessel login
```

### `Prepublish`
NPM 레지스트리 혹은 `package.json` 파일의 `publishConfig`에 설정된 레지스트리에 개발된 라이브러리를 퍼블리시 하기 전 수행될 작업을 진행한다.
```bash
$ vessel prepublish
```

## License
프로젝트 라이센스는 [LICENSE](https://mornya.github.io/documents/LICENSE-ISC) 파일 참조.
