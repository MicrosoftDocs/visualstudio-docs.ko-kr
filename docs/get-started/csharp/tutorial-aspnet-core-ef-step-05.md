---
title: '5단계: Azure에 ASP.NET Core 앱 배포'
description: 이 동영상 자습서 및 단계별 지침을 사용하여 Azure에 ASP.NET Core 웹앱을 배포합니다.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: dc13dbdadb0c9bca25a816b15c5a99039bff454c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580024"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>5단계: Azure에 ASP.NET Core 앱 배포

다음 단계에 따라 ASP.NET Core 앱과 해당 데이터베이스를 Azure에 배포합니다.

_이 동영상에 따라 Azure에 첫 번째 ASP.NET Core 앱을 배포합니다._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>프로젝트 열기

Visual Studio 2019에서 ASP.NET Core 앱을 엽니다. [이 자습서 시리즈의 4단계](tutorial-aspnet-core-ef-step-04.md)에 구성된 대로 앱에서 EF Core를 통한 설정과 작동하는 웹 API를 이미 사용하고 있어야 합니다.

## <a name="publish-to-azure-app-service"></a>Azure App Service에 게시

솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다. **App Service** 및 **새로 만들기**의 기본 설정을 그대로 사용하고 **게시** 단추를 클릭합니다. Azure 계정이 아직 없는 경우 **Azure 체험 계정 만들기**를 클릭하고 간단한 등록 프로세스를 완료합니다.

SQL Server를 추가합니다. 관리자 사용자 이름 및 암호를 지정합니다.

![Visual Studio 2019 Azure SQL Server 만들기](media/vs-2019/vs2019-azure-sql-server.png)

Application Insights를 추가합니다.

**만들기** 단추를 클릭하여 계속합니다.

![Visual Studio 2019 새 Azure App Service 만들기](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Azure Portal 및 호스트된 앱 살펴보기

App Service가 만들어지면 사이트가 브라우저에서 시작됩니다. 또한 Azure Portal에서 App Service를 찾을 수 있습니다. App Service의 사용 가능한 옵션을 살펴보면 앱을 시작하고 중지할 수 있는 **개요** 섹션을 찾을 수 있습니다.

![Azure App Service 옵션](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>확장성

앱을 강화하고 스케일 아웃하는 옵션을 살펴볼 수 있습니다. 강화는 앱을 호스트하는 각 인스턴스에 제공되는 리소스를 늘리는 것을 말합니다. 스케일 아웃은 앱을 호스트하는 인스턴스 수를 늘리는 것을 말합니다. 자동으로 부하에 따라 앱을 호스트하는 데 사용되는 인스턴스 수를 늘린 후 부하가 감소하면 해당 인스턴스를 줄이는 앱의 자동 크기 조정을 구성할 수 있습니다.

### <a name="security-and-compliance"></a>보안 및 규정 준수

Azure를 사용하여 앱을 호스트하는 또 다른 이점은 보안 및 규정 준수입니다. Azure App Service는 ISO SOC 및 PCI 규정 준수를 제공합니다. Azure Active Directory를 사용하거나 Twitter, Facebook, Google 또는 Microsoft 같은 소셜 로그인을 사용하여 사용자를 인증하도록 선택할 수 있습니다. IP 제한 사항을 만들고, 서비스 ID를 관리하고, 사용자 지정 도메인을 추가하고, 앱의 SSL을 지원할 뿐 아니라 앱 콘텐츠, 구성 및 데이터베이스의 복원 가능한 보관 복사본을 사용하여 백업을 구성할 수 있습니다. 이 기능은 [인증/권한 부여], [ID], [백업] 및 [SSL 설정] 메뉴 옵션에서 액세스합니다.

### <a name="deployment-slots"></a>배포 슬롯

일반적으로 앱을 배포할 때 앱이 다시 시작되는 동안 잠시 가동이 중지됩니다. 배포 슬롯을 사용하면 별도의 스테이징 인스턴스 또는 인스턴스 세트에 배포하고 프로덕션으로 전환하기 전에 이 인스턴스를 준비할 수 있어 이 문제를 피할 수 있습니다. 전환은 즉각적이고 원활한 트래픽 리디렉션입니다. 전환한 후 프로덕션에 문제가 있으면 항상 마지막으로 알려진 정상 프로덕션 상태로 다시 전환할 수 있습니다.

## <a name="update-connection-string"></a>연결 문자열 업데이트

기본적으로 Azure에서는 새 앱이 새 SQL Server 데이터베이스에 연결할 때 `DefaultConnection`이라는 연결 문자열을 사용해야 합니다. 현재 이 자습서의 앞부분에서 만든 앱은 `AppDbContext`라는 연결 문자열을 사용합니다. *appsettings.json* 및 *Startup.cs*에서 이 문자열을 변경한 후 앱을 다시 배포해야 합니다.

## <a name="test-the-app-running-in-azure"></a>Azure에서 실행 중인 앱 테스트

*/Games* 경로로 이동하여 새 게임을 추가하고 나열된 게임을 확인할 수 있습니다. 그런 다음, */swagger* 경로로 이동하고 여기서 웹 API 엔드포인트를 사용하여 앱 API가 작동하는지 확인합니다.

지금까지 이 동영상 자습서 시리즈를 완료했습니다.

## <a name="next-steps"></a>다음 단계

다음 무료 리소스에서 ASP.NET Core 애플리케이션을 설계하는 방법을 자세히 알아보세요.

[ASP.NET Core 애플리케이션 아키텍처](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>참조

- [Visual Studio를 사용하여 Azure에 ASP.NET Core 앱 게시](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)