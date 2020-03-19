---
title: Node.js를 사용하여 Vue.js 앱 만들기
description: Vue.js 프레임워크를 사용하여 Visual Studio에서 Node.js 애플리케이션을 만들 수 있습니다.
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: af781f5735a3539d8b0e2d098bb9252bc60193fc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "70180273"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Visual Studio용 Node.js 도구를 사용하여 Vue.js 애플리케이션 만들기

Visual Studio는 JavaScript 또는 TypeScript로 [Vue.js](https://vuejs.org/) 프레임워크를 사용한 앱 개발을 지원합니다.

Visual Studio에서 Vue.js 애플리케이션을 개발할 때 다음과 같은 새로운 기능이 지원됩니다.

* *.vue* 파일에서 스크립트, 스타일 및 템플릿 블록에 대한 지원
* *.vue* 파일에서 `lang` 특성 인식
* Vue.js 프로젝트 및 파일 템플릿

## <a name="prerequisites"></a>사전 요구 사항

* **Node.js 개발** 워크로드와 Visual Studio 2017 버전 15.8 이상 버전이 설치되어 있어야 합니다.

    > [!IMPORTANT]
    > 이 문서에서는 Visual Studio 2017 버전 15.8부터만 사용할 수 있는 기능이 필요합니다.

    ::: moniker range=">=vs-2019"
    필요한 버전이 아직 설치되어 있지 않은 경우 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)를 설치하세요.
    ::: moniker-end
    ::: moniker range="vs-2017"
    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)  페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end

    워크로드는 설치해야 하지만 Visual Studio는 이미 있는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **Node.js 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

* ASP.NET Core 프로젝트를 만들려면 ASP.NET 및 웹 개발 및 .NET Core 플랫폼 간 개발 워크로드를 설치해야 합니다.

* Node.js 런타임을 설치해야 합니다.

    아직 설치되지 않은 경우 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치합니다. 일반적으로, 설치된 Node.js 런타임은 Visual Studio에서 자동으로 검색됩니다. 설치된 런타임에서 검색되지 않을 경우 속성 페이지에서 설치된 런타임을 참조하도록 프로젝트를 구성할 수 있습니다. (프로젝트를 만든 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.)

## <a name="create-a-vuejs-project-using-a-template"></a>템플릿을 사용하여 Vue.js 프로젝트 만들기

새 Vue.js 템플릿을 사용하여 새 프로젝트를 만들 수 있습니다. 템플릿 사용은 시작을 위한 가장 쉬운 방법입니다. 자세한 단계는 [Visual Studio를 사용하여 첫 번째 Vue.js 앱 만들기](../javascript/quickstart-vuejs-with-nodejs.md)를 참조하세요.

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core 및 Vue CLI를 사용하여 Vue.js 프로젝트 만들기

Vue.js는 빠르게 프로젝트를 스캐폴딩하기 위한 공식 CLI를 제공합니다. CLI를 사용하여 애플리케이션을 만들려는 경우 이 문서의 단계를 수행하여 개발 환경을 설정합니다.

> [!IMPORTANT]
> 이러한 단계는 사용자가 Vue.js 프레임워크를 사용한 경험이 있다고 가정합니다. 그렇지 않은 경우 [Vue.js](https://vuejs.org/)를 방문하여 프레임워크에 대해 자세히 알아보세요.

### <a name="create-a-new-aspnet-core-project"></a>새 ASP.NET Core 프로젝트 만들기

이 예제에서는 빈 ASP.NET Core 애플리케이션(C#)을 사용합니다. 그러나 다양한 프로젝트 및 프로그래밍 언어 중에서 선택할 수 있습니다.

#### <a name="create-an-empty-project"></a>빈 프로젝트 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl+Q**를 입력하여 검색 상자를 열고 **asp.net**을 입력한 후 **새 ASP.NET Core 웹 애플리케이션 만들기**를 선택합니다. 표시되는 대화 상자에서 **클라이언트 앱**의 이름을 선택한 다음, **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 을 확장한 후 **웹**을 선택합니다. 가운데 창에서 **ASP.NET Core 웹 애플리케이션**을 선택하고 **클라이언트 앱**의 이름을 입력한 다음, **확인**을 선택합니다.
    ::: moniker-end

    **ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않는 경우 먼저 **ASP.NET 및 웹 개발** 워크로드 및 .**NET Core** 개발 워크로드를 설치해야 합니다. 워크로드를 설치하려면 **새 프로젝트**(**파일** > **새로 만들기** > **프로젝트**를 선택) 대화 상자의 왼쪽 창에서 **Visual Studio 설치 관리자 열기** 링크를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. 필요한 워크로드를 선택합니다.

1. **비어 있음**을 선택한 다음, **확인**을 클릭합니다.

    Visual Studio에서 프로젝트를 만들고 솔루션 탐색기에서 열립니다(오른쪽 창).

#### <a name="configure-the-project-startup-file"></a>프로젝트 시작 파일 구성

* *./Startup.cs* 파일을 열고, 구성 메서드에 다음 줄을 추가합니다.

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>vue CLI 설치

vue cli npm 모듈을 설치하려면 명령 프롬프트를 열고 버전 3.0인 경우(현재는 베타) `npm install --g vue-cli` 또는 `npm install -g @vue/cli`를 입력합니다.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>vue CLI를 사용하여 새 클라이언트 애플리케이션 스캐폴드

1. 명령 프롬프트로 이동한 후 현재 디렉터리를 프로젝트 루트 폴더로 변경합니다.

1. `vue init webpack client-app`을 입력하고 추가 질문에 대답하라는 메시지가 나타나면 단계를 수행합니다.

    > [!NOTE]
    >  ‘.vue’ 파일의 경우 변환을 수행하려면 WebPack 또는 유사한 프레임워크를 로더와 함께 사용해야 합니다. TypeScript 및 Visual Studio는 *.vue* 파일을 컴파일하는 방법을 모릅니다. 묶음의 경우도 마찬가지로, TypeScript는 ES2015 모듈(즉, `import` 문과 `export` 문)을 브라우저에서 로드할 단일 최종 *.js* 파일로 변환하는 방법을 모릅니다. 이 경우도 WebPack이 가장 적합한 옵션입니다. 이 프로세스를 Visual Studio 내에서 MSBuild를 사용해 구동하려면 Visual Studio 템플릿에서 시작해야 합니다. 현재 Vue.js 개발을 위해 기본 제공되는 ASP.NET 템플릿이 없습니다.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>webpack 구성을 수정하여 wwwroot로 빌드된 파일 출력

* *./client-app/config/index.js* 파일을 열고 `build.index` 및 `build.assetsRoot`를 wwwroot 경로로 변경합니다.

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>빌드가 트리거될 때마다 프로젝트가 클라이언트 앱을 빌드하도록 지시

1. Visual Studio에서 **프로젝트** > **속성** > **이벤트 빌드**로 이동합니다.

1. **빌드 전 이벤트 명령줄**에서 `npm --prefix ./client-app run build`를 입력합니다.

#### <a name="configure-webpacks-output-module-names"></a>webpack의 출력 모듈 이름 구성

* *./client-app/build/webpack.base.conf.js* 파일을 열고 다음 속성을 출력 속성에 추가합니다.

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI를 사용하여 TypeScript 지원 추가

이러한 단계는 vue-cli 3.0이 필요합니다. 현재는 베타 버전입니다.

1. 명령 프롬프트로 이동한 후 현재 디렉터리를 프로젝트 루트 폴더로 변경합니다.

1. `vue create client-app`을 입력한 다음, **기능을 수동으로 선택**을 선택합니다.

1. **Typescript**를 선택한 다음, 다른 원하는 옵션을 선택합니다.

1. 나머지 단계를 수행하고 질문에 답합니다.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript용 Vue.js 프로젝트 구성

1. *./client-app/tsconfig.json* 파일을 열고 `noEmit:true`를 컴파일러 옵션에 추가합니다.

    이 옵션을 설정하면 Visual Studio에서 빌드할 때마다 프로젝트가 복잡해지는 것을 방지합니다.

1. 다음으로 *./client-app/* 에서 *vue.config.js* 파일을 만들고 다음 코드를 추가합니다.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    위의 코드는 webpack을 구성하고 wwwroot 폴더를 설정합니다.

#### <a name="build-with-vue-cli-30"></a>vue-cli 3.0을 사용하여 빌드

vue-cli 3.0의 알 수 없는 문제로 인해 빌드 프로세스를 자동화하지 못할 수 있습니다. wwwroot 폴더를 새로 고치려고 할 때마다 클라이언트 앱 폴더에서 `npm run build` 명령을 실행해야 합니다.

또는 ASP.NET 프로젝트 속성을 사용하여 빌드 전 이벤트로 vue-cli 3.0 프로젝트를 빌드할 수 있습니다. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음, **빌드** 탭의 **빌드 전 이벤트 명령줄** 텍스트 상자에 다음 명령을 포함합니다.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>제한 사항

* `lang` 특성은 JavaScript 및 TypeScript 언어만 지원합니다. 사용 가능한 값은 js, jsx, ts 및 tsx입니다.
* `lang` 특성은 템플릿 또는 스타일 태그를 사용하여 작동하지 않습니다.
* *.vue* 파일의 스크립트 블록 디버깅은 전처리된 특성으로 인해 지원되지 않습니다.
* TypeScript는 *.vue* 파일을 모듈로 인식하지 않습니다. TypeScript에게 *.vue* 파일을 설명하는 다음과 같은 코드를 포함하는 파일이 필요합니다(vue-cli 3.0 템플릿에는 이미 이 파일이 포함되어 있음).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* 프로젝트 속성에서 빌드 전 이벤트로서의 `npm run build` 명령 실행은 vue-cli 3.0을 사용하는 경우 작동하지 않습니다.

## <a name="see-also"></a>참조

- [Vue 시작 가이드입니다](https://vuejs.org/v2/guide).
- [Vue CLI 프로젝트입니다](https://github.com/vuejs/vue-cli).
- [Webpack 구성 설명서입니다](https://webpack.js.org/configuration/).
