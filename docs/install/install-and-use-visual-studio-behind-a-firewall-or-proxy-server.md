---
title: 방화벽 또는 프록시 서버 뒤에 설치 및 사용
description: 조직에서 방화벽 또는 프록시 서버를 사용하는 경우 허용 목록에 추가하거나 열려는 도메인 URL, 포트 및 프로토콜을 검토합니다.
ms.date: 06/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ce11689cc8cba45473a918668a07ddcc6cdc2ee3
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387163"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>방화벽 또는 프록시 서버 배후에서 Visual Studio와 Azure 서비스 설치 및 사용

사용자 또는 사용자 조직에서 방화벽 또는 프록시 서버와 같은 보안 조치를 사용하는 경우 Visual Studio와 Azure 서비스를 설치 및 사용할 때 최상의 경험을 얻으려면 특정 포트 및 프로토콜을 열고 특정 도메인 URL을 “허용 목록”에 추가하는 것이 좋습니다.

* **[Visual Studio 설치](#install-visual-studio)** : 이 표에는 원하는 모든 구성 요소 및 워크로드에 액세스할 수 있도록 허용 목록에 추가할 도메인 URL이 나와 있습니다.

* **[Visual Studio 및 Azure 서비스 사용](#use-visual-studio-and-azure-services)** : 이 표에는 원하는 모든 기능과 서비스에 액세스할 수 있도록 허용 목록에 추가할 도메인 URL과 열려는 포트 및 프로토콜이 나와 있습니다.

> [!NOTE]
> 이 문서는 Windows의 Visual Studio용으로 작성되었지만 어떤 정보는 방화벽 또는 프록시 서버 배후에서 [Mac용 Visual Studio 설치](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)에도 적용됩니다.

## <a name="install-visual-studio"></a>Visual Studio 설치

### <a name="urls-to-add-to-an-allow-list"></a>허용 목록에 추가할 URL

Visual Studio 설치 관리자는 다양한 도메인과 다운로드 서버에서 파일을 다운로드하기 때문에 UI 또는 배포 스크립트에서 다음 도메인 URL을 신뢰할 수 있는 도메인으로 허용 목록에 추가하는 것이 좋습니다.

#### <a name="microsoft-domains"></a>Microsoft 도메인

| 도메인 | 용도 |
| - | - |
| go.microsoft.com | 설치 URL 확인 |
| aka.ms | 설치 URL 확인 |
| download.visualstudio.microsoft.com | 설치 패키지 다운로드 위치 |
| download.microsoft.com | 설치 패키지 다운로드 위치 |
| download.visualstudio.com | 설치 패키지 다운로드 위치 |
| dl.xamarin.com | 설치 패키지 다운로드 위치 |
| xamarin-downloads.azureedge.net | Android SDK 패키지 다운로드 목록 위치 |
| marketplace.visualstudio.com | Visual Studio 확장 다운로드 위치 |
| \*  | Visual Studio 확장 다운로드 위치 |
| visualstudio.microsoft.com | 문서 위치 |
| docs.microsoft.com | 문서 위치 |
| msdn.microsoft.com | 문서 위치 |
| www\.microsoft.com | 문서 위치 |
| \*.windows.net | 로그인 위치 |
| \*.microsoftonline.com | 로그인 위치 |
| \*.live.com | 로그인 위치 |
| | |

#### <a name="non-microsoft-domains"></a>타사 도메인

| 도메인 | 이러한 워크로드 설치 |
| - | - |
| archive.apache.org | JavaScript를 사용한 모바일 개발(Cordova) |
| cocos2d-x.org | C++를 사용한 게임 개발(Cocos) |
| download.epicgames.com | C++를 사용한 게임 개발(Unreal Engine) |
| download.oracle.com | JavaScript를 사용한 모바일 개발(Java SDK) <br /><br />.NET을 사용한 모바일 개발(Java SDK) |
| download.unity3d.com | Unity를 사용한 게임 개발(Unity) |
| netstorage.unity3d.com | Unity를 사용한 게임 개발(Unity) |
| dl.google.com | JavaScript를 사용한 모바일 개발(Android SDK 및 NDK, 에뮬레이터) <br /><br />.NET을 사용한 모바일 개발(Android SDK 및 NDK, 에뮬레이터) |
| www\.incredibuild.com | C++를 사용한 게임 개발(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | C++를 사용한 게임 개발(IncrediBuild) |
| www\.python.org | Python 개발(Python) <br /><br />데이터 과학 및 분석 애플리케이션(Python) |
| developerservices2.apple.com | Xamarin.iOS 프로비저닝 |
| developer.apple.com | Xamarin.iOS 프로비저닝 |
| appstoreconnect.apple.com | Xamarin.iOS 프로비저닝 |
| idmsa.apple.com | Xamarin.iOS 프로비저닝 |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Visual Studio 및 Azure 서비스 사용

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>허용 목록에 추가할 URL 및 여는 포트와 프로토콜

방화벽이나 프록시 서버 배후에서 Visual Studio 또는 Azure 서비스를 사용할 때 필요한 모든 요소에 액세스할 수 있도록 하려면 다음 URL을 허용 목록에 추가하고 다음 포트와 프로토콜을 여는 것이 좋습니다.

| 서비스 또는 시나리오 | DNS 엔드포인트 | 프로토콜<br/>/포트 | 설명 |
| - | - | -: | - | - |
| URL<br>확인 | go.microsoft.com<br><br>aka.ms | | URL을 줄이는 데 사용되며, 더 긴 URL로 확인됩니다. |
| 시작 페이지 | vsstartpage.blob.core.windows.net | 443 | 시작 페이지에 표시된 개발자 뉴스를 표시하는 데 사용(Visual Studio 2017만 해당) |
| 대상<br> 알림 <br>서비스 | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | 전체 알림 목록을 특정 유형의 컴퓨터/사용 시나리오에만 적용 가능한 목록으로 필터링하는 데 사용됩니다. |
| 확장명 <br>업데이트 확인 | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | 설치된 확장에 대한 업데이트를 사용할 수 있는 경우 알림을 제공하는 데 사용됩니다. <br><br> 로그인 위치로 사용됩니다. |
| AI 프로젝트 <br>통합 | az861674.vo.msecnd.net | 443<br> | 등록된 Application Insights 계정에 사용량 현황 데이터를 보내도록 새 프로젝트를 구성하는 데 사용됩니다. |
| 코드 렌즈 | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | 파일이 마지막으로 업데이트된 시기, 변경 타임라인, 변경과 관련된 작업 항목, 작성자 등에 대한 정보를 편집기에서 제공하는 데 사용됩니다. |
| 실험적 <br>기능 사용 | visualstudio-devdiv-c2s.msedge.net | 80 | 실험적인 새 기능이나 기능 변경을 활성화하는 데 사용됩니다. |
| ID “배지” <br>(사용자 이름 및 아바타)<br>를 갖는 <br>로밍 설정 | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | IDE에서 사용자 이름 및 아바타를 표시하는 데 사용됩니다. <br><br> 설정 변경 내용이 컴퓨터 간에 로밍되도록 하는 데 사용됩니다. |
| 원격 설정 | az700632.vo.msecnd.net | 443 | Visual Studio에서 문제를 유발하는 것으로 알려진 확장을 해제하는 데 사용됩니다. |
| Windows 도구 | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Windows 앱 스토어 시나리오에 사용됩니다. |
| JSON 스키마 <br>검색 <br><br>JSON 스키마 <br>정의<br><br>JSON 스키마 <br>지원: <br>Azure 리소스 | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | JSON 문서를 편집할 때 사용자가 사용할 수 있는 JSON 스키마를 검색하고 다운로드하는 데 사용됩니다. <br><br>JSON에 대한 메타 유효성 검사 스키마를 가져오는 데 사용됩니다.<br><br>Azure Resource Manager 배포 템플릿의 현재 스키마를 가져오는 데 사용됩니다. |
| NPM 패키지 <br>검색 | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | NPM 패키지를 검색하는 데 필요하며, 웹 프로젝트의 클라이언트 쪽 스크립트 패키지 설치에 사용됩니다. |
| Bower 패키지<br> 아이콘<br><br>Bower 패키지 <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | 기본 Bower 패키지 아이콘을 제공합니다.  <br><br>Bower 패키지를 검색하는 기능을 제공합니다. |
| NuGet<br><br>NuGet 패키지<br> 검색 | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | 서명된 NuGet 패키지를 확인하는 데 사용됩니다.<br><br>NuGet 패키지 및 버전을 검색하는 데 필요합니다. |
| GitHub 리포지토리 정보 | api.github.com | https/443 | Bower 패키지에 대한 추가 정보를 가져오는 데 필요합니다. |
| 웹 Linter | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter<br>탐색기 템플릿<br>검색 <br><br>Cookiecutter <br>탐색기 프로젝트<br> 만들기 | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | 추천 피드 및 GitHub 리포지토리에서 온라인 템플릿을 검색하는 데 사용됩니다. <br><br>PyPI(Python 패키지 인덱스)에서 cookiecutter Python 패키지의 일회성 주문형 설치를 요구하는 cookiecutter 템플릿에서 프로젝트를 만드는 데 사용됩니다. |
| Python 패키지 <br>검색<br><br>Python 패키지 <br>관리<br><br>단추를 사용하여 새 <br>Python <br> 프로젝트 <br>템플릿 | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | pip 패키지를 검색하는 기능을 제공합니다.<br><br>pip가 없을 경우 자동으로 pip를 설치하는 데 사용됩니다. <br><br>다음과 같은 새 Python 프로젝트 템플릿을 cookiecutter 템플릿 URL로 확인하는 데 사용됩니다.<br> - 분류자 프로젝트<br>- 클러스터링 프로젝트 <br> - 재발 프로젝트 <br> - PyKinect를 사용하는 PyGame <br> - Pyvot 프로젝트 |
| Office 웹 <br>추가 기능(add-in) <br> file:/// <br>확인 <br>서비스 | verificationservice.osi.office.net | https/443 | Office 웹 추가 기능에 대한 매니페스트의 유효성을 검사하는 데 사용됩니다. |
| SharePoint 및 <br>Office 추가 기능 | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | SharePoint Online 및 Office 365에 대한 SharePoint 및 Office 추가 기능을 게시 및 테스트하는 데 사용됩니다. |
| 워크플로 관리자 <br>테스트 서비스<br> 호스트 | | http/12292 | 워크플로를 사용하여 SharePoint 추가 기능을 테스트하기 위해 자동으로 생성되는 방화벽 규칙입니다. |
| 자동으로 수집되는 <br>안정성 통계 <br>및 기타 <br>CEIP(사용자 환경 <br>개선 프로그램)<br> : Azure SDK 및 <br>SQL 도구 <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | 사용자의 안정성 통계(크래시/응답하지 않는 데이터)를 Microsoft로 보내는 데 사용됩니다. Windows 오류 보고가 사용으로 설정된 경우 실제 크래시/응답하지 않는 덤프는 여전히 업로드됩니다. 통계 정보만 표시되지 않습니다. <br>Visual Studio에 대한 Azure Tools SDK 확장의 익명 사용 패턴 및 Visual Studio에 대한 SQL 도구의 사용 패턴을 표시하는 데 사용됩니다. |
| Visual Studio <br> CEIP(사용자 환경 <br>개선 프로그램) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | 익명 사용 패턴 및 오류 로그를 수집하는 데 사용됩니다. <br><br>UI 고정 문제를 추적하는 데 사용됩니다. |
| 만들기 및<br>관리 <br>: Azure 리소스 | management.azure.com <br>management.core.windows.net | https/443 | 웹 애플리케이션, Azure Functions 또는 WebJob의 게시를 지원하기 위해 Azure Websites 또는 기타 리소스를 만드는 데 사용됩니다. |
| 업데이트된 웹 게시 도구 <br>확인 및 확장 <br>권장 사항 | marketplace.visualstudio.com | https/443 | 업데이트된 게시 도구의 가용성을 확인하는 데 사용됩니다. 사용하지 않도록 설정할 경우 웹 게시에 사용 가능한 권장 확장이 표시되지 않을 수 있습니다. |
| 업데이트된 Azure 리소스 <br>만들기 엔드포인트 정보 | \*.blob.core.windows.net | https/443 | 특정 Azure 서비스용 Azure 리소스를 만드는 데 사용되는 엔드포인트 업데이트에 사용됩니다. 사용하지 않도록 설정할 경우 마지막으로 다운로드한 엔드포인트 위치 또는 기본 제공 엔드포인트 위치가 대신 사용됩니다. |
| 원격 디버깅 및 <br>원격 프로파일링 <br>: Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | 원격 디버거를 Azure Websites에 연결하는 데 사용됩니다. 사용하지 않도록 설정할 경우 원격 디버거를 Azure Websites에 연결할 수 없습니다. |
| Active Directory <br>Graph | graph.windows.net | https/443 | 새 Azure Active Directory 애플리케이션을 프로비전하는 데 사용됩니다. Office 365 MSGraph 연결된 서비스 공급자에서도 사용됩니다. |
| Azure Functions <br>CLI 업데이트 <br>확인 | functionscdn.azureedge.net | https/443 | Azure Functions CLI의 업데이트된 버전을 확인하는 데 사용됩니다. 사용하지 않도록 설정할 경우 CLI의 캐시된 복사본(Azure Functions 구성 요소가 보유한 복사본)이 대신 사용됩니다. |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | HTTP는 빌드 중 Gradle 다운로드에 사용됩니다. HTTPS는 Cordova 플러그 인을 프로젝트에 포함하는 데 사용됩니다. |
| 클라우드 탐색기 | 1. &#60;클러스터 엔드포인트&#62; <br>Service Fabric <br>2. &#60;관리 엔드포인트&#62;<br>일반 클라우드 확장 <br>3. &#60;그래프 엔드포인트&#62;<br>일반 클라우드 확장<br>4. &#60;스토리지 계정 엔드포인트&#62;<br>스토리지 노드 <br>5. &#60;Azure Portal URL&#62;<br>일반 클라우드 확장 <br>6. &#60;키 자격 증명 모음 엔드포인트&#62; <br>Azure Resource Manager VM 노드<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric 원격 디버깅 및 ETW 추적 | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dynamic | 1. 예: test12.eastus.cloudapp.com<br>2. 구독을 검색하고 Azure 리소스를 검색/관리합니다.<br>3. Azure Stack 구독을 검색합니다.<br>4. 스토리지 리소스(예: mystorageaccount.blob.core.windows.net)를 관리합니다.<br>5. “포털에서 열기” 상황에 맞는 메뉴 옵션(Azure Portal에서 리소스를 엽니다.)<br>6. VM 디버깅을 위해 키 자격 증명 모음을 만들고 사용합니다(예: myvault.vault.azure.net). <br><br>7. 클러스터의 노드 수와 사용 가능한 포트를 기준으로 포트 블록을 동적으로 할당합니다. <br><br>포트 블록은 최소 10개의 포트로 노드 수의 3배를 가져오려고 합니다.<br><br>스트리밍 추적의 경우 810에서 포트 블록을 가져오려고 시도합니다. 해당 포트 블록이 이미 사용된 경우 다음 블록을 가져오려고 시도합니다. 부하 분산 장치가 비어 있으면 810의 포트가 사용될 가능성이 큽니다. <br><br>디버깅과 마찬가지로, 다음 포트 블록 집합 4개는 예약되어 있습니다. <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- forwarderPortx86: 31399,<br>- fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;사용자의 클라우드 서비스&#62;.cloudapp.net <br> &#60;사용자의 VM&#62;.&#60;영역&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1.  Cloud Services VM에 대한 원격 데스크톱 <br><br> 2.  개인 진단 구성의 스토리지 계정 구성 요소 <br><br> 3.  Azure 포털 <br><br> 4. 서버 탐색기 - Azure Storage &#42;는 고객이 명명한 스토리지 계정입니다.  <br><br> 5.  포털 열기 &#47; 구독 인증서 다운로드 &#47; 설정 파일 게시 링크 <br><br>6. a) 클라우드 서비스 및 VM에 대한 원격 디버그용 커넥터 로컬 포트<br> 6. b) 클라우드 서비스 및 VM에 대한 원격 디버그용 커넥터 공용 포트 <br> 6. c) 클라우드 서비스 및 VM에 대한 원격 디버그용 전달자 로컬 포트 <br> 6. d) 클라우드 서비스 및 VM에 대한 원격 디버그용 전달자 공용 포트  <br> 6. e) 클라우드 서비스 및 VM에 대한 원격 디버그용 파일 업로더 로컬 포트 <br> 6. f) 클라우드 서비스 및 VM에 대한 원격 디버그용 파일 업로더 공용 포트 |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. 설명서 <br><br> 2. 클러스터 기능 만들기 <br><br>3. &#42;는 Azure Key Vault 이름입니다(예: test11220180112110108.vault.azure.net).  <br><br>  4. &#42;는 동적입니다(예: vsspsextprodch1su1.vsspsext.visualstudio.com). |
| 스냅샷 <br>디버거 | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. 원격 서비스/서버 IP 주소/FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022(Visual Studio 버전 종속) | 1. App Service SKU 크기에 대해 .json 파일 쿼리 <br>2. 다양한 Azure RM 호출 <br>3. 사이트 준비 호출  <br>4. 고객의 대상 App Service Kudu 엔드포인트 <br>5. nuget.org에 게시된 쿼리 사이트 확장 버전 <br>6. [원격 디버깅](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | ASA 작업을 확인, 제출, 실행 및 관리하는 데 사용됩니다. <br><br> HDI 클러스터를 찾아보고 HDI 작업을 제출, 진단 및 디버그하는 데 사용됩니다. |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | 작업을 컴파일, 제출, 확인, 진단 및 디버그하는 데 사용됩니다. ADLS 파일을 찾는 데 사용됩니다. 파일을 업로드 및 다운로드하는 데 사용됩니다. |
| 패키징 서비스 | [계정].visualstudio.com <br/> [계정].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | \*.npmjs.org, \*.nuget.org 및 \*.nodejs.org는 특정 빌드 작업 시나리오(예: NuGet 도구 설치 관리자, 노드 도구 설치 관리자) 또는 피드와 함께 공용 업스트림을 사용하려는 경우에만 필요합니다. 다른 세 가지 도메인은 패키징 서비스의 핵심 기능에 필요합니다. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Azure DevOps Services와 연결하는 데 사용됨 |
| Azure Service Bus | \*.servicebus.windows.net | ampq/5671 및 5672, </br> sbmp/9350~9354, </br> http/80, </br> https/443 | 큐, 토픽 및 구독을 만드는 데 사용됩니다. </br> Service Bus 큐 및 토픽에서 메시지를 보내고 받는 데에도 사용됩니다. |
| Azure Cosmos DB | \*.documents.azure.com | https/443 | 핵심 문서 데이터베이스 API를 호출하는 데 사용됩니다. |
| 개발자 커뮤니티 | sendvsfeedback2.azurewebsites.net/api | https/443 | 개발자 커뮤니티 피드백 도구 API를 호출하는 데 사용됩니다(내 문제, 검색, 투표, 주석, 제출, 업로드, 재개). |
| IntelliCode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Intellicode API를 호출하는 데 사용됩니다. |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 | Live Share API를 호출하는 데 사용됩니다. |
| Visual Studio Codespaces | \*.online.visualstudio.com | https/443 | Visual Studio Codespaces API를 호출하는 데 사용됩니다. |
| JavaScript 자동 형식 획득 | registry.npmjs.org | https/443 | 인기 있는 JavaScript 라이브러리에 Intellisense를 제공하기 위해 TypeScript 형식 정의를 설치하는 데 사용됩니다. |
| Visual Studio 구독 라이선싱 서비스 | app.vssps.visualstudio.com/apis/<br/>Licensing/ClientRights | https/443 | 온라인 활성화에 대한 라이선싱 |
| 디버거 | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon.\*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>SSH를 통해 Unix/macOS에서 .NET Core 디버깅을 위한 디버거 비트를 다운로드하는 데 사용됩니다. <br><br>2. <br>원격 Windows Docker 컨테이너 디버깅을 위한 디버거 비트를 다운로드하는 데 사용됩니다.<br><br> 3. .NET Framework 소스 단계별 실행에 사용됨 <br><br> 4. <br>사용자가 등록하는 경우 NuGet.org 기호 서버에 게시된 기호를 다운로드하는 데 사용됩니다.<br><br> 5. 사용자가 등록하는 경우 MS 기호 및 이진 파일을 다운로드하는 데 사용되며, 덤프에서 관리 코드를 디버깅하는 데 필요할 수도 있습니다. |
| Visual Studio Codespaces| \*.online.visualstudio.com | https/443 | Visual Studio Codespaces API를 호출하는 데 사용됩니다. |
| Xamarin Android 앱 게시 | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Visual Studio에서 직접 Xamarin Android 애플리케이션을 게시/업로드하기 위해 Google Play 스토어 서비스와 상호 작용하는 데 사용됩니다. |
| Azure Container Registry | *.azurecr.io | https/443 | CICD 파이프라인 구성을 위해 Azure에서 호스트되는 컨테이너 레지스트리에 액세스 |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>네트워크 관련 오류 문제 해결

때로는 방화벽 또는 프록시 서버 배후에서 Visual Studio를 설치하거나 사용할 때 네트워크 또는 프록시 관련 오류가 발생할 수 있습니다. 이러한 오류 메시지의 솔루션에 대한 자세한 내용은 [Visual Studio 설치 또는 사용 시의 네트워크 관련 오류 문제 해결](troubleshooting-network-related-errors-in-visual-studio.md) 페이지를 참조하세요.

## <a name="get-support"></a>지원 받기

설치 관련 문제를 위한 [**설치 채팅**](https://visualstudio.microsoft.com/vs/support/#talktous)(영어만 가능) 지원 옵션이 제공됩니다.

몇 가지 추가 지원 옵션은 다음과 같습니다.

* Visual Studio 설치 관리자와 Visual Studio IDE에 모두 표시되는 [문제 보고](../ide/how-to-report-a-problem-with-visual-studio.md) 도구를 통해 Microsoft에 제품 문제를 보고합니다.
* [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/)에서 기능을 제안하고, 제품 문제를 추적하고, 답변을 찾습니다.
* [GitHub](https://github.com/)을 사용하여 [Gitter 커뮤니티의 Visual Studio 관련 대화](https://gitter.im/Microsoft/VisualStudio)에서 본사 및 다른 Visual Studio 개발자와 소통합니다.

## <a name="see-also"></a>참조

* [Live Share 연결 요구 사항](/visualstudio/liveshare/reference/connectivity/)
* [Visual Studio의 네트워크 설치 만들기](create-a-network-installation-of-visual-studio.md)
* [Visual Studio에서 네트워크 관련 오류 문제 해결](troubleshooting-network-related-errors-in-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [방화벽 또는 프록시 서버 배후에 설치(Mac용 Visual Studio)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
