---
title: 첫 번째 Node.js 앱 만들기
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: 이 빠른 시작에서는 Visual Studio를 사용하여 Node.js 앱 만들기
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386165"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 Node.js 앱 만들기

Visual Studio IDE(통합 개발 환경)에 대한 이 5~10분 분량의 소개에서는 간단한 Node.js 웹앱을 만듭니다.

## <a name="prerequisites"></a>필수 조건

시작하기 전에 Visual Studio를 설치하고 Node.js 환경을 설정합니다.

### <a name="install-visual-studio"></a>Visual Studio 설치

::: moniker range=">=vs-2019"
아직 Visual Studio 2019를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end
::: moniker range="vs-2017"
아직 Visual Studio 2017을 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Node.js 환경 설정

Visual Studio를 사용하면 Node.js 개발에 자주 사용되는 도구를 설치하고 환경을 설정하는 데 도움이 됩니다.

1. Visual Studio에서 **도구** > **도구 및 기능 가져오기** 로 이동합니다.

1. Visual Studio 설치 관리자에서 **Node.js 개발** 워크로드를 선택하고 **수정** 을 선택하여 워크로드를 다운로드 및 설치합니다.

    ![Visual Studio 설치 관리자의 Node.js 워크로드](../ide/media/quickstart-nodejs-workload.png)

1. [Node.js 런타임](https://nodejs.org/en/download/)의 LTS 버전을 설치합니다. 외부 프레임워크 및 라이브러리와의 호환성을 위해 LTS 버전을 사용하는 것이 좋습니다.

    Node.js는 32비트 및 64비트 아키텍처용으로 빌드되어 있으나 Node.js 설치 프로그램은 한 번에 하나의 설치된 버전만 지원합니다.

1. Visual Studio가 설치된 런타임을 검색하지 못하는 경우(보통은 문제없이 검색합니다) 프로젝트가 설치된 런타임을 참조하도록 구성합니다.

   1. [프로젝트를 만든](#create-your-app-project) 후에 프로젝트 노드를 마우스 오른쪽 단추로 클릭합니다.

   1. **속성** 을 선택하고 **Node.exe 경로** 를 설정합니다. Node.js의 전역 설치를 사용하거나 각 Node.js 프로젝트에서 로컬 인터프리터의 경로를 지정할 수 있습니다.

## <a name="create-your-app-project"></a>앱 프로젝트 만들기

1. [Node.js 런타임](https://nodejs.org/en/download/)의 LTS 버전을 아직 설치하지 않았다면 설치합니다. 자세한 내용은 [필수 조건](#prerequisites)을 참조하세요.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"

    1. **Esc** 키를 눌러 시작 창을 닫습니다.

    1. **Ctrl + Q** 를 눌러 검색 상자를 열고 **Node.js** 를 입력합니다.

    1. **빈 Node.js 웹 애플리케이션(JavaScript)** 을 선택합니다. 대화 상자에서 **만들기** 를 선택합니다.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

    1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **JavaScript** 를 확장하고 **Node.js** 를 선택합니다.

    1. 가운데 창에서 **빈 Node.js 웹 애플리케이션** 을 선택하고 **확인** 을 선택합니다.

    ::: moniker-end
    
    **빈 Node.js 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio가 프로젝트를 만들고 엽니다. 왼쪽 편집기에 프로젝트의 *server.js* 파일이 열립니다.

## <a name="explore-the-ide"></a>IDE 탐색

1. 오른쪽 창에서 **솔루션 탐색기** 를 살펴봅니다.

   ![솔루션 탐색기](../ide/media/quickstart-nodejs-solution-explorer.png)

   - 굵게 강조 표시된 항목이 프로젝트입니다. 프로젝트를 설정할 때 지정한 이름이 적용되어 있습니다. 디스크에서 이 프로젝트는 프로젝트 폴더의 *.njsproj* 파일로 표시됩니다.

   - 최상위 수준은 기본적으로 프로젝트와 이름이 동일한 솔루션입니다. 디스크에서 *.sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다.

   - **npm** 노드에 설치된 npm 패키지가 표시됩니다. npm 노드를 마우스 오른쪽 단추로 클릭하고 대화 상자를 사용하여 npm 패키지를 검색 및 설치할 수 있습니다.

1. 명령 프롬프트에서 npm 패키지 또는 Node.js 명령을 설치하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **여기서 명령 프롬프트 열기** 를 선택합니다.

   ![노드 dot j s 명령 프롬프트](../ide/media/quickstart-nodejs-command-prompt.png)

1. 소스 코드로 테스트 이동하려면 열려 있는 *server.js* 파일에서 **http.createServer** 를 선택하고 **F12** 를 누르거나 상황에 맞는 메뉴(마우스 오른쪽 단추 클릭)에서 **정의로 이동** 을 선택합니다. 이 명령을 실행하면 *http.d.ts* 에 있는 `createServer` 함수의 정의로 이동합니다.

   ![[정의로 이동] 바로 가기 메뉴](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js* 로 돌아가서 `res.end('Hello World\n');` 코드 줄을 찾습니다. 코드를 다음과 같이 수정합니다.

    `res.end('Hello World\n' + res.connection.`

    **connection.** 을 입력하면 IntelliSense가 코드 입력을 자동 완성하는 옵션을 제공합니다.

   ![IntelliSense 자동 완성](../ide/media/quickstart-nodejs-intellisense.png)

1. **localPort** 를 선택하고 **);** 을 입력하여 문을 완성합니다.

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>앱 실행

1. **Ctrl+F5**(또는 **디버그** > **디버깅하지 않고 시작**)를 눌러서 앱을 실행합니다. 
 
   앱이 브라우저에서 열립니다.

1. 브라우저에 "Hello World" 메시지와 로컬 포트 번호가 표시되는지 확인합니다.

축하합니다! Visual Studio를 사용하여 간단한 Node.js 앱을 만들었습니다. 자세히 알아보려면 목차의 **자습서** 섹션을 살펴보세요.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [앱을 Linux App Service에 배포](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js 및 Express에 대한 자습서](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js 및 React에 대한 자습서](../javascript/tutorial-nodejs-with-react-and-jsx.md)
