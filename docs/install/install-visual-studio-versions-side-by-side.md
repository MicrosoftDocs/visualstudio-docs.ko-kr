---
title: Visual Studio 버전 side-by-side 설치
ms.date: 03/05/2019
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
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114651"
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
