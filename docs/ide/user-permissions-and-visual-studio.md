---
title: 관리자 권한으로 실행
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927031b4755644aeac553367a4f8a08faa0c0992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75718638"
---
# <a name="user-permissions-and-visual-studio"></a>사용자 권한 및 Visual Studio

보안을 위해 가급적 일반 사용자로 Visual Studio를 실행해야 합니다.

> [!WARNING]
> 신뢰할 수 있는 사람이나 신뢰할 수 있는 위치에서 제공되지 않는 Visual Studio 솔루션은 컴파일하거나 실행하거나 디버깅하지 마십시오.

일반 사용자로 Visual Studio IDE에서 거의 모든 작업을 수행할 수 있습니다. 다음 작업을 완료하려면 관리자 권한이 필요합니다.

|영역|Task|참조 항목|
|----------|----------| - |
|설치|Visual Studio 설치 또는 수정|[Visual Studio 설치](../install/install-visual-studio.md), [Visual Studio 수정](../install/modify-visual-studio.md)|
||로컬 도움말 콘텐츠를 설치, 업데이트 또는 제거합니다.|[로컬 도움말 콘텐츠 설치 및 관리](../help-viewer/install-manage-local-content.md)|
|도구 상자|**도구 상자**에 클래식 COM 컨트롤을 추가합니다.|[도구 상자](../ide/reference/toolbox.md)|
|빌딩|구성 요소를 등록하는 빌드 후 이벤트를 사용합니다.|[사용자 지정 빌드 단계 및 빌드 이벤트 이해](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ 프로젝트를 빌드할 때 등록 단계를 포함합니다.||
|디버깅|높은 권한으로 실행되는 애플리케이션 디버깅합니다.|[디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET 웹 사이트와 같이 다른 사용자 계정으로 실행되는 애플리케이션을 디버깅합니다.|[ASP.NET 및 AJAX 애플리케이션 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XBAP(XAML 브라우저 애플리케이션) 영역에서 디버깅합니다.|[WPF 호스트(PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||에뮬레이터를 사용하여 Microsoft Azure용 클라우드 서비스 프로젝트를 디버깅합니다.|[Visual Studio에서 클라우드 서비스 디버깅](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||원격 디버깅을 위한 방화벽을 구성합니다.|[원격 디버깅](../debugger/remote-debugging.md)|
|성능 도구|관리자 권한으로 실행하는 애플리케이션에 연결합니다.|[초보자를 위한 성능 프로파일링 지침](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU 프로파일러를 사용합니다.|[GPU 프로파일링](../profiling/gpu-usage.md)|
|배포|로컬 컴퓨터에서 IIS(인터넷 정보 서비스)에 웹 애플리케이션을 배포합니다.|[Visual Studio를 사용하여 ASP.NET 웹앱 배포](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>관리자 권한으로 Visual Studio 실행

관리자 권한으로 Visual Studio를 실행해야 할 경우 다음 단계에 따라 IDE를 엽니다.

> [!NOTE]
> 이러한 지침은 Windows 10에 대한 것입니다. 다른 버전의 Windows와 유사합니다.

::: moniker range="vs-2017"

1. **시작** 메뉴를 열고 Visual Studio 2017로 스크롤합니다.

1. **Visual Studio 2017**의 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **추가** > **관리자 권한으로 실행**을 선택합니다.

   Visual Studio가 시작되면 제목 표시줄의 제품 이름 뒤에 **(관리자)** 가 나타납니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **시작** 메뉴를 열고 Visual Studio 2019로 스크롤합니다.

1. **Visual Studio 2019**의 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **추가** > **관리자 권한으로 실행**을 선택합니다.

   Visual Studio가 시작되면 제목 표시줄의 제품 이름 뒤에 **(관리자)** 가 나타납니다.

::: moniker-end

또한 애플리케이션 바로 가기를 수정하여 항상 관리자 권한으로 실행하도록 할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio 설치](../install/install-visual-studio.md)
