---
title: Linux App Service에 Node.js 앱 게시
description: Azure에서 Linux App Service에 Visual Studio에서 생성한 Node.js 애플리케이션을 게시할 수 있습니다.
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d75bb4f5274201b7cf745ff8c7c6f27b869855c3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445014"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Azure에 Node.js 애플리케이션 게시(Linux App Service)

이 자습서에서는 간단한 Node.js 애플리케이션을 만들고 Azure에 게시하는 작업을 안내합니다.

Azure에 Node.js 애플리케이션을 게시할 때 몇 가지 옵션이 있습니다. 여기에는 Azure App Service, 사용자가 선택한 OS를 실행하는 VM, Kubernetes 관리를 위한 Azure Container Service(AKS), Docker를 사용하는 컨테이너 인스턴스 등이 포함됩니다. 이러한 각 옵션에 대한 자세한 내용은 [컴퓨팅](https://azure.microsoft.com/product-categories/compute/)을 참조하세요.

이 자습서에서는 앱을 [Linux App Service](/azure/app-service/containers/app-service-linux-intro)에 배포합니다.
Linux App Service는 Linux Docker 컨테이너를 배포하여 Node.js 애플리케이션을 실행합니다(Windows에서 IIS 뒤에서 Node.js 앱을 실행하는 Windows App Service와는 반대).

이 자습서에서는 Visual Studio용 Node.js 도구를 사용하여 설치한 템플릿에서 시작하는 Node.js 애플리케이션을 만들고, 코드를 GitHub의 리포지토리로 푸시한 다음, GitHub 리포지토리에서 배포할 수 있도록 Azure 웹 포털을 통해 Azure App Service를 프로비전하는 방법을 설명합니다. 명령줄을 사용하여 Azure App Service를 프로비전하고 로컬 Git 리포지토리에서 코드를 푸시하려면 [Node.js 앱 만들기](/azure/app-service/containers/quickstart-nodejs)를 참조하세요.

이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.
> [!div class="checklist"]
> * Node.js 프로젝트 만들기
> * 코드에 대한 GitHub 리포지토리 만들기
> * Azure에서 Linux App Service 만들기
> * Linux에 배포

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

    아직 설치되지 않은 경우 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치합니다. 일반적으로, 설치된 Node.js 런타임은 Visual Studio에서 자동으로 검색됩니다. 설치된 런타임이 검색되지 않으면 속성 페이지에서 설치된 런타임을 참조하도록 프로젝트를 구성할 수 있습니다(프로젝트를 만든 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure에서 실행하도록 Node.js 프로젝트 만들기

1. Visual Studio를 엽니다.

1. 새 TypeScript Express 앱을 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **Node.js**를 입력한 다음, **새 기본 Azure Node.js Express 4 애플리케이션 만들기**(TypeScript)를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **TypeScript**를 확장한 다음, **Node.js**를 선택합니다. 가운데 창에서 **기본 Azure Node.js Express 4 애플리케이션**을 선택한 후 **확인**을 선택합니다.

    ![새로운 TypeScript Express 앱 만들기](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    **기본 Azure Node.js Express 4 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **Node.js 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

    Visual Studio가 프로젝트를 만들어 솔루션 탐색기(오른쪽 창)에서 엽니다.

1. **F5** 키를 눌러 앱을 빌드 및 실행하고, 예상한 대로 잘 실행되는지 확인합니다.

1. **파일** > **소스 제어에 추가**를 선택하여 프로젝트에 대한 로컬 Git 리포지토리를 만듭니다.

    이 시점에서 Express 프레임워크를 사용하고 TypeScript에서 작성된 Node.js 앱이 작동하고 로컬 소스 제어에 체크 인됩니다.

1. 다음 단계를 진행하기 전에 원하는 대로 프로젝트를 편집합니다.

## <a name="push-code-from-visual-studio-to-github"></a>코드를 Visual Studio에서 GitHub로 푸시

Visual Studio에 대해 GitHub를 설정하려면 다음을 수행합니다.

1. [Visual Studio용 GitHub 확장](https://visualstudio.github.com/)이 설치되어 있는지 확인하고 **도구** > **확장 및 업데이트** 메뉴 항목을 사용하여 활성화합니다.

2. 메뉴에서 **보기** > **기타 Windows** > **GitHub**를 선택합니다.

    GitHub 창이 열립니다.

3. GitHub 창에서 **시작** 단추가 표시되지 않는 경우 **파일** > **소스 제어에 추가**를 클릭하고 UI가 업데이트될 때까지 기다립니다.

    ![GitHub 창 열기](../javascript/media/azure-github-get-started.png)

4. **시작**을 클릭합니다.

    GitHub에 이미 연결되어 있는 경우 도구 상자는 다음 그림과 같이 표시됩니다.

    ![GitHub 리포지토리 설정](../javascript/media/azure-github-publish.png)

5. 게시할 새 리포지토리에 대한 필드를 완료한 다음, **게시**를 클릭합니다.

    잠시 후 “리포지토리가 성공적으로 생성됨”이란 배너가 나타납니다.

    다음 섹션에서는 이 리포지토리에서 Linux에서 Azure App Service로 게시하는 방법을 알아봅니다.

## <a name="create-a-linux-app-service-in-azure"></a>Azure에서 Linux App Service 만들기

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 왼쪽에 있는 서비스 목록에서 **App Services**를 선택한 다음, **추가**를 클릭합니다.

3. 필요한 경우 새 앱을 호스트하는 새 리소스 그룹 및 App Service 계획을 만듭니다.

4. 그림에 표시된 것처럼 **OS**를 **Linux**로 설정하고, **런타임 스택** 필요한 Node.js 버전으로 설정했는지 확인합니다.

    ![Linux App Service 만들기](../javascript/media/azure-create-appservice-annotated.png)

5. **만들기**를 클릭하여 App Service를 만듭니다.

    배포하는 데 몇 분 정도 걸릴 수 있습니다.

6. 배포된 후 **애플리케이션 설정** 섹션으로 이동하고 `SCM_SCRIPT_GENERATOR_ARGS`란 이름 및 `--node` 값의 설정을 추가합니다.

    ![애플리케이션 설정](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > App Service 배포 프로세스는 추론 집합을 사용하여 시도 및 실행할 애플리케이션의 유형을 결정합니다. .*sln* 파일이 배포된 콘텐츠에서 검색되면 MSBuild 기반 프로젝트가 배포되는 것으로 가정합니다. 위에서 추가된 설정은 이 논리를 재정의하고 Node.js 애플리케이션임을 명시적으로 지정합니다. 이 설정이 없으면 .*sln* 파일이 App Service에 배포되는 리포지토리의 일부인 경우 Node.js 애플리케이션은 배포에 실패하게 됩니다.

7. **애플리케이션 설정**에서 이름이 `WEBSITE_NODE_DEFAULT_VERSION`이고 값이 `8.9.0`인 다른 설정을 추가합니다.

8. 배포된 후 App Service를 열고 **배포 옵션**을 선택합니다.

    ![배포 옵션](../javascript/media/azure-deployment-options.png)

9. **원본 선택**을 클릭한 다음, **GitHub**를 선택한 다음, 필요한 권한을 구성합니다.

    ![GitHub 권한](../javascript/media/azure-choose-source.png)

10. 게시할 리포지토리 및 분기를 선택한 다음, **확인**을 선택합니다.

    ![Linux App Service에 게시](../javascript/media/azure-repo-and-branch.png)

    동기화하는 동안 **배포 옵션** 페이지가 나타납니다.

    ![배포 및 GitHub와 동기화](../javascript/media/azure-deployment-options-sync.png)

    동기화가 완료된 후 확인 표시가 표시됩니다.

    사이트는 현재 GitHub 리포지토리에서 Node.js 애플리케이션을 실행하고 있으며, Azure App Service에 대해 생성된 URL에서 액세스할 수 있습니다(기본적으로 Azure App Service에 지정된 이름 뒤에는 “.azurewebsites.net”이 옴”).

## <a name="modify-your-app-and-push-changes"></a>사용자 앱 수정 및 변경 내용 푸시

1. 여기에 나와 있는 코드를 *app.ts*에서 줄 `app.use('/users', users);` 뒤에 추가합니다. 그러면 REST API가 URL */api*에서 추가됩니다.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. 코드를 빌드하고 로컬로 테스트한 다음, 체크 인하고 GitHub에 푸시합니다.

    Azure Portal에서 GitHub 리포지토리의 변경 내용을 검색하는 데 몇 분 정도 걸립니다. 그런 다음, 배포의 새 동기화가 시작됩니다. 다음 그림과 비슷하게 나타납니다.

    ![수정 및 동기화](../javascript/media/azure-changes-detected.png)

3. 배포가 완료되면 공용 사이트로 이동하고 */api*를 URL에 추가합니다. JSON 응답이 반환됩니다.

## <a name="troubleshooting"></a>문제 해결

* node.exe 프로세스가 중단되는 경우(즉, 처리되지 않은 예외가 발생) 컨테이너가 다시 시작됩니다.
* 컨테이너가 시작되면 Node.js 프로세스를 시작하는 방법을 파악하는 다양한 추론을 통해 실행됩니다. 구현에 대한 세부 정보는 [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js)에서 볼 수 있습니다.
* 조사를 위해 SSH를 통해 실행 중인 컨테이너에 연결할 수 있습니다. Azure Portal을 사용하여 손쉽게 수행할 수 있습니다. App Service를 선택하고 **개발 도구** 섹션의 **SSH**에 도달할 때까지 도구 목록을 아래로 스크롤합니다.
* 문제 해결을 돕기 위해 App Service에 대한 **진단 로그** 설정으로 이동하고 **Docker 컨테이너 로깅** 설정을 **해제**에서 **파일 시스템**으로 변경합니다. 로그가 */home/LogFiles/* _docker.log*에 있는 컨테이너에 생성되며, SSH 또는 FTP(S)를 사용하여 상자에서 액세스할 수 있습니다.
* 사용자 지정 도메인 이름을 기본적으로 할당된 *.azurewebsites.net URL이 아닌 사이트에 할당할 수도 있습니다. 자세한 내용은 [사용자 지정 도메인 매핑](/azure/app-service/app-service-web-tutorial-custom-domain) 항목을 참조하세요.
* 프로덕션으로 이동하기 전에 추가 테스트를 위해 스테이징 사이트를 배포하는 것이 가장 좋습니다. 이를 구성하는 방법에 대한 자세한 내용은 [스테이징 환경 만들기](/azure/app-service/web-sites-staged-publishing) 항목을 참조하세요.
* 더 자주 묻는 질문은 [Linux의 App Service에 대한 FAQ](/azure/app-service/containers/app-service-linux-faq)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Linux App Service를 만들고 서비스에 Node.js 애플리케이션을 배포하는 방법을 알아봅니다. Linux App Service에 대해 자세히 알아볼 수도 있습니다.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
