---
title: Azure Functions 소개
description: Mac용 Visual Studio에서 Azure Functions 사용
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: f2621ab30099baae5521c8b2226f288ec1a2531b
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938858"
---
# <a name="introduction-to-azure-functions"></a>Azure Functions 소개

Azure Functions는 클라우드에서 명시적인 인프라 프로비전이나 관리 없이 이벤트 중심 코드 조각을 만들고 실행하는 방법입니다. Azure Functions에 대한 자세한 내용은 [Azure Functions 설명서](/azure/azure-functions/)를 참조하세요.

## <a name="requirements"></a>요구 사항

Azure 함수 도구는 **Mac용 Visual Studio 7.5**에 포함됩니다.

함수를 만들어 배포하려면 [https://azure.com/free](https://azure.com/free)에서 무료로 제공하는 Azure 구독도 필요합니다.

## <a name="creating-your-first-azure-functions-project"></a>Azure Functions 프로젝트 처음 만들기

1. Mac용 Visual Studio에서 **파일 > 새 솔루션**을 선택합니다.
2. 새 프로젝트 대화 상자에서 **클라우드 > 일반**의 Azure Functions 템플릿을 선택하고 **다음**을 클릭합니다.

    ![Azure Functions 옵션을 표시하는 새 프로젝트 대화 상자](media/azure-functions-image1.png)

3. 사용할 초기 Azure Functions 템플릿을 선택하여 함수 이름을 입력하고 **다음**을 클릭합니다.

    ![Azure Functions 템플릿을 표시하는 새 프로젝트 대화 상자](media/azure-functions-image2.png)

    선택한 함수의 형식에 따라 다음 페이지에서는 다음 이미지에 설명된 액세스 권한과 같은 세부 정보를 입력하라는 메시지가 표시됩니다.

    ![추가 옵션을 표시하는 새 프로젝트 대화 상자](media/azure-functions-image3.png)

    다양한 유형의 Azure Functions 템플릿 및 각 템플릿을 구성하는 데 필요한 바인딩 속성에 대한 자세한 내용은 [사용 가능한 함수 템플릿](#available-function-templates) 섹션을 참조하세요. 이 예제에서는 액세는 권한이 익명으로 설정된 Http 트리거를 사용하고 있습니다.

4. 매개 변수를 설정한 후 프로젝트의 위치를 선택하고 **만들기**를 선택합니다.

Mac용 Visual Studio는 기본 함수가 포함된 .NET Standard 프로젝트를 만듭니다. 여기에는 **Newtonsoft.Json** 패키지뿐 아니라 여러 **AzureWebJobs** 패키지에 대한 NuGet 참조가 포함됩니다.

![템플릿의 새 Azure 함수를 표시하는 Mac용 Visual Studio 편집기](media/azure-functions-newproj.png)

새 프로젝트에는 다음 파일이 포함됩니다.

* **your-function-name.cs** – 이 클래스에는 선택한 함수에 대한 상용구 코드를 포함합니다. 여기에는 함수 이름이 있는 **FunctionName** 특성 및 이 함수를 트리거하는 대상을 지정하는 트리거 특성( 예: HTTP 요청)을 포함합니다. 함수 메서드에 대한 자세한 내용은 [Azure Functions C# 개발자 참조](/azure/azure-functions/functions-dotnet-class-library) 문서를 참조하세요.
* **host.json** – 이 파일은 함수 호스트에 대한 전역 구성 옵션을 설명합니다. 이 파일의 예제 파일과 사용 가능한 설정 정보는 [Azure Functions에 대한 host.json 참조](/azure/azure-functions/functions-host-json)를 참조하세요.
* **local.settings.json** – 이 파일은 함수를 로컬로 실행하기 위한 모든 설정을 포함합니다. 이러한 설정은 Azure Functions Core Tools에서 사용됩니다. 자세한 내용은 Azure Functions 핵심 도구 문서의 [로컬 설정 파일](/azure/azure-functions/functions-run-local#local-settings-file)을 참조하세요.

Mac용 Visual Studio에서 새 Azure Functions 프로젝트를 만들었으므로 이제 로컬 컴퓨터에서 기본 HTTP 트리거 함수를 테스트할 수 있습니다.

## <a name="testing-the-function-locally"></a>로컬로 함수 테스트

Mac용 Visual Studio에서 Azure Functions 지원을 통해 로컬 개발 컴퓨터에서 함수틀 테스트 및 디버그할 수 있습니다.

1. 함수를 로컬로 테스트하려면 Mac용 Visual Studio에서 **실행** 단추를 누릅니다.

    ![Mac용 Visual Studio에서 디버그 시작](media/azure-functions-run.png)

1. Azure Functions에서 프로젝트를 실행하면 로컬 디버그가 시작되고 다음 이미지에서처럼 새 터미널 창이 열립니다.

    ![함수 출력을 표시하는 터미널 창](media/azure-functions-terminal.png)

    출력에서 URL을 복사합니다.

3. HTTP 요청에 대한 URL을 브라우저의 주소 표시줄에 붙여 넣습니다. `?name=<yourname>` 쿼리 문자열을 URL의 마지막에 추가하고 요청을 실행합니다. 다음 이미지에서는 함수가 반환한 로컬 GET 요청에 대한 응답을 브라우저에 보여 줍니다.

    ![브라우저의 http 요청](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>프로젝트에 다른 함수 추가

함수 템플릿을 사용하면 가장 일반적인 트리거 및 템플릿을 통해 새 함수를 신속하게 만들 수 있습니다. 다른 유형의 함수를 만들려면 다음을 수행합니다.

1. 새 함수를 추가하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고**추가 > 함수 추가...** 를 선택합니다.

    ![새 함수를 추가하기 위한 컨텍스트 작업](media/azure-functions-addnew.png)

2. **새 Azure 함수** 대화 상자에서 필요한 함수를 선택합니다.

    ![새 Azure 함수 대화 상자](media/azure-functions-image4.png)

    Azure 함수 템플릿 목록은 [사용 가능한 함수 템플릿](#available-function-templates) 섹션에 나와 있습니다.

위의 절차를 사용하여 함수 앱 프로젝트에 더 많은 함수를 추가할 수 있습니다. 프로젝트에서 각 함수는 다른 트리거를 가질 수 있지만 함수에는 정확히 하나의 트리거만 있어야 합니다. 자세한 내용은 [Azure Functions 트리거 및 바인딩 개념](/azure/azure-functions/functions-triggers-bindings)을 참조하세요.

## <a name="publish-to-azure"></a>Azure에 게시

1. 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **게시 > Azure에 게시**(![Azure 메뉴 옵션에 게시](media/azure-functions-image5.png))를 선택합니다.
2. Azure 계정을 Mac용 Visual  Studio에 이미 연결한 경우 사용 가능한 앱 서비스 목록이 표시됩니다. 로그인하지 않은 경우 로그인하라는 메시지가 표시됩니다.
3. **Azure App Service 게시** 대화 상자에서 기존 앱 서비스를 선택하거나 **새로 만들기**를 클릭하여 새 앱을 만들 수 있습니다.
4. **새 App Service 만들기** 대화 상자에서 ![Azure 메뉴 옵션에 게시](media/azure-functions-image7.png) 설정을 입력합니다.

    |설정  |Description  |
    |---------|---------|
    |**App Service 이름**|새 함수 앱을 식별하는 전역적으로 고유한 이름입니다.|
    |**구독**|사용할 Azure 구독입니다.|
    |**[리소스 그룹](/azure/azure-resource-manager/resource-group-overview)**|함수 앱을 만들 리소스 그룹의 이름입니다. **+** 를 선택하여 새 리소스 그룹을 만듭니다.|
    |**[서비스 계획](/azure/azure-functions/functions-scale)**|기존 계획을 선택하거나 사용자 지정 계획을 만듭니다. 가까운 지역 또는 함수에 액세스하는 다른 서비스 근처의 위치를 선택합니다.|

    > [!CAUTION]
    > **가격 책정**을 **소비**로 설정된 상태에서 사용자 저정 서비스 계획을 만들려는 경우 프로비전 오류로 인해 게시가 실패하는 Mac용 Visual Studio 7.6 버전의 버그가 있습니다. 이는 다음 서비스 릴리스에서 수정될 예정입니다.

5. **다음**을 클릭하여 스토리지 계정을 만듭니다. Functions 런타임에는 Azure Storage 계정이 필요합니다. **사용자 지정**을 클릭하여 범용 스토리지 계정을 만들거나 기존 스토리지 계정을 사용합니다.

    ![Azure 메뉴 옵션에 게시](media/azure-functions-image8.png)

6. **만들기**를 클릭하여 이러한 설정으로 Azure에서 함수 앱 및 관련 리소스를 만들고 함수 프로젝트 코드를 배포합니다.

7. 게시 중에 "Azure에서 함수 버전 업데이트"를 알리는 대화 상자가 표시될 수 있습니다. **예**를 클릭합니다.

    ![Azure 메뉴 옵션에 게시](media/azure-functions-image12.png)

> [!CAUTION]
> `FUNCTIONS_EXTENSION_VERSION`이 "beta"로 올바르게 설정되지 않은 Mac용 Visual Studio 7.6 버전에 버그가 있습니다. 이는 함수가 실행되지 않을 수 있음을 의미합니다. 이 문제를 해결하려면 [함수 앱 설정](#function-app-settings)으로 이동하여 `FUNCTIONS_EXTENSION_VERSION`을 "-1"에서 "beta"로 설정합니다.

## <a name="function-app-settings"></a>함수 앱 설정

local.settings.json에서 추가한 모든 설정을 Azure의 함수 앱에도 추가해야 합니다. 이러한 설정은 프로젝트를 게시할 때 자동으로 업로드되지 않습니다.

앱 설정에 액세스하려면 [https://ms.portal.azure.com/](https://ms.portal.azure.com/)의 Azure Portal로 이동합니다. **Function App** 아래에서 **Function App**을 선택하고 함수 이름을 강조 표시합니다.

![Azure 함수 메뉴](media/azure-functions-image9.png)

**개요** 탭에서 **구성된 기능** 아래의 **애플리케이션 설정**을 선택합니다.

![Azure 함수의 탭을 통해](media/azure-functions-image10.png)

여기에서 새 애플리케이션 설정을 추가하거나 기존 애플리케이션을 수정할 수 있는 함수 앱에 대한 애플리케이션 설정을 설정할 수 있습니다.

![Azure Portal의 애플리케이션 설정 영역](media/azure-functions-image11.png)

설정할 필요가 있는 중요한 설정은 `FUNCTIONS_EXTENSION_VERSION`입니다. Mac용 Visual Studio에서 게시할 때 이 값을 **베타**로 설정해야 합니다.

## <a name="available-function-templates"></a>사용 가능한 함수 템플릿

- **GitHub 트리거** - GitHub 리포지토리에서 발생하는 이벤트에 응대합니다. 자세한 내용은 [Azure functions 문서의 GitHub 부분](/azure/azure-functions/functions-create-github-webhook-triggered-function)을 참조하세요.
  - GitHub commenter – 문제 또는 끌어오기 요청에 대한 GitHub 웹후크를 받고 주석을 추가할 때 실행되는 함수입니다.
  - GitHub WebHook – 이 함수는 GitHub 웹후크 요청을 받을 때 실행됩니다.

- **HTTP** – HTTP 요청을 사용하여 코드 실행을 트리거합니다. 다음 HTTP 트리거에 대한 명시적 템플릿이 있습니다.
  - HTTP 트리거
  - Http GET CRUD
  - Http POST CRUD
  - 매개 변수가 있는 http 트리거

- **Timer** - 미리 정의된 일정에 따라 정리 또는 기타 일괄 처리 작업을 실행합니다. 이 템플릿에는 이름과 일정 등 두 필드가 있고 6개 필드 CRON 식입니다. 자세한 내용은 [Azure functions 문서의 Timer 부분](/azure/azure-functions/functions-create-scheduled-function)을 참조하세요.

- **Queue Trigger** – Azure Storage 큐에 도착하면 메시지에 응답하는 함수입니다. 함수 이름 외에도 이 템플릿은 **경로**(메시지를 읽을 큐의 이름)와 스토리지 계정 **연결**(스토리지 계정 연결 문자열을 포함하는 앱 설정의 이름)을 사용합니다. 자세한 내용은 [Azure 함수 문서의 큐 스토리지 부분](/azure/azure-functions/functions-create-storage-queue-triggered-function)을 참조하세요.

- **Blob Trigger** – 컨테이너에 추가되는 Azure Storage Blob를 처리합니다. 함수 이름 외에도 이 템플릿은 경로 및 연결 속성을 사용합니다. 경로 속성은 트리거가 모니터링할 스토리지 계정 내의 경로입니다. 연결 계정은 스토리지 계정 연결 문자열을 포함하는 앱 설정의 이름입니다. 자세한 내용은 [Azure Functions Blob Storage 문서](/azure/azure-functions/functions-create-storage-blob-triggered-function)를 참조하세요.

- **일반 웹후크** – 웹후크를 지원하는 서비스에서 요청을 수신할 때마다 실행되는 간단한 함수입니다. 자세한 내용은 [Azure Functions 문서의 일반 웹후크 부분](/azure/azure-functions/functions-create-generic-webhook-triggered-function)을 참조하세요.

- **영속 함수 오케스트레이션** – 영속 함수를 사용하면 서버가 없는 환경에서 상태 저장 함수를 작성할 수 있습니다. 확장은 상태, 검사점 및 다시 시작을 관리합니다. 자세한 내용은 Azure Functions 설명서의 [영속 함수](/azure/azure-functions/durable-functions-overview) 부분을 참조하세요.

- **Image Resizer** - Blob가 컨테이너에 추가될 때마다 크기 조정된 이미지를 만드는 함수입니다. 이 템플릿은 트리거, 소형 이미지 출력, 중간 이미지 출력을 위해 경로 및 연결을 사용합니다.

- **SAS token** – 지정된 Azure Storage 컨테이너 및 Blob 이름에 대한 SAS 토큰을 생성하는 함수입니다. 함수 이름 외에도 이 템플릿은 경로 및 연결 속성을 사용합니다. 경로 속성은 트리거가 모니터링할 스토리지 계정 내의 경로입니다. 연결 계정은 스토리지 계정 연결 문자열을 포함하는 앱 설정의 이름입니다. **액세스 권한**도 설정해야 합니다. 권한 부여 수준은 함수에 API 키가 필요한지 여부, 사용할 키, 함수의 함수 키 사용, 관리자의 마스터 키 사용을 제어합니다. 자세한 내용은 [SAS 토큰을 생성하기 위한 C# Azure 함수](https://github.com/Azure-Samples/functions-dotnet-sas-token/) 샘플을 참조하세요.
