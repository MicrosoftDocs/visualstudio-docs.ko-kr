---
title: 첫 번째 Node.js 앱 만들기
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ecd65c0348ac16a2097061726e3896961ae04482
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617054"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 Node.js 앱 만들기

Visual Studio IDE(통합 개발 환경)에 대한 이 5~10분 분량의 소개에서는 간단한 Node.js 웹 애플리케이션을 만듭니다.

## <a name="prerequisites"></a>사전 요구 사항

* Node.js 개발 워크로드와 Visual Studio가 설치되어 있어야 합니다.

    ::: moniker range=">=vs-2019"
    아직 Visual Studio 2019를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    아직 Visual Studio 2017을 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end

    워크로드는 설치해야 하지만 Visual Studio는 이미 있는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **Node.js 개발** 워크로드를 선택한 다음 **수정** 을 선택합니다.

    ![VS 설치 관리자에서 Node.js 워크로드](../ide/media/quickstart-nodejs-workload.png)

* Node.js 런타임을 설치해야 합니다.

    아직 설치하지 않은 경우 외부 프레임워크 및 라이브러리와의 호환성을 최대화하기 위해 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치하는 것이 좋습니다. Node.js는 32비트 및 64비트 아키텍처용으로 빌드됩니다. Node.js 워크로드에 포함된 Visual Studio의 Node.js 도구는 두 버전을 모두 지원합니다. 하나만 필요하며 Node.js 설치 관리자는 한 번에 하나의 설치만 지원합니다.
    
    일반적으로, 설치된 Node.js 런타임은 Visual Studio에서 자동으로 검색됩니다. 설치된 런타임이 검색되지 않으면 속성 페이지에서 설치된 런타임을 참조하도록 프로젝트를 구성할 수 있습니다(프로젝트를 만든 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하여 **속성** 을 선택하고 **Node.exe 경로** 를 설정합니다). Node.js의 전역 설치를 사용하거나 각 Node.js 프로젝트에서 로컬 인터프리터 경로를 지정할 수 있습니다. 

## <a name="create-a-project"></a>프로젝트 만들기

먼저 Node.js 웹 애플리케이션 프로젝트를 만듭니다.

1. Node.js 런타임이 아직 설치되어 있지 않으면 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치합니다.

    자세한 내용은 필수 조건을 참조하세요.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q** 를 입력하여 검색 상자를 열고 **Node.js** 를 입력한 다음, **새 빈 Node.js 웹 애플리케이션 프로젝트 만들기**(JavaScript)를 선택합니다. 표시되는 대화 상자에서 **만들기** 를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **JavaScript** 를 확장한 다음, **Node.js** 를 선택합니다. 가운데 창에서 **빈 Node.js 웹 애플리케이션** 을 선택한 후 **확인** 을 선택합니다.
    ::: moniker-end
    **빈 Node.js 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio에서 새 솔루션을 만들고 프로젝트를 엽니다. *server.js* 가 왼쪽 창의 편집기에서 열립니다.

## <a name="explore-the-ide"></a>IDE 탐색

1. 오른쪽 창에서 **솔루션 탐색기** 를 살펴봅니다.

   ![솔루션 탐색기](../ide/media/quickstart-nodejs-solution-explorer.png)

   - 굵게 강조 표시된 것은 **새 프로젝트** 대화 상자에서 지정한 이름을 사용하는 프로젝트입니다. 디스크에서 이 프로젝트는 프로젝트 폴더의 *.njsproj* 파일로 표시됩니다.

   - 최상위 수준은 기본적으로 프로젝트와 이름이 동일한 솔루션입니다. 디스크에서 *.sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다.

   - npm 노드에는 설치된 npm 패키지가 있으면 표시됩니다. npm 노드를 마우스 오른쪽 버튼으로 클릭하고 대화 상자를 사용하여 npm 패키지를 검색하고 설치할 수 있습니다.

1. 명령 프롬프트에서 npm 패키지 또는 Node.js 명령을 설치하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **여기서 명령 프롬프트 열기** 를 선택합니다.

   ![Node.js 명령 프롬프트](../ide/media/quickstart-nodejs-command-prompt.png)

1. 편집기(왼쪽 창)의 *server.js* 파일에서 `http.createServer`를 선택한 후 **F12** 키를 누르거나 상황에 맞는 메뉴에서(마우스 오른쪽 단추 클릭) **정의로 이동** 을 선택합니다. 이 명령을 실행하면 *index.d.ts* 에 있는 `createServer` 함수에 대한 정의가 표시됩니다.

   ![[정의로 이동] 바로 가기 메뉴](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js* 로 돌아간 다음, 이 코드 줄, `res.end('Hello World\n');`의 문자열 끝 부분에 커서를 놓고 다음과 같이 수정합니다.

    `res.end('Hello World\n' + res.connection.`

    `connection.`을 입력한 부분에 IntelliSense가 코드 입력을 자동 완성하는 옵션을 제공합니다.

   ![IntelliSense 자동 완성](../ide/media/quickstart-nodejs-intellisense.png)

1. **localPort** 를 선택한 다음 `);`을 입력하고 명령문을 완성하면 다음과 같이 표시됩니다.

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>애플리케이션 실행

1. **Ctrl**+**F5**(또는 **디버그 &gt; 디버깅하지 않고 시작**)를 눌러서 애플리케이션을 실행합니다. 앱이 브라우저에서 열립니다.

1. 브라우저 창에 "Hello World"와 로컬 포트 번호가 표시됩니다.

1. 웹 브라우저를 닫습니다.

Visual Studio IDE 및 Node.js로 시작한 이 빠른 시작을 완료한 것을 축하합니다. 해당 기능을 보다 자세히 알아보려면 목차에서 **자습서** 섹션에 있는 자습서를 읽어보세요.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [앱을 Linux App Service에 배포](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js 및 Express에 대한 자습서](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js 및 React에 대한 자습서](../javascript/tutorial-nodejs-with-react-and-jsx.md)