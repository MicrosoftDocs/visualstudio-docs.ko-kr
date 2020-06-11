---
title: MSBuild 15에 대한 기존 애플리케이션 업데이트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c141d1e35db1e5ce334606b255d99ce2c0afc29b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184031"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>MSBuild 15에 대한 기존 애플리케이션 업데이트

15.0 이전 MSBuild 버전에서 MSBuild는 GAC(전역 어셈블리 캐시)에서 로드되었으며 MSBuild 확장은 레지스트리에 설치되었습니다. 이는 모든 애플리케이션이 동일한 버전의 MSBuild를 사용했고 동일한 도구 집합에 액세스했음을 보장했지만 서로 다른 버전의 Visual Studio의 병렬 설치를 방지했습니다.

더 빠르고, 더 작은 병렬 설치를 지원하기 위해 Visual Studio 2017 및 이후 버전에서는 더 이상 GAC에 MSBuild를 배치하거나 레지스트리를 수정하지 않습니다. 그러나 이는 MSBuild API를 사용하여 프로젝트를 평가하거나 빌드하려는 애플리케이션이 Visual Studio 설치를 암시적으로 사용할 수 없음을 의미합니다.

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio에서 MSBuild 사용

애플리케이션의 프로그래밍 방식 빌드가 Visual Studio 또는 *MSBuild.exe* 내에서 수행된 빌드와 일치하도록 보장하려면 Visual Studio에서 MSBuild 어셈블리를 로드하고 Visual Studio 내에서 사용할 수 있는 SDK를 사용합니다. Microsoft.Build.Locator NuGet 패키지는 이 프로세스를 간소화합니다.

## <a name="use-microsoftbuildlocator"></a>Microsoft.Build.Locator 사용

애플리케이션에서 *Microsoft.Build.Locator.dll*을 재배포하는 경우 다른 MSBuild 어셈블리를 배포할 필요가 없습니다.

MSBuild 15 및 로케이터 API를 사용하도록 프로젝트를 업데이트하려면 아래에 설명된 프로젝트에서 몇 가지를 변경해야 합니다. 프로젝트를 업데이트하는 데 필요한 변경의 예를 보려면 [MSBuildLocator 리포지토리에서 예제 프로젝트에 만든 커밋](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)을 참조하세요.

### <a name="change-msbuild-references"></a>MSBuild 참조 변경

MSBuild가 중앙 위치에서 로드되도록 하려면 애플리케이션과 함께 해당 어셈블리를 배포하지 말아야 합니다.

중앙 위치에서 MSBuild를 로드하지 않도록 프로젝트를 변경하기 위한 메커니즘은 MSBuild를 참조하는 방법에 따라 달라집니다.

#### <a name="use-nuget-packages-preferred"></a>NuGet 패키지 사용(기본 설정됨)

이러한 지침에서는 [PackageReference 스타일 NuGet 참조](/nuget/consume-packages/package-references-in-project-files)를 사용한다고 가정합니다.

해당 NuGet 패키지에서 MSBuild 어셈블리를 참조하도록 프로젝트 파일을 변경합니다. 어셈블리가 빌드 시에만 필요하고 출력 디렉터리에 복사하지 말아야 함을 NuGet에 알리도록 `ExcludeAssets=runtime`을 지정합니다.

MSBuild 패키지의 주 및 부 버전은 지원하려는 Visual Studio의 최소 버전보다 작거나 같아야 합니다. 예를 들어 Visual Studio 2017 및 이후 버전을 지원하려면 패키지 버전 `15.1.548`을 참조하세요.

예를 들어 이 XML을 사용할 수 있습니다.

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>확장 어셈블리 사용

NuGet 패키지를 사용할 수 없는 경우 Visual Studio와 함께 배포되는 MSBuild 어셈블리를 참조할 수 있습니다. MSBuild를 직접 참조하는 경우 `Copy Local`을 `False`로 설정하여 출력 디렉터리에 복사되지 않도록 합니다. 프로젝트 파일에서 이 설정은 다음 코드와 같이 표시됩니다.

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>바인딩 리디렉션

Microsoft.Build.Locator 패키지를 참조하면 애플리케이션에서 버전 15.1.0.0으로의 필요한 바인딩 리디렉션을 자동으로 사용하도록 보장합니다. 이 버전으로의 바인딩 리디렉션은 MSBuild 15와 MSBuild 16을 모두 지원합니다.

### <a name="ensure-output-is-clean"></a>출력 정리 확인

*Microsoft.Build.\*.dll* 어셈블리를 포함하지 않는지 확인하도록 프로젝트를 빌드하고 출력 디렉터리를 검사합니다(*Microsoft.Build.Locator.dll* 이외, 다음 단계에서 추가됨).

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Microsoft.Build.Locator에 대한 패키지 참조 추가

[Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/)에 대한 NuGet 패키지 참조를 추가합니다.

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Microsoft.Build.Locator 패키지에 대한 `ExcludeAssets=runtime`을 지정하지 마십시오.

### <a name="register-instance-before-calling-msbuild"></a>MSBuild를 호출하기 전에 인스턴스 등록

> [!IMPORTANT]
> MSBuildLocator를 호출하는 메서드에서는 `Microsoft.Build` 네임스페이스의 MSBuild 형식을 참조할 수 없습니다. 예를 들어 다음을 수행할 수 없습니다.
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> 대신 다음을 수행해야 합니다.
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

로케이터 API 호출을 추가하는 가장 간단한 방법은 다음에 호출을 추가하는 것입니다.

```csharp
MSBuildLocator.RegisterDefaults();
```

애플리케이션 시작 코드

MSBuild의 로드에 대한 세부적인 제어를 원하는 경우 `MSBuildLocator.QueryVisualStudioInstances()`의 결과를 선택하여 `MSBuildLocator.RegisterInstance()`에 수동으로 전달할 수 있지만 일반적으로 필요하지 않습니다.
