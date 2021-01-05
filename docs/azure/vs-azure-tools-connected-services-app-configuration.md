---
title: 연결된 서비스를 사용 하 여 Azure 앱 구성 추가 Microsoft Docs
description: Visual Studio를 사용 하 여 Azure 구성 서비스 종속성을 앱에 추가 연결된 서비스
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727296"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Visual Studio를 사용 하 여 Azure 앱 구성 추가 연결된 서비스

이 자습서에서는 ASP.NET Core 또는 모든 형식의 ASP.NET 프로젝트를 사용 하는지에 관계 없이 Visual Studio에서 웹 프로젝트에 대 한 구성 및 기능 플래그를 관리 하기 위해 Azure 앱 구성을 사용 하 여 시작 하는 데 필요한 모든 항목을 쉽게 추가 하는 방법을 알아봅니다. Visual Studio의 연결된 서비스 기능을 사용 하 여 Visual Studio에서 Azure의 앱 구성 리소스에 연결 하는 데 필요한 모든 코드, NuGet 패키지 및 구성 설정을 자동으로 추가 하도록 할 수 있습니다. 이 기능을 사용 하려면 Visual Studio 2019 버전 16.9 이상을 사용 해야 합니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 연결된 서비스](/visualstudio/mac/connected-services)를 참조하세요.

## <a name="prerequisites"></a>필수 조건

- Azure 워크 로드가 설치 된 Visual Studio
- 지원 되는 형식 중 하나에 해당 하는 프로젝트

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>연결된 서비스를 사용 하 여 Azure 앱 구성에 연결

1. Visual Studio에서 새 프로젝트를 엽니다.

1. **솔루션 탐색기** 에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가** 를 선택 합니다.

    ![Azure 연결된 서비스 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. **연결된 서비스** 탭에서 **서비스 종속성** 에 대 한 + 아이콘을 선택 합니다.

    ![서비스 종속성 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **종속성 추가** 페이지에서 **Azure 앱 구성** 을 선택 합니다.

    ![앱 구성 추가](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    아직 로그인 하지 않은 경우 Azure 계정에 로그인 합니다. Azure 계정이 없으면 [무료 평가판](https://azure.microsoft.com/free/dotnet)에 등록할 수 있습니다.

1. **Azure 앱 구성** 구성 화면에서 구독 및 기존 구성 저장소를 선택 합니다. 그런 후 **다음** 을 선택합니다.

    앱 구성 저장소를 만들어야 하는 경우 다음 단계로 이동 합니다. 그렇지 않을 경우 6단계로 건너뜁니다.

    ![프로젝트에 기존 구성 계정 추가](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. 앱 구성 저장소를 만들려면 다음을 수행 합니다.

   1. **앱 구성 저장소** 헤더의 오른쪽에 있는 + 아이콘을 선택 합니다. 

   1. **Azure 앱 구성: 새** 대화 상자 만들기를 입력 하 고 **만들기** 를 선택 합니다. 리소스 이름 필드는 고유 해야 합니다. 

       ![새 Azure 앱 구성 저장소](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. **Azure 앱 구성** 대화 상자가 표시 되 면 새 구성 저장소가 목록에 표시 됩니다. 이 새 저장소를 선택 하 고 **다음** 을 선택 합니다.

1. 연결 문자열 이름을 입력 하 고 연결 문자열을 로컬 비밀 파일에 저장할지, 아니면 [Azure Key Vault](/azure/key-vault)에 저장할지를 선택 합니다.

   ![연결 문자열 지정](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. **변경 내용 요약** 화면에는 프로세스를 완료 한 경우 프로젝트에 적용 되는 모든 수정 사항이 표시 됩니다. 변경 내용이 양호 하면 **마침** 을 선택 합니다.

   ![변경 내용 요약](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. **종속성 구성 프로세스가** 완료 되 면 이제 프로젝트의 **서비스 종속성** 노드 아래에 Azure 앱 구성이 표시 됩니다.

## <a name="next-steps"></a>다음 단계

[Azure 앱 구성 설명서](/azure/azure-app-configuration/overview)의 Azure 앱 구성에 대해 알아봅니다.

## <a name="see-also"></a>추가 정보

- [앱 구성에서 동적 구성을 사용 하는 방법에 대 한 자습서 ASP.NET Core 앱 연결](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)