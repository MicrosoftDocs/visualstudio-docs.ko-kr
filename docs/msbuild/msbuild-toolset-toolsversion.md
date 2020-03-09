---
title: MSBuild 도구 집합(ToolsVersion) | Microsoft Docs
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6aaa6309e04f5143b70ff233c0b621ab2350b9c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633124"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild 도구 집합(ToolsVersion)

MSBuild는 애플리케이션을 빌드하기 위한 작업, 대상 및 도구로 구성된 도구 집합을 사용합니다. 일반적으로 MSBuild 도구 집합에는 *microsoft.common.tasks* 파일, *microsoft.common.targets* 파일 및 컴파일러(예: *csc.exe* 및 *vbc.exe*)가 포함되어 있습니다. 대부분의 도구 집합을 사용하여 애플리케이션을 둘 이상의 .NET Framework 버전 및 둘 이상의 시스템 플랫폼으로 컴파일할 수 있습니다. 그러나 MSBuild 2.0 도구 집합을 사용해서는 .NET Framework 2.0만 대상으로 할 수 있습니다.

## <a name="toolsversion-attribute"></a>ToolsVersion 특성

::: moniker range=">=vs-2019"
 프로젝트 파일에서 [Project](../msbuild/project-element-msbuild.md) 요소의 `ToolsVersion` 특성에 도구 집합을 지정합니다. 다음 예제에서는 MSBuild “현재” 도구 세트를 사용하여 프로젝트를 빌드해야 하도록 지정합니다.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 프로젝트 파일에서 [Project](../msbuild/project-element-msbuild.md) 요소의 `ToolsVersion` 특성에 도구 집합을 지정합니다. 다음 예제에서는 MSBuild 15.0 도구 집합을 사용하여 프로젝트를 빌드해야 하도록 지정합니다.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> 일부 프로젝트 형식은 `ToolsVersion` 대신 `sdk` 특성을 사용합니다. 자세한 내용은 [패키지, 메타데이터, 프레임워크](/dotnet/core/packages) 및 [.NET Core용 csproj 형식에 대한 추가 사항](/dotnet/core/tools/csproj)을 참조하세요.

## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion 특성의 작동 방식

 Visual Studio에서 프로젝트를 만들거나 기존 프로젝트를 업그레이드할 때 `ToolsVersion`이라는 특성이 자동으로 프로젝트 파일에 포함되고 해당 값은 Visual Studio 버전에 포함된 MSBuild의 버전에 해당합니다. 자세한 내용은 [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)를 참조하세요.

 `ToolsVersion` 값이 프로젝트 파일에 정의되면 MSBuild는 해당 값을 사용하여 프로젝트에 사용 가능한 도구 집합 속성의 값을 확인합니다. 도구 집합 속성 하나는 `$(MSBuildToolsPath)`이며, 이 속성은 .NET Framework 도구의 경로를 지정합니다. 이 도구 집합 속성(또는 `$(MSBuildBinPath)`)만 필수입니다.

 Visual Studio 2013부터 MSBuild 도구 집합 버전은 Visual Studio 버전 번호와 동일합니다. MSBuild는 프로젝트 파일에 지정된 도구 집합 버전과 관계없이 Visual Studio 내에서와 명령줄에서 기본값인 이 도구 집합으로 설정됩니다.  -ToolsVersion 플래그를 사용하여 이 동작을 재정의할 수 있습니다. 자세한 내용은 [ToolsVersion 설정 재정의](../msbuild/overriding-toolsversion-settings.md)를 참조하세요.

 다음 예제에서 MSBuild는 예약된 속성 `MSBuildToolsPath`를 사용하여 *Microsoft.CSharp.targets* 파일을 찾습니다.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 사용자 지정 도구 집합을 정의하여 `MSBuildToolsPath`의 값을 수정할 수 있습니다. 자세한 내용은 [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)을 참조하세요.

 명령줄에서 솔루션을 빌드하고 *msbuild.exe*에 대해 `ToolsVersion`을 지정하면 솔루션의 각 프로젝트에서 자체 `ToolsVersion`을 지정하더라도 모든 프로젝트 및 해당 프로젝트 간 종속성이 해당 `ToolsVersion`에 따라 빌드됩니다. 프로젝트별로 `ToolsVersion` 값을 정의하려면 [ToolsVersion 설정 재정의](../msbuild/overriding-toolsversion-settings.md)를 참조하세요.

 `ToolsVersion` 특성은 프로젝트 마이그레이션에도 사용됩니다. 예를 들어, Visual Studio 2010에서 Visual Studio 2008 프로젝트를 열면 프로젝트 파일이 ToolsVersion=“4.0”을 포함하도록 업데이트됩니다. 그런 다음 Visual Studio 2008에서 해당 프로젝트를 열려고 하면 업그레이드된 `ToolsVersion`이 인식되지 않으므로 이 특성이 여전히 3.5로 설정된 것처럼 프로젝트가 빌드됩니다.

 Visual Studio 2010과 Visual Studio 2012는 ToolsVersion 4.0을 사용합니다. Visual Studio 2013은 ToolsVersion 12.0을 사용합니다. Visual Studio 2015는 ToolsVersion 14.0을 사용하고 Visual Studio 2017은 ToolsVersion 15.0을 사용합니다. 많은 경우에 Visual Studio의 여러 버전에서 프로젝트를 수정하지 않고 열 수 있습니다. Visual Studio는 항상 올바른 도구 집합을 사용하지만 사용된 버전이 프로젝트 파일의 버전과 일치하지 않을 경우 알림이 표시됩니다. 도구 집합은 대부분의 경우에 호환되므로 거의 모든 경우에 이 경고는 심각하지 않습니다.

 이 항목의 뒷부분에 설명되어 있는 하위 도구 집합을 통해 MSBuild는 빌드가 실행되는 컨텍스트를 기반으로 사용할 도구 집합을 자동으로 전환할 수 있습니다. 예를 들어, MSBuild는 Visual Studio 2012에서 실행될 때 Visual Studio 2010에서 실행될 때보다 최신 도구 집합을 사용하며 사용자가 명시적으로 프로젝트 파일을 변경할 필요가 없습니다.

## <a name="toolset-implementation"></a>도구 집합 구현

 도구 집합을 구성하는 다양한 도구, 대상 및 작업의 경로를 선택하여 도구 집합을 구현합니다. MSBuild가 정의하는 도구 집합의 도구는 다음 소스에서 가져옵니다.

- .NET Framework 폴더

- 추가 관리되는 도구

  관리되는 도구에는 *ResGen.exe* 및 *TlbImp.exe*가 포함됩니다.

MSBuild는 다음과 같이 도구 집합에 액세스하는 두 가지 방법을 제공합니다.

- 도구 집합 속성 사용

- <xref:Microsoft.Build.Utilities.ToolLocationHelper> 메서드 사용

도구 집합 속성은 도구의 경로를 지정합니다. Visual Studio 2017부터 시작하여 MSBuild는 더 이상 고정된 위치를 갖지 않습니다. 기본적으로 Visual Studio 설치 위치에 대해 상대적인 *MSBuild\15.0\Bin* 폴더에 있습니다. 이전 버전에서 MSBuild는 프로젝트 파일의 `ToolsVersion` 특성 값을 사용하여 해당 레지스트리 키를 찾은 다음, 레지스트리 키의 정보를 사용하여 도구 집합 속성을 설정합니다. 예를 들어, `ToolsVersion`의 값이 `12.0`인 경우 MSBuild는 이 레지스트리 키에 따라 도구 세트 속성을 설정합니다. **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 다음은 도구 집합 속성입니다.

- `MSBuildToolsPath`는 MSBuild 이진의 경로를 지정합니다.

- `SDK40ToolsPath`는 MSBuild 4.x(4.0 또는 4.5일 수 있음)용 추가 관리되는 도구의 경로를 지정합니다.

- `SDK35ToolsPath`는 MSBuild 3.5용 추가 관리되는 도구의 경로를 지정합니다.

또는 <xref:Microsoft.Build.Utilities.ToolLocationHelper> 클래스의 메서드를 호출하여 프로그래밍 방식으로 도구 집합을 확인할 수 있습니다. 이 클래스에는 다음과 같은 메서드가 포함되어 있습니다.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>는 .NET Framework 폴더의 경로를 반환합니다.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>은 .NET Framework 폴더에 있는 파일의 경로를 반환합니다.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>는 관리되는 도구 폴더의 경로를 반환합니다.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>은 일반적으로 관리되는 도구 폴더에 있는 파일의 경로를 반환합니다.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121))는 빌드 도구의 경로를 반환합니다.

### <a name="sub-toolsets"></a>하위 도구 집합

 15.0 이전 버전의 MSBuild의 경우 MSBuild는 레지스트리 키를 사용하여 기본 도구의 경로를 지정합니다. 키에 하위 키가 포함된 경우 MSBuild는 하위 키를 사용하여 추가 도구가 포함되어 있는 하위 도구 집합의 경로를 지정합니다. 이 경우 도구 집합은 두 키 모두에 정의되어 있는 속성 정의를 결합하여 정의됩니다.

> [!NOTE]
> 도구 집합 속성 이름이 충돌하는 경우 하위 키 경로에 대해 정의된 값이 루트 키 경로에 대해 정의된 값을 재정의합니다.

 하위 도구 집합은 `VisualStudioVersion` 빌드 속성이 있을 때 활성화됩니다. 이 속성은 다음 값 중 하나를 사용할 수 있습니다.

- “10.0”은 .NET Framework 4 하위 도구 집합을 지정합니다.

- “11.0”은 .NET Framework 4.5 하위 도구 집합을 지정합니다.

- “12.0”은 .NET Framework 4.5.1 하위 도구 집합을 지정합니다.

하위 도구 집합 10.0 및 11.0은 ToolsVersion 4.0과 함께 사용되어야 합니다. 나중 버전에서는 하위 도구 집합 버전과 ToolsVersion이 일치해야 합니다.

빌드 중에 MSBuild는 자동으로 `VisualStudioVersion` 속성의 기본값을 확인하여 설정합니다(아직 정의되지 않은 경우).

MSBuild는 `ToolLocationHelper` 열거형 값을 매개 변수로 추가하는 `VisualStudioVersion` 메서드에 대한 오버로드를 제공합니다.

하위 도구 집합은 .NET Framework 4.5에서 도입되었습니다.

## <a name="see-also"></a>참조

- [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)
- [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)
