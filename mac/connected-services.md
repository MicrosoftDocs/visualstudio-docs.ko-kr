---
title: 연결된 서비스
description: Mac용 Visual Studio 내에서 모바일 앱에 Azure 데이터 스토리지, 인증 및 푸시 알림 추가
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: 8a1287d82096677d20a498756de3d2a9f5af259b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85938762"
---
# <a name="connected-services-walkthrough"></a>연결된 서비스 연습

연결된 서비스 워크플로는 Azure Portal 워크플로를 Mac용 Visual Studio로 가져오므로 서비스를 추가하기 위해 프로젝트를 나갈 필요가 없습니다.

이 연습에서는 클라우드 데이터 스토리지, 인증 및 푸시 알림을 플랫폼 간 Xamarin.Forms PCL(이식 가능한 클래스 라이브러리) 애플리케이션으로 가져오는 Azure 백 엔드 서비스를 추가하는 방법을 보여줍니다.

1. 솔루션에서 **연결된 서비스** 노드를 두 번 클릭하여 시작하면 **서비스 갤러리**가 표시됩니다.
  애플리케이션 유형에 대한 모든 사용 가능한 서비스 목록입니다. 서비스(예: **Azure App Service를 사용한 모바일 백 엔드**)를 클릭하여 선택합니다.

    [![Mac용 Visual Studio에서 연결된 Services 노드](media/connected-services-image001-sml.png "Mac용 Visual Studio에서 연결된 Services 노드")](media/connected-services-image001.png#lightbox)

2. 서비스 세부 정보 페이지에서는 설치될 서비스 및 종속성에 대해 설명합니다.
  **추가** 단추를 클릭하여 앱에 종속성을 추가합니다.

    [![Azure를 사용한 모바일 백 엔드](media/connected-services-image002-sml.png "Azure를 사용한 모바일 백 엔드")](media/connected-services-image002.png#lightbox)

3. 종속성은 작업할 PCL 및 플랫폼별 프로젝트 모두에 추가해야 합니다.
  참조할(직접 또는 간접적으로) 모든 프로젝트에 서비스를 추가하려면 확인란을 선택합니다.

    [![서비스를 참조해야 하는 모든 프로젝트 확인](media/connected-services-image003-sml.png "서비스를 참조해야 하는 모든 프로젝트 확인")](media/connected-services-image003.png#lightbox)

4. NuGet 패키지용 **라이선스 승인** 대화 상자에서 **동의**를 선택합니다.
  MobileClient 및 종속성을 위한 대화 상자 및 오프라인 데이터 동기화에 필요한 SQLiteStore를 위한 대화 상자 등 동의를 위한 대화 상자는 두 개가 있을 수 있습니다.

    [![라이선스 계약에 동의](media/connected-services-image004-sml.png "라이선스 계약에 동의")](media/connected-services-image004.png#lightbox)

    ![라이선스 승인 창](media/connected-services-image005.png "라이선스 승인 창")

5. 일단 종속성이 추가되면 Azure와 통신에 사용하려는 계정을 사용하여 로그인하라고 요구 받습니다.
  이미 Microsoft ID로 로그인한 경우 Mac용 Visual Studio는 Azure 구독 및 이와 관련된 모든 앱 서비스를 페치하려고 시도합니다. 구독이 없는 경우 Azure Portal에서 구독 계획을 구매하거나 무료 평가판에 등록하여 구독을 추가할 수 있습니다.

6. 목록에서 앱 서비스를 선택합니다. Azure에서 앱 서비스의 해당 URL을 사용하여 `MobileServiceClient` 개체에 대한 템플릿 코드를 채웁니다.

    [![목록에서 앱 서비스 선택](media/connected-services-image006-sml.png "목록에서 앱 서비스 선택")](media/connected-services-image006.png#lightbox)

    나열된 서비스가 없는 경우 **새로 만들기** 단추(9단계 참조)를 클릭합니다.

7. `MobileServiceClient`에 대한 템플릿 코드를 PCL로 복사합니다. 파일 위치의 인스턴스가 하나만 있는 경우 파일 위치는 중요하지 않습니다.
  권장하는 방법은 `MobileServiceClient`를 사용하고 모든 Azure 상호 작용을 처리하는 `AzureService` 클래스를 만드는 것입니다.

    ![구성 코드를 앱에 복사](media/connected-services-image007.png "구성 코드를 앱에 복사")

8. **다음 단계**의 설명서에 따라 데이터, 오프라인 동기화, 인증 및 푸시 알림을 앱에 추가합니다.

    [![다음 단계 지침 검토](media/connected-services-image008-sml.png "다음 단계 지침 검토")](media/connected-services-image008.png#lightbox)

9. 기존 앱 서비스가 없는 경우 Mac용 Visual Studio 내에서 새 서비스를 만들 수 있습니다.
  서비스 목록의 왼쪽 하단에서 **새로 만들기** 단추를 클릭하여 **새 앱 서비스** 대화 상자를 엽니다.

    [![Mac용 Visual Studio에서 새 앱 서비스 만들기](media/connected-services-image009-sml.png "Mac용 Visual Studio에서 새 앱 서비스 만들기")](media/connected-services-image009.png#lightbox)

새 서비스에 다음 매개 변수가 필요합니다.

- **앱 서비스 이름** – 계획에 대한 고유 이름/ID
- **구독** – 서비스에 대한 비용을 지불하기 위해 사용하려는 구독
- **리소스 그룹** – 프로젝트에 대한 모든 Azure 리소스를 구성하는 방법입니다. 기존 서비스를 사용하거나 새 서비스를 만드는 옵션입니다. 첫 Azure 서비스인 경우 새 서비스를 만듭니다.
- **서비스 계획** – 위치 및 이를 사용하는 모든 리소스 비용을 결정합니다. 기존 서비스를 사용하거나 새 서비스를 만드는 옵션입니다. 첫 Azure 서비스인 경우 기본 서비스를 사용하거나 무료 계층(F1)에서 새 서비스를 만듭니다.

자세한 내용은 [모바일 앱 설명서](/azure/app-service-mobile/)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [연결된 서비스(Windows의 Visual Studio)](/visualstudio/azure/vs-azure-tools-connected-services-storage)