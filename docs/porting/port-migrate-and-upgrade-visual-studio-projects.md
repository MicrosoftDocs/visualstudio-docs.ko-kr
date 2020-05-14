---
title: 프로젝트 포팅, 마이그레이션 및 업그레이드
description: 현재 및 이전 버전의 Visual Studio에서 만든 프로젝트 지원에 대한 참조입니다.
ms.date: 11/26/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload: multiple
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.openlocfilehash: 221fd38b6035c1e41d9a768f5e30117dd3f4d35c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75406343"
---
# <a name="project-migration-and-upgrade-reference-for-visual-studio"></a>프로젝트 마이그레이션 및 Visual Studio에 대한 업그레이드 참조

::: moniker range="vs-2017"

각 버전의 Visual Studio에서는 일반적으로 이전 형식의 프로젝트, 파일 및 기타 자산을 대부분 지원합니다. 이러한 항목을 [이전처럼](../ide/solutions-and-projects-in-visual-studio.md) 사용할 수 있습니다. 최신 기능에 의존하지 않을 경우 Visual Studio에서는 Visual Studio 2015, Visual Studio 2013, Visual Studio 2012와 같은 이전 버전과의 호환성을 유지하려 합니다. 버전별로 특정한 기능은 [릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes/)를 참조하세요.

일부 프로젝트 형식 변경은 이후에 지원될 수 있습니다. 최신 버전의 Visual Studio에서 특정 프로젝트를 더 이상 지원하지 않거나, 더 이상 이전 버전과 호환되지 않도록 프로젝트를 업데이트할 수 있습니다. 마이그레이션 문제의 현재 상태는 [Visual Studio 개발자 커뮤니티 사이트](https://developercommunity.visualstudio.com)를 참조하세요.

이 현재 문서에서는 Visual Studio 2017에서 마이그레이션할 수 있는 프로젝트 형식에 대해서만 세부 정보를 제공합니다. 이 문서에서는 Visual Studio 2017에서 더 이상 지원되지 않는 프로젝트 유형을 제외하므로 마이크레이션할 수 없습니다. 이 문서에서는 마이그레이션 문제가 없는 지원되는 프로젝트 유형도 제외됩니다. 해당 목록은 [플랫폼 대상 지정 및 호환성](/visualstudio/productinfo/vs2017-compatibility-vs)에서 확인할 수 있습니다.

> [!IMPORTANT]
> 특정 프로젝트 형식은 Visual Studio 설치 관리자를 통해 적절한 워크로드를 설치해야 합니다. 워크로드가 설치되어 있지 않으면 Visual Studio에서 알 수 없거나 호환되지 않는 프로젝트 형식을 보고합니다. 이 경우 설치 옵션을 확인하고 다시 시도하세요. Visual Studio 2017의 프로젝트 지원에 대한 자세한 내용은 [플랫폼 대상 지정 및 호환성](/visualstudio/productinfo/vs2017-compatibility-vs) 문서를 참조하세요.

## <a name="project-types"></a>프로젝트 형식

다음 목록에서는 이전 버전에서 만든 프로젝트에 대한 Visual Studio 2017의 지원에 대해 설명합니다.

여기에 나열된 프로젝트 또는 파일 형식이 표시되지 않는 경우 [이 문서의 Visual Studio 2015 버전](/visualstudio/porting/porting-migrating-and-upgrading-visual-studio-projects?view=vs-2015)을 참조하고 이 페이지의 맨 아래에 **이 페이지에 대한** > **피드백 보내기** 옵션을 사용하여 프로젝트의 세부 정보를 제공해 주세요. (익명으로 “이 페이지가 도움이 되었나요?” 컨트롤을 사용하면 피드백에 응답할 수 없습니다.)

| 프로젝트 형식 | 고객 지원팀 |
| --- | --- |
| .NET Core 프로젝트(.xproj) | Visual Studio 2015로 만든 프로젝트는 xproj 프로젝트 파일을 포함하는 미리 보기 도구를 사용했습니다. Visual Studio 2017에서 xproj 형식은 csproj 형식으로 마이그레이션해야만 지원됩니다. xproj 파일을 열면 파일을 SDK 스타일의 csproj 형식으로 마이그레이션해야 한다는 메시지가 표시됩니다. (xproj 파일의 백업이 생성됩니다.) SDK 스타일의 csproj 프로젝트는 Visual Studio 2015 및 이전 버전에서 지원되지 않습니다. 자세한 내용은 [csproj 형식으로 .NET Core 프로젝트 마이그레이션](/dotnet/core/migration/#visual-studio)을 참조하세요.|
| Application Insights를 사용하도록 지정한 ASP.NET 웹 애플리케이션 및 ASP.NET Core 웹 애플리케이션 | 각 Visual Studio 사용자의 리소스 정보가 사용자 인스턴스별 레지스트리에 저장됩니다. 이 정보는 사용자가 프로젝트를 열지 않고 Azure Application Insights 데이터를 검색하려는 경우에 사용됩니다. Visual Studio 2015에서는 Visual Studio 2017과 다른 레지스트리 위치를 사용하므로 충돌하지 않습니다.<br/><br/>사용자가 ASP.NET 웹 애플리케이션 또는 ASP.NET Core 웹 애플리케이션을 만들면 리소스가 .suo 파일에 저장됩니다. 사용자는 Visual Studio 2015 또는 2017에서 프로젝트를 열 수 있으며, Visual Studio에서 두 버전 간 사용 중인 프로젝트 및 솔루션이 지원될 경우 두 버전 모두에서 리소스 정보가 사용됩니다. 사용자는 각 제품에 대해 한 번 인증해야 합니다. 예를 들어 Visual Studio 2015에서 프로젝트를 만든 다음 Visual Studio 2017에서 열 경우 사용자는 Visual Studio 2017에서 인증해야 합니다. |
| C#/Visual Basic Webform 또는 Windows Form | Visual Studio 2017 및 Visual Studio 2015에서 프로젝트를 열 수 있습니다. |
| 데이터베이스 유닛 테스트 프로젝트(csproj, .vbproj) | 이전 데이터 유닛 테스트 프로젝트는 Visual Studio 2017에 로드되지만 GAC 종속성 버전을 사용합니다. 최신 종속성을 사용하도록 단위 테스트 프로젝트를 업그레이드하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **SQL Server 단위 테스트 프로젝트로 변환...** 을 선택합니다. |
| F# | Visual Studio 2017에서는 Visual Studio 2013 및 2015에서 만든 프로젝트를 열 수 있습니다. 이러한 프로젝트에서 Visual Studio 2017 기능을 사용하려면 프로젝트 속성을 열고 대상 fsharp.core를 F# 4.1로 변경합니다. Visual Studio 설치 관리자의 **F# 언어 지원** 옵션은 기본적으로 .NET 워크로드와 함께 선택되지 않습니다. 워크로드에 대해 해당 옵션을 선택하거나 **개발 작업** 아래 **개별 구성 요소** 탭에서 해당 옵션을 선택하여 포함해야 합니다. |
| InstallShield<br/>MSI 설정 | Visual Studio 2010에서 만든 설치 관리자 프로젝트는 [Visual Studio 설치 관리자 프로젝트 확장](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects)을 사용하여 이후 버전에서 열 수 있습니다. 또한 [WiX 도구 집합 Visual Studio 2017 확장](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)을 참조하세요. InstallShield Limited Edition은 더 이상 Visual Studio에 포함되지 않습니다. Visual Studio 2017에 대한 가용성은 [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)에서 확인하세요. |
| LightSwitch | LightSwitch는 Visual Studio 2017에서 더 이상 지원되지 않습니다. Visual Studio 2012 이전 버전에서 만들고 Visual Studio 2013 또는 Visual Studio 2015에서 연 프로젝트는 업그레이드되며 이후에는 Visual Studio 2013 또는 Visual Studio 2015에서만 열 수 있습니다. |
| Visual Studio용 Microsoft Azure 도구 | 이러한 형식의 프로젝트를 열려면 먼저 [Azure SDK for.NET](https://azure.microsoft.com/downloads/)을 설치한 다음 프로젝트를 엽니다. 필요한 경우 프로젝트가 업데이트됩니다. |
| 모델-뷰-컨트롤러 프레임워크(ASP.NET MVC) | MVC 버전 및 Visual Studio 지원:<ul><li>Visual Studio 2010 SP1은 MVC 2 및 MVC 3을 지원합니다. MVC 4 지원은 [Visual Studio 2010 SP1용 ASP.NET 4 MVC 4 다운로드](https://www.microsoft.com/download/details.aspx?id=30683)를 통해 추가됩니다.</li><li>Visual Studio 2012에서는 MVC 3 및 MVC 4만 지원합니다.</li><li>Visual Studio 2013에서는 MVC 4 및 MVC 5만 지원합니다.</li><li>Visual Studio 2017 및 Visual Studio 2015는 MVC 4(기존 프로젝트는 열 수 있지만 새 프로젝트는 만들 수 없음) 및 MVC 5를 지원합니다.</li></ul><br/>MVC 버전 업그레이드:<ul><li>MVC 2에서 MVC 3로 자동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 애플리케이션 업그레이더](https://archive.codeplex.com/?p=aspnet)를 참조하세요.</li><li>MVC 2에서 MVC 3로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 도구 업데이트로 ASP.NET MVC 2 프로젝트 업그레이드](https://archive.codeplex.com/?p=aspnet)를 참조하세요.</li><li>MVC 3에서 MVC 4로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 프로젝트를 ASP.NET MVC 4로 업그레이드](/aspnet/whitepapers/mvc4-release-notes)를 참조하세요. 프로젝트 대상이 .NET Framework 3.5 SP1일 경우 대상을 변경하여 .NET Framework 4를 사용해야 합니다.</li><li>MVC 4에서 MVC 5로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 4 및 Web API 프로젝트를 ASP.NET MVC 5 및 Web API 2로 업그레이드하는 방법](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2)을 참조하세요.</li></ul> |
| 모델링 | Visual Studio에서 프로젝트를 자동으로 업데이트하도록 허용하면 Visual Studio 2015, Visual Studio 2013 또는 Visual Studio 2012에서 프로젝트를 열 수 있습니다.<br/><br/>모델링 프로젝트의 형식은 Visual Studio 2015 및 Visual Studio 2017 간에 변경되지 않으므로 어느 버전에서든 프로젝트를 열고 수정할 수 있습니다. 하지만 Visual Studio 2017의 동작에 차이가 있습니다.<ul><li>모델링 프로젝트를 메뉴 및 템플릿에서 “종속성 유효성 검사” 프로젝트라고 합니다.</li><li>UML 다이어그램은 Visual Studio 2017에서 더 이상 지원되지 않습니다. UML 파일은 솔루션 탐색기에 이전처럼 나열되지만 XML 파일로 열립니다. UML 다이어그램을 보거나, 만들거나, 편집하려면 Visual Studio 2015를 사용하세요.</li><li>Visual Studio 2017에서는 모델링 프로젝트를 빌드할 때 더 이상 아키텍처 종속성 유효성 검사가 수행되지 않습니다. 대신 각 코드 프로젝트를 빌드할 때 유효성 검사가 수행됩니다. 이 변경은 모델링 프로젝트에 영향을 주지 않지만 유효성을 검사할 코드 프로젝트를 변경해야 합니다. Visual Studio 2017에서는 필요한 경우 코드 프로젝트를 자동으로 변경할 수 있습니다([자세한 정보](/visualstudio/modeling/validate-code-with-layer-diagrams?view=vs-2017#live-dependency-validation)).</li></ul> |
| MSI 설정(vdproj) | InstallShield 프로젝트를 참조하세요. |
| Office 2007 VSTO | Visual Studio 2017에 단방향 업그레이드가 필요합니다. |
| Office 2010 VSTO | 프로젝트 대상이 .NET Framework 4일 경우 Visual Studio 2010 SP1 이상에서 이 프로젝트를 열 수 있습니다. 다른 모든 프로젝트에는 단방향 업그레이드가 필요합니다. |
| Service Fabric(sfproj) | Service Fabric 애플리케이션 프로젝트가 ASP.NET Core 서비스 프로젝트를 참조하지 않을 경우 Visual Studio 2015 또는 Visual Studio 2017에서 Service Fabric 애플리케이션 프로젝트를 열 수 있습니다. Visual Studio 2015의 Service Fabric 프로젝트를 Visual Studio 2017에서 여는 경우 xproj 형식에서 csproj 형식으로 단방향 마이그레이션됩니다. 이 표에서 앞부분에 있는 “.NET Core 프로젝트(xproj)”를 참조하세요. |
| SharePoint 2010 | Visual Studio 2017을 사용하여 SharePoint 솔루션 프로젝트를 열면 SharePoint 2013 또는 SharePoint 2016으로 업그레이드됩니다. 업그레이드를 위해서는 “.NET 데스크톱 개발” 워크로드가 Visual Studio 2017에 설치되어 있어야 합니다.<br/><br/>SharePoint 프로젝트를 업그레이드하는 방법에 대한 자세한 내용은 [SharePoint 2013으로 업그레이드](https://technet.microsoft.com/library/cc303420.aspx), [SharePoint Server 2013에서 워크플로 업데이트](https://technet.microsoft.com/library/dn133867.aspx) 및 [데이터베이스 연결 업그레이드를 위해 SharePoint Server 2016 팜 만들기](https://technet.microsoft.com/library/cc263026(v=office.16).aspx)를 참조하세요. |
| SharePoint 2016 | Office 개발자 도구 미리 보기 2에서 만든 SharePoint 추가 기능 프로젝트를 Visual Studio 2017에서 열 수 없습니다. 이 제한을 해결하려면 csproj 또는 vbproj 파일에 있는 `MinimumVisualStudioVersion`을 12.0으로, `MinimumOfficeToolsVersion`을 12.2로 업데이트합니다. |
| Silverlight | Silverlight 프로젝트는 Visual Studio 2017에서 지원되지 않습니다. Silverlight 애플리케이션을 유지하려면 Visual Studio 2015를 계속 사용합니다. |
| SQL Server Reporting Services 및 SQL Server Analysis Services(SSRS, SSDT, SSAS, MSAS) | 이러한 프로젝트 형식에 대한 지원은 Visual Studio 갤러리의 두 가지 확장 기능을 통해 제공됩니다.  [Microsoft Analysis Services 모델링 프로젝트](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) 및 [Microsoft Reporting Services 프로젝트](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). SSDT는 Visual Studio 2017에서 데이터 스토리지 및 처리 워크로드를 지원합니다. 자세한 내용은 [Visual Studio용 SSDT(SQL Server Data Tools) 다운로드 및 설치](/sql/ssdt/download-sql-server-data-tools-ssdt) 페이지를 참조하세요.|
| SSIS(SQL Server Integration Services) | Visual Studio 2017에 대한 지원은 SSDT(SQL Server Data Tools)를 통해 제공됩니다. 자세한 내용은 [Visual Studio용 SSDT(SQL Server Data Tools) 다운로드 및 설치](/sql/ssdt/download-sql-server-data-tools-ssdt) 페이지 및 [SSIS(SQL Server Integration Services)](https://techcommunity.microsoft.com/t5/SQL-Server-Integration-Services/bg-p/SSIS) 팀 블로그를 참조하세요. |
| Visual C++ | Visual Studio 2017을 사용하여 Visual Studio 2010까지 이전 버전의 Visual Studio에서 만든 프로젝트에서 작업할 수 있습니다. 프로젝트를 처음 열면 최신 컴파일러 및 도구 집합으로 업그레이드하거나 원래 항목을 계속 사용하는 옵션이 있습니다. 원래 항목을 계속 사용하도록 선택하면 Visual Studio 2017에서는 프로젝트 파일을 수정하지 않으며 이전 Visual Studio 설치의 도구 집합을 사용하여 프로젝트를 빌드합니다. 원래 옵션을 유지하는 것은 필요한 경우 원래 버전의 Visual Studio에서 프로젝트를 열 수 있음을 의미합니다. 자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](/cpp/porting/use-native-multi-targeting)를 참조하세요. |
| Visual Studio 확장성/VSIX | MinimumVersion 14.0 이하의 프로젝트는 업데이트를 통해 MinimumVersion 15.0으로 선언됩니다. 그러면 이전 버전의 Visual Studio에서 프로젝트를 열 수 없습니다. 이전 버전에서 프로젝트를 열 수 있도록 허용하려면 MinimumVersion을 `$(VisualStudioVersion)`(으)로 설정합니다. 참고 항목 [방법: Visual Studio 2017로 확장성 프로젝트 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Microsoft Test Manager 또는 Visual Studio 2010 SP1 이상을 사용하여 이러한 버전에서 만든 환경을 열 수 있습니다. 그러나 Visual Studio 2010 SP1의 경우 환경을 만들기 전에 Microsoft Test Manager 버전이 Team Foundation Server 버전과 일치해야 합니다. |
| Apache Cordova용 Visual Studio Tools | Visual Studio 2017에서 프로젝트를 열 수는 있지만 이전 버전과 호환되지 않습니다. Visual Studio 2015에서 프로젝트를 열면 프로젝트를 수정하도록 허용할지 여부를 묻는 메시지가 표시됩니다. 이 수정은 프로젝트에서 `taco.json` 파일 대신 도구 집합을 사용하여 Cordova 라이브러리의 버전, 플랫폼 및 플러그인, 노드/npm 종속성을 관리하도록 업그레이드합니다. 자세한 내용은 [마이그레이션 가이드](/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015)를 참조하세요. |
| 웹 배포(wdproj) | 게시 프로필 지원이 추가되면서 Visual Studio 2012에서 웹 배포 프로젝트 지원이 제거되었습니다. Visual Studio 2017에 동등한 기능이 없으므로 이러한 프로젝트에 대한 자동 마이그레이션 경로는 없습니다. 대신, [StackOverflow](https://stackoverflow.com/a/12061065/1203388)에 설명된 대로 텍스트 편집기에서 wdproj 파일을 열고 사용자 지정을 복사하여 pubxml(게시 프로필) 파일에 붙여넣습니다. |
| Windows Communication Foundation, Windows Workflow Foundation | Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 및 Visual Studio 2012에서 이 프로젝트를 열 수 있습니다. |
| Windows Presentation Foundation | Visual Studio 2017, Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 SP1에서 이 프로젝트를 열 수 있습니다. |
| Windows 스토어/전화 앱 | Visual Studio 2017에서는 Windows 스토어 8.1 및 8.0, Windows Phone 8.1 및 8.0용 프로젝트가 지원되지 않습니다. 이러한 앱을 유지하려면 Visual Studio 2015를 계속 사용합니다. Windows Phone 7.x 프로젝트를 유지하려면 Visual Studio 2012를 사용합니다. |

## <a name="how-visual-studio-decides-when-to-migrate-a-project"></a>Visual Studio가 프로젝트를 마이그레이션하는 시기를 결정하는 방식

새 버전의 각 Visual Studio는 일반적으로 동일한 프로젝트가 다른 버전에서 열리고 수정되고 빌드될 수 있도록 이전 버전과 호환성을 유지하려 합니다. 그러나 일부 프로젝트 형식이 더 이상 지원되지 않을 정도로 시간이 흐르면 변경을 피할 수가 없습니다. (Visual Studio 2017에서 지원되는 프로젝트 형식에 대한 [플랫폼 타키팅 및 호환성](/visualstudio/productinfo/vs2017-compatibility-vs)을 참조합니다.) 이러한 경우에는 최신 버전의 Visual Studio가 프로젝트를 로드하지 않고 마이그레이션 경로를 제공하지 않습니다. Visual Studio 이전 버전의 프로젝트가 이를 지원하도록 유지해야 하기 때문입니다.

다른 경우에 최신 버전의 Visual Studio는 프로젝트를 열 수 있지만 이전 버전과 호환되지 않게 렌더링하는 방식으로 프로젝트를 업데이트하거나 마이그레이션해야 합니다. Visual Studio는 이러한 마이그레이션이 필요한지 여부를 결정하는 많은 기준을 사용합니다.

- Visual Studio 2013 RTM으로 돌아간 플랫폼의 대상 버전과의 호환성.

- Visual Studio 이전 버전과 디자인 타임 자산의 호환성. (즉 Visual Studio 2017의 다른 채널, Visual Studio 2015 RTM 및 업데이트 3, Visual Studio 2013 RTM 및 업데이트 5, Visual Studio 2012 업데이트 4, Visual Studio 2010 SP 1.) Visual Studio 2017은 이전 버전에서 프로젝트를 열 수 있을 정도로 더 이상 사용되지 않는 디자인 타임 자산을 손상시키지 않는 것을 목표로 합니다.

- 새로운 디자인 타임 자산이 이전 버전 Visual Studio 2013 RTM & 업데이트 5와의 호환성을 중단하는지 여부.

문제의 프로젝트 유형의 엔지니어링 소유자는 이러한 기준을 지향하며 지원, 호환성 및 마이그레이션이 관련된 위치에서 호출을 합니다. Visual Studio는 가능한 Visual Studio 버전 간에 투명한 호환성을 유지하려 합니다. 이는 Visual Studio의 한 버전에서 프로젝트를 만들고 수정할 수 있고 다른 버전에서도 작동한다는 의미입니다.

그러나 이 아티클에 설명된 일부 프로젝트 유형에서처럼 이러한 호환성이 가능하지 않은 경우 Visual Studio는 업그레이드 마법사를 열고 필요한 단방향 변경을 합니다.

이러한 단방향 변경이 프로젝트 파일에서 `ToolsVersion` 속성의 변경을 포함할 수 있습니다. 이는 정확하게 MSBuild의 버전이 프로젝트의 소스 코드를 사용자가 원하는 실행가능하고 배포가능한 아티팩트로 바꿀 수 있음을 나타냅니다. 곧 이전 버전의 Visual Studio와 호환되지 않는 프로젝트를 렌더링한 것은 *Visual Studio* 버전이 아니라 `ToolsVersion`에서 결정한 대로 *MSBuild* 버전입니다. Visual Studio 버전이 프로젝트의 `ToolsVersion`과 일치하는 MSBuild 도구 체인을 포함하는 한은 Visual Studio는 해당 도구 체인이 프로젝트를 빌드하도록 호출할 수 있습니다.

이전 버전에서 만든 프로젝트와 최대한 호환성을 유지하기 위해 Visual Studio 2017은 `ToolsVersion` 15, 14, 12 및 4를 지원하는 데 필요한 MSBuild 도구 체인을 포함합니다. 이러한 `ToolsVersion` 값 중 하나를 사용하는 프로젝트는 성공적인 빌드를 발생해야 합니다. ([플랫폼 대상 지정 및 호환성](/visualstudio/productinfo/vs2017-compatibility-vs)에 설명된 대로 Visual Studio 2017이 프로젝트 형식을 항상 지원하는지 여부의 주제.)

이 컨텍스트에서 수동으로 프로젝트를 최신 `ToolsVersion` 값으로 업데이트하거나 마이그레이션해야 하는지 여부의 의문이 자연스럽게 발생합니다. 이러한 변경은 필요하지 않으며, 프로젝트를 다시 빌드하도록 수정해야 하는 많은 오류 및 경고를 발생시킬 가능성이 있습니다. 또한 Visual Studio가 향후 특정 `ToolsVersion`에 대한 지원을 중단하는 경우 특히 `ToolsVersion` 값을 변경해야 하기 때문에 프로젝트를 열면 프로젝트 마이그레이션 프로세스를 트리거하게 됩니다. 이러한 경우 해당 특정 프로젝트 형식에 대한 하위 시스템은 변경될 사항을 정확히 알고 이 아티클의 앞에서 설명한 대로 자동으로 이러한 변경을 수행할 수 있습니다.

## <a name="next-steps"></a>다음 단계

자세한 논의 내용은 다음 아티클을 참조하십시오.

- [ToolsVersion 지침](../msbuild/msbuild-toolset-toolsversion.md)
- [프레임워크 대상 지정 지침](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>참조

[프로젝트 마이그레이션 및 Visual Studio 2019에 대한 업그레이드 참조](port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2019)

::: moniker-end

::: moniker range="vs-2019"

새 버전의 Visual Studio에서는 대부분의 형식의 프로젝트, 파일 및 기타 자산을 지원합니다. 최신 기능을 사용하지 않는 경우 [이전과 동일하게](../ide/solutions-and-projects-in-visual-studio.md) 사용할 수 있습니다.

Microsoft에서는 Visual Studio 2017, Visual Studio 2015, Visual Studio 2013, Visual Studio 2012와 같은 이전 버전과의 호환성을 유지하려고 노력합니다. 하지만 일부 프로젝트 형식 변경은 이후에 지원될 수 있습니다. 최신 버전의 Visual Studio는 특정 프로젝트를 지원하지 않거나, 더 이상 이전 버전과 호환되지 않도록 프로젝트를 업데이트해야 할 수도 있습니다. 

> [!NOTE]
> 마이그레이션 문제의 현재 상태는 [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com)를 참조하세요. 각 Visual Studio 버전과 관련된 기능에 대한 자세한 내용은 [릴리스 정보](/visualstudio/releases/2019/release-notes/)를 참조하세요.

> [!IMPORTANT]
> 일부 프로젝트 형식에는 특정 워크로드가 필요합니다. 워크로드가 설치되어 있지 않으면 Visual Studio에서 알 수 없거나 호환되지 않는 프로젝트 형식을 보고합니다. 이 경우 [Visual Studio 설치 관리자의 설치 옵션](../install/modify-visual-studio.md)을 확인하고 다시 시도하세요. Visual Studio 2019의 프로젝트 지원에 대한 자세한 내용은 [플랫폼 대상 지정 및 호환성](/visualstudio/releases/2019/compatibility) 페이지를 참조하세요.

## <a name="project-types"></a>프로젝트 형식

다음 목록에서는 이전 버전에서 만든 프로젝트에 대한 Visual Studio 2019의 지원에 대해 설명합니다.

여기에 나열된 프로젝트 또는 파일 형식이 표시되지 않는 경우 [이 문서의 Visual Studio 2017 버전](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2017)을 참조하세요. 이 페이지의 아래쪽에 있는 **다음에 대한 피드백 보내기** > **이 페이지** 단추를 사용하여 프로젝트 세부 정보를 제공할 수도 있습니다. (익명으로 “이 페이지가 도움이 되었나요?” 컨트롤을 사용하면 피드백에 응답할 수 없습니다.)

| 프로젝트 형식 | 고객 지원팀 |
| --- | --- |
| .NET Core 프로젝트(.xproj) | Visual Studio 2015로 만든 프로젝트는 xproj 프로젝트 파일을 포함하는 미리 보기 도구를 사용했습니다.<br/><br/>Visual Studio 2017: xproj 형식은 csproj 형식으로 마이그레이션해야만 지원됩니다. xproj 파일을 열면 파일을 SDK 스타일의 csproj 형식으로 마이그레이션해야 한다는 메시지가 표시됩니다. (xproj 파일의 백업이 생성됩니다.) SDK 스타일의 csproj 프로젝트는 Visual Studio 2015 및 이전 버전에서 지원되지 않습니다. <br/><br/>Visual Studio 2019: 버전 16.3 이상에서는 xproj 프로젝트를 로드하거나 마이그레이션할 수 없습니다. 자세한 내용은 [csproj 형식으로 .NET Core 프로젝트 마이그레이션](/dotnet/core/migration/#visual-studio)을 참조하세요.|
| Application Insights를 사용하도록 지정한 ASP.NET 웹 애플리케이션 및 ASP.NET Core 웹 애플리케이션 | 각 Visual Studio 사용자의 리소스 정보가 사용자 인스턴스별 레지스트리에 저장됩니다. 이 정보는 사용자가 프로젝트를 열지 않고 Azure Application Insights 데이터를 검색하려는 경우에 사용됩니다. Visual Studio 2015에서는 Visual Studio 2017 및 Visual Studio 2019와 다른 레지스트리 위치를 사용하므로 충돌하지 않습니다.<br/><br/>사용자가 ASP.NET 웹 애플리케이션 또는 ASP.NET Core 웹 애플리케이션을 만들면 리소스가 .suo 파일에 저장됩니다. 사용자는 Visual Studio 2015, Visual Studio 2017 또는 Visual Studio 2019에서 프로젝트를 열 수 있으며, Visual Studio가 두 버전 모두에서 사용되는 프로젝트 및 솔루션을 지원하는 한 각각에 대해 리소스 정보가 사용됩니다. 사용자는 각 제품에 대해 한 번 인증해야 합니다. 예를 들어 Visual Studio 2017에서 프로젝트를 만들고 Visual Studio 2019에서 열 경우 사용자는 Visual Studio 2019에서 인증해야 합니다. |
| C#/Visual Basic Webform 또는 Windows Form | Visual Studio 2019, Visual Studio 2017 및 Visual Studio 2015에서 프로젝트를 열 수 있습니다. |
| 코딩된 UI 테스트 | Visual Studio 2019에서는 자동화된 UI 기반 기능 테스트를 위해 코딩된 UI 테스트는 사용되지 않습니다. <br/><br/>Visual Studio 2019는 코딩된 UI 테스트에 대한 마지막 릴리스가 될 것입니다. 웹앱 테스트에는 Selenium을 사용하고, 데스크톱 및 UWP 앱 테스트에는 WinAppDriver가 있는 Appium을 사용하는 것이 좋습니다. |
| 데이터베이스 유닛 테스트 프로젝트(csproj, .vbproj) | 이전 데이터 유닛 테스트 프로젝트는 Visual Studio 2019에 로드되지만 GAC 종속성 버전을 사용합니다. 최신 종속성을 사용하도록 단위 테스트 프로젝트를 업그레이드하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **SQL Server 단위 테스트 프로젝트로 변환...** 을 선택합니다. |
| F# | Visual Studio 2019는 Visual Studio 2013, Visual Studio 2015 및 Visual Studio 2017에서 만든 프로젝트를 열 수 있습니다. 새 프로젝트에 대한 이전 Visual Studio 템플릿과의 주요 차이점은 FSharp.Core 버전이 항상 NuGet 패키지라는 것입니다. F#은 기본적으로 모든 .NET 워크로드와 함께 설치됩니다.|
| InstallShield<br/>MSI 설정 | Visual Studio 2010에서 만든 설치 관리자 프로젝트는 [Visual Studio 설치 관리자 프로젝트 확장](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects)을 사용하여 이후 버전에서 열 수 있습니다. 또한 [WiX 도구 집합 Visual Studio 2017 확장](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)을 참조하세요. InstallShield Limited Edition은 더 이상 Visual Studio에 포함되지 않습니다. Visual Studio 2019에 대한 가용성은 [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)에서 확인하세요. |
| LightSwitch | LightSwitch는 Visual Studio 2019 또는 Visual Studio 2017에서 더 이상 지원되지 않습니다. Visual Studio 2012 이전 버전에서 만들고 Visual Studio 2013 또는 Visual Studio 2015에서 연 프로젝트는 업그레이드되며 이후에는 Visual Studio 2013 또는 Visual Studio 2015에서만 열 수 있습니다. |
| 부하 테스트 | Visual Studio 2019에서는 웹 성능 및 부하 테스트 기능이 더 이상 사용되지 않습니다. <br/><br/>Visual Studio 2019는 부하 테스트에 대한 마지막 릴리스가 될 것입니다. Apache JMeter, Akamai CloudTest, Blazemeter와 같은 대체 부하 테스트 도구를 사용합니다.  |
| Visual Studio용 Microsoft Azure 도구 | 이러한 형식의 프로젝트를 열려면 먼저 [Azure SDK for.NET](https://azure.microsoft.com/downloads/)을 설치한 다음 프로젝트를 엽니다. 필요한 경우 프로젝트가 업데이트됩니다. |
| Microsoft Test Manager | Microsoft Test Manager 및 Feedback Client는 Visual Studio 2019부터 더 이상 Visual Studio에서 제공되지 않습니다. <br/><br/>수동 및 예비 테스트 요구 사항에 대해 Azure 테스트 계획(Azure DevOps의 일부)을 활용합니다. 자세한 내용은 Azure DevOps 설명서의 [Guidance on Microsoft Test Manager usage](/azure/devops/test/mtm/guidance-mtm-usage?view=azure-devops)(Microsoft Test Manager 사용 참고 자료) 페이지를 참조하세요. |
| 모델-뷰-컨트롤러 프레임워크(ASP.NET MVC) | MVC 버전 및 Visual Studio 지원:<ul><li>Visual Studio 2010 SP1은 MVC 2 및 MVC 3을 지원합니다. MVC 4 지원은 [Visual Studio 2010 SP1용 ASP.NET 4 MVC 4 다운로드](https://www.microsoft.com/download/details.aspx?id=30683)를 통해 추가됩니다.</li><li>Visual Studio 2012에서는 MVC 3 및 MVC 4만 지원합니다.</li><li>Visual Studio 2013에서는 MVC 4 및 MVC 5만 지원합니다.</li><li>Visual Studio 2019, Visual Studio 2017 및 Visual Studio 2015는 MVC 4(기존 프로젝트는 열 수 있지만 새 프로젝트는 만들 수 없음) 및 MVC 5를 지원합니다.</li></ul><br/>MVC 버전 업그레이드:<ul><li>MVC 2에서 MVC 3로 자동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 애플리케이션 업그레이더](https://archive.codeplex.com/?p=aspnet)를 참조하세요.</li><li>MVC 2에서 MVC 3로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 도구 업데이트로 ASP.NET MVC 2 프로젝트 업그레이드](https://archive.codeplex.com/?p=aspnet)를 참조하세요.</li><li>MVC 3에서 MVC 4로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 프로젝트를 ASP.NET MVC 4로 업그레이드](/aspnet/whitepapers/mvc4-release-notes)를 참조하세요. 프로젝트 대상이 .NET Framework 3.5 SP1일 경우 대상을 변경하여 .NET Framework 4를 사용해야 합니다.</li><li>MVC 4에서 MVC 5로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 4 및 Web API 프로젝트를 ASP.NET MVC 5 및 Web API 2로 업그레이드하는 방법](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2)을 참조하세요.</li></ul> |
| 모델링 | Visual Studio에서 프로젝트를 자동으로 업데이트하도록 허용하면 Visual Studio 2015, Visual Studio 2013 또는 Visual Studio 2012에서 프로젝트를 열 수 있습니다.<br/><br/>Visual Studio 2015 이후 모델링 프로젝트의 형식은 변경되지 않았으며, 이러한 버전에서 프로젝트를 열고 수정할 수 있습니다. 하지만 Visual Studio 2017 및 Visual Studio 2019의 동작에 차이가 있습니다.<ul><li>모델링 프로젝트를 메뉴 및 템플릿에서 “종속성 유효성 검사” 프로젝트라고 합니다.</li><li>UML 다이어그램은 Visual Studio 2017 및 Visual Studio 2019에서 더 이상 지원되지 않습니다. UML 파일은 솔루션 탐색기에 이전처럼 나열되지만 XML 파일로 열립니다. UML 다이어그램을 보거나, 만들거나, 편집하려면 Visual Studio 2015를 사용하세요.</li><li>Visual Studio 2019에서는 모델링 프로젝트를 빌드할 때 더 이상 아키텍처 종속성 유효성 검사가 수행되지 않습니다. 대신 각 코드 프로젝트를 빌드할 때 유효성 검사가 수행됩니다. 이 변경은 모델링 프로젝트에 영향을 주지 않지만 유효성을 검사할 코드 프로젝트를 변경해야 합니다. Visual Studio 2019에서는 필요한 경우 코드 프로젝트를 자동으로 변경할 수 있습니다.</li></ul> |
| MSI 설정(vdproj) | InstallShield 프로젝트를 참조하세요. |
| Office 2007 VSTO | Visual Studio 2019에 대한 단방향 업그레이드가 필요합니다. |
| Office 2010 VSTO | 프로젝트 대상이 .NET Framework 4일 경우 Visual Studio 2010 SP1 이상에서 이 프로젝트를 열 수 있습니다. 다른 모든 프로젝트에는 단방향 업그레이드가 필요합니다. |
| PCL(이식 가능한 클래스 라이브러리) | 이식 가능한 클래스 라이브러리(또는 PCL)는 이제 지원되지 않습니다. Visual Studio 2019가 여전히 열리고 빌드되지만 새 PCL 프로젝트를 만들 수는 없습니다. PCL 프로젝트의 코드를 .NET Standard 프로젝트로 마이그레이션하는 것이 좋습니다.<br/><br/>PCL 지원은 더 이상 기본적으로 포함되지 않지만 Visual Studio "개별 구성 요소" 탭에서 사용할 수 있습니다. |
| Python 워크로드 | Visual Studio 2019에서는 Python Windows IoT Core 앱에 대한 지원이 제거되었습니다. Visual Studio 2019 미리 보기에는 동등한 기능이 없으므로 이러한 프로젝트에 대한 자동 마이그레이션 경로는 없습니다.<br/><br/>Visual Studio 2017을 계속 사용할 수 있습니다. |
| R Tools for Visual Studio | Visual Studio용 R 도구가 Visual Studio 2019의 데이터 과학 워크로드에서 제거되었습니다.<br/><br/>Visual Studio 2017 또는 RStudio와 같은 대안을 계속 사용할 수 있습니다. |
| Service Fabric(sfproj) | Service Fabric 애플리케이션 프로젝트가 ASP.NET Core 서비스 프로젝트를 참조하지 않을 경우 Visual Studio 2015, Visual Studio 2017 및 Visual Studio 2019 미리 보기에서 Service Fabric 애플리케이션 프로젝트를 열 수 있습니다. Visual Studio 2017 또는 Visual Studio 2019 미리 보기에서 열리는 Visual Studio 2015의 Service Fabric 프로젝트는 xproj 형식에서 csproj 형식으로 단방향 마이그레이션됩니다. 이 표에서 앞부분에 있는 “.NET Core 프로젝트(xproj)”를 참조하세요. |
| SharePoint 2010 | Visual Studio 2019를 사용하여 SharePoint 솔루션 프로젝트를 열면 SharePoint 2013 또는 SharePoint 2016으로 업그레이드됩니다. 업그레이드를 위해서는 ".NET 데스크톱 개발" 워크로드가 Visual Studio 2019에 설치되어 있어야 합니다.<br/><br/>SharePoint 프로젝트를 업그레이드하는 방법에 대한 자세한 내용은 [SharePoint 2013으로 업그레이드](https://technet.microsoft.com/library/cc303420.aspx), [SharePoint Server 2013에서 워크플로 업데이트](https://technet.microsoft.com/library/dn133867.aspx) 및 [데이터베이스 연결 업그레이드를 위해 SharePoint Server 2016 팜 만들기](https://technet.microsoft.com/library/cc263026(v=office.16).aspx)를 참조하세요. |
| SharePoint 2016 | Office 개발자 도구 미리 보기 2에서 만든 SharePoint 추가 기능 프로젝트를 Visual Studio 2019에서 열 수 없습니다. 이 제한을 해결하려면 csproj 또는 vbproj 파일에 있는 `MinimumVisualStudioVersion`을 12.0으로, `MinimumOfficeToolsVersion`을 12.2로 업데이트합니다. |
| Silverlight | Silverlight 프로젝트는 Visual Studio 2019에서 지원되지 않습니다. Silverlight 애플리케이션을 유지하려면 Visual Studio 2015를 계속 사용합니다. |
| SQL - Redgate | Redgate의 SQL 변경 Automation Core(이전에는 ReadyRoll Core라고 함), SQL Prompt Core 및 SQL Search는 Visual Studio 설치 관리자에서 더 이상 제공되지 않습니다.<br/><br/>이러한 기능에 대해서는 Visual Studio 2017을 계속 사용할 수 있습니다. Visual Studio 2019에서 Redgate의 SQL Toolbelt에 사용할 수 있는 유료 SQL Change Automation 및 SQL Prompt 제품으로 업그레이드할 수 있습니다.|
| SQL Server Reporting Services 및 SQL Server Analysis Services(SSRS, SSDT, SSAS, MSAS) | 이러한 프로젝트 형식에 대한 지원은 Visual Studio 갤러리의 두 가지 확장 기능을 통해 제공됩니다.  [Microsoft Analysis Services 모델링 프로젝트](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) 및 [Microsoft Reporting Services 프로젝트](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). SSDT는 Visual Studio 2019에서 데이터 스토리지 및 처리 워크로드를 지원합니다. 자세한 내용은 [Visual Studio용 SSDT(SQL Server Data Tools) 다운로드 및 설치](/sql/ssdt/download-sql-server-data-tools-ssdt) 페이지를 참조하세요. |
| SSIS(SQL Server Integration Services) | Visual Studio 2019 지원을 사용할 수 있습니다. 자세한 내용은 [Visual Studio용 SSDT(SQL Server Data Tools) 다운로드 및 설치](/sql/ssdt/download-sql-server-data-tools-ssdt) 페이지와 [SSIS(SQL Server Integration Services)](https://techcommunity.microsoft.com/t5/SQL-Server-Integration-Services/bg-p/SSIS) 팀 블로그 및 Marketplace의 [SQL Server Integration Services 프로젝트](https://marketplace.visualstudio.com/items?itemName=SSIS.SqlServerIntegrationServicesProjects&ssr=false#overview) 페이지를 참조하세요. |
| 테스트 창 확장 | Visual Studio 2019에서는 이전에 공용으로 표시되었지만 공식적으로 문서화되지 않은 테스트 창 API의 일부가 제거되었습니다. 확장 유지 관리자에게 조기 경고하기 위해 광범위하게 표시되는 API가 Visual Studio 2017에서 더 이상 사용되지 않는 것으로 표시되었습니다. 아는 바로는, 이러한 API에 대한 종속성을 사용하는 확장은 거의 없습니다. 자세한 정보 및 업데이트는 [사용되지 않는 테스트 관련 API의 전체 목록](https://github.com/Microsoft/vstest/issues/1830)을 보세요. 시나리오에 영향을 주는 경우 [개발자 커뮤니티](https://developercommunity.visualstudio.com)에 알려주세요. |
| Visual C++ | Visual Studio 2019를 사용하여 Visual Studio 2010까지 이전 버전의 Visual Studio에서 만든 프로젝트에서 작업할 수 있습니다. 프로젝트를 처음 열면 최신 컴파일러 및 도구 집합으로 업그레이드하거나 원래 항목을 계속 사용하는 옵션이 있습니다. 원래 항목을 계속 사용하도록 선택하면 Visual Studio 2019에서는 프로젝트 파일을 수정하지 않으며 이전 Visual Studio 설치의 도구 집합을 사용하여 프로젝트를 빌드합니다. 원래 옵션을 유지하는 것은 필요한 경우 원래 버전의 Visual Studio에서 프로젝트를 열 수 있음을 의미합니다. 자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](/cpp/porting/use-native-multi-targeting)를 참조하세요. |
| Visual Studio 확장성/VSIX | MinimumVersion 14.0 이하의 프로젝트는 업데이트를 통해 MinimumVersion 15.0으로 선언됩니다. 그러면 이전 버전의 Visual Studio에서 프로젝트를 열 수 없습니다. 이전 버전에서 프로젝트를 열 수 있도록 허용하려면 MinimumVersion을 `$(VisualStudioVersion)`(으)로 설정합니다. 참고 항목 [방법: Visual Studio 2017로 확장성 프로젝트 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Microsoft Test Manager 또는 Visual Studio 2010 SP1 이상을 사용하여 이러한 버전에서 만든 환경을 열 수 있습니다. 그러나 Visual Studio 2010 SP1의 경우 환경을 만들기 전에 Microsoft Test Manager 버전이 Team Foundation Server 버전과 일치해야 합니다. |
| Apache Cordova용 Visual Studio Tools | Visual Studio 2019에서 Apache Cordova에 대한 지원이 제거되었습니다. Visual Studio 2019에 동등한 기능이 없으므로 이러한 프로젝트에 대한 자동 마이그레이션 경로는 없습니다.<br/><br/>Visual Studio Code 확장용 Cordova Tools(최신 버전의 Cordova 지원)를 사용하거나 Visual Studio 2017을 계속 사용할 수 있습니다. |
| 웹 배포(wdproj) | 게시 프로필 지원이 추가되면서 Visual Studio 2012에서 웹 배포 프로젝트 지원이 제거되었습니다. Visual Studio 2019에 동등한 기능이 없으므로 이러한 프로젝트에 대한 자동 마이그레이션 경로는 없습니다. 대신, [StackOverflow](https://stackoverflow.com/a/12061065/1203388)에 설명된 대로 텍스트 편집기에서 wdproj 파일을 열고 사용자 지정을 복사하여 pubxml(게시 프로필) 파일에 붙여넣습니다. |
| Windows Communication Foundation, Windows Workflow Foundation | Visual Studio 2019, Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 및 Visual Studio 2012에서 이 프로젝트를 열 수 있습니다. |
| Windows Presentation Foundation | Visual Studio 2019, Visual Studio 2017, Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 SP1에서 이 프로젝트를 열 수 있습니다. |
| Windows Phone 앱 | Windows Phone용 프로젝트는 Visual Studio 2019에서 지원되지 않습니다. <br/><br/>Windows Phone 8.x 앱을 유지하려면 Visual Studio 2015를 사용합니다. Windows Phone 7.x 프로젝트를 유지하려면 Visual Studio 2012를 사용합니다. |
| Windows 스토어 응용 프로그램 | JavaScript 유니버설 Windows 프로젝트는 Visual Studio 2019에서 지원되지 않습니다. 이러한 프로젝트를 유지 관리하려면 Visual Studio 2017을 사용하세요. <br/><br/>Visual Studio 2019 설치 관리자에서 Windows 10 Fall Creators Update(빌드 16299) 이전 버전의 Windows 10 SDK가 제거되었습니다. 이전 SDK를 수동으로 다운로드하거나 프로젝트의 대상을 다시 지정하여 최신 SDK를 사용할 수 있습니다.<br/><br/>project.json을 사용하는 유니버설 Windows 프로젝트는 지원되지 않습니다. 패키지 참조를 사용하도록 이러한 프로젝트를 업그레이드하는 것이 좋습니다. 또는 project.json 파일에 Microsoft.NET.Test.Sdk 버전 16.0.0.0에 대한 참조를 추가합니다.<br/><br/>Windows Store 8.1 및 8.0용 프로젝트는 Visual Studio 2019에서 지원되지 않습니다. 이러한 앱을 유지하려면 Visual Studio 2015를 계속 사용합니다. |
| Xamarin | Visual Studio 및 Visual Studio for Mac용 Xamarin Live Player 확장이 제거되었습니다. 이렇게 하면 페어링 화면과 모든 통합이 제거됩니다. 대신 빌드된 Xamarin.Forms Previewer를 사용합니다.<br/><br/>Android용 Visual Studio 에뮬레이터가 Visual Studio 설치 관리자에서 제거되었습니다. 대신 Google Android 에뮬레이터에서 새 Hyper-V 지원을 사용합니다. |

## <a name="migrate-a-project"></a>프로젝트 마이그레이션

이전 버전과의 호환성을 유지하려고 노력하지만 이전 버전과 호환되지 않는 변경 내용이 있을 수 있습니다. (Visual Studio 2019에서 지원되는 프로젝트 형식에 대한 [플랫폼 타키팅 및 호환성](/visualstudio/releases/2019/compatibility)을 참조하세요.) 이 경우 새 버전의 Visual Studio가 프로젝트를 로드하거나 마이그레이션 경로를 제공하지 않습니다. 해당 프로젝트를 이전 버전 Visual Studio에서 유지해야 할 수도 있습니다.

때로는 최신 버전의 Visual Studio에서 프로젝트를 열 수 있지만 이전 버전과 호환되지 않게 렌더링하는 방식으로 프로젝트를 업데이트하거나 마이그레이션해야 합니다. Visual Studio는 이러한 마이그레이션이 필요한지 여부를 결정하는 많은 기준을 사용합니다.

- Visual Studio 2013 RTM으로 돌아간 플랫폼의 대상 버전과의 호환성.

- Visual Studio 이전 버전과 디자인 타임 자산의 호환성. (즉 Visual Studio 2019, Visual Studio 2017의 다른 채널, Visual Studio 2015 RTM 및 업데이트 3, Visual Studio 2013 RTM 및 업데이트 5, Visual Studio 2012 업데이트 4, Visual Studio 2010 SP 1.) Visual Studio 2019는 이전 버전에서 프로젝트를 열 수 있을 정도로 더 이상 사용되지 않는 디자인 타임 자산을 손상시키지 않는 것을 목표로 합니다.

- 새로운 디자인 타임 자산이 이전 버전 Visual Studio 2013 RTM & 업데이트 5와의 호환성을 중단하는지 여부.

해당 프로젝트 유형을 소유한 엔지니어링 팀은 이러한 기준을 지향하여 지원, 호환성 및 마이그레이션 관련 결정을 내립니다. 다시 한 번, Microsoft에서는 한 버전의 Visual Studio에서 프로젝트를 만들고 수정하면 다른 버전에서도 작동하도록 Visual Studio 버전 간 호환성을 유지하려고 노력합니다.

경우에 따라 호환성이 가능하지 않습니다. 그러면 Visual Studio가 업그레이드 마법사를 열어 필요한 단방향 변경을 수행합니다. 이러한 단방향 변경이 프로젝트 파일에서 `ToolsVersion` 속성의 변경을 포함할 수 있습니다. 이 속성은 정확하게 어떤 버전의 MSBuild가 프로젝트의 소스 코드를 사용자가 원하는 실행가능하고 배포 가능한 아티팩트로 바꿀 수 있는지 표시합니다. 

이전 버전의 Visual Studio와 호환되지 않는 프로젝트를 렌더링한 것은 *Visual Studio* 버전이 아니라 `ToolsVersion`에서 결정한 *MSBuild* 버전입니다. 사용자의 Visual Studio 버전이 프로젝트의 `ToolsVersion`과 일치하는 MSBuild 도구 체인을 포함하는 경우 Visual Studio는 해당 도구 체인이 프로젝트를 빌드하도록 호출할 수 있습니다.

이전 버전에서 만든 프로젝트와 호환성을 유지하기 위해 Visual Studio 2019는 `ToolsVersion` 15, 14, 12 및 4를 지원하는 데 필요한 MSBuild 도구 체인을 포함합니다. 이러한 `ToolsVersion` 값 중 하나를 사용하는 프로젝트는 성공적인 빌드를 발생해야 합니다. (다시 한 번, [플랫폼 대상 지정 및 호환성](/visualstudio/releases/2019/compatibility)에 설명된 대로 Visual Studio 2019가 프로젝트 형식을 지원하는지 여부에 따라 다릅니다.)

프로젝트를 수동으로 업데이트하거나 최신 `ToolsVersion` 값으로 마이그레이션하기를 원할 수도 있습니다. 이러한 변경은 필요하지 않으며, 프로젝트를 다시 빌드하도록 하려면 수정해야 하는 많은 오류 및 경고를 발생시킬 가능성이 있습니다. 또한 Visual Studio가 나중에 특정 `ToolsVersion`을 지원하지 않는 경우 프로젝트를 열 때 해당 `ToolsVersion` 값을 변경해야 하므로 프로젝트 마이그레이션 프로세스가 트리거됩니다.

## <a name="next-steps"></a>다음 단계

자세한 논의 내용은 다음 아티클을 참조하십시오.

- [ToolsVersion 지침](../msbuild/msbuild-toolset-toolsversion.md)
- [프레임워크 대상 지정 지침](../ide/visual-studio-multi-targeting-overview.md)

## <a name="see-also"></a>참조

[프로젝트 마이그레이션 및 Visual Studio 2017에 대한 업그레이드 참조](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2017)

::: moniker-end
