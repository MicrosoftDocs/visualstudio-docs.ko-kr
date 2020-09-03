---
title: 대상 .NET Framework
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b7c3c2b6b81f8f7793bda35c6b220e43caee9b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770449"
---
# <a name="framework-targeting-overview"></a>Framework 대상 지정 개요

Visual Studio에서는 프로젝트에서 대상으로 하려는 .NET의 버전을 지정할 수 있습니다. 프레임워크 대상 지정을 통해 애플리케이션에서 지정된 프레임워크 버전에서 제공되는 기능만 사용하도록 할 수 있습니다. .NET Framework 앱이 다른 컴퓨터에서 실행되려면 애플리케이션이 대상으로 하는 Framework 버전이 컴퓨터에 설치된 Framework 버전과 호환되어야 합니다.

Visual Studio 솔루션에는 여러 가지 버전의 .NET을 대상으로 하는 프로젝트가 포함될 수 있습니다.  그러나 단일 빌드에 대한 참조 조건을 사용하여 단일 버전의 .NET을 대상으로 빌드하거나 각 버전에 대해 여러 이진 파일을 재귀적으로 빌드하는 것만 가능합니다.  대상 프레임워크에 대한 자세한 내용은 [대상 프레임워크](/dotnet/standard/frameworks)를 참조하세요.

> [!TIP]
> 다른 플랫폼에 대한 애플리케이션을 대상으로 지정할 수도 있습니다. 자세한 내용은 [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)을 참조하세요.

## <a name="framework-targeting-features"></a>프레임워크 대상 지정 기능

프레임워크 대상 지정에는 다음 기능이 포함됩니다.

- 이전 버전의 프레임워크를 대상으로 하는 프로젝트를 열면 Visual Studio에서 프로젝트를 자동으로 업그레이드하거나 대상을 있는 그대로 유지할 수 있습니다.

- .NET Framework 프로젝트를 만들 때 대상으로 지정할 .NET Framework의 버전을 지정할 수 있습니다.

- 단일 프로젝트에서 [여러 프레임워크를 대상 지정](/dotnet/standard/frameworks#how-to-specify-target-frameworks)할 수 있습니다.

- 같은 솔루션에 포함된 여러 프로젝트에서 각각 .NET의 다른 버전을 대상으로 지정할 수 있습니다.

- 기존 프로젝트에서 대상으로 지정하는 .NET의 버전을 변경할 수 있습니다.

   프로젝트가 대상으로 하는 .NET의 버전을 변경하면 Visual Studio에서는 필요에 따라 참조 및 구성 파일을 변경합니다.

이전 프레임워크 버전을 대상으로 지정하는 프로젝트 관련 작업을 할 경우 Visual Studio에서는 다음과 같이 개발 환경을 동적으로 변경합니다.

- **새 항목 추가** 대화 상자, **새 참조 추가** 대화 상자 및 **서비스 참조 추가** 대화 상자에서 항목을 필터링하여 대상 버전에서 사용할 수 없는 선택 항목을 생략합니다.

- **도구 상자**에서 사용자 지정 컨트롤을 필터링하여 대상 버전에서 사용할 수 없는 컨트롤을 제거하고 여러 컨트롤을 사용할 수 있을 경우에는 가장 최신 컨트롤만 표시합니다.

- **IntelliSense**를 필터링하여 대상 버전에서 사용할 수 없는 언어 기능을 생략합니다.

- **속성** 창에서 속성을 필터링하여 대상 버전에서 사용할 수 없는 속성을 생략합니다.

- 메뉴 옵션을 필터링하여 대상 버전에서 사용할 수 없는 옵션을 생략합니다.

- 빌드에는 컴파일러 버전 및 대상 버전에 적절한 컴파일러 옵션을 사용합니다.

> [!NOTE]
> - 프레임워크 대상 지정을 수행해도 애플리케이션이 제대로 실행되지 않을 수 있습니다. 애플리케이션을 테스트하여 대상 버전에 대해 실행되는지 확인해야 합니다.
> - .NET Framework 2.0 이하의 프레임워크 버전은 대상으로 지정할 수 없습니다.

## <a name="select-a-target-framework-version"></a>대상 프레임워크 버전 선택

.NET Framework 프로젝트를 만들 때 프로젝트 템플릿을 선택한 후 대상 .NET Framework 버전을 선택할 수 있습니다. 사용 가능한 프레임워크 목록에는 선택한 템플릿 유형에 적용 가능한 설치된 프레임워크 버전이 포함됩니다. 비 .NET Framework 프로젝트 템플릿의 경우(예: .NET Core 템플릿), **Framework** 드롭다운 목록이 나타나지 않습니다.

::: moniker range="vs-2017"

![VS 2017의 프레임워크 드롭다운](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![VS 2019의 프레임워크 드롭다운](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>대상 프레임워크 변경

기존 Visual Basic, C# 또는 F# 프로젝트의 경우, 프로젝트 속성 대화 상자에서 대상 .NET 버전을 변경합니다. C++ 프로젝트의 대상 버전을 변경하는 방법에 대한 자세한 내용은 [대상 프레임워크 및 플랫폼 도구 집합을 수정하는 방법](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)을 참조하세요.

1. **솔루션 탐색기**에서 변경하려는 프로젝트의 오른쪽 클릭 메뉴를 열고 **속성**을 선택합니다.

1. **속성** 창의 왼쪽 열에서 **애플리케이션** 탭을 선택합니다.

   ![프로젝트 속성 애플리케이션 탭](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > UWP 앱을 만든 후에는 Windows 또는 .NET의 대상 버전을 변경할 수 없습니다.

1. **대상 프레임워크** 목록에서 원하는 버전을 선택합니다.

1. [확인] 대화 상자가 나타나면 **예** 단추를 선택합니다.

   프로젝트가 언로드됩니다. 다시 로드되면 이 프로젝트는 방금 선택한 .NET 버전을 대상으로 지정합니다.

> [!NOTE]
> 코드에 사용자가 대상으로 지정한 것과 다른 버전의 .NET에 대한 참조가 포함된 경우, 코드를 컴파일하거나 실행할 때 오류 메시지가 나타날 수 있습니다. 이러한 오류를 해결하려면 참조를 수정합니다. [.NET 대상 지정 오류 문제 해결](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)을 참조하세요.

> [!TIP]
> 대상 프레임워크에 따라 프로젝트 파일에서 다음과 같이 표시될 수 있습니다.
>
> - .NET Core 앱: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - .NET Standard 앱: `<TargetFramework>netstandard2.0</TargetFramework>`
> - .NET Framework 앱: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>시스템 및 사용자 어셈블리 참조 확인

.NET 버전을 대상으로 지정하려면 먼저 적절한 어셈블리 참조를 설치해야 합니다. [.NET 다운로드](https://www.microsoft.com/net/download/windows) 페이지에서 다양한 버전의 .NET 개발자 팩을 다운로드할 수 있습니다.

.NET Framework 프로젝트의 경우 **참조 추가** 대화 상자에서는 실수로 프로젝트에 추가될 수 없도록 대상 .NET Framework 버전과 관련이 없는 시스템 어셈블리를 비활성화합니다. (시스템 어셈블리는 .NET Framework 버전에 포함된 *.dll* 파일입니다.) 대상 버전 이상의 프레임워크 버전에 속한 참조는 확인되지 않고 이런 참조에 따라 결정되는 컨트롤을 추가할 수 없습니다. 해당 참조를 사용하도록 설정하려면 프로젝트의 .NET Framework 대상을 참조가 포함된 대상으로 다시 설정합니다.

어셈블리 참조에 대한 자세한 내용은 [디자인 타임에 어셈블리 확인](../msbuild/resolving-assemblies-at-design-time.md)을 참조하세요.

## <a name="enable-linq"></a>LINQ 사용

.NET Framework 3.5 이상을 대상으로 지정하면 **System.Core**에 대한 참조 및 <xref:System.Linq>에 대한 프로젝트 수준 가져오기(Visual Basic에서만)가 자동으로 추가됩니다. LINQ 기능을 사용하려면 `Option Infer`도 켜야 합니다(Visual Basic에서만). 대상을 이전 .NET Framework 버전으로 변경하면 참조 및 가져오기가 자동으로 제거됩니다. 자세한 내용은 [LINQ 작업](/dotnet/csharp/tutorials/working-with-linq)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [대상 프레임워크](/dotnet/standard/frameworks)
- [멀티 타기팅(MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [방법: 대상 프레임워크 및 플랫폼 도구 세트 수정(C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
