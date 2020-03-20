---
title: '빠른 시작: 첫 번째 Vue.js 앱 만들기'
description: 이 빠른 시작에서는 Visual Studio용 Node.js 도구를 사용하여 Visual Studio에서 Vue.js 앱을 만듭니다.
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a1995353d00f9e48811f388e1d853c93850b85f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235108"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 Vue.js 앱 만들기

Visual Studio IDE(통합 개발 환경)에 대한 이 5~10분 분량의 소개에서는 간단한 Vue.js 웹 애플리케이션을 만들고 실행할 것입니다.

> [!IMPORTANT]
> 이 문서에서는 Visual Studio 2017 버전 15.8부터 사용할 수 있는 Vue.js 템플릿이 필요합니다.

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

    아직 설치하지 않은 경우 외부 프레임워크 및 라이브러리와의 호환성을 최대화하기 위해 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치하는 것이 좋습니다. Node.js는 32비트 및 64비트 아키텍처용으로 빌드됩니다. Node.js 워크로드에 포함된 Visual Studio의 Node.js 도구는 두 버전을 모두 지원합니다. 하나만 필요하며 Node.js 설치 관리자는 한 번에 하나의 설치만 지원합니다.
    
    일반적으로, 설치된 Node.js 런타임은 Visual Studio에서 자동으로 검색됩니다. 설치된 런타임이 검색되지 않으면 속성 페이지에서 설치된 런타임을 참조하도록 프로젝트를 구성할 수 있습니다(프로젝트를 만든 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하여 **속성**을 선택하고 **Node.exe 경로**를 설정합니다). Node.js의 전역 설치를 사용하거나 각 Node.js 프로젝트에서 로컬 인터프리터 경로를 지정할 수 있습니다. 

## <a name="create-a-project"></a>프로젝트 만들기

먼저 Vue.js 웹 애플리케이션 프로젝트를 만듭니다.

1. Node.js 런타임이 아직 설치되어 있지 않으면 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치합니다.

    자세한 내용은 필수 조건을 참조하세요.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl+Q**를 입력하여 검색 상자를 열고, **Basic Vue.js**를 입력한 다음, **Basic Vue.js 웹 애플리케이션**(JavaScript 또는 TypeScript)을 선택합니다. 표시되는 대화 상자에서 **basic-vuejs**의 이름을 선택한 다음, **만들기**를 선택합니다.

    ![Vue.js 템플릿](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **JavaScript** 또는 **TypeScript**를 확장한 다음, **Node.js**를 선택합니다. 가운데 창에서 **기본 Vue.js 웹 애플리케이션**을 선택하고 **basic-vuejs**의 이름을 입력한 다음, **확인**을 선택합니다.

    ![Vue.js 템플릿](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **기본 Vue.js 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio가 새 프로젝트를 만듭니다. 새 프로젝트가 솔루션 탐색기(오른쪽 창)에 열립니다.

1. 애플리케이션에 필요한 npm 패키지 설치 진행률은 출력 창(아래쪽 창)을 확인합니다.

1. 솔루션 탐색기에서 **npm** 노드를 열고 나열된 npm 패키지가 모두 설치되었는지 확인합니다.

    패키지가 누락된(느낌표 아이콘) 경우는 **npm** 노드를 마우스 오른쪽 버튼으로 클릭하고 **누락된 npm 패키지 설치**를 선택합니다.

## <a name="explore-the-ide"></a>IDE 탐색

1. 오른쪽 창에서 **솔루션 탐색기**를 살펴봅니다.

     ![Vue.js 솔루션](../javascript/media/vuejs-solution.png)

   - 굵게 강조 표시된 것은 **새 프로젝트** 대화 상자에서 지정한 이름을 사용하는 프로젝트입니다. 디스크에서 이 프로젝트는 프로젝트 폴더의 .*njsproj* 파일로 표시됩니다.

   - 최상위 수준은 기본적으로 프로젝트와 이름이 동일한 솔루션입니다. 디스크에서 .*sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다.

   - **npm** 노드에는 설치된 모든 npm 패키지가 표시됩니다. npm 노드를 마우스 오른쪽 버튼으로 클릭하고 대화 상자를 사용하여 npm 패키지를 검색하고 설치할 수 있습니다.

2. npm 패키지를 설치하거나 명령 프롬프트에서 Node.js 명령을 실행하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **여기서 명령 프롬프트 열기**를 선택합니다.

## <a name="add-a-vue-file-to-the-project"></a>프로젝트에 .vue 파일 추가

1. 솔루션 탐색기에서 *src/components* 폴더와 같은 폴더를 마우스 오른쪽 단추로 클릭한 다음, **추가** > **새 항목**을 선택합니다.

1. **JavaScript Vue 단일 파일 구성 요소** 또는 **TypeScript Vue 단일 파일 구성 요소** 중 하나를 선택하고 **추가**를 클릭합니다.

    Visual Studio가 새 파일을 프로젝트에 추가합니다.

## <a name="build-the-project"></a>프로젝트 빌드

1. (TypeScript 프로젝트에만 해당) Visual Studio에서 **빌드** > **솔루션 정리**를 선택합니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에 포함된 TypeScript 템플릿에서 이 단계를 건너뜁니다.
    ::: moniker-end

1. 그런 다음, **빌드** > **솔루션 빌드**를 선택하여 프로젝트를 빌드합니다. 빌드 결과를 보려면 **출력** 창을 확인하고 **출력 보기** 목록에서 **빌드**를 선택합니다.

    JavaScript Vue.js 프로젝트 템플릿(및 이전 버전의 TypeScript 템플릿)은 빌드 후 이벤트를 구성하여 `build` npm 스크립트를 사용합니다. 이 설정을 수정하려면 Windows Explorer에서 프로젝트 파일( *\<projectname\>.njsproj*)을 열고 다음 코드 줄을 찾습니다.

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>애플리케이션 실행

1. **Ctrl**+**F5**(또는 **디버그 &gt; 디버깅하지 않고 시작**)를 눌러서 애플리케이션을 실행합니다.

   콘솔에 *개발 서버 시작*이라는 메시지가 표시됩니다.

   그런 다음, 앱이 브라우저에서 열립니다.
   
   실행 중인 앱이 표시되지 않으면 페이지를 새로 고칩니다.

   ![브라우저에서 실행 중인 Vue.js 앱](../javascript/media/vuejs-running-app.png)

1. 웹 브라우저를 닫습니다.

이 빠른 시작을 완료한 것을 축하 드립니다! Vue.js로 Visual Studio IDE를 사용하는 데 도움이 되었기를 바랍니다. 해당 기능을 보다 자세히 알아보려면 목차에서 **자습서** 섹션에 있는 자습서를 읽어보세요.

## <a name="next-steps"></a>다음 단계

- [Node.js 및 Express에 대한 자습서](tutorial-nodejs.md) 살펴보기
- [Node.js 및 React에 대한 자습서](tutorial-nodejs-with-react-and-jsx.md) 살펴보기
- [앱을 Linux App Service에 배포](../javascript/publish-nodejs-app-azure.md)