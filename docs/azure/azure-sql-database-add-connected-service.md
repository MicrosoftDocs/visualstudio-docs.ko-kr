---
title: Azure SQL Database에 대 한 연결 추가 | Microsoft Docs
description: Visual Studio를 사용 하 여 앱에 Azure SQL Database 연결을 추가 연결된 서비스
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: e1594ea4239b4200bf72ec4a2ef2c558839ef95c
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643248"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Azure SQL Database에 대 한 연결 추가

Visual Studio를 사용 하면 **연결된 서비스** 기능을 사용 하 여 다음 중 하나를 Azure SQL database에 연결할 수 있습니다.

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>연결된 서비스를 사용 하 여 Azure SQL Database에 연결

1. Visual Studio에서 프로젝트를 엽니다.

1. **솔루션 탐색기**에서 **연결된 서비스** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **연결 된 서비스 추가**를 선택 합니다.

1. **연결된 서비스** 탭에서 **서비스 종속성**에 대 한 + 아이콘을 선택 합니다.

    ![서비스 종속성 추가](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **종속성 추가** 페이지에서 **Azure SQL Database**를 선택 합니다.

    ![Azure SQL Database 서비스 추가](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    아직 로그인 하지 않은 경우 Azure 계정에 로그인 합니다. Azure 계정이 없으면 [무료 평가판](https://azure.microsoft.com/account/free)에 등록할 수 있습니다.

1. **Azure SQL Database 구성** 화면에서 기존 Azure SQL Database를 선택 하 고 **다음**을 선택 합니다.

    새 구성 요소를 만들어야 하는 경우 다음 단계로 이동 합니다. 그러지 않은 경우 7단계로 건너뜁니다.

    ![기존 Azure SQL Database 구성 요소에 연결](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Azure SQL Database 만들려면 다음을 수행 합니다.

   1. 화면 맨 아래에서 **SQL Database 만들기를** 선택 합니다.

   1. **새 화면 만들기 Azure SQL Database** 를 입력 하 고 **만들기**를 선택 합니다.

       ![새 Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. **Azure SQL Database 구성** 화면이 표시 되 면 목록에 새 데이터베이스가 표시 됩니다. 목록에서 새 데이터베이스를 선택 하 고 **다음**을 선택 합니다.

1. 연결 문자열 이름을 입력 하거나 기본값을 선택 하 고 연결 문자열을 로컬 비밀 파일에 저장할지, 아니면 [Azure Key Vault](/azure/key-vault)에 저장할지를 선택 합니다.

   ![연결 문자열 지정](./media/azure-sql-database-add-connected-service/connection-string.png)

1. **변경 내용 요약** 화면에는 프로세스를 완료 한 경우 프로젝트에 적용 되는 모든 수정 사항이 표시 됩니다. 변경 내용이 양호 하면 **마침**을 선택 합니다.

   ![변경 내용 요약](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   방화벽 규칙을 설정 하 라는 메시지가 표시 되 면 **예**를 선택 합니다.

   ![방화벽 규칙](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. 연결은 **연결된 서비스** 탭의 **서비스 종속성** 섹션 아래에 나타납니다.

   ![서비스 종속성](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>참고 항목

- [Azure SQL Database 제품 페이지](https://azure.microsoft.com/services/sql-database/)
- [Azure SQL Database 설명서](/azure/azure-sql/database/)
- [연결된 서비스(Mac용 Visual Studio)](/visualstudio/mac/connected-services)
