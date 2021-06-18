---
title: Visual Studio 확장 업데이트
description: Visual studio 2022를 사용 하도록 Visual Studio 확장을 업데이트 하는 방법에 대해 알아봅니다.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 514c9654a741e4e1e565f0cb2becdbe3157fab0c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308589"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Visual studio 2022 용 Visual Studio 확장 업데이트

이 가이드에 따라 Visual Studio 2022 미리 보기를 사용 하도록 확장을 업데이트할 수 있습니다. Visual Studio 2022 Preview는 64 비트 응용 프로그램으로, VS SDK에서 몇 가지 주요 변경 사항을 소개 합니다. 이 가이드에서는 visual studio 2022의 현재 미리 보기를 사용 하 여 확장을 작동 하는 데 필요한 단계를 안내 하므로 Visual Studio 2022가 GA에 도달 하기 전에 확장을 사용자가 설치할 수 있습니다.

## <a name="installing"></a>설치

Visual [studio 2022 preview 다운로드](https://visualstudio.microsoft.com/vs/preview/vs2022)에서 visual Studio 2022 preview를 설치 합니다.

### <a name="extensions-written-in-a-net-language"></a>.NET 언어로 작성 된 확장 프로그램

관리 되는 확장에 대 한 Visual Studio 2022를 대상으로 하는 VS SDK는 NuGet에서 *배타적* 으로 사용 됩니다.

- [VisualStudio](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17.x 버전) 메타 패키지는 필요한 참조 어셈블리를 대부분 또는 모두 가져옵니다.
- Visual Studio 2022 호환 VSIX를 작성할 수 있도록 [Microsoft..](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) n a m a. x 버전의 패키지를 VSIX 프로젝트에서 참조 해야 합니다.

확장은 "Any CPU" 또는 "x64" 플랫폼으로 컴파일해야 *합니다* . "X86" 플랫폼은 Visual Studio 2022의 64 비트 프로세스와 호환 되지 않습니다.

### <a name="extensions-written-in-c"></a>C + +로 작성 된 확장

C + +로 컴파일된 확장에 대 한 VS SDK는 정상적으로 설치 된 Visual Studio SDK와 함께 사용할 수 있습니다.

확장은 Visual Studio 2022 SDK 및 amd64에 대해 특별히 컴파일해야 *합니다* .

### <a name="update-your-extension-to-visual-studio-2022"></a>Visual Studio 2022로 확장 업데이트

#### <a name="extensions-with-running-code"></a>실행 중인 코드가 포함 된 확장

실행 중인 코드가 포함 된 확장은 Visual Studio 2022 용으로 특별히 컴파일해야 *합니다* . Visual Studio 2022는 특별히 Visual Studio 2022를 대상으로 하지 않는 확장을 로드 하지 않습니다.

Visual studio 2022 확장을 Visual Studio 2022로 마이그레이션하는 방법에 대해 알아봅니다.

1. [프로젝트를 현대화](#modernize-your-vsix-project).
1. Visual Studio 2022 및 이전 버전을 대상으로 지정할 수 있도록 [소스 코드를 공유 프로젝트로 리팩터링](#use-shared-projects-for-multi-targeting) 합니다.
1. [Visual Studio 2022 대상 VSIX 프로젝트](#add-a-visual-studio-2022-target)와 [패키지/어셈블리 다시 매핑 테이블](migrated-assemblies.md)을 추가 합니다.
1. [필요한 코드를 조정](#handle-breaking-api-changes)합니다.
1. [Visual Studio 2022 확장 테스트](#test-your-extension)
1. [Visual Studio 2022 확장을 게시](#publish-your-extension)합니다.

#### <a name="extensions-without-running-code"></a>코드를 실행 하지 않고 확장

실행 중인 코드 (예: 프로젝트/항목 템플릿)를 포함 하지 않는 확장은 두 개의 고유 VSIXs 프로덕션을 포함 하 여 위의 단계를 수행 하는 데 필요 *하지 않습니다* .

대신, 해당 `source.extension.vsixmanifest` 파일에서 다음과 같이 두 개의 설치 대상을 선언 하도록 단일 VSIX를 수정 해야 합니다.

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

공유 프로젝트 및 여러 VSIXs 사용에 대 한이 문서의 단계를 건너뛸 수 있습니다. [테스트](#test-your-extension)를 진행할 수 있습니다.

> [!NOTE]
> Visual studio 2022 Preview를 사용 하 여 *새* visual studio 확장을 작성 하 고 visual studio 2019 또는 이전 버전을 대상으로 하려는 경우 [이 가이드](target-previous-versions.md)를 확인 하세요.

### <a name="msbuild-tasks"></a>MSBuild 작업

MSBuild 작업을 작성 하는 경우 Visual Studio 2022에서 64 비트 MSBuild.exe 프로세스로 로드 될 가능성이 높습니다. 작업에서 32 비트 프로세스를 실행 해야 하는 경우 [이 msbuild 설명서](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) 를 참조 하 여 msbuild가 32 비트 프로세스에서 작업을 로드 하는 것을 알 수 있도록 합니다.

## <a name="modernize-your-vsix-project"></a>VSIX 프로젝트 현대화

Visual Studio 2022 지원을 확장에 추가 하기 전에 다음을 비롯 하 여 기존 프로젝트를 정리 하 고 현대화 하는 것이 좋습니다.

1. [packages.config에서로 `PackageReference` 마이그레이션합니다 ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. 직접 어셈블리 VS SDK 어셈블리 참조를 PackageReference items로 바꿉니다.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > *많은* 어셈블리 참조를 *하나의* PackageReference로 바꿀 수 있습니다.
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   대상으로 하는 Visual Studio의 최소 버전과 일치 하는 패키지 버전을 선택 해야 합니다.

   VS SDK에 고유 하지 않은 일부 어셈블리 (예: Newtonsoft.Json.dll)는 Visual studio 2022 이전에는 간단한 참조를 통해 검색 가능 하지만 visual studio `<Reference Include="Newtonsoft.Json" />` 2022에서는 MSBuild의 기본 어셈블리 검색 경로에서 일부 Visual studio 런타임 및 SDK 디렉터리를 제거 하기 2022 때문에 패키지 참조가 대신 필요 합니다.

   직접 어셈블리 참조에서 NuGet 패키지 참조로 전환 하는 경우 NuGet이 종속성의 전이적 닫기를 자동으로 설치 하므로 추가 어셈블리 참조 및 분석기 패키지를 선택할 수 있습니다. 이는 일반적으로 정상 이지만 빌드 중에 추가 경고가 플래그가 지정 될 수 있습니다. 이러한 경고를 해결 하 고 최대한 많은 문제를 해결 하 고 코드 영역을 사용 하 여 해결할 수 없는 경고를 억제 `#pragma warning disable <id>` 합니다.

## <a name="use-shared-projects-for-multi-targeting"></a>다중 대상 지정을 위해 공유 프로젝트 사용

[공유 프로젝트](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) 는 Visual Studio 2015에서 도입 된 프로젝트 형식입니다. Visual Studio의 공유 프로젝트를 사용 하면 소스 코드 파일을 여러 프로젝트 간에 공유 하 고, 조건부 컴파일 기호와 고유한 참조 집합을 사용 하 여 다른 방식으로 빌드할 수 있습니다.

Visual Studio 2022에는 모든 이전 VS 버전의 고유한 참조 어셈블리 집합이 필요 하기 때문에, 공유 프로젝트를 사용 하 여 확장을 Visual Studio 2022 및 Visual Studio 2022 (이상 버전)로 편리 하 게 다중 대상으로 지정 하 여 코드 공유를 제공 하지만 고유한 참조를 제공 하는 것이 좋습니다.

Visual Studio 확장의 컨텍스트에서 visual studio 2022 이상 및 Visual Studio 2019 및 이전 버전에 대 한 VSIX 프로젝트 하나를 사용할 수 있습니다. 이러한 각 프로젝트에는 `source.extension.vsixmanifest` 및 16KB sdk 또는 17.x sdk에 대 한 패키지 참조만 포함 됩니다. 이러한 VSIX 프로젝트에는 두 VS 버전에서 공유할 수 있는 모든 소스 코드를 호스팅하는 새 공유 프로젝트에 대 한 공유 프로젝트 참조도 있습니다.

이 문서에서는 Visual Studio 2019를 대상으로 하 고 Visual Studio 2022에서 확장을 사용 하려는 VSIX 프로젝트가 이미 있다고 가정 합니다.

이러한 모든 단계는 Visual Studio 2019을 사용 하 여 완료할 수 있습니다.

1. 아직 수행 하지 않은 경우 [프로젝트를 현대화](#modernize-your-vsix-project) 하 여 나중에이 업데이트 프로세스의 단계를 용이 하 게 합니다.

1. VS SDK를 참조 하는 각 기존 프로젝트의 솔루션에 새 공유 프로젝트를 추가 합니다.
   ![새 프로젝트 명령 추가 ](media/update-visual-studio-extension/add-new-project.png)
    ![ 새 프로젝트 템플릿](media/update-visual-studio-extension/new-shared-project-template.png)

1. 각 VS SDK 참조 프로젝트의 참조를 해당 하는 공유 프로젝트에 추가 합니다.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="공유 프로젝트 참조 추가" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. 각 VS SDK 참조 프로젝트의 모든 소스 코드 (.cs, .resx 포함)를 해당 공유 프로젝트로 이동 합니다.
`source.extension.vsixmanifest`VSIX 프로젝트에 파일을 그대로 둡니다.
   ![공유 프로젝트에 모든 원본 파일이 포함 되어 있습니다.](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. 메타 데이터 파일 (릴리스 정보, 라이선스, 아이콘 등) 및 VSCT 파일은 공유 디렉터리로 이동 하 여 VSIX 프로젝트에 연결 된 파일로 추가 해야 합니다.
   ![메타 데이터 및 VSCT 파일을 연결 된 파일로 추가](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - 메타 데이터 파일의 경우 빌드를로 설정 하 `Content` 고 VSIX에 Include를로 설정 `true` 합니다.

      ![VSIX에 메타 데이터 파일 포함](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - VSCT 파일의 경우 빌드를로 설정 하 `VSCTCompile` 고 VSIX에 포함 하지 않습니다.
      Visual Studio에서는이 설정이 지원 되지 않지만 프로젝트를 언로드하고로 변경 하 여 빌드 작업을 수동으로 변경할 수 있습니다. `Content``VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![VSCT 파일을 VSCTCompile로 설정](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. 프로젝트를 빌드하여 새 오류가 도입 되지 않았는지 확인 합니다.

이제 프로젝트에서 Visual Studio 2022 지원을 추가할 준비가 되었습니다.

## <a name="add-a-visual-studio-2022-target"></a>Visual Studio 2022 대상 추가

이 문서에서는 [Visual Studio 확장을 공유 프로젝트로 요소](#use-shared-projects-for-multi-targeting)를 구분 하는 단계를 완료 했다고 가정 합니다.

Visual Studio 2019를 사용 하 여 완료할 수 있는 다음 단계를 사용 하 여 확장에 Visual Studio 2022 지원 추가를 계속 합니다.

1. 새 VSIX 프로젝트를 솔루션에 추가 합니다. 이 프로젝트는 Visual Studio 2022를 대상으로 합니다. 템플릿과 함께 제공 된 소스 코드를 모두 제거 하 고 *`source.extension.vsixmanifest` 파일을 보관* 합니다.

1. 새 VSIX 프로젝트에서 Visual Studio 2019 대상 VSIX가 참조 하는 동일한 공유 프로젝트에 공유 프로젝트 참조를 추가 합니다.

   ![하나의 공유 프로젝트와 두 개의 VSIX 프로젝트를 포함 하는 솔루션](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. 새 VSIX 프로젝트가 올바르게 빌드되는지 확인 합니다. 컴파일러 오류를 해결 하려면 원본 VSIX 프로젝트와 일치 하는 참조를 추가 해야 할 수도 있습니다.

1. 관리 되는 VS 확장의 경우 NuGet 패키지 관리자를 사용 하거나 프로젝트 파일을 직접 편집 하 여 Visual Studio 2022에서 대상 프로젝트 파일의 16kb (또는 이전 버전)에서 17.x 패키지 버전으로 패키지 참조를 업데이트 합니다.

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Nuget.org에서 실제로 사용할 수 있는 버전을 사용 합니다. 이전에 사용 된 것은 데모용 으로만 사용 됩니다.

   대부분의 경우 패키지 Id가 변경 되었습니다. Visual Studio 2022의 변경 내용 목록은 [패키지/어셈블리 매핑 표](migrated-assemblies.md) 를 참조 하세요.

   C + +로 작성 된 확장에는를 사용 하 여 컴파일할 수 있는 SDK가 아직 없습니다.

1. C + + 프로젝트의 경우 amd64에 대해 컴파일되어야 합니다. 관리 되는 확장의 경우 대상으로 지정 하는 모든 CPU에 대해 프로젝트를 변경 하는 것이 좋습니다 `x64` . Visual Studio 2022에서 확장이 항상 64 비트 프로세스에서 로드 됨을 반영 합니다. `Any CPU` 는 해도 되지만 x64 전용 네이티브 이진 파일을 참조 하는 경우 경고를 생성할 수 있습니다.

   확장이 네이티브 모듈에 있을 수 있는 모든 종속성은 x86 이미지에서 amd64 이미지로 업데이트 되어야 합니다.

1. `source.extension.vsixmanifest`Visual Studio 2022를 대상으로 하는 파일을 편집 합니다. `<InstallationTarget>`Visual Studio 2022을 반영 하 고 amd64 페이로드를 나타내려면 태그를 설정 합니다.

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Visual Studio 2019에서이 파일에 대 한 디자이너는 새 요소를 노출 하지 않으므로 `ProductArchitecture` 이 변경 작업은 **솔루션 탐색기** 의 **연결 프로그램** 명령을 통해 액세스할 수 있는 xml 편집기를 사용 하 여 수행 해야 합니다.

   이 `ProductArchitecture` 요소는 중요 합니다. Visual Studio 2022는 확장을 설치 *하지 않습니다* .

   | 요소 | 값 | Description |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | 이 VSIX에서 지원하는 플랫폼입니다. 대/소문자 구분 안 함 요소당 하나의 플랫폼과 InstallTarget당 하나의 요소. 17.0 미만 제품 버전의 경우 기본값은 x86이며 생략할 수 있습니다.  제품 버전 17.0 이상의 경우 이 요소가 필요하며 기본값이 없습니다. Visual Studio 2022의 경우 이 요소에 유효한 콘텐츠는 "amd64"뿐입니다. |

1. source.extension.vsixmanifest에 필요한 다른 조정을 Visual Studio 2019(있는 경우)를 대상으로 하는 것과 일치하도록 합니다. `Identity`매니페스트의 요소에서 VSIX의 ID는 두 확장에 대해 동일해야 합니다.

이 시점에서 Visual Studio 2022 대상 확장 VSIX가 있습니다. Visual Studio 2022 대상 VSIX 프로젝트를 빌드하고 표시되는 [빌드 중단을 통해 작업해야](#handle-breaking-api-changes)합니다. Visual Studio 2022 대상 VSIX 프로젝트에 빌드 중단이 없는 경우 축하합니다. 테스트할 준비가 되었습니다.

## <a name="handle-breaking-api-changes"></a>주요 API 변경 처리

Visual Studio 2022에는 이전 버전에서 실행되었을 때 코드를 변경해야 할 수 있는 [주요 API 변경 내용이](breaking-api-list.md) 있습니다. 각 코드에 대한 코드를 업데이트하는 방법에 대한 팁은 해당 문서를 검토합니다.

코드를 조정할 때는 Visual Studio 2022에 대한 지원을 추가하는 동시에 코드가 사전 Visual Studio 2022를 계속 지원할 수 있도록 [조건부 컴파일을](#use-conditional-compilation-symbols) 사용하는 것이 좋습니다.

Visual Studio 2022 대상 확장 빌드가 완료되면 [테스트를](#test-your-extension)계속 진행합니다.

## <a name="use-conditional-compilation-symbols"></a>조건부 컴파일 기호 사용

Visual Studio 2022 및 이전 버전에 대해서도 동일한 소스 코드를 사용하려는 경우 코드를 포크하여 주요 변경 내용에 맞게 조정할 수 있도록 조건부 컴파일을 사용해야 할 수 있습니다. 조건부 컴파일은 특정 위치의 다양한 API를 수용하면서 대부분의 코드를 공유하는 데 사용할 수 있는 C#, Visual Basic 및 C++ 언어의 기능입니다.

전처리기 지시문 및 조건부 컴파일 기호 사용에 대한 자세한 내용은 Microsoft 문서 [#if 전처리기 지시문](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)에서 확인할 수 있습니다.

이전 Visual Studio 버전을 대상으로 하는 프로젝트에는 다른 API를 사용하도록 코드를 포크하는 데 사용할 수 있는 조건부 컴파일 기호가 필요합니다. 다음 이미지와 같이 프로젝트 속성 페이지에서 조건부 컴파일 기호를 설정할 수 있습니다.

![조건부 컴파일 기호 설정](media/update-visual-studio-extension/conditional-compilation-symbols.png)

기본적으로 입력하는 기호는 하나의 구성에만 적용될 수 있기 때문에 *모든* 구성에 대해 컴파일 기호를 설정해야 합니다.

### <a name="c-techniques"></a>C \# 기술

그런 다음, 다음 코드와 같이 해당 기호를 프로세서 전 지시문( )으로 사용할 수 `#if` 있습니다. 그런 다음 코드를 포크하여 서로 다른 Visual Studio 버전 간의 주요 변경을 처리할 수 있습니다.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

경우에 따라 를 사용하여 `var` 형식의 이름을 지정하지 않아도 되므로 지역이 필요하지 않은 경우도 `#if` 있습니다. 위의 조각은 다음과 같이 작성할 수도 있습니다.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

구문을 사용하는 경우 `#if` 아래 표시된 문서의 언어 서비스 컨텍스트 드롭다운을 사용하여 구문 강조 표시를 변경하는 방법과 언어 서비스에서 제공하는 다른 도움말을 통해 확장과 다른 확장의 한 대상 Visual Studio 버전에 집중할 수 있습니다.

![공유 프로젝트의 조건부 컴파일](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>XAML 공유 기술

XAML에는 전처리기 기호를 기반으로 콘텐츠를 사용자 지정할 수 있는 전처리기 가 없습니다. Visual Studio 2022 버전과 이전 버전 간에 콘텐츠가 달라야 하는 두 XAML 페이지를 복사하고 유지 관리해야 할 수 있습니다.

그러나 경우에 따라 Visual Studio 2022 및 이전 버전에서 고유한 어셈블리에 있는 형식에 대한 참조는 어셈블리를 참조하는 네임스페이스를 제거하여 하나의 XAML 파일에서 계속 나타낼 수 있습니다.

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>확장 테스트

Visual Studio 2022를 대상으로 하는 확장을 테스트하려면 Visual Studio 2022 미리 보기를 설치해야 합니다.
Visual Studio 2022 미리 보기 이전 버전의 Visual Studio 64비트 확장을 실행할 수 없습니다.

Visual Studio 2022 미리 보기를 사용하여 Visual Studio 2022 또는 이전 버전을 대상으로 하는지 여부에 관계없이 확장을 빌드하고 테스트할 수 있습니다. Visual Studio 2022에서 VSIX 프로젝트를 시작할 때 Visual Studio 실험적 인스턴스가 시작됩니다.

확장을 지원하려는 각 버전의 Visual Studio 테스트하는 것이 좋습니다.

이제 [확장을 게시할](#publish-your-extension)준비가 되었습니다.

## <a name="publish-your-extension"></a>확장 게시

2022년 Visual Studio 대상을 확장에 추가하고 테스트했습니다. 이제 전 세계에 대한 확장을 게시할 준비가 되었습니다.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

[Visual Studio Marketplace](https://marketplace.visualstudio.com/) 확장을 게시하면 새 사용자가 확장을 찾아 설치할 수 있습니다. 확장이 Visual Studio 2022를 단독으로 대상으로 하는지 또는 이전 VS 버전을 대상으로 하는지 여부에 관계없이 Marketplace에서 지원합니다.

나중에 Marketplace에서 하나의 Marketplace 목록에 여러 VSIX를 업로드할 수 있게 되며, 이를 통해 Visual Studio 2022를 대상으로 하는 VSIX 및 사전 Visual Studio 2022 VSIX를 업로드할 수 있습니다. 사용자는 VS 확장 관리자를 사용할 때 설치한 VS 버전에 적합한 VSIX를 자동으로 가져옵니다.

Visual Studio 2022의 미리 보기 릴리스의 경우 Marketplace는 Marketplace 목록당 단일 VSIX 파일만 지원합니다. Visual Studio 2022는 미리 보기로 제공됩니다. 확장에 대한 별도의 Visual Studio 2022 Marketplace 목록만 있는 것이 좋습니다. 이렇게 하면 이전 버전의 Visual Studio 고객에게 영향을 주지 않고 필요에 따라 Visual Studio 2022 확장을 반복할 수 있습니다. 확장의 출처가 일반 확장보다 2022년 Visual Studio 경우에도 확장을 '미리 보기'로 표시하여 안정성이 저하될 수 있다는 예상을 설정할 수도 있습니다.

### <a name="custom-installer"></a>사용자 지정 설치 관리자

확장을 설치하는 MSI/EXE를 빌드하고 확장의 일부(일부)를 설치할 vsixinstaller.exe 생성하는 경우 Visual Studio 2022의 VSIX 설치 관리자가 업데이트되었는지 알고 있습니다. 개발자는 Visual Studio 2022와 함께 제공되는 VSIX 설치 관리자 버전을 사용하여 Visual Studio 2022에 대한 확장을 설치해야 합니다. Visual Studio 2022의 VSIX 설치 관리자도 동일한 컴퓨터에 Visual Studio 2022와 함께 설치된 이전 버전의 Visual Studio 대상으로 하는 적용 가능한 확장을 설치합니다.

### <a name="network-share"></a>네트워크 공유

LAN 또는 다른 방법으로 확장을 공유할 수 있습니다. Visual Studio 2022 및 Visual Studio 이전 버전을 대상으로 하는 경우 여러 VSIX를 개별적으로 공유하고 사용자가 설치한 Visual Studio 버전에 따라 설치할 VSIX를 알 수 있도록 파일 이름을 지정(또는 고유한 폴더에 배치)해야 합니다.

### <a name="other-considerations"></a>기타 고려 사항

#### <a name="dependencies"></a>종속성

VSIX가 요소를 통해 다른 VSIX를 종속성으로 지정하는 경우 `<dependency>` 참조된 각 VSIX는 VSIX와 동일한 대상 및 제품 아키텍처에 설치해야 합니다. 종속 VSIX가 대상 Visual Studio 설치를 지원하지 않으면 VSIX가 실패합니다. 종속 VSIX가 사용자보다 더 많은 대상과 아키텍처를 지원해도 괜찮습니다. 이 제한은 종속 항목이 있는 VSIX의 배포 및 배포 접근 방식이 해당 종속 항목의 배포 및 배포 방식을 미러해야 임을 의미합니다.

## <a name="q--a"></a>Q & A

**Q:** 데이터(예: 템플릿)만 제공하므로 확장에 interop 변경이 필요하지 않습니다. Visual Studio 2022도 포함하는 단일 확장을 만들 수 있나요?

**A:** 예!  이에 대한 자세한 내용은 [코드를 실행하지 않고 확장을](#extensions-without-running-code) 참조하세요.

**Q:** NuGet 종속성이 이전 interop 어셈블리를 가져오고 충돌 클래스를 발생시키고 있습니다.

**A**: 중복 어셈블리를 방지하려면 .csproj 파일에 다음 줄을 추가합니다.

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

이렇게 하면 패키지 참조가 다른 dependencies에서 이전 버전의 어셈블리를 가져올 수 없습니다.

**Q:** 내 소스 파일을 공유 프로젝트로 전환한 후 Visual Studio 명령 및 핫키가 작동하지 않습니다.

**A:** 이미지 최적화 프로그램 샘플의 [2.4단계에서는](samples.md#step-2---refactor-source-code-into-a-shared-project) VSCT 파일을 VSCT 파일로 컴파일되도록 연결된 항목으로 추가하는 방법을 보여 줍니다.

## <a name="next-steps"></a>다음 단계

각 단계에 대한 프로젝트 및 코드 변경 내용에 대한 링크가 있는 단계별 예제 [ImageOptimizer](samples.md)를 따릅니다.
