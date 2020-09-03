---
title: npm 패키지 관리
description: Visual Studio를 통해 Node.js 패키지 관리자(npm)를 사용하여 패키지를 관리할 수 있습니다.
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 6b53fb34b3cff444e57491f878f8385bdb523c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285051"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio에서 npm 패키지 관리

npm을 사용하면 Node.js 애플리케이션에서 사용할 패키지를 설치하고 관리할 수 있습니다. Visual Studio를 사용하면 쉽게 npm과 상호 작용하고 UI를 통해 또는 직접 npm 명령을 실행할 수 있습니다. npm에 익숙하지 않고 자세히 알아보려면 [npm 설명서](https://docs.npmjs.com/)로 이동합니다.

npm과 Visual Studio의 통합은 프로젝트 형식에 따라 달라집니다.
* [Node.JS](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [폴더 열기(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm에는 프로젝트 루트에 *node_modules* 폴더와 *package.json*이 필요합니다. 앱의 폴더 구조가 다른 경우 Visual Studio를 사용하여 npm 패키지를 관리하려면 폴더 구조를 수정해야 합니다.

## <a name="nodejs-projects"></a>Node.js 프로젝트

Node.js 프로젝트의 경우 아래와 같은 작업을 수행할 수 있습니다.
* [솔루션 탐색기에서 패키지 설치](#npmInstallWindow)
* [솔루션 탐색기에서 설치된 패키지 관리](#solutionExplorer)
* [Node.js 대화형 창에서 `.npm` 명령 사용](#interactive)

이러한 기능은 함께 작동하며 프로젝트 시스템 및 프로젝트의 *package.json* 파일과 동기화됩니다.

### <a name="prerequisites"></a>사전 요구 사항

프로젝트에 npm 지원을 추가하려면 **Node.js development** 워크로드 및 Node.js 런타임이 설치되어 있어야 합니다. 자세한 단계는[Node.js 프로젝트 만들기](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json)를 참조하세요.

> [!NOTE]
> 기존 Node.js 프로젝트의 경우 **기존 Node.js 코드에서** 솔루션 템플릿이나 [폴더 열기(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) 프로젝트 형식을 사용하여 프로젝트에서 npm을 사용하도록 설정합니다.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> 솔루션 탐색기에서 패키지 설치(Node.js)

Node.js 프로젝트의 경우 npm 패키지를 설치하는 가장 쉬운 방법은 npm 패키지 설치 창을 사용하는 것입니다. 이 창에 액세스하려면 프로젝트에서 **npm** 노드를 마우스 오른쪽 단추로 클릭하고 **새 npm 패키지 설치**를 선택합니다.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="솔루션 탐색기에서 새 npm 패키지 설치" border="true":::

이 창에서 패키지를 검색, 옵션 지정 및 설치할 수 있습니다.

![npm 패키지 검색](../javascript/media/search-package.png)

* **종속성 유형** - **표준**, **개발** 및 **선택적** 패키지 간에 선택합니다. 표준은 패키지가 런타임 종속성임을 지정하지만 개발은 패키지가 개발 중에만 필요함을 지정합니다.
* **package.json에 추가** - 권장됩니다. 이 구성 가능 옵션은 사용되지 않습니다.
* **선택한 버전** - 설치하려는 패키지의 버전을 선택합니다.
* **기타 npm 인수** - 다른 표준 npm 인수를 지정합니다. 예를 들어 `@~0.8`과 같은 버전 값을 입력하여 버전 목록에서 사용할 수 없는 특정 버전을 설치할 수 있습니다.

**출력** 창의 **npm** 출력에서 설치 진행률을 볼 수 있습니다. 이 작업에는 약간의 시간이 걸릴 수 있습니다.

![npm 출력](../javascript/media/npm-output.png)

> [!TIP]
> 원하는 범위로 검색 쿼리를 추가하여 범위가 지정된 패키지를 검색할 수 있습니다(예: `@types/mocha`를 입력하여 mocha에 대한 TypeScript 정의 파일을 찾음). TypeScript에 대한 형식 정의를 설치할 때 npm 인수 필드에 `@ts2.6`을 추가하여 대상이 되는 TypeScript 버전을 지정할 수도 있습니다.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>솔루션 탐색기에서 설치된 패키지 관리(Node.js)

npm 패키지는 솔루션 탐색기에 표시됩니다. **npm** 노드 아래에 있는 항목은 *package.json* 파일의 종속성을 모방합니다.

![npm 패키지 검색](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>패키지 상태

* ![설치된 패키지](../javascript/media/installed-npm.png) - package.json에 설치 및 나열
* ![외부 패키지](../javascript/media/extraneous-npm.png) - 설치되었지만 package.json에 명시적으로 나열되지 않음
* ![누락된 패키지](../javascript/media/missing-npm.png) - 설치되지 않았지만 package.json에 나열됨

::: moniker range=">=vs-2019"
**npm** 노드를 마우스 오른쪽 단추로 클릭하여 다음 작업 중 하나를 수행합니다.

* **새 npm 패키지 설치** 새 패키지를 설치하는 UI를 엽니다.
* **npm 패키지 설치** npm 설치 명령을 실행하여 *package.json*에 나열된 모든 패키지를 설치합니다. (`npm install`을 실행합니다.)
* **npm 패키지를 업데이트** *package.json*에 지정된 semver 범위에 따라 패키지를 최신 버전으로 업데이트합니다. (`npm update --save`를 실행합니다.) Semver 범위는 일반적으로 “~” 또는 “^”을 사용하여 지정됩니다. 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

패키지 노드를 마우스 오른쪽 단추로 클릭하여 다음 작업 중 하나를 수행합니다.

* **npm 패키지 설치** npm 설치 명령을 실행하여 *package.json*에 나열된 패키지 버전을 설치합니다. (`npm install`을 실행합니다.)
* **npm 패키지 업데이트** *package.json*에 지정된 semver 범위에 따라 패키지를 최신 버전으로 업데이트합니다. (`npm update --save`를 실행합니다.) Semver 범위는 일반적으로 “~” 또는 “^”을 사용하여 지정됩니다.
* **npm 패키지 제거** 설치된 패키지를 제거하고 *package.json*에서 제거합니다.(`npm uninstall --save`를 실행합니다.)
::: moniker-end
::: moniker range="vs-2017"
패키지 노드 또는 **npm** 노드를 마우스 오른쪽 단추로 클릭하여 다음 작업 중 하나를 수행합니다.
* *package.json*에 나열된 **누락된 패키지 설치**
* 최신 버전으로 **npm 패키지 업데이트**
* *package.json*에서 **패키지 제거** 및 제거
::: moniker-end

>[!NOTE]
> npm 패키지 문제 해결에 대한 도움말은 [문제 해결](#troubleshooting-npm-packages)을 참조하세요.

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Node.js 대화형 창에서 npm 명령 사용(Node.js)

Node.js 대화형 창에서 `.npm` 명령을 사용하여 npm 명령을 실행할 수도 있습니다. 창을 열려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Node.js 대화형 창 열기**를 선택합니다.

창에서 다음과 같은 명령을 사용하여 패키지를 설치할 수 있습니다.

`.npm install azure@4.2.3`

 > [!Tip]
 > 기본적으로 npm은 프로젝트의 홈 디렉터리에서 실행됩니다. 솔루션에 여러 프로젝트가 있는 경우 프로젝트의 이름 또는 경로를 대괄호로 지정합니다.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 프로젝트에 package.json 파일이 없는 경우 `.npm init -y`를 사용하여 기본 항목이 있는 새 package.json 파일을 만듭니다.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core 프로젝트

ASP.NET Core 프로젝트와 같은 프로젝트의 경우 프로젝트에서 npm 지원을 통합하고 npm을 사용하여 패키지를 설치할 수 있습니다.
* [프로젝트에 npm 지원 추가](#npmAdd)
* [package.json을 사용하여 패키지 설치](#npmInstallPackage)

>[!NOTE]
> ASP.NET Core 프로젝트의 경우 npm 대신 [라이브러리 관리자](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) 또는 YARN을 사용하여 클라이언트 쪽 JavaScript 및 CSS 파일을 설치할 수도 있습니다.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> 프로젝트에 npm 지원 추가(ASP.NET Core)

프로젝트에 *package.json* 파일이 포함되어 있지 않다면 프로젝트에 *package.json*을 추가하여 npm 지원을 사용하도록 설정할 수 있습니다.

1. 아직 Node.js를 설치하지 않은 경우 외부 프레임워크 및 라이브러리와의 호환성을 최대화하기 위해 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치하는 것이 좋습니다.

   npm에 Node.js가 필요합니다.

1. *package.json* 파일을 추가하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다. **npm 구성 파일**을 선택하고 기본 이름을 사용하고 **추가**를 클릭합니다.

   ![프로젝트에 package.json 추가](../javascript/media/npm-add-package-json.png)

   npm 구성 파일이 표시되지 않으면 Node.js 개발 도구가 설치되지 않은 것입니다. Visual Studio 설치 관리자를 사용하여 **Node.js 개발** 워크로드를 추가할 수 있습니다. 그런 다음, 이전 단계를 반복합니다.

1. *package.json*의 `dependencies` 또는 `devDependencies` 섹션에 하나 이상의 npm 패키지를 포함합니다. 예를 들어 파일에 다음을 추가할 수 있습니다.

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

파일을 저장하면 Visual Studio가 솔루션 탐색기의 **Dependencies / npm** 노드 아래에 패키지를 추가합니다. 이 노드가 표시되지 않는다면 **package.json**을 마우스 오른쪽 단추로 클릭하고 **패키지 복원**을 선택합니다.

>[!NOTE]
> 일부 시나리오에서는 솔루션 탐색기가 설치된 npm 패키지에 대한 올바른 상태를 표시하지 않을 수도 있습니다. 자세한 내용은 [문제 해결](#troubleshooting-npm-packages)을 참조하세요.

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>package.json을 사용하여 패키지 설치(ASP.NET Core)

npm이 포함된 패키지의 경우 `package.json`을 사용하여 npm 패키지를 구성할 수 있습니다. 솔루션 탐색기에서 npm 노드를 마우스 오른쪽 단추로 클릭하고 **package.json 열기**를 선택합니다.

![npm 패키지 검색](../javascript/media/npm-add-package.png)

*package.json*의 IntelliSense가 npm 패키지의 특정 버전을 선택할 수 있도록 지원합니다.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="npm 패키지 버전 선택" border="true":::

파일을 저장하면 Visual Studio가 솔루션 탐색기의 **Dependencies / npm** 노드 아래에 패키지를 추가합니다. 이 노드가 표시되지 않는다면 **package.json**을 마우스 오른쪽 단추로 클릭하고 **패키지 복원**을 선택합니다.

패키지를 설치하는 데 몇 분 정도 걸릴 수 있습니다. **출력** 창에서 **npm** 출력으로 전환하여 패키지 설치 진행률을 확인하세요.

![npm 출력](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>npm 패키지 문제 해결

* npm에 Node.js가 필요합니다. 아직 Node.js를 설치하지 않은 경우 외부 프레임워크 및 라이브러리와의 호환성을 최대화하기 위해 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치하는 것이 좋습니다.

* Node.js 프로젝트의 경우 npm 지원을 위해 **Node.js 개발** 워크로드를 설치해야 합니다.

* 일부 시나리오에서는 [여기](https://github.com/aspnet/Tooling/issues/479)에 설명된 알려진 문제로 인해 솔루션 탐색기가 설치된 npm 패키지에 대한 올바른 상태를 표시하지 않을 수도 있습니다. 예를 들어 패키지가 설치되었지만 설치되지 않은 것으로 보일 수 있습니다. 대부분의 경우에는 *package.json*을 삭제하고 Visual Studio를 다시 시작한 다음 이 문서의 앞부분에서 설명한 것처럼 *package.json* 파일을 다시 추가하여 솔루션 탐색기를 업데이트할 수 있습니다. 또는 패키지를 설치할 때 npm 출력 창을 사용하여 설치 상태를 확인할 수 있습니다.

* 앱 또는 변환 컴파일 TypeScript 코드를 빌드할 때 오류가 발생하는 경우 잠재적인 오류 원인으로 npm 패키지 비호환성을 확인합니다. 오류를 식별하려면 이 문서의 앞부분에서 설명한 대로 패키지를 설치할 때 npm 출력 창을 확인합니다. 예를 들어 npm 패키지 버전 중 하나 이상이 사용되지 않아 오류를 일으킬 경우 오류를 수정하려면 최신 버전을 설치해야 합니다. *package.json*을 사용하여 npm 패키지 버전을 제어하는 방법에 대한 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

