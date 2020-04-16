---
title: Node.js 및 Express 앱 만들기
description: 이 자습서에서는 Visual Studio용 Node.js 도구를 사용하여 앱을 만듭니다.
ms.date: 09/24/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 260bc6ff6eb2d0bfbf0b9abd19062892c358728a
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224526"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>자습서: Visual Studio에서 Node.js 및 Express 앱 만들기

Node.js 및 Express를 사용하여 Visual Studio를 개발하기 위한 이 자습서에서는 Node.js 웹 애플리케이션을 만들고, 일부 코드를 추가하며, IDE의 일부 기능을 살펴보고, 앱을 실행합니다. 

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.
> [!div class="checklist"]
> * Node.js 프로젝트 만들기
> * 일부 코드를 추가합니다.
> * IntelliSense를 사용하여 코드 편집
> * 앱 실행
> * 디버거에서 중단점에 도달

## <a name="before-you-begin"></a>시작하기 전 주의 사항

다음은 몇 가지 주요 개념을 소개하는 빠른 FAQ입니다.

### <a name="what-is-nodejs"></a>Node.js란?

Node.js는 JavaScript 서버 쪽을 실행하는 서버 쪽 JavaScript 런타임 환경입니다.

### <a name="what-is-npm"></a>npm이란?

npm는 Node.js를 위한 기본 패키지 관리자입니다. 패키지 관리자는 프로그래머가 Node.js 라이브러리의 소스 코드를 쉽게 게시 및 공유하게 하며, 라이브러리의 설치, 업데이트 및 제거를 간소화하도록 설계되었습니다.

### <a name="what-is-express"></a>Express란?

Express는 웹 애플리케이션 프레임워크로, Node.js가 웹 애플리케이션을 빌드하기 위한 서버 프레임워크로 사용됩니다. Express를 사용하면 Pug(이전의 Jade)와 같이 UI를 만들 수 있는 프런트 엔드 프레임워크를 다양하게 선택할 수 있습니다. 이 자습서에서는 Pug가 사용되었습니다.

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

    이 자습서는 Node.js 8.10.0를 사용하여 테스트했습니다.

## <a name="create-a-new-nodejs-project"></a>새 Node.js 프로젝트 만들기

Visual Studio는 *프로젝트*에서 단일 애플리케이션에 대한 파일을 관리합니다. 프로젝트에는 소스 코드, 리소스 및 구성 파일이 포함됩니다.

이 자습서에서는 Node.js 및 Express 앱에 대한 코드를 포함한 간단한 프로젝트부터 시작합니다.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **Node.js**를 입력한 다음, **새 기본 Azure Node.js Express 4 애플리케이션 만들기**(JavaScript)를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **JavaScript**를 확장한 다음, **Node.js**를 선택합니다. 가운데 창에서 **기본 Azure Node.js Express 4 애플리케이션**을 선택한 후 **확인**을 선택합니다.
    ::: moniker-end
    **기본 Azure Node.js Express 4 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio가 새 솔루션을 만들고 오른쪽 창에서 프로젝트를 엽니다. *app.js* 프로젝트 파일이 편집기에 열립니다(왼쪽 창).

    ![프로젝트 구조](../javascript/media/tutorial-project-structure.png)

    (1) **bold** 강조 표시된 것은 **새 프로젝트** 대화 상자에서 지정한 이름을 사용하는 프로젝트입니다. 파일 시스템에서 이 프로젝트는 프로젝트 폴더의 *.njsproj* 파일로 표시됩니다. 속성을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하여 프로젝트와 연결된 환경 변수와 속성을 설정할 수 있습니다. 프로젝트 파일이 Node.js 프로젝트 소스에 사용자 지정 변경을 하지 않으므로 다른 개발 도구와 라운드트립을 수행할 수 있습니다.

    (2) 최상위 수준은 기본적으로 프로젝트와 이름이 동일한 솔루션입니다. 디스크에서 *.sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다.

    (3) npm 노드에는 설치된 모든 npm 패키지가 표시됩니다. 대화 상자를 사용하여 npm 패키지를 검색하고 설치하거나 *package.json*에서 설정 및 npm 노드에서 마우스 오른쪽 단추로 클릭 옵션을 사용하여 업데이트 패키지를 설치 및 업데이트하려면 Npm 노드를 마우스 오른쪽 단추로 클릭할 수 있습니다.

    (4) *package.json*은 로컬로 설치된 패키지에 대한 패키지 버전 및 종속성을 관리하기 위해 npm에서 사용하는 파일입니다. 이 파일에 대한 자세한 내용은 [package.json configuration](../javascript/configure-packages-with-package-json.md)을 참조하세요.

    (5) *app.js*와 같은 프로젝트 파일은 프로젝트 노드 아래 표시됩니다. *app.js*는 프로젝트 시작 파일이므로 **굵게** 표시됩니다. 프로젝트에서 파일을 마우스 오른쪽 단추로 클릭하고 **Node.js 시작 파일로 설정**을 선택하여 시작 파일을 설정할 수 있습니다.

1. **npm** 노드를 열고 모든 필수 npm 패키지가 존재하는지 확인합니다.

    패키지가 누락된(느낌표 아이콘) 경우는 **npm** 노드를 마우스 오른쪽 버튼으로 클릭하고 **누락된 npm 패키지 설치**를 선택합니다.

## <a name="add-some-code"></a>일부 코드를 추가합니다.

애플리케이션은 프런트 엔드 JavaScript 프레임워크에 대해 Pug를 사용합니다. Pug은 HTML로 컴파일되는 간단한 표시 코드를 사용합니다. (Pug은 *app.js*에서 뷰 엔진으로 설정됩니다. *app.js*에서 뷰 엔진을 설정하는 코드는 `app.set('view engine', 'pug');`입니다.)

1. 솔루션 탐색기(오른쪽 창)에서 Views 폴더를 연 다음, *index.pug*를 엽니다.

1. 콘텐츠를 다음 표시로 바꿉니다.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    앞의 코드는 제목 및 환영 메시지가 있는 HTML 페이지를 동적으로 생성하기 위해 사용됩니다. 페이지에는 단추를 누를 때마다 변경되는 이미지를 표시하는 코드도 포함됩니다.

1. Routes 폴더에서 *index.js*를 엽니다.

1. `router.get` 호출 앞에 다음 코드를 추가합니다.

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    이 코드는 동적으로 생성된 HTML 페이지에 전달할 데이터 개체를 만듭니다.

1. `router.get` 함수 호출을 다음 코드로 바꿉니다.

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    앞의 코드는 Express 라우터 개체를 사용하여 현재 페이지를 설정하고 페이지를 렌더링하여 제목 및 데이터 개체를 페이지에 전달합니다. *index.pug* 파일은 *index.js*가 실행될 때 로드될 페이지로 여기에 지정됩니다. *index.js*는 *app.js* 코드에서 기본 경로로 구성됩니다(표시되지 않음).

    Visual Studio의 여러 기능을 보여주기 위해 `res.render`가 포함된 코드 줄에 의도적인 오류가 있습니다. 앱을 실행하기 전에 오류를 해결해야 합니다. 다음 섹션에서 설명합니다.

## <a name="use-intellisense"></a>IntelliSense 사용

IntelliSense는 코드를 작성할 때 지원하는 Visual Studio 도구입니다.

1. *index.js*에서 `res.render`을 포함한 코드 줄으로 이동합니다.

1. `data` 문자열 뒤에 커서를 놓고 `: get`을 입력하면 IntelliSense가 앞서 코드에서 정의된 `getData` 함수를 표시합니다. `getData`를 선택합니다.

    ![IntelliSense 사용](../javascript/media/tutorial-nodejs-intellisense.png)

1. 괄호를 추가하여 `getData()` 함수를 호출합니다.

1. `"data"` 앞의 쉼표(`,`)를 제거하면 해당 식에 녹색의 구문 강조 표시가 나타납니다. 구문 강조 표시 위에 마우스를 가져갑니다.

    ![구문 오류 보기](../javascript/media/tutorial-nodejs-syntax-checking.png)

    이 메시지의 마지막 줄에 JavaScript 인터프리터가 쉼표(`,`)를 예상했다는 메시지가 나타납니다.

1. 아래쪽 창에서 **오류 목록** 탭을 클릭합니다.

    경고 및 설명이 파일 이름 및 줄 번호와 함께 표시됩니다.

    ![오류 목록 보기](../javascript/media/tutorial-nodejs-error-list.png)

1. `"data"` 앞에 쉼표(`,`)를 추가하여 코드를 수정합니다.

    수정되면 코드 줄은 다음과 같습니다. `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>중단점 설정

다음으로 Visual Studio 디버거가 연결된 앱을 실행하려고 합니다. 그렇게 하기 전에 중단점을 설정해야 합니다.

1. *index.js*에서 다음 코드 줄 앞의 왼쪽 여백을 클릭하여 중단점을 설정합니다.

    `res.render('index', { title: 'Express', "data": getData() });`

    중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다.

    ![중단점 설정](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>애플리케이션 실행

1. 디버그 도구 모음(예: Microsoft Edge 또는 Chrome)에서 디버그 대상을 선택합니다.

    ::: moniker range=">=vs-2019"
    ![디버그 대상 선택](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![디버그 대상 선택](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    머신에서 Chrome을 사용할 수 있지만 옵션으로 표시되지 않는 경우 디버그 대상 드롭다운 목록에서 **브라우저 선택**을 선택하고 기본 브라우저 대상으로 Chrome을 선택합니다(**기본값으로 설정** 선택).

1. **F5**(**디버그** > **디버깅 시작**) 키를 눌러 애플리케이션을 실행합니다.

    디버거가 설정한 중단점에서 일시 중지됩니다. 이제 앱 상태를 검사할 수 있습니다.

1. `getData`에 마우스를 가져가 DataTip에서 속성 보기

    ![변수 검사](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. **F5**(**디버그** > **계속**) 키를 눌러 계속합니다.

    앱이 브라우저에서 열립니다.

    브라우저 창에서 제목은 "Express", 첫 단락에 "Welcome to Express"가 표시됩니다.

1. 단추를 클릭하면 다른 이미지가 표시됩니다.

    ![브라우저에서 실행 중인 앱](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. 웹 브라우저를 닫습니다.

## <a name="optional-publish-to-azure-app-service"></a>(선택 사항) Azure App Service에 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

   ![Azure App Service에 게시](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure App Service**를 선택합니다.

    **App Service** 대화 상자에서는 Azure 계정에 로그인하여 기존 Azure 구독에 로그인할 수 있습니다.

1. 나머지 단계에 따라 구독을 선택하고, 리소스 그룹을 선택하거나 만들고, 앱 서비스 평면을 만들거나 선택한 다음 Azure에 게시할 때 나타나는 단계를 따릅니다. 자세한 내용은 [웹 배포를 사용하여 Azure 웹 사이트에 게시](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)를 참조하세요.

1. **출력** 창에서 Azure에 배포하는 진행률이 표시됩니다.

    제대로 배포되면 Azure App Service를 실행하는 브라우저에서 앱이 열립니다. 단추를 클릭하면 이미지가 표시됩니다.

   ![Azure App Service에서 실행 중인 앱](../javascript/media/tutorial-nodejs-running-in-azure.png)

축하합니다. 이 자습서를 마쳤습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [앱을 Linux App Service에 배포](../javascript/publish-nodejs-app-azure.md)
