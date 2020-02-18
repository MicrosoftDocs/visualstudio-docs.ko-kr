---
title: JavaScript 또는 TypeScript 앱 디버그
description: Visual Studio는 Visual Studio에서 JavaScript and TypeScript 앱의 디버깅을 지원합니다.
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2020
ms.locfileid: "75678976"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Visual Studio에서 JavaScript 또는 TypeScript 앱 디버그

Visual Studio를 사용하여 JavaScript 및 TypeScript 코드를 디버깅할 수 있습니다. 중단점을 설정 및 적중하고, 디버거를 연결하고, 변수를 검사하고, 호출 스택을 보고, 다른 디버깅 기능을 사용할 수 있습니다.

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다. 수행 중인 앱 개발 형식에 따라 Visual Studio와 함께 **Node.js 개발 워크로드**를 설치해야 할 수 있습니다.

## <a name="debug-server-side-script"></a>서버 쪽 스크립트 디버그

1. Visual Studio에서 프로젝트를 연 상태에서 서버 쪽 JavaScript 파일(예: *server.js*)을 열고 왼쪽 여백의 여백을 클릭하여 중단점을 설정합니다.

    ![중단점 설정](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다.

1. 앱을 실행하려면 **F5**(**디버그** > **디버깅 시작**)을 누릅니다.

    디버거는 설정한 중단점에서 일시 중지합니다(현재 명령문은 노란색으로 표시됩니다). 이제 **로컬** 및 **조사식** 창과 같은 디버거 창을 사용하여 현재 범위 내에 있는 변수를 가리킴으로써 앱 상태를 검사할 수 있습니다.

1. 앱을 계속하려면 **F5** 키를 누릅니다.

1. Chrome 개발자 도구 또는 F12 도구를 사용하려는 경우 **F12**를 누릅니다. JavaScript 콘솔을 사용하여 앱과 상호 작용하고 DOM을 검사하려면 이러한 도구를 사용할 수 있습니다.

## <a name="debug-client-side-script"></a>클라이언트 쪽 스크립트 디버그

::: moniker range=">=vs-2019"
Visual Studio는 Chrome 및 Microsoft Edge(Chromium)에 대해서만 클라이언트 쪽 디버깅을 지원합니다. 일부 시나리오에서는 디버거가 자동으로 JavaScript 및 TypeScript 코드와 HTML 파일의 포함된 스크립트에서 중단점을 적중합니다. ASP.NET 앱에서 클라이언트 쪽 스크립트를 디버깅하는 방법에 대해서는 블로그 게시물 [Debug JavaScript in Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) 및 [Google Chrome에 대한 이 게시물](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome)을 참조하세요. ASP.NET Core에서 TypeScript를 디버깅하는 방법에 대해서는 [TypeScript를 사용하여 ASP.NET Core 앱 만들기](tutorial-aspnet-with-typescript.md)를 참조하세요.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio는 Chrome 및 Internet Explorer에 대해서만 클라이언트 쪽 디버깅 지원을 제공합니다. 일부 시나리오에서는 디버거가 자동으로 JavaScript 및 TypeScript 코드와 HTML 파일의 포함된 스크립트에서 중단점을 적중합니다. ASP.NET 앱에서 클라이언트 쪽 스크립트를 디버깅하는 방법에 대해서는 블로그 게시물 [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)을 참조하세요.
::: moniker-end

ASP.NET 이외 애플리케이션의 경우 여기에 설명된 단계를 따르세요.

### <a name="prepare-your-app-for-debugging"></a>디버깅을 위해 앱 준비

소스가 TypeScript 또는 Babel과 같은 transpiler에 의해 축소되거나 생성되는 경우 최상의 디버깅 환경을 위해 [소스 맵](#generate_source_maps)을 사용해야 합니다. 소스 맵이 없으면 실행 중인 클라이언트 쪽 스크립트에 디버거를 계속 연결할 수 있습니다. 그러나 원래 소스 파일이 아닌 축소 또는 트랜스파일된 파일에서만 중단점을 설정하고 적중할 수 있습니다. 예를 들어 Vue.js 앱에서 축소된 스크립트는 `eval` 문에 문자열로 전달되므로 소스 맵을 사용하지 않는 한 Visual Studio 디버거를 사용하여 효과적으로 이 코드를 단계별로 실행할 방법이 없습니다. 복잡한 디버깅 시나리오에서는 Chrome 개발자 도구 또는 Microsoft Edge용 F12도 사용할 수 있습니다.

소스 맵을 생성하는 방법에 대한 도움말은 [디버깅에 대한 소스 맵 생성](#generate_source_maps)을 참조하세요.

### <a name="prepare_the_browser_for_debugging"></a> 디버그할 브라우저 준비

::: moniker range=">=vs-2019"
이 시나리오에서는 현재 IDE에서 **Microsoft Edge 베타**라고 되어 있는 Microsoft Edge(Chromium) 또는 Chrome을 사용합니다.
::: moniker-end
::: moniker range="vs-2017"
이 시나리오에서는 Chrome을 사용합니다.
::: moniker-end

1. 대상 브라우저의 모든 창을 닫습니다.

   다른 브라우저 인스턴스에서는 디버깅을 사용하도록 설정하여 브라우저를 열지 못하게 할 수 있습니다. (브라우저 확장이 실행 중이고 전체 디버그 모드를 방해할 수 있으므로 예기치 않은 Chrome 인스턴스를 찾으려면 작업 관리자를 열어야 할 수 있습니다.)

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

Visual Studio에서 디버거를 연결하고 클라이언트 쪽 코드에서 중단점을 적중하려면 디버거는 올바른 프로세스를 식별하기 위한 도움이 필요합니다. 이를 사용하는 한 방법은 다음과 같습니다.

1. Visual Studio로 전환한 다음 JavaScript 파일, TypeScript 파일 또는 JSX 파일일 수 있는 소스 코드에서 중단점을 설정합니다. (return 문 또는 var 선언과 같은 중단점을 허용하는 코드 줄에 중단점을 설정합니다.)

    ![중단점 설정](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    트랜스파일된 파일에서 특정 코드를 찾으려면 **Ctrl**+**F**(**편집** > **찾기 및 바꾸기** > **빠른 찾기**)를 사용합니다.

    클라이언트 쪽 코드의 경우 TypeScript 파일의 중단점에 도달하려면 일반적으로 *.vue* 또는 JSX 파일에 [소스 맵](#generate_source_maps)을 사용해야 합니다. Visual Studio에서 디버깅을 지원하려면 소스 맵을 올바르게 구성해야 합니다.

2. Visual Studio에서 디버그 대상으로 대상 브라우저를 선택하여 **Ctrl**+**F5**(**디버그** > **디버깅하지 않고 시작**) 키를 눌러 브라우저에서 앱을 실행합니다.

    ::: moniker range=">=vs-2019"
    식별 이름을 사용하여 브라우저 구성을 만들었다면 이를 디버그 대상으로 선택합니다.
    ::: moniker-end

    앱이 새 브라우저 탭에서 열립니다.

3. **디버그** > **프로세스에 연결**을 선택합니다.

    > [!TIP]
    > Visual Studio 2017부터 이러한 단계를 수행하여 처음으로 프로세스에 연결할 때 **디버그** > **프로세스에 다시 연결**을 선택하여 동일 프로세스에 신속하게 다시 연결할 수 있습니다.

4. **프로세스에 연결** 대화 상자에서 연결할 수 있는 브라우저 인스턴스의 필터링된 목록을 가져옵니다.
    ::: moniker range=">=vs-2019"
    Visual Studio 2019의 **연결 대상** 필드에서 대상 브라우저에 대해 올바른 디버거 **JavaScript(Chrome)** 또는 **JavaScript(Microsoft Edge - Chromium)** 를 선택하고 필터 상자에 **chrome** 또는 **edge**를 입력하여 검색 결과를 필터링합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017의 **연결 대상** 필드에서 **WebKit 코드**를 선택하고 필터 상자에 **chrome**을 입력해 검색 결과를 필터링합니다.
    ::: moniker-end

5. 올바른 호스트 포트(이 예제에서는 localhost)를 사용하여 브라우저 프로세스를 선택하고 **연결**을 선택합니다.

    올바른 브라우저 인스턴스를 선택하는 데 도움이 되도록 포트(예: 1337)가 **제목** 필드에 나타날 수도 있습니다.

    ::: moniker range=">=vs-2019"
    다음 예제에서는 Microsoft Edge(Chromium) 브라우저를 찾는 방법을 보여 줍니다.

    ![프로세스에 연결](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![프로세스에 연결](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM 탐색기와 JavaScript 콘솔이 Visual Studio에서 열릴 때 디버거가 올바르게 연결됐는지 알 수 있습니다. 이러한 디버깅 도구는 크롬 개발자 도구 및 F12 Tools for Microsoft Edge와 유사합니다.
    ::: moniker-end

    > [!TIP]
    > 디버거가 연결되지 않고 “디버그 어댑터를 시작하지 못했습니다” 또는 “프로세스에 연결할 수 없습니다. 현재 상태에서는 작업을 수행할 수 없습니다.”라는 메시지가 표시되는 경우 디버깅 모드로 브라우저를 시작하기 전에 Windows 작업 관리자를 사용하여 대상 브라우저의 모든 인스턴스를 닫습니다. 실행 중인 브라우저 확장 프로그램이 전체 디버그 모드를 방지할 수 있습니다.

6. 중단점이 있는 코드가 이미 실행됐을 수 있기 때문에 브라우저 페이지를 새로 고칩니다. 필요한 경우 작업을 수행하여 중단점이 있는 코드를 실행합니다.

    디버거에서 일시 중지된 동안 변수를 가리키고 디버거 창을 사용하여 앱 상태를 검사할 수 있습니다. 단계별 코드 실행(**F5**, **F10** 및 **F11**)으로 디버거로 이동할 수 있습니다. 기본 디버깅 기능에 대한 자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

    앱 유형, 이전에 수행한 단계 및 브라우저 상태와 같은 기타 요소에 따라 변환 컴파일된 *.js* 파일 또는 소스 파일에서 중단점을 적중할 수 있습니다. 어느 경우든 단계별 코드를 실행하고 변수를 검사할 수 있습니다.

   * TypeScript, JSX 또는 *.vue* 소스 파일에서 코드를 분석해야 하지만 이를 수행할 수 없는 경우 [문제 해결](#troubleshooting_source_maps) 섹션에 설명된 대로 환경이 올바르게 설정되어 있는지 확인합니다.

   * 트랜스파일된 JavaScript 파일(예: *app-bundle.js*)에서 코드를 중단해야 하는데 그럴 수 없는 경우 *filename.js.map* 소스 맵 파일을 제거합니다.

### <a name="troubleshooting_source_maps"></a> 중단점 및 소스 맵 문제 해결

TypeScript 또는 JSX 소스 파일에서 코드를 중단해야 하는데 그럴 수 없는 경우 이전 단계에 설명된 대로 **프로세스에 연결**을 사용하여 디버거를 연결합니다. 환경이 올바르게 설정되었는지 확인합니다.

* 디버그 모드에서 브라우저를 실행할 수 있도록 Chrome 확장 프로그램(작업 관리자 사용)을 비롯한 모든 브라우저 인스턴스를 닫았습니다.
      
* [디버그 모드에서 브라우저를 시작](#prepare_the_browser_for_debugging)해야 합니다.

* 소스 맵 파일에 소스 파일에 대한 올바른 상대 경로가 포함되어 있는지와 Visual Studio 디버거가 소스 파일을 찾지 못하게 하는 *webpack:///* 등의 지원되지 않는 접두사가 포함되지 않았는지 확인합니다. 예를 들어 *webpack:///.app.tsx*와 같은 참조를 *./app.tsx*로 수정할 수 있습니다. 이러한 작업은 테스트에 유용한 소스 맵 파일 또는 사용자 지정 빌드 구성을 통해 수동으로 수행할 수 있습니다. 자세한 내용은 [디버깅에 대한 소스 맵 생성](#generate_source_maps)을 참조하세요.

또는 소스 파일(예: *app.tsx*)에서 코드를 중단해야 하는데 그럴 수 없는 경우 소스 파일에서 `debugger;` 문을 사용하거나 대신 Chrome 개발자 도구(또는 Microsoft Edge의 F12 도구)에서 중단점을 설정합니다.

## <a name="generate_source_maps"></a> 디버깅에 대한 소스 맵 생성

Visual Studio에는 JavaScript 소스 파일에 소스 맵을 사용하고 생성하는 기능이 있습니다. 이는 소스가 TypeScript 또는 Babel과 같은 transpiler에 의해 축소되거나 생성되는 경우에 종종 필요합니다. 사용 가능한 옵션은 프로젝트 형식에 따라 달라집니다.

* Visual Studio의 TypeScript 프로젝트는 기본적으로 소스 맵을 생성합니다. 자세한 내용은 [tsconfig.json 파일을 사용하여 소스 맵 구성](#configure_source_maps)을 참조하세요.

* JavaScript 프로젝트에서 webpack과 같은 번들러와 TypeScript 컴파일러(또는 Babel)와 같은 컴파일러를 사용하여 소스 맵을 생성해야 하며, 이를 프로젝트에 추가할 수 있습니다. TypeScript 컴파일러의 경우 *tsconfig.json* 파일을 추가하고 `sourceMap` 컴파일러 옵션을 설정해야 합니다. 기본 webpack 구성을 사용하여 이 작업을 수행하는 방법을 보여주는 예제는 [React를 사용하여 Node.js 앱 만들기](../javascript/tutorial-nodejs-with-react-and-jsx.md)를 참조하세요.

> [!NOTE]
> 소스 맵을 처음 사용하는 경우 계속하기 전에 [JavaScript 소스 맵 소개](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/)를 읽어보세요. 

소스 맵에 대한 고급 설정을 구성하려면 *tsconfig.json* 또는 TypeScript 프로젝트의 프로젝트 설정을 사용합니다. 그러나 둘 다를 사용하지는 마세요.

Visual Studio를 사용하여 디버깅을 사용하려면 생성된 소스 맵의 소스 파일에 대한 참조가 올바른지 확인해야 합니다(테스트가 필요할 수 있음). 예를 들어 webpack을 사용하는 경우 소스 맵 파일의 참조에는 Visual Studio에서 TypeScript 또는 JSX 소스 파일을 찾을 수 없도록 하는 *webpack:///* 접두사가 포함되어 있습니다. 특히 디버깅을 위해 수정하는 경우 소스 파일에 대한 참조(예: *app.tsx*)는 *webpack:///./app.tsx*와 같은 항목에서 디버깅을 사용하는 *./app.tsx*와 같은 항목으로 변경되어야 합니다(경로는 소스 파일에 상대적임). 다음 예에서는 가장 일반적인 번들 중 하나인 webpack에서 소스 맵을 구성하여 Visual Studio에서 사용하는 방법을 보여 줍니다.

(webpack만 해당) 트랜스파일된 JavaScript 파일이 아닌 JSX 파일의 TypeScript에서 중단점을 설정하는 경우 webpack 구성을 업데이트해야 합니다. 예를 들어 *webpack-config.js*에서 다음 코드를 바꾸어야 할 수 있습니다.

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

이 코드로 바꿉니다.

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Visual Studio에서 클라이언트 쪽 코드의 디버깅을 사용하도록 설정하는 개발 전용 설정입니다.

복잡한 시나리오의 경우 브라우저 도구(**F12**)는 사용자 지정 접두사를 변경할 필요가 없으므로 디버깅에 가장 적합합니다.

### <a name="configure_source_maps"></a> tsconfig.json 파일을 사용하여 소스 맵 구성

*tsconfig.json* 파일을 프로젝트에 추가하면 Visual Studio는 디렉터리 루트를 TypeScript 프로젝트로 처리합니다. 파일을 추가하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **추가 > 새 항목 > TypeScript JSON 구성 파일**을 선택합니다. 다음과 같은 *tsconfig.json* 파일이 프로젝트에 추가됩니다.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>tsconfig.json에 대한 컴파일러 옵션

* **inlineSourceMap**: 각 소스 파일에 대해 별도의 소스 맵을 만드는 대신 소스 맵이 있는 단일 파일을 내보냅니다.
* **inlineSources**: 단일 파일 내에서 소스 맵과 함께 소스를 내보냅니다. *inlineSourceMap* 또는 *sourceMap*을 설정해야 합니다.
* **mapRoot**: 디버거에서 기본 위치 대신 소스 맵( *.map*) 파일을 찾아야 하는 위치를 지정합니다. 런타임 *.map* 파일이 *.js* 파일과 다른 위치에 있어야 하는 경우 이 플래그를 사용합니다. 지정된 위치가 소스 맵에 포함되어 디버거를 *.map* 파일의 위치로 안내합니다.
* **sourceMap**: 해당하는 *.map* 파일을 생성합니다.
* **sourceRoot**: 소스 위치 대신 디버거에서 TypeScript 파일을 찾아야 하는 위치를 지정합니다. 런타임 소스가 디자인 시 위치와 다른 위치에 있어야 하는 경우 이 플래그를 사용합니다. 지정된 위치가 소스 맵에 포함되어 소스 파일이 있는 위치로 디버거를 안내합니다.

컴파일러 옵션에 대한 자세한 내용은 TypeScript Handbook의 [컴파일러 옵션](https://www.typescriptlang.org/docs/handbook/compiler-options.html) 페이지를 확인합니다.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>프로젝트 설정을 사용하여 소스 맵 구성(TypeScript 프로젝트)

프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **프로젝트 > 속성 > TypeScript 빌드 > 디버깅**을 선택하여 프로젝트 속성을 통해 소스 맵 설정을 구성할 수도 있습니다.

이러한 프로젝트 설정을 사용할 수 있습니다.

* **소스 맵 생성**(*tsconfig.json*의 **sourceMap**과 동일): 해당하는 *.map* 파일을 생성합니다.
* **소스 맵의 루트 디렉터리 지정**(*tsconfig.json*의 **mapRoot**와 동일): 생성된 위치 대신 디버거에서 맵 파일을 찾아야 하는 위치를 지정합니다. 런타임 *.map* 파일이 .js 파일과 다른 위치에 배치해야 하는 경우 이 플래그를 사용합니다. 지정된 위치가 소스 맵에 포함되어 맵 파일이 있는 위치로 디버거를 안내합니다.
* **TypeScript 파일의 루트 디렉터리 지정**(*tsconfig.json*의 **sourceRoot**와 동일): 소스 위치 대신 디버거에서 TypeScript 파일을 찾아야 하는 위치를 지정합니다. 런타임 소스 파일이 디자인 시 위치와 다른 위치에 있어야 하는 경우 이 플래그를 사용합니다. 지정된 위치가 소스 맵에 포함되어 소스 파일이 있는 위치로 디버거를 안내합니다.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor(ASP.NET)를 사용하여 동적 파일에 JavaScript 디버그

::: moniker range=">=vs-2019"
Visual Studio 2019부터 Visual Studio는 Chrome 및 Microsoft Edge(Chromium)에 대해서만 디버깅을 지원합니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio는 Chrome 및 Internet Explorer에 대해서만 디버깅 지원을 제공합니다.
::: moniker-end

하지만 Razor 구문(cshtml, vbhtml)으로 생성된 파일에서 중단점을 자동으로 적중할 수 없습니다. 이러한 종류의 파일을 디버그하는 데 사용할 수는 두 가지 방법이 있습니다.

* **중단하려는 곳에 `debugger;` 문을 배치합니다**. 그러면 동적 스크립트 실행을 중지하고 생성되는 동안 즉시 디버깅을 시작합니다.
* **Visual Studio에서 페이지를 로드하고 동적 문서를 엽니다**. 디버깅 중에 동적 파일을 열고, 중단점을 설정하고, 이 메서드가 작동하도록 페이지를 새로 고쳐야 합니다. Chrome 또는 Internet Explorer를 사용하는지에 따라 다음 전략 중 하나를 사용하여 파일을 찾을 수 있습니다.

   Chrome의 경우 **솔루션 탐색기 > 스크립트 문서 > YourPageName**으로 이동합니다.

    > [!NOTE]
    > Chrome을 사용하는 경우 **\<스크립트> 태그 간에 소스를 사용할 수 없음**이라는 메시지가 표시될 수 있습니다. 괜찮습니다. 디버깅을 계속하세요.

   ::: moniker range=">=vs-2019"
   Microsoft Edge(Chromium)의 경우 Chrome과 동일한 절차를 사용합니다.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Internet Explorer의 경우 **솔루션 탐색기 > 스크립트 문서 > Windows Internet Explorer > YourPageName**으로 이동합니다.
   ::: moniker-end

자세한 내용은 [Google Chrome에서 ASP.NET 프로젝트의 클라이언트 쪽 디버깅](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)을 참조하세요.
