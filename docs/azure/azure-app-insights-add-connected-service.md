---
title: 연결된 서비스를 사용 하 여 Azure 애플리케이션 Insights 추가 Microsoft Docs
description: Visual Studio를 사용 하 여 연결 된 서비스를 추가 하 여 앱에 Azure 애플리케이션 Insights 추가
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643290"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Visual Studio를 사용 하 여 Azure 애플리케이션 Insights 추가 연결된 서비스

Visual Studio를 사용 하 여 다음 중 하나를 **연결된 서비스** 기능을 사용 하 여 Azure 애플리케이션 Insights에 연결할 수 있습니다.

- .NET Framework 콘솔 앱
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (콘솔 앱, WPF, Windows Forms, 클래스 라이브러리 포함)
- .NET Core 작업자 역할
- Azure 기능
- 유니버설 Windows 플랫폼 앱
- Xamarin
- Cordova

연결된 서비스 기능은 필요한 모든 참조와 연결 코드를 프로젝트에 추가하고 구성 파일을 적절하게 수정합니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 연결된 서비스](/visualstudio/mac/connected-services)를 참조하세요.
## <a name="prerequisites"></a>필수 구성 요소

- Azure 워크 로드가 설치 된 Visual Studio
- 지원 되는 형식 중 하나에 해당 하는 프로젝트

## <a name="connect-to-azure-application-insights-using-connected-services"></a>연결된 서비스를 사용 하 여 Azure 애플리케이션 Insights에 연결

1. Visual Studio에서 프로젝트를 엽니다.

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가**를 선택 합니다.

1. **연결된 서비스** 탭에서 **서비스 종속성**에 대 한 + 아이콘을 선택 합니다.

    ![서비스 종속성 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **종속성 추가** 페이지에서 **Azure 애플리케이션 Insights**를 선택 합니다.

    ![Azure 애플리케이션 Insights 추가](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    아직 로그인 하지 않은 경우 Azure 계정에 로그인 합니다. Azure 계정이 없으면 [무료 평가판](https://azure.microsoft.com/account/free)에 등록할 수 있습니다.

1. **Azure 애플리케이션 Insights 구성** 화면에서 기존 Azure 애플리케이션 Insights 구성 요소를 선택 하 고 **다음**을 선택 합니다.

    새 구성 요소를 만들어야 하는 경우 다음 단계로 이동 합니다. 그러지 않은 경우 7단계로 건너뜁니다.

    ![기존 Application Insights 구성 요소에 연결](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Application Insights 구성 요소를 만들려면 다음을 수행 합니다.

   1. 화면 맨 아래에 **새 Application Insights 구성 요소 만들기를** 선택 합니다.

   1. **새 화면 만들기 Application Insights** 를 입력 하 고 **만들기**를 선택 합니다.

       ![새 Azure 앱 Insights 구성 요소](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. **Azure 애플리케이션 Insights 구성** 화면이 표시 되 면 목록에 새 구성 요소가 표시 됩니다. 목록에서 새 구성 요소를 선택 하 고 **다음**을 선택 합니다.

1. 계측 키 이름을 입력 하거나 기본값을 선택 하 고, 연결 문자열을 로컬 비밀 파일에 저장할지, 아니면 [Azure Key Vault](/azure/key-vault)에 저장할지를 선택 합니다.

   ![연결 문자열 지정](./media/azure-app-insights-add-connected-service/connection-string.png)

1. **변경 내용 요약** 화면에는 프로세스를 완료 한 경우 프로젝트에 적용 되는 모든 수정 사항이 표시 됩니다. 변경 내용이 양호 하면 **마침**을 선택 합니다.

   ![변경 내용 요약](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. 연결은 **연결된 서비스** 탭의 **서비스 종속성** 섹션 아래에 나타납니다.

   ![서비스 종속성](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>추가 정보

- [Azure Monitor 제품 페이지](https://azure.microsoft.com/services/monitor/)
- [Azure 앱 Insights 설명서](/azure/azure-monitor/app/app-insights-overview/)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)
