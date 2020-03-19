---
title: 고급 기능
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65ce2b986114dc553b87db846262c931d74b4c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78235201"
---
# <a name="features-of-visual-studio"></a>Visual Studio의 기능

[Visual Studio IDE 개요](../get-started/visual-studio-ide.md) 문서에서는 Visual Studio에 대한 기본적인 소개를 제공합니다. 이 문서에서는 숙련된 개발자 또는 이미 Visual Studio에 익숙한 개발자에게 보다 적합한 기능에 대해 설명합니다.

## <a name="modular-installation"></a>모듈식 설치

Visual Studio의 모듈식 설치 관리자를 사용하면 *워크로드*를 선택하고 설치할 수 있습니다. 워크로드는 선호하는 프로그래밍 언어 또는 플랫폼에 필요한 기능의 그룹입니다. 이 전략을 통해 Visual Studio 설치에 필요한 공간을 더 작게 유지할 수 있습니다. 즉 Visual Studio를 설치하고 업데이트하는 속도도 매우 빨라집니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range=">=vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

시스템에 Visual Studio를 설치하는 방법에 대한 자세한 내용은 [Visual Studio 설치](../install/install-visual-studio.md)를 참조하세요.

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure용 클라우드 사용 앱 만들기

Visual Studio는 Microsoft Azure에서 구동하는 클라우드 지원 애플리케이션을 쉽게 만들 수 있는 도구 모음을 제공합니다. IDE에서 직접 Microsoft Azure의 애플리케이션과 서비스를 구성, 빌드, 디버그, 패키징 및 배포할 수 있습니다. Azure 도구 및 템플릿을 받으려면 Visual Studio를 설치할 때 **Azure 개발** 워크로드를 선택합니다.

![Azure 개발 워크로드](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

**Azure 개발** 워크로드를 설치한 후, **새 프로젝트** 대화 상자에서 다음과 같은 C#용 **클라우드** 템플릿을 사용할 수 있습니다.

![Visual Studio용 클라우드 프로젝트 템플릿](media/cloud-project-templates.png)

::: moniker-end

Visual Studio의 [클라우드 탐색기](/azure/vs-azure-tools-resources-managing-with-cloud-explorer)를 사용하여 Visual Studio 내에서 Azure 기반 클라우드 리소스를 보고 관리할 수 있습니다. 이러한 리소스에는 가상 머신, 테이블, SQL 데이터베이스 등이 포함될 수 있습니다. **클라우드 탐색기**에서는 로그인한 Azure 구독으로 관리되는 모든 계정의 Azure 리소스를 보여 줍니다. 그리고 특정 작업에 Azure Portal이 필요한 경우 **클라우드 탐색기**에 이동해야 하는 포털 내 위치로 이동하는 링크가 제공됩니다.

![Visual Studio의 클라우드 탐색기](media/cloud-explorer.png)

다음과 같이 **연결된 서비스**를 통해 앱에 대한 Azure 서비스를 활용할 수 있습니다.

- 사용자가 [Azure Active Directory](/azure/active-directory/active-directory-whatis)의 계정을 사용하여 웹앱에 연결할 수 있도록 [Active Directory에 연결된 서비스](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- Blob 스토리지, 큐 및 테이블용 [Azure Storage 연결 서비스](/azure/vs-azure-tools-connected-services-storage)
- 웹앱의 비밀 관리를 위한 [Key Vault 연결 서비스](/azure/key-vault/vs-key-vault-add-connected-service)

사용 가능한 **연결된 서비스**는 프로젝트 형식에 따라 다릅니다. **솔루션 탐색기**의 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **연결된 서비스**를 선택하여 서비스를 추가합니다.

![Visual Studio에 연결된 서비스](media/connected-services.png)

자세한 내용은 [Visual Studio 및 Azure를 사용하여 클라우드로 이동](https://visualstudio.microsoft.com/vs/azure-tools/)을 참조하세요.

## <a name="create-apps-for-the-web"></a>웹앱 만들기

웹은 현대 세계를 이끌고 있고, Visual Studio에서 이를 위한 앱을 작성할 수 있습니다. ASP.NET, Node.js, Python, JavaScript 및 TypeScript를 사용하여 웹앱을 만들 수 있습니다. Visual Studio는 Angular, jQuery, Express 등과 같은 웹 프레임워크를 이해합니다. ASP.NET Core 및 .NET Core는 Windows, Mac 및 Linux 운영 체제에서 실행됩니다. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)는 MVC, WebAPI 및 SignalR에 대한 주요 업데이트이며 Windows, Mac 및 Linux에서 실행됩니다.  ASP.NET Core는 최신 클라우드 기반 웹앱 및 서비스를 빌드하기 위한 간결하고 구성 가능한 .NET 스택을 제공하도록 처음부터 다시 설계되었습니다.

자세한 내용은 [최신 웹 도구](https://visualstudio.microsoft.com/vs/modern-web-tooling/)를 참조하세요.

## <a name="build-cross-platform-apps-and-games"></a>플랫폼 간 앱 및 게임 제작

Visual Studio를 사용하여 Android, iOS 및 기타 [모바일 디바이스](https://visualstudio.microsoft.com/vs/mobile-app-development/)뿐 아니라 macOS, Linux, Windows용 앱과 게임을 빌드할 수 있습니다.

- Windows, macOS 및 Linux에서 실행되는 [.NET Core](/dotnet/core/) 앱을 빌드합니다.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)을 사용하여 C# 및 F#으로 iOS, Android 및 Windows용 모바일 앱을 빌드합니다.

- HTML, CSS, JavaScript 등의 표준 웹 기술을 사용하여 [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)로 iOS, Android 및 Windows용 모바일 앱을 빌드할 수 있습니다.

- [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md)를 사용하여 C#으로 2D 및 3D 게임을 빌드합니다.

- iOS, Android 및 Windows 디바이스용 네이티브 C++ 앱을 빌드합니다. [플랫폼 간 개발용 C++](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)를 사용하여 iOS, Android 및 Windows용으로 빌드된 라이브러리에서 공통 코드를 공유합니다.

- [Android Emulator](../cross-platform/visual-studio-emulator-for-android.md)를 사용하여 Android 앱을 배포, 테스트 및 디버그합니다.

## <a name="connect-to-databases"></a>데이터베이스에 연결

**서버 탐색기**를 사용하면 원격으로, 로컬로, Azure, Salesforce.com, Office 365 및 웹 사이트에서 SQL Server 인스턴스와 자산을 찾아보고 관리할 수 있습니다. **서버 탐색기**를 열려면 주 메뉴에서 **보기** > **서버 탐색기**를 선택합니다. 서버 탐색기 사용에 대한 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)를 참조하세요.

[SSDT(SQL Server Data Tools)](/sql/ssdt/download-sql-server-data-tools-ssdt)는 SQL Server, Azure SQL Database 및 Azure SQL Data Warehouse를 위한 강력한 개발 환경입니다. 이 도구를 사용하면 데이터베이스를 빌드, 디버그, 유지 관리 및 리팩터링할 수 있습니다. 데이터베이스 프로젝트에 대해 작업하거나, 온-프레미스 또는 오프-프레미스로 연결된 데이터베이스 인스턴스에 대해 직접 작업할 수 있습니다.

Visual Studio의 **SQL Server 개체 탐색기**는 SQL Server Management Studio와 비슷한 데이터베이스 개체 보기를 제공합니다. SQL Server 개체 탐색기를 사용하면 소규모 데이터베이스 관리 및 디자인 작업을 수행할 수 있습니다. 작업의 예로는 SQL Server 개체 탐색기에서 바로 테이블 데이터 편집, 스키마 비교, 상황에 맞는 메뉴를 사용하여 쿼리 실행 등이 있습니다.

![SQL Server 개체 탐색기](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>코드 디버그, 테스트 및 향상

코드를 작성할 때 이를 실행하고 버그와 성능을 테스트해야 합니다. Visual Studio의 최신 디버깅 시스템을 사용하면 로컬 프로젝트에서 실행 중인 코드를 원격 디바이스 또는 [디바이스 에뮬레이터](../cross-platform/visual-studio-emulator-for-android.md)에서 디버그할 수 있습니다. 한 번에 문 하나씩, 코드를 단계별로 실행하고 변수를 검사할 수 있습니다. 지정된 조건이 true인 경우에만 적중되는 중단점을 설정할 수 있습니다. 디버그 옵션을 코드 편집기 자체에서 관리할 수 있으므로 코드를 떠날 필요가 없습니다. Visual Studio의 디버깅에 대한 자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

앱 성능 향상에 대한 자세한 내용은 Visual Studio의 [프로파일링](../profiling/profiling-feature-tour.md) 기능을 참조하세요.

[테스트](../test/improve-code-quality.md)를 위해 Visual Studio는 단위 테스트, Live Unit Testing, IntelliTest, 부하 및 성능 테스트 등을 제공합니다. Visual Studio에는 디자인, 보안 및 기타 형식의 결함을 파악하는 고급 [코드 분석](../code-quality/code-analysis-for-managed-code-overview.md) 기능도 있습니다.

## <a name="deploy-your-finished-application"></a>완성된 애플리케이션 배포

애플리케이션을 사용자나 고객에게 배포할 준비가 되었을 때 Visual Studio에서 제공하는 도구를 사용하여 해당 작업을 수행할 수 있습니다. 배포 옵션으로는 Microsoft Store에 배포, SharePoint 사이트에 배포, InstallShield 또는 Windows Installer 기술을 사용한 배포가 있습니다. 이 경우 IDE를 통해 모두 액세스할 수 있습니다. 자세한 내용은 [애플리케이션, 서비스 및 구성 요소 배포](../deployment/deploying-applications-services-and-components.md)를 참조하세요.

## <a name="manage-your-source-code-and-collaborate-with-others"></a>소스 코드 관리 및 다른 사용자와 공동 작업

GitHub를 포함한 모든 공급자가 호스팅하는 Git 리포지토리에서 원본 코드를 관리할 수 있습니다. 또는 [Azure DevOps Services](/azure/devops/index)를 사용하여 전체 프로젝트의 버그 및 작업 항목과 함께 코드를 관리하세요. Visual Studio에서 팀 탐색기를 사용하여 Git 리포지토리를 관리하는 방법에 대해 알아보려면 [Git 및 Azure Repos 시작하기](/azure/devops/repos/git/gitquickstart?tabs=visual-studio)를 참조하세요. Visual Studio에는 기본 제공된 다른 소스 제어 기능이 있습니다. 이에 대한 자세한 내용은 [Visual Studio의 새로운 Git 기능(블로그)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/)을 참조하세요.

Azure DevOps Services는 소프트웨어를 계획, 호스트, 자동화 및 배포하고 팀의 협업을 지원하기 위한 클라우드 기반 서비스입니다. Azure DevOps Services는 Git 리포지토리(분산형 버전 제어) 및 Team Foundation 버전 제어(중앙 집중식 버전 제어)를 둘 다 지원합니다. 버전 제어 시스템에 저장된 코드의 연속 빌드 및 릴리스(CI/CD)를 위한 파이프라인을 지원합니다. 또한 Azure DevOps Services는 스크럼, CMMI 및 Agile 개발 방법론도 지원합니다.

TFS(Team Foundation Server)는 Visual Studio용 애플리케이션 수명 주기 관리 허브입니다. 개발 프로세스와 관련된 모든 사람이 단일 솔루션을 사용하여 참여할 수 있도록 해줍니다. TFS는 성격이 다른 팀과 프로젝트들을 관리하는 데 유용합니다.

네트워크에 Azure DevOps 조직 또는 Team Foundation Server가 있는 경우 Visual Studio의 **팀 탐색기** 창을 통해 연결합니다. 이 창에서 코드를 소스 제어에 체크 인 또는 체크 아웃하고, 작업 항목을 관리하고, 빌드를 시작하고, 단체 방 및 작업 영역에 액세스할 수 있습니다. 검색 상자나 **보기** > **팀 탐색기** 또는 **팀** > **연결 관리**의 주 메뉴에서 **팀 탐색기**를 열 수 있습니다.

다음 이미지는 Azure DevOps Services에서 호스트되는 솔루션에 대한 **팀 탐색기** 창을 보여 줍니다.

![Visual Studio 팀 탐색기](../ide/media/vs2017_teamexplorer_devops.png)

팀의 개발자들이 버전 제어에 체크 인한 코드를 빌드하도록 빌드 프로세스를 자동화할 수도 있습니다. 예를 들어 밤마다 또는 코드를 체크 인할 때마다 하나 이상의 프로젝트를 빌드할 수 있습니다. 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)를 참조하세요.

## <a name="extend-visual-studio"></a>Visual Studio 확장

요구되는 적절한 기능이 Visual Studio에 없으면 추가할 수 있습니다! 워크플로와 스타일에 따라 IDE를 개인 설정하고, Visual Studio와 아직 통합되지 않은 외부 도구에 대한 지원을 추가하고, 기존 기능을 수정하여 생산성을 높일 수 있습니다. 최신 버전의 Visual Studio 확장성 도구(VS SDK)를 찾으려면 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하세요.

.NET 컴파일러 플랫폼("Roslyn")을 사용하여 사용자 고유의 코드 분석기 및 코드 생성기를 작성할 수 있습니다. [Roslyn](https://github.com/dotnet/Roslyn)(영문)에서 필요한 모든 항목을 찾으세요.

Microsoft 개발자와 개발 커뮤니티에서 만든 [기존 Visual Studio용 확장](https://marketplace.visualstudio.com/vs)을 찾아 보세요.

Visual Studio 확장에 대한 자세한 내용은 [Visual Studio IDE 확장](https://visualstudio.microsoft.com/vs/extend/)을 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)
- [Visual Studio 2017의 새로운 기능](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019의 새로운 기능](../ide/whats-new-visual-studio-2019.md)
