---
title: Node.js 및 React 앱 만들기
description: 이 자습서에서는 Visual Studio용 Node.js 도구를 사용하여 앱을 만듭니다.
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faf418155708ebc577efea57ed3352953a8d577d
ms.sourcegitcommit: 5920a8b0c68350f11eabc1652a19b04d0196881a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75622564"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>자습서: Visual Studio에서 Node.js 및 React 앱 만들기

Visual Studio를 사용하면 쉽게 Node.js 프로젝트를 만들고 IntelliSense 및 Node.js를 지원하는 다른 기본 제공 기능을 경험할 수 있습니다. Visual Studio용 이 자습서에서는 Visual Studio 템플릿에서 Node.js 웹 애플리케이션 프로젝트를 만듭니다. 그런 다음, React를 사용하여 간단한 앱을 만듭니다.

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.
> [!div class="checklist"]
> * Node.js 프로젝트 만들기
> * NPM 패키지 추가
> * 앱에 React 코드 추가
> * JSX 트랜스파일
> * 디버거 연결

## <a name="before-you-begin"></a>시작하기 전 주의 사항

다음은 몇 가지 주요 개념을 소개하는 빠른 FAQ입니다.

### <a name="what-is-nodejs"></a>Node.js란?

Node.js는 JavaScript 서버 쪽을 실행하는 서버 쪽 JavaScript 런타임 환경입니다.

### <a name="what-is-npm"></a>npm이란?

npm는 Node.js를 위한 기본 패키지 관리자입니다. 패키지 관리자는 프로그래머가 Node.js 라이브러리의 소스 코드를 쉽게 게시 및 공유하게 하며, 라이브러리의 설치, 업데이트 및 제거를 간소화하도록 설계되었습니다.

### <a name="what-is-react"></a>React란?

React는 UI를 만드는 데 사용되는 프런트 엔드 프레임워크입니다.

### <a name="what-is-jsx"></a>JSX란?

JSX는 일반적으로 UI 요소를 설명하기 위해 React와 함께 사용되는 JavaScript 구문 확장입니다. JSX 코드는 일반 JavaScript로 트랜스파일되어야 브라우저에서 실행할 수 있습니다.

### <a name="what-is-webpack"></a>webpack이란?

webpack은 브라우저에서 실행될 수 있도록 JavaScript 파일을 번들로 제공합니다. 다른 리소스와 자산으로 변환하거나 패키지화할 수도 있습니다. 종종 JSX 또는 TypeScript 코드를 일반 JavaScript로 트랜스파일하도록 Babel 또는 TypeScript 등의 컴파일러를 지정하는 데 사용됩니다.

## <a name="prerequisites"></a>사전 요구 사항

* Node.js 개발 워크로드와 Visual Studio가 설치되어 있어야 합니다.

    ::: moniker range=">=vs-2019"
    아직 Visual Studio 2019를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    아직 Visual Studio 2017을 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end

    워크로드는 설치해야 하지만 Visual Studio는 이미 있는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **Node.js 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

    ![VS 설치 관리자에서 Node.js 워크로드](../ide/media/quickstart-nodejs-workload.png)

* Node.js 런타임을 설치해야 합니다.

    이 자습서는 버전 10.16.0을 사용하여 테스트했습니다.

    아직 설치되지 않은 경우 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치합니다. 일반적으로, 설치된 Node.js 런타임은 Visual Studio에서 자동으로 검색됩니다. 설치된 런타임이 검색되지 않으면 속성 페이지에서 설치된 런타임을 참조하도록 프로젝트를 구성할 수 있습니다(프로젝트를 만든 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다).

## <a name="create-a-project"></a>프로젝트 만들기

먼저 Node.js 웹 애플리케이션 프로젝트를 만듭니다.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q** 입력하여 검색 상자를 열고 **Node.js**를 입력한 다음, **빈 Node.js 웹 애플리케이션 - JavaScript**를 선택합니다. (이 자습서에서는 TypeScript 컴파일러를 사용하지만 단계에서는 **JavaScript** 템플릿으로 시작해야 합니다.)
    
    표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **JavaScript**를 확장한 다음, **Node.js**를 선택합니다. 가운데 창에서 **빈 Node.js 웹 애플리케이션**을 선택하고, 이름을 **NodejsWebAppBlank**로 입력하고, **확인**을 선택합니다.
    ::: moniker-end
    **빈 Node.js 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio가 새 솔루션을 만들고 프로젝트를 엽니다.

    ![솔루션 탐색기에서 Node.js 프로젝트](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) **bold** 강조 표시된 것은 **새 프로젝트** 대화 상자에서 지정한 이름을 사용하는 프로젝트입니다. 파일 시스템에서 이 프로젝트는 프로젝트 폴더의 *.njsproj* 파일로 표시됩니다. 속성을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하여 프로젝트와 연결된 환경 변수와 속성을 설정할 수 있습니다. 프로젝트 파일이 Node.js 프로젝트 소스에 사용자 지정 변경을 하지 않으므로 다른 개발 도구와 라운드트립을 수행할 수 있습니다.

    (2) 최상위 수준은 기본적으로 프로젝트와 이름이 동일한 솔루션입니다. 디스크에서 *.sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다.

    (3) npm 노드에는 설치된 모든 npm 패키지가 표시됩니다. 대화 상자를 사용하여 npm 패키지를 검색하고 설치하거나 *package.json*에서 설정 및 npm 노드에서 마우스 오른쪽 단추로 클릭 옵션을 사용하여 업데이트 패키지를 설치 및 업데이트하려면 Npm 노드를 마우스 오른쪽 단추로 클릭할 수 있습니다.

    (4) *package.json*은 로컬로 설치된 패키지에 대한 패키지 버전 및 종속성을 관리하기 위해 npm에서 사용하는 파일입니다. 이 파일에 대한 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

    (5) *server.js*와 같은 프로젝트 파일은 프로젝트 노드 아래에 표시됩니다. *server.js*는 프로젝트 시작 파일이므로 **굵게** 표시됩니다. 프로젝트에서 파일을 마우스 오른쪽 단추로 클릭하고 **Node.js 시작 파일로 설정**을 선택하여 시작 파일을 설정할 수 있습니다.

## <a name="add-npm-packages"></a>NPM 패키지 추가

이 앱이 제대로 실행되려면 많은 npm 모듈이 필요합니다.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. 솔루션 탐색기(오른쪽 창)의 프로젝트에서 **npm** 노드를 마우스 오른쪽 버튼으로 클릭하고 **새 npm 패키지 설치**를 선택합니다.

    **새 npm 패키지 설치** 대화 상자에서 최신 패키지 버전 설치 또는 버전 지정을 선택할 수 있습니다. 이러한 패키지의 현재 버전 설치를 선택하고 나중에 예기치 않은 오류가 발생하면 나중에 이러한 단계에서 설명된 정확한 패키지 버전을 설치해야 할 수 있습니다.

1. **새 npm 패키지 설치** 대화 상자에서 React 패키지를 검색하고 **패키지 설치**를 선택하여 설치합니다.

    ![npm 패키지 설치](../javascript/media/tutorial-nodejs-react-install-packages.png)

    패키지를 설치 진행률을 확인하려면 **출력** 창을 선택합니다(**출력 보기** 필드에서 **Npm**선택). 설치 시 패키지가 **npm** 노드 아래 표시됩니다.

    프로젝트의 *package.json* 파일은 패키지 버전을 포함하여 새 패키지 정보로 업데이트됩니다.

1. UI를 사용하여 나머지 패키지를 한 번에 하나씩 검색하고 추가하는 대신 *package.json*에 다음 코드를 붙여넣습니다. 이렇게 하려면 다음 코드와 함께 `dependencies` 섹션을 추가합니다.

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    빈 템플릿 버전에 `dependencies` 섹션이 이미 있는 경우는 앞에 나온 JSON 코드로 바꾸기만 하면 됩니다. 이 파일의 사용에 대한 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

1. 변경 내용을 저장합니다.

1. 프로젝트에서 **npm** 노드를 마우스 오른쪽 단추로 클릭하고 **npm 패키지 업데이트**를 선택합니다.

    아래쪽 창에서 **출력** 창을 선택하여 패키지 설치 진행률을 확인합니다. 설치하는 데 몇 분 정도 걸릴 수 있으며 즉시 결과를 확인할 수는 없습니다. 출력을 보려면 **출력** 창의 **출력 표시** 필드에서 **Npm**을 선택합니다.

    설치된 후 솔루션 탐색기에 표시된 대로 여기 npm 모듈이 있습니다.

    ![NPM 패키지](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > 명령줄을 사용하여 npm 패키지를 설치하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **여기서 명령 프롬프트 열기**를 선택합니다. 표준 Node.js 명령을 사용하여 패키지를 설치합니다.

## <a name="add-project-files"></a>프로젝트 파일 추가

이러한 단계에서는 프로젝트에 새 파일 4개를 추가합니다.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

이 간단한 앱에 대해서는 프로젝트 루트에서 새 프로젝트 파일을 추가합니다. (대부분의 앱에서 일반적으로 하위 폴더에 파일을 추가하고 상대 경로 참조를 적절하게 조정합니다.)

1. 솔루션 탐색기에서 **NodejsWebAppBlank** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **새 항목 추가** 대화 상자에서 **TypeScript JSX 파일**을 선택하고 *app.tsx* 이름을 입력하고 **추가** 또는 **확인**을 선택합니다.

1. *webpack-config.js*를 추가하려면 이러한 단계를 반복합니다. TypeScript JSX 파일 대신 **JavaScript 파일**을 선택합니다.

1. *index.html*을 프로젝트에 추가하려면 동일한 단계를 반복합니다. JavaScript 파일 대신 **HTML 파일**을 선택합니다.

1. *tsconfig.json*을 프로젝트에 추가하려면 동일한 단계를 반복합니다. JavaScript 파일 대신 **TypeScript JSON 구성 파일**을 선택합니다.

## <a name="add-app-code"></a>앱 코드 추가

1. *server.js*를 열고 기존 코드를 다음 코드로 바꿉니다.

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   이전 코드는 Express를 사용하여 웹 애플리케이션 서버로 Node.js를 시작합니다. 위의 코드는 프로젝트 속성에서 구성된 포트 번호에 포트를 설정합니다(기본적으로 포트는 구성 속성에서 1337로 구성됩니다). 프로젝트 속성을 열려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. *app.tsx*를 열고 다음 코드를 추가합니다.

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    위의 코드는 JSX 구문과 React를 사용하여 간단한 메시지를 표시합니다.

1. *index.html*을 열고 **body** 섹션을 다음 코드로 바꿉니다.

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    이 HTML 페이지는 일반 JavaScript로 트랜스파일된 JSX 및 React 코드를 포함하는 *app-bundle.js*를 로드합니다. 현재 *app-bundle.js*는 빈 파일입니다. 다음 섹션에서 코드를 트랜스파일하는 옵션을 구성합니다.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Webpack 및 TypeScript 컴파일러 옵션 구성

위의 단계에서 *webpack-config.js*를 프로젝트에 추가했습니다. 다음으로, webpack 구성 코드를 추가합니다. JSX를 일반 JavaScript로 번들 및 트랜스파일하려면 입력 파일(*app.tsx*) 및 출력 파일(*app-bundle.js*)을 지정하는 간단한 webpack 구성을 추가합니다. 트랜스파일하려면 일부 TypeScript 컴파일러 옵션을 구성합니다. 이 코드는 webpack 및 TypeScript 컴파일러를 도입하려는 기본 구성입니다.

1. 솔루션 탐색기에서 *webpack-config.js*를 열고 다음 코드를 추가합니다.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    webpack 구성 코드는 webpack에게 TypeScript 로더를 사용해 JSX를 트랜스파일하도록 지시합니다.

1. *tsconfig.json*을 열고 다음 코드로 기본 코드를 대체하여 TypeScript 컴파일러 옵션을 지정합니다.

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    소스 파일로 *app.tsx*를 지정합니다.

## <a name="transpile-the-jsx"></a>JSX 트랜스파일

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **여기서 명령 프롬프트 열기**를 선택합니다.

1. 명령 프롬프트에 다음 명령을 입력합니다.

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    명령 프롬프트 창에 결과가 표시됩니다.

    ![webpack 실행](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    위의 출력 대신 오류를 참조하면 앱이 작동하기 전에 해당 오류를 해결해야 합니다. npm 패키지 버전이 이 자습서에 표시된 버전과 다른 경우 오류의 원인이 될 수 있습니다. 오류를 수정하는 한 방법은 이전 단계에서 표시된 정확한 버전을 사용하는 것입니다. 또한 이러한 패키지 버전 중 하나 이상이 사용되지 않아 오류를 일으킬 경우 오류를 수정하려면 최신 버전을 설치해야 합니다. *package.json*을 사용하여 npm 패키지 버전을 제어하는 방법에 대한 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **기존 폴더**를 선택한 다음, *dist* 폴더를 선택하고 **폴더 선택**을 선택합니다.

    Visual Studio는 *app-bundle.js* 및 *app-bundle.js.map*을 포함하는 프로젝트에 *dist* 폴더를 추가합니다.

1. *app-bundle.js*를 열고 트랜스파일된 JavaScript 코드를 봅니다.

1. 외부에서 수정된 파일을 다시 로드하라는 메시지가 나타나면 **모두 예**를 선택합니다.

    ![수정한 파일 로드](../javascript/media/tutorial-nodejs-react-reload-files.png)

*app.tsx*를 변경할 때마다 webpack 명령을 다시 실행해야 합니다. 이 단계를 자동화하려면 빌드 스크립트를 추가하여 JSX를 트랜스파일합니다.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>빌드 스크립트를 추가하여 JSX를 트랜스파일

Visual Studio 2019부터 빌드 스크립트가 필요합니다. 앞의 섹션에서 표시된 것처럼, 명령줄에서 JSX를 변환 컴파일하기보다 Visual Studio에서 빌드할 때 JSX를 변환 컴파일할 수 있습니다.

* *package.json*을 열고 `dependencies` 섹션 뒤에 다음 섹션을 추가합니다.

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>앱 실행

1. Microsoft Edge 또는 Chrome을 현재 디버그 대상으로 선택합니다.

    ::: moniker range=">=vs-2019"
    ![디버그 대상으로 크롬 선택](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![디버그 대상으로 크롬 선택](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    컴퓨터에서 Chrome을 사용할 수 있지만 옵션으로 표시되지 않는 경우 디버그 대상 드롭다운 목록에서 **웹 브라우저(browsername)** > **웹 브라우저 선택**을 선택하고 기본 브라우저 대상으로 **Chrome**을 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    컴퓨터에서 Chrome을 사용할 수 있지만 옵션으로 표시되지 않는 경우 디버그 대상 드롭다운 목록에서 **웹 브라우저(browsername)** > **Google Chrome**을 선택하고 기본 브라우저 대상으로 **Chrome**을 선택합니다.
    ::: moniker-end

1. 앱을 실행하려면 **F5**(**디버그** > **디버깅 시작**) 키 또는 녹색 화살표 단추를 누릅니다.

    디버거가 수신 대기하는 포트를 보여주는 Node.js 콘솔 창이 열립니다.

    Visual Studio는 *server.js* 시작 파일을 시작하여 앱을 시작합니다.

    ![브라우저에서 React 실행](../javascript/media/tutorial-nodejs-react-running-react.png)

1. 브라우저 창을 닫습니다.

1. 콘솔 창을 닫습니다.

## <a name="set-a-breakpoint-and-run-the-app"></a>중단점 설정 및 앱 실행

1. *server.js*에서 `staticPath` 선언 왼쪽의 여백을 클릭해 중단점을 설정합니다.

    ![중단점 설정](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다.

1. 앱을 실행하려면 **F5**(**디버그** > **디버깅 시작**) 키를 누릅니다.

    디버거는 설정한 중단점에서 일시 중지합니다(현재 명령문은 노란색으로 표시됩니다). 이제 **로컬** 및 **조사식** 창과 같은 디버거 창을 사용하여 현재 범위 내에 있는 변수를 가리킴으로써 앱 상태를 검사할 수 있습니다.

1. 앱을 계속하려면 **F5** 키를 누릅니다.

1. Chrome 개발자 도구 또는 Microsoft Edge용 F12 도구를 사용하려는 경우 **F12**를 누릅니다. JavaScript 콘솔을 사용하여 앱과 상호 작용하고 DOM을 검사하려면 이러한 도구를 사용할 수 있습니다.

1. 콘솔 및 웹 브라우저를 닫습니다.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>클라이언트 쪽 React 코드에서 중단점 설정 및 적중

이전 섹션에서 서버 쪽 Node.js 코드에 디버거를 연결했습니다. Visual Studio에서 디버거를 연결하고 클라이언트 쪽 React 코드에서 중단점을 적중하려면 디버거는 올바른 프로세스를 식별하기 위한 도움이 필요합니다. 이를 사용하는 한 방법은 다음과 같습니다.

### <a name="prepare-the-browser-for-debugging"></a>디버그할 브라우저 준비

::: moniker range=">=vs-2019"
이 시나리오에서는 현재 IDE에서 **Microsoft Edge 베타**라고 되어 있는 Microsoft Edge(Chromium) 또는 Chrome을 사용합니다.
::: moniker-end
::: moniker range="vs-2017"
이 시나리오에서는 Chrome을 사용합니다.
::: moniker-end

1. 대상 브라우저의 모든 창을 닫습니다.

   다른 브라우저 인스턴스에서는 디버깅을 사용하도록 설정하여 브라우저를 열지 못하게 할 수 있습니다. (브라우저 확장이 실행 중이고 전체 디버그 모드를 방해할 수 있으므로 예기치 않은 Chrome 인스턴스를 찾으려면 작업 관리자를 열어야 할 수 있습니다.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge(Chromium)의 경우 Chrome의 모든 인스턴스도 종료합니다. 두 브라우저는 모두 chromium 코드베이스를 공유하기 때문에 최상의 결과를 제공합니다.
   ::: moniker-end

   ::: moniker range=">=vs-2019"
   Microsoft Edge(Chromium)의 경우 Chrome의 모든 인스턴스도 종료합니다. 두 브라우저는 모두 chromium 코드 베이스를 사용하기 때문에 최상의 결과를 제공합니다.
   ::: moniker-end

2. 디버깅을 사용하도록 설정된 상태로 브라우저를 시작합니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019부터 **디버그** 도구 모음에서 **브라우저 선택...** >을 선택하고, **추가**를 선택한 다음, **인수** 필드에서 플래그를 설정하여 브라우저 시작 시 `--remote-debugging-port=9222` 플래그를 설정할 수 있습니다. 브라우저에 대해 **디버깅 포함 Microsoft Edge** 또는 **디버깅 포함 Chrome**과 같은 다른 식별 이름을 사용하세요. 자세한 내용은 [릴리스 정보](/visualstudio/releases/2019/release-notes-v16.2)를 참조하세요.

    ![디버깅 사용 설정 상태로 열도록 브라우저 설정](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    또는 Windows **시작** 단추에서 **실행** 명령을 열고(마우스 오른쪽 단추로 클릭하고 **실행** 선택) 다음 명령을 입력합니다.

    `msedge --remote-debugging-port=9222`

    또는

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **시작** 단추(**실행**을 마우스 오른쪽 단추로 클릭하고 선택)에서 **실행** 명령을 열고 다음 명령을 입력합니다.

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    이렇게 하면 디버깅을 사용하도록 설정된 상태로 브라우저가 시작됩니다.

    앱이 아직 실행되고 있지 않으므로 빈 브라우저 페이지를 가져옵니다.

### <a name="attach-the-debugger-to-client-side-script"></a>클라이언트 쪽 스크립트에 디버거 연결

1. Visual Studio로 전환한 다음 소스 코드에서 *app-bundle.js* 또는 *app.tsx*로 중단점을 설정합니다.

    *app-bundle.js*의 경우 다음 그림에 표시된 것처럼 `render()` 함수에서 중단점을 설정합니다.

    ![중단점 설정](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    트랜스파일된 *app-bundle.js* 파일에서 `render()` 함수를 찾으려면 **Ctrl**+**F**를 사용합니다(**편집** > **찾기 및 바꾸기** > **빠른 찾기** 사용).

    *app.tsx*의 경우 `return` 문에서 `render()` 함수 내부에 중단점을 설정합니다.

    ![중단점 설정](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. *.tsx* 파일(*app-bundle.js* 아님)에서 중단점을 설정하는 경우 *webpack-config.js*를 업데이트해야 합니다. 다음 코드를

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    이 코드로 바꿉니다.

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Visual Studio에서 디버깅을 사용하도록 설정하는 개발 전용 설정입니다. 이 설정을 사용하면 앱을 빌드할 때 소스 맵 파일 *app-bundle.js.map*에서 생성된 참조를 재정의할 수 있습니다. 기본적으로 소스 맵 파일의 webpack 참조에는 Visual Studio에서 소스 파일 *app.tsx*를 찾을 수 없도록 하는 *webpack:///* 접두사가 포함되어 있습니다. 특히 이 변경을 수행하면 소스 파일 *app.tsx*에 대한 참조가 *webpack:///./app.tsx*에서 *./app.tsx*로 변경되어 디버깅을 사용할 수 있습니다.

3. Visual Studio에서 디버그 대상으로 대상 브라우저를 선택하여 **Ctrl**+**F5**(**디버그** > **디버깅하지 않고 시작**) 키를 눌러 브라우저에서 앱을 실행합니다.

    ::: moniker range=">=vs-2019"
    식별 이름을 사용하여 브라우저 구성을 만들었다면 이를 디버그 대상으로 선택합니다.
    ::: moniker-end

    앱이 새 브라우저 탭에서 열립니다.

4. **디버그** > **프로세스에 연결**을 선택합니다.

    > [!TIP]
    > Visual Studio 2017부터 이러한 단계를 수행하여 처음으로 프로세스에 연결할 때 **디버그** > **프로세스에 다시 연결**을 선택하여 동일 프로세스에 신속하게 다시 연결할 수 있습니다.

5. **프로세스에 연결** 대화 상자에서 연결할 수 있는 브라우저 인스턴스의 필터링된 목록을 가져옵니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019의 **연결 대상** 필드에서 대상 브라우저에 대해 올바른 디버거 **JavaScript(Chrome)** 또는 **JavaScript(Microsoft Edge - Chromium)** 를 선택하고 필터 상자에 **chrome** 또는 **edge**를 입력하여 검색 결과를 필터링합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017의 **연결 대상** 필드에서 **WebKit 코드**를 선택하고 필터 상자에 **chrome**을 입력해 검색 결과를 필터링합니다.
    ::: moniker-end

6. 올바른 호스트 포트(이 예제에서는 localhost)를 사용하여 브라우저 프로세스를 선택하고 **연결**을 선택합니다.

    올바른 브라우저 인스턴스를 선택하는 데 도움이 되도록 포트(1337)가 **제목** 필드에 나타날 수도 있습니다.

    ::: moniker range=">=vs-2019"
    다음 예제에서는 Microsoft Edge(Chromium) 브라우저를 찾는 방법을 보여 줍니다.

    ![프로세스에 연결](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![프로세스에 연결](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM 탐색기와 JavaScript 콘솔이 Visual Studio에서 열릴 때 디버거가 올바르게 연결됐는지 알 수 있습니다. 이러한 디버깅 도구는 크롬 개발자 도구 및 F12 Tools for Microsoft Edge와 유사합니다.
    ::: moniker-end

    > [!TIP]
    > 디버거가 연결되지 않고 “프로세스에 연결할 수 없습니다. 현재 상태에서는 작업을 수행할 수 없습니다.”라는 메시지가 표시되는 경우, 디버깅 모드로 브라우저를 시작하기 전에 작업 관리자를 사용하여 대상 브라우저의 모든 인스턴스를 닫습니다. 실행 중일 수 있는 브라우저 확장 프로그램이 전체 디버그 모드를 방지할 수 있습니다.

7. 중단점이 있는 코드가 이미 실행됐기 때문에 중단점을 적중하려면 브라우저 페이지를 새로 고치기 합니다.

    디버거에서 일시 중지된 동안 변수를 가리키고 디버거 창을 사용하여 앱 상태를 검사할 수 있습니다. 단계별 코드 실행(**F5**, **F10** 및 **F11**)으로 디버거로 이동할 수 있습니다. 기본 디버깅 기능에 대한 자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

    환경 및 브라우저 상태와 함께 이전에 수행한 단계에 따라 *app.tsx*에서 매핑된 위치 또는 *app-bundle.js*에서 중단점을 적중할 수 있습니다. 어느 경우든 단계별 코드를 실행하고 변수를 검사할 수 있습니다.

   * *app.tsx*에서 코드를 중단해야 하는데 그럴 수 없는 경우 이전 단계에 설명된 대로 **프로세스에 연결**을 사용하여 디버거를 연결합니다. 환경이 올바르게 설정되었는지 확인합니다.

      * 디버그 모드에서 브라우저를 실행할 수 있도록 Chrome 확장 프로그램(작업 관리자 사용)을 비롯한 모든 브라우저 인스턴스를 닫았습니다. 디버그 모드에서 브라우저를 시작해야 합니다.

      * 소스 맵 파일에 Visual Studio 디버거가 *app.tsx*를 찾을 수 없도록 하는 *webpack:///./app.tsx*가 아니라 *./app.tsx*에 대한 참조를 포함하도록 합니다.
       또는 *app.tsx*에서 코드를 중단해야 하는데 그럴 수 없는 경우 *app.tsx*에서 `debugger;` 문을 사용하거나 대신 Chrome 개발자 도구(또는 Microsoft Edge의 F12 도구)에서 중단점을 설정합니다.

   * *app-bundle.js*에서 코드를 중단해야 하는데 그럴 수 없는 경우 *app-bundle.js.map* 소스 맵 파일을 제거합니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [앱을 Linux App Service에 배포](../javascript/publish-nodejs-app-azure.md)
