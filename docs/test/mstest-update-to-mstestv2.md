---
title: MSTestV2로 업데이트
description: MSTestV1에서 MSTestV2로 업데이트하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366272"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>MSTestV1에서 MSTestV2로 업그레이드

*.csproj* 에서 참조되는 MSTest 버전의 대상을 MSTestV1에서 MSTestV2로 변경하여 테스트 프로젝트를 업그레이드할 수 있습니다. MSTestV1의 일부 기능을 MSTestV2로 가져오지 않았으므로 오류를 해결하려면 일부 내용을 변경해야 할 수 있습니다. 더 이상 작동하지 않을 기능을 이해하려면 [MSTestV2에서 지원되지 않는 MSTestV1 기능](#mstestv1-features-that-are-not-supported-in-mstestv2)을 참조하세요. 해당 기능 중 일부는 테스트에서 제거해야 할 수 있습니다.

1. 단위 테스트 프로젝트에서 Microsoft.VisualStudio.QualityTools.UnitTestFramework에 대한 어셈블리 참조를 제거합니다.
2. nuget.org에서 [MSTest.TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) 및 [MSTest.TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) 패키지를 포함하는 MSTestV2에 대한 NuGet 패키지 참조를 추가합니다. 다음 명령을 사용하여 NuGet 패키지 관리자 콘솔에서 패키지를 설치할 수 있습니다.

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>이전 스타일 csproj 예제

MSTestV1을 대상으로 하는 샘플 *.csproj*:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

현재 MSTestV2를 대상으로 하는 샘플 *.csproj*:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> 코딩된 UI 테스트 또는 웹 부하 테스트에 해당하는 테스트 프로젝트는 MSTestV2와 호환되지 않습니다. 해당 프로젝트 형식은 사용되지 않습니다. [코딩된 UI 테스트 사용 중단](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) 및 [웹 부하 테스트 사용 중단](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)에 관해 자세히 알아봅니다.

### <a name="sdk-style-csproj-net-core-and-net-5"></a>SDK 스타일 csproj(.NET Core 및 .NET 5)

*.csproj* 가 최신 SDK 스타일 *.csproj* 인 경우 MSTestV2를 이미 사용하고 있을 가능성이 큽니다. NuGet에서 [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) 및 [MSTestV2 어댑터](https://www.nuget.org/packages/MSTest.TestAdapter/)의 NuGet 패키지를 찾을 수 있습니다.

예제:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>MSTestV2로 업그레이드하는 이유

2016년에 MSTestV2를 사용하여 MSTest 프레임워크를 발전시키는 후속 단계를 발표했습니다. 알림 [블로그 게시물](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)에서 해당 변경 내용을 자세히 알아볼 수 있습니다.

* MSTestV2는 [NuGet 패키지](https://www.nuget.org/packages/MSTest.TestFramework/)로 전달되기 때문에 더 쉽게 다운로드하고 업데이트할 수 있습니다.
* MSTestV2는 [오픈 소스](https://github.com/microsoft/testfx)입니다.
* 균일한 앱 플랫폼 지원 - MSTestV2는 .NET Framework, .NET Core, ASP.NET Core 및 UWP에서 균일한 앱 플랫폼 지원을 제공하는 컨버지드 구현입니다. [자세히 알아봅니다](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* 해당 구현은 완전한 플랫폼 간(Windows, Linux, Mac) 구현입니다. [자세히 알아봅니다](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2는 .NET Framework 4.5.0 이상, .NET Core 1.0 이상(유니버설 Windows 앱 10 이상), ASP.NET Core 1.0 이상 및 .NET 5 이상을 대상으로 지정할 수 있습니다.
* 균일한 단일 최종 사용자 확장성 메커니즘을 제공합니다. [자세히 알아봅니다](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* 모든 MSTest 기반 테스트 프로젝트에서 균일한 `DataRow` 지원을 제공합니다. [자세히 알아봅니다](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* 클래스 또는 어셈블리 수준에서 `TestCategory` 특성을 배치할 수 있습니다. [자세히 알아봅니다](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* 다른 어셈블리에 정의된 기본 클래스의 테스트 메서드가 이제 파생 테스트 클래스에서 검색 및 실행됩니다. 해당 변경 내용으로 인해 파생 테스트 클래스 형식에 일관된 동작이 제공됩니다. 호환성을 위해 해당 동작이 필요하지 않은 경우 다음 실행 설정을 사용하여 다시 변경할 수 있습니다.

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* 테스트의 [어셈블리 내 병렬 실행](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md)을 통해 병렬 실행을 더 세부적으로 제어합니다. 이렇게 하면 어셈블리 내에서 테스트를 병렬로 실행할 수 있습니다.
* `TestClass`의 `TestCleanup` 메서드는 해당 `TestInitialize` 메서드가 실패하는 경우에도 호출됩니다. [문제 세부 정보](https://github.com/Microsoft/testfx/issues/250)
* `AssemblyInitialize` 및 `ClassInitialize`에 소요된 시간은 테스트 기간으로 계산되지 않습니다. 해당 변경 내용은 테스트 시간 초과에 미치는 영향을 제한합니다.
* 실행할 수 없는 테스트는 `.runsettings` 파일에서 어댑터 노드에 속한 `MapNotRunnableToFailed` 태그를 통해 실패로 표시되도록 구성할 수 있습니다.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>MSTestV2에서 지원되지 않는 MSTestV1 기능

*   “순서가 지정된 테스트”에는 테스트를 포함할 수 없습니다.
*   어댑터는 *.testsettings* 파일을 통해 구성할 수 없습니다. 테스트 실행 구성에는 새 [ *.runsettings* 파일](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 사용합니다.
*   어댑터는 *.vsmdi* 파일로 지정된 테스트 목록을 지원하지 않습니다.
*   “코딩된 UI 테스트 프로젝트” 및 “웹 성능 및 부하 테스트 프로젝트” 형식은 지원되지 않습니다. [코딩된 UI 테스트 사용 중단](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) 및 [웹 부하 테스트 사용 중단](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)에 관해 자세히 알아봅니다.

## <a name="see-also"></a>참조

- [`.runsettings`를 사용하여 테스트 실행 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [코드 단위 테스트](../test/unit-test-your-code.md)
- [테스트 탐색기를 사용하여 단위 테스트 디버그](../test/debug-unit-tests-with-test-explorer.md)
