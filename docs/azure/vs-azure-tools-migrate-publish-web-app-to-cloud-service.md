---
title: 웹앱을 Azure Cloud Service에 마이그레이션 및 게시
description: Visual Studio를 사용하여 Azure 클라우드 서비스로 웹 애플리케이션을 마이그레이션 및 게시하는 방법에 대해 알아보세요.
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c95c96815872c259cab761d8b4af36141f866dbd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280559"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>방법: Visual Studio에서 Azure 클라우드 서비스로 웹 응용 프로그램 마이그레이션 및 게시

Azure의 호스팅 서비스와 확장 기능을 활용하기 위해 웹 애플리케이션을 Azure 클라우드 서비스로 마이그레이션 및 배포해야 하는 경우가 있습니다. 최소의 변경 작업만 수행하면 됩니다. 이 문서에서는 클라우드 서비스에 배포하는 내용만 다룹니다. App Service에 대한 내용은 [Azure App Service에 웹앱 배포](/azure/app-service/app-service-deploy-local-git)를 참조하세요.

> [!Important]
> 이 마이그레이션은 특정 ASP.NET, WCF 및 WCF 워크플로 프로젝트에 대해서만 지원 됩니다. ASP.NET Core 프로젝트에는 지원되지 않습니다. [지원되는 프로젝트 템플릿](#supported-project-templates)을 참조하세요.

## <a name="migrate-a-project-to-cloud-services"></a>프로젝트를 클라우드 서비스로 마이그레이션

1. 솔루션 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가 > 새 프로젝트 ...** 를 선택 하 고 새 **Azure 클라우드 서비스 (클래식)** 프로젝트를 기존 솔루션에 추가 합니다.
1. **새 Microsoft Azure 클라우드 서비스 (클래식)** 대화 상자에서 프로젝트에 역할을 추가 하지 않고 확인을 클릭 합니다.
1. 새로 추가 된 Cloud Services 프로젝트에서 역할 노드를 마우스 오른쪽 단추로 클릭 하 고 **솔루션에서 웹 역할 프로젝트 추가**...를 선택 합니다.
1. **역할 프로젝트에 연결** 대화 상자에서 웹 역할로 연결할 프로젝트를 선택 합니다.

   > [!Important]
   > 이 웹 애플리케이션에 필요한 다른 어셈블리 또는 파일이 있는 경우 이러한 파일에 대한 속성을 수동으로 설정해야 합니다. 이러한 속성을 설정하는 방법은 [서비스 패키지에 파일 포함](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package)을 참조하세요.

### <a name="errors-and-warnings"></a>오류 및 경고

발생하는 모든 경고 또는 오류는 어셈블리 누락처럼 Azure에 배포하기 전에 해결해야 하는 문제를 나타냅니다.

애플리케이션을 빌드하고 컴퓨팅 에뮬레이터를 사용하여 로컬로 실행하거나 Azure에 게시할 경우 "지정한 경로 및/또는 파일 이름이 너무 깁니다."라는 오류가 표시될 수 있습니다. 이 오류는 정규화된 Azure 프로젝트 이름이 146자를 초과한다는 의미입니다. 이 문제를 해결하려면 경로 길이가 짧은 폴더로 솔루션을 이동합니다.

경고를 오류로 처리하는 방법은 [Visual Studio에서 Azure 클라우드 서비스 프로젝트 구성](vs-azure-tools-configuring-an-azure-project.md)을 참조하세요.

### <a name="test-the-migration-locally"></a>로컬로 마이그레이션 테스트

1. Visual Studio **솔루션 탐색기**에서 추가된 클라우드 서비스 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 클릭합니다.
1. **디버그 > 디버깅 시작**(F5)을 선택하여 Azure 디버깅 환경을 시작합니다. 이 환경은 다양한 Azure 서비스 에뮬레이션을 제공합니다.

### <a name="use-an-azure-sql-database-for-your-application"></a>애플리케이션에 Azure SQL Database 사용

온-프레미스 SQL Server 데이터베이스를 사용하는 웹 애플리케이션에 대한 연결 문자열이 있는 경우, 그 대신 데이터베이스를 Azure SQL Database로 마이그레이션하고 연결 문자열을 업데이트해야 합니다. 이 프로세스에 대한 지침은 다음 항목을 참조하세요.

- [클라우드에서 SQL Database로 SQL Server 데이터베이스 마이그레이션](/azure/sql-database/sql-database-cloud-migrate)
- [Visual Studio에서 .NET(C#)을 사용하여 Azure SQL 데이터베이스 연결 및 쿼리](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>애플리케이션을 Azure Cloud Service에 게시

1. [Visual Studio에서 Azure 애플리케이션 게시 또는 배포 준비](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)의 설명에 따라 Azure 구독에서 필요한 클라우드 서비스 및 스토리지 계정을 만듭니다.
1. Visual Studio에서 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Microsoft Azure에 게시... **("게시…" 명령과 다름)를 선택합니다.
1. 나타나는 **Azure 애플리케이션 게시**에서, 계정을 사용하여 Azure 구독에 로그인하고 **다음 &gt;** 을 선택합니다.
1. 선택한 환경 및 구성에 맞는 대상 클라우드 서비스를 **설정 > 일반 설정** 탭의 **클라우드 서비스** 드롭다운 목록에서 선택합니다.
1. **설정 &gt; 고급 설정**에서 사용할 스토리지 계정을 선택하고 **다음 &gt;** 을 선택합니다.
1. **진단**에서 Application Insights에 정보를 보낼 것인지 선택합니다.
1. **다음 >** 을 선택하여 요약 정보를 살펴본 후 **게시**를 선택하여 배포를 시작합니다.
1. Visual Studio에서 진행률을 추적할 수 있는 활동 로그 창이 열립니다.

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (선택 사항) 배포 프로세스를 취소하려면 활동 로그에서 개별 항목을 마우스 오른쪽 단추로 클릭하고 **취소한 후 제거**를 선택합니다. 이 명령은 배포 프로세스를 중지하고 Azure에서 배포 환경을 삭제합니다. 참고: 이 배포 환경을 배포한 후 제거하려면 [Azure Portal](https://portal.azure.com)을 사용해야 합니다.
1. (선택 사항) 역할 인스턴스가 시작되면 Visual Studio의 **서버 탐색기 > Cloud Services** 노드에 자동으로 배포 환경이 표시됩니다. 여기에서 개별 역할 인스턴스의 상태를 볼 수 있습니다.
1. 배포 후 애플리케이션에 액세스하려면 **Azure 활동 로그**에 URL과 함께 **완료됨** 상태가 나타날 때 배포 옆의 화살표를 선택합니다. Azure에서 특정 유형의 웹 애플리케이션을 시작하는 방법은 다음 표를 참조하세요.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>컴퓨팅 에뮬레이터를 사용하여 Azure에서 애플리케이션 시작

모든 종류의 애플리케이션은 **디버그 &gt; 디버깅 시작**(F5)을 선택하여 Visual Studio 디버거에 연결된 브라우저에서 시작할 수 있습니다. ASP.NET 빈 웹 애플리케이션 프로젝트를 사용하는 경우 먼저 애플리케이션에 `.aspx` 페이지를 추가하고 웹 프로젝트의 시작 페이지로 설정해야 합니다.

다음 표에는 Azure에서 애플리케이션을 시작하는 방법이 자세히 설명되어 있습니다.

| 웹 애플리케이션 유형 | Azure에서 실행 |
| --- | --- |
| ASP.NET 웹 애플리케이션<br/>(MVC 2, MVC 3, MVC 4 포함) | **Azure 활동 로그**의 **배포** 탭에서 URL을 선택합니다. |
| ASP.NET 빈 웹 애플리케이션 | 애플리케이션에 기본 `.aspx` 페이지가 있는 경우 **Azure 활동 로그**의 **배포** 탭에서 URL을 선택합니다. 다른 페이지로 이동하려면 브라우저에서 `<deployment_url>/<page_name>.aspx` 양식의 URL을 입력합니다. |
| WCF 서비스 애플리케이션<br/>WCF 워크플로 서비스 애플리케이션 | `.svc` 파일을 WCF 서비스 프로젝트의 시작 페이지로 설정합니다. 그런 다음 `<deployment_url>/<service_file>.svc`로 이동합니다. |
| ASP.NET 동적 엔터티<br/>SQL에 대한 ASP.NET Dynamic Data Linq | 다음 섹션의 설명에 따라 연결 문자열을 업데이트합니다. 그런 다음 `<deployment_url>/<page_name>.aspx`로 이동합니다. Linq to SQL의 경우 Azure SQL 데이터베이스를 사용해야 합니다. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>ASP.NET 동적 엔터티의 연결 문자열 업데이트

1. 앞에서 설명한 (#Use-an-azuresql-database-for-your-application)에 따라 ASP.NET 동적 엔터티 웹 애플리케이션에 대한 SQL Azure 데이터베이스를 만듭니다.
1. Azure Portal에서 이 데이터베이스에 필요한 테이블과 필드를 추가합니다.
1. `web.config` 파일에서 연결 문자열을 다음 형식으로 지정하고 파일을 저장합니다.

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    다음과 같이 SQL Azure 데이터베이스의 ADO.NET 연결 문자열을 사용하여 *connectionString* 값을 업데이트합니다.

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>지원되는 프로젝트 템플릿

클라우드 서비스로 마이그레이션 및 게시할 수 있는 애플리케이션은 아래 표의 템플릿 중 하나를 사용해야 합니다. ASP.NET Core는 지원되지 않습니다.

| 템플릿 그룹 | 프로젝트 템플릿 |
| --- | --- |
| 웹 | ASP.NET 웹 애플리케이션(.NET Framework) |
| 웹 | ASP.NET MVC 2 웹 애플리케이션 |
| 웹 | ASP.NET MVC 3 웹 애플리케이션 |
| 웹 | ASP.NET MVC4 웹 애플리케이션 |
| 웹 | ASP.NET 빈 웹 애플리케이션(또는 사이트) |
| 웹 | ASP.NET MVC 2 빈 웹 애플리케이션 |
| 웹 | ASP.NET 동적 데이터 엔터티 웹 애플리케이션 |
| 웹 | SQL 웹 애플리케이션에 대한 ASP.NET Dynamic Data Linq |
| WCF | WCF 서비스 애플리케이션 |
| WCF | WCF 워크플로 서비스 애플리케이션 |
| 워크플로 | WCF 워크플로 서비스 애플리케이션 |

## <a name="next-steps"></a>다음 단계

- [Visual Studio에서 Azure 애플리케이션 게시 또는 배포 준비](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [명명 된 인증 자격 증명을 설정](vs-azure-tools-setting-up-named-authentication-credentials.md)합니다.
