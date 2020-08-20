---
title: 연결된 서비스를 사용 하 여 Azure CosmosDB 추가 | Microsoft Docs
description: Visual Studio를 사용 하 여 연결 된 서비스를 추가 하 여 앱에 Azure CosmosDB 지원 추가
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2d23081f541fbc12581450c60c6eb4b09f20c64a
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643272"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Visual Studio를 사용 하 여 앱에 Azure Cosmos DB 추가 연결된 서비스

Visual Studio를 사용 하 여 다음 중 하나를 **연결된 서비스** 기능을 사용 하 여 Azure Cosmos DB에 연결할 수 있습니다.

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
## <a name="prerequisites"></a>사전 요구 사항

- Azure 워크 로드가 설치 된 Visual Studio
- 지원 되는 형식 중 하나에 해당 하는 프로젝트

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>연결된 서비스를 사용 하 여 Azure Cosmos DB에 연결

1. Visual Studio에서 프로젝트를 엽니다.

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가**를 선택 합니다.

1. **연결된 서비스** 탭에서 **서비스 종속성**에 대 한 + 아이콘을 선택 합니다.

    ![서비스 종속성 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **종속성 추가** 페이지에서 **Azure Cosmos DB**를 선택 합니다.

    ![Azure Cosmos DB 추가](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    아직 로그인 하지 않은 경우 Azure 계정에 로그인 합니다. Azure 계정이 없으면 [무료 평가판](https://azure.microsoft.com/account/free)에 등록할 수 있습니다.

1. **Azure Cosmos DB** 화면에서 기존 Azure Cosmos DB를 선택 하 고 **다음**을 선택 합니다.

    데이터베이스를 만들어야 하는 경우 다음 단계로 이동 합니다. 그러지 않은 경우 7단계로 건너뜁니다.

    ![프로젝트에 기존 Cosmos DB 추가](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Azure Cosmos DB 만들려면 다음을 수행 합니다.

   1. 화면 맨 아래에 **새 Azure Cosmos DB 만들기를** 선택 합니다.

   1. **새 화면 만들기 Azure Cosmos DB** 를 입력 하 고 **만들기**를 선택 합니다.

       ![새 Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. **Azure Cosmos DB 구성** 대화 상자가 표시 되 면 목록에 새 데이터베이스가 표시 됩니다. 목록에서 새 데이터베이스를 선택 하 고 **다음**을 선택 합니다.

1. 연결 문자열 이름을 입력 하 고 연결 문자열을 로컬 비밀 파일에 저장할지, 아니면 [Azure Key Vault](/azure/key-vault)에 저장할지를 선택 합니다.

   ![연결 문자열 지정](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. **변경 내용 요약** 화면에는 프로세스를 완료 한 경우 프로젝트에 적용 되는 모든 수정 사항이 표시 됩니다. 변경 내용이 양호 하면 **마침**을 선택 합니다.

   ![변경 내용 요약](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. 연결은 **연결된 서비스** 탭의 **서비스 종속성** 섹션 아래에 나타납니다.

   ![서비스 종속성](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>참고 항목

- [Azure Cosmos DB 제품 페이지](https://azure.microsoft.com/services/cosmos-db/)
- [Azure Cosmos DB 설명서](/azure/cosmos-db/)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)
