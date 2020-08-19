---
title: Visual Studio 버전 side-by-side 설치
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 717a9cd3f4157c276ce7d0dd5c41cac625581ba6
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250259"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio 버전 side-by-side 설치

이미 예전 또는 보다 최신 버전의 Visual Studio가 설치된 컴퓨터에 Visual Studio를 설치할 수 있습니다.

::: moniker range="vs-2017"

버전을 side-by-side 설치하기 전에 다음과 같은 조건을 검토합니다.

* Visual Studio 2017을 사용하여 Visual Studio 2015에서 만든 솔루션을 여는 경우 Visual Studio 2017에 특정 기능을 구현하지 않았다면 나중에 이전 버전에서 다시 솔루션을 열어 수정할 수 있습니다.

* Visual Studio 2017을 사용하여 Visual Studio 2015 이하 버전에서 만든 솔루션을 열려면 Visual Studio 2017과 호환되도록 프로젝트와 파일을 수정해야 할 수 있습니다. 자세한 내용은 [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) 페이지를 참조하세요.

::: moniker-end

::: moniker range=">= vs-2019"

버전을 side-by-side 설치하기 전에 다음과 같은 조건을 검토합니다.

* Visual Studio 2019를 사용하여 Visual Studio 2017에서 만든 솔루션을 여는 경우 Visual Studio 2019에 특정 기능을 구현하지 않았다면 나중에 이전 버전에서 다시 솔루션을 열어 수정할 수 있습니다.

* Visual Studio 2019를 사용하여 Visual Studio 2017 이하 버전에서 만든 솔루션을 열려면 Visual Studio 2019와 호환되도록 프로젝트와 파일을 수정해야 할 수 있습니다. 자세한 내용은 [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md) 페이지를 참조하세요.

::: moniker-end

* 둘 이상의 버전이 설치된 컴퓨터에서 Visual Studio 버전을 제거하면 Visual Studio의 파일 연결이 모든 버전에 대해 제거됩니다.

* 모든 확장이 호환되는 것은 아니므로 Visual Studio에서는 확장을 자동으로 업그레이드하지 않습니다. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 소프트웨어 게시자에서 확장을 다시 설치해야 합니다.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Visual Studio 부 버전 동시 설치

하나의 Visual Studio 부 버전에서 다음 부 버전으로 업그레이드하는 경우 Visual Studio 설치 관리자는 기본적으로 현재 설치를 해당 채널의 다음 버전으로 업데이트합니다. 예를 들어 16.6.4 미리 보기를 설치할 때 설치 관리자는 현재 설치된 16.6.3 미리 보기를 바꾸려고 시도합니다. 두 버전이 모두 16.6 미리 보기 채널에 속하기 때문입니다. 이렇게 대체하면 이전 버전의 Visual Studio가 머신의 공간을 차지하지 않습니다. 일부 특정한 경우에는 부 버전을 함께 설치하는 것이 유용할 수도 있습니다. 이 예에서는 16.6.3과 16.6.4를 모두 동일한 머신에 설치하는 것을 의미합니다.

1. 기존 버전의 Visual Studio와 함께 설치하려는 부 버전용 [Visual Studio 부트스트래퍼 파일](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release)을 다운로드합니다.
2. 관리자 모드로 명령 프롬프트를 엽니다. 그러려면 Windows 시작 메뉴를 열고 “cmd”를 입력한 다음 명령 프롬프트 검색 결과를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 선택합니다. 명령 프롬프트에서 Visual Studio 부트스트래퍼 파일이 있는 폴더로 디렉터리를 변경합니다.
3. 다음 명령을 실행하여 설치 위치에 대한 새 폴더 경로를 지정하고 .exe 파일 이름을 설치하는 Visual Studio 버전의 해당 부트스트래퍼 이름으로 바꿉니다. .exe 파일 이름은 다음 파일 중 하나와 일치하거나 유사해야 합니다.
   * vs_community.exe(Visual Studio Community의 경우)
   * vs_professional.exe(Visual Studio Professional의 경우)
   * vs_enterprise.exe(Visual Studio Enterprise의 경우)

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. 설치 관리자 대화 상자에 따라 설치에 필요한 구성 요소를 선택합니다. 자세한 내용은 [Visual Studio 설치](install-visual-studio.md#step-4---choose-workloads)를 참조하세요.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework 버전 및 side-by-side 설치

Visual Basic, Visual C# 및 Visual F# 프로젝트는 **프로젝트 디자이너**의 **대상 프레임워크** 옵션을 사용하여 프로젝트에 사용할 .NET Framework 버전을 지정합니다. C++ 프로젝트의 경우 .vcxproj 파일을 수정하여 수동으로 대상 프레임워크를 변경할 수 있습니다. 자세한 내용은 [.NET Framework의 버전 호환성](/dotnet/framework/migration-guide/version-compatibility) 페이지를 참조하세요.

프로젝트를 만들 때 **새 프로젝트** 대화 상자의 **.NET Framework** 목록에서 프로젝트 대상으로 사용할 .NET Framework 버전을 지정할 수 있습니다.

언어별 정보는 다음 테이블에서 해당 항목을 참조하세요.

::: moniker range="vs-2017"

| 언어 | 항목 |
|--------------|-----------|
| Visual Basic | [프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [프로젝트 디자이너, 애플리케이션 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Visual Studio에서 Visual F#을 사용하여 개발](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [방법: 대상 프레임워크 및 플랫폼 도구 세트 수정](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio 설치](install-visual-studio.md?view=vs-2017)
* [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| 언어 | 항목 |
|--------------|-----------|
| Visual Basic | [프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [프로젝트 디자이너, 애플리케이션 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Visual Studio에서 Visual F#을 사용하여 개발](../ide/fsharp-visual-studio.md) |
| C++ | [방법: 대상 프레임워크 및 플랫폼 도구 세트 수정](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
