---
title: 확장을 왕복 하는 방법
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: ca1f367510aa9730c1b3b212438579a8eaeb0e8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387280"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>방법: Visual Studio 2019/2017 및 Visual Studio 2015과 호환 되는 확장 만들기

이 문서에서는 Visual Studio 2015와 Visual studio 2019 또는 Visual Studio 2017 간에 확장성 프로젝트를 라운드트립 하는 방법을 설명 합니다. 이 업그레이드를 완료 한 후에는 프로젝트를 Visual Studio 2015 및 Visual Studio 2019 또는 2017 둘 다에서 열고 빌드하고 설치 하 고 실행할 수 있습니다. 참조로, Visual Studio 2015 및 Visual Studio 2019 또는 2017 사이에서 라운드트립할 수 있는 일부 확장은 [VS SDK 확장성 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)에서 찾을 수 있습니다.

Visual Studio 2019/2017 에서만 빌드 하려고 하지만 출력 VSIX를 Visual Studio 2015 및 Visual Studio 2019/2017 둘 다에서 실행 하려는 경우에는 [확장 마이그레이션 문서](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)를 참조 하세요.

> [!NOTE]
> 버전 간 Visual Studio의 변경으로 인해 한 버전에서 작동 하는 일부 항목은 다른 버전에서 작동 하지 않습니다. 액세스 하려는 기능을 두 버전 모두에서 사용할 수 있는지 또는 확장에서 예기치 않은 결과가 발생 하는지 확인 합니다.

다음은 VSIX를 라운드트립 하기 위해이 문서에서 완료 해야 하는 단계에 대 한 개요입니다.

1. 올바른 NuGet 패키지를 가져옵니다.
2. 확장 매니페스트 업데이트:
    * 설치 대상
    * 필수 구성 요소
3. 업데이트 .Csproj:
    * `<MinimumVisualStudioVersion>`를 업데이트합니다.
    * `<VsixType>` 속성 추가
    * 디버깅 속성을 `($DevEnvDir)` 3 번 추가 합니다.
    * 빌드 도구 및 대상 가져오기에 대 한 조건을 추가 합니다.

4. 빌드 및 테스트

## <a name="environment-setup"></a>환경 설정

이 문서에서는 컴퓨터에 다음이 설치 되어 있다고 가정 합니다.

* VS SDK가 설치 된 Visual Studio 2015
* 확장성 워크 로드가 설치 된 Visual Studio 2019 또는 2017

## <a name="recommended-approach"></a>권장 접근 방식

Visual Studio 2019 또는 2017 대신 Visual Studio 2015을 사용 하 여 업그레이드를 시작 하는 것이 좋습니다. Visual Studio 2015에서 개발 하는 주요 혜택은 Visual Studio 2015에서 사용할 수 없는 어셈블리를 참조 하지 않도록 하는 것입니다. Visual Studio 2019 또는 2017에서 개발 하는 경우 Visual Studio 2019 또는 2017에만 존재 하는 어셈블리에 대 한 종속성이 발생할 수 있습니다.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>project.js에 대 한 참조가 없는지 확인

이 문서의 뒷부분에서 **.csproj* 파일에 조건부 import 문을 삽입 합니다. NuGet 참조가project.js에 저장 된 경우 * 에*는이 작업이 수행 되지 않습니다. 따라서 모든 NuGet 참조를 *packages.config* 파일로 이동 하는 것이 좋습니다.
프로젝트에 파일 * 에 대 한project.js* 포함 되어 있는 경우:

* *project.js*의 참조를 기록해 둡니다.
* **솔루션 탐색기**에서 파일 *의project.js* 를 프로젝트에서 삭제 합니다. 그러면 파일 * 에서project.js* 삭제 되 고 프로젝트에서 제거 됩니다.
* NuGet 참조를 프로젝트에 다시 추가 합니다.
  * **솔루션** 을 마우스 오른쪽 단추로 클릭 하 고 **솔루션용 NuGet 패키지 관리**를 선택 합니다.
  * Visual Studio에서 자동으로 *packages.config* 파일을 만듭니다.

> [!NOTE]
> 프로젝트에 EnvDTE 패키지가 포함 된 경우 **참조 추가** 를 선택 하 고 적절 한 참조를 추가 하 **여 참조를** 마우스 오른쪽 단추로 클릭 하 여 추가 해야 할 수 있습니다. NuGet 패키지를 사용 하면 프로젝트를 빌드하는 동안 오류가 발생할 수 있습니다.

## <a name="add-appropriate-build-tools"></a>적절 한 빌드 도구 추가

적절 하 게 빌드 및 디버그할 수 있도록 하는 빌드 도구를 추가 해야 합니다. Microsoft는이 VisualStudio 작업에 대 한 어셈블리를 만들었습니다.

Visual Studio 2015 및 2019/2017에서 VSIXv3를 빌드 및 배포 하려면 다음 NuGet 패키지가 필요 합니다.

버전 | 빌드된 도구
--- | ---
Visual Studio 2015 | VisualStudio입니다. 14.0
Visual Studio 2019 또는 2017 | Microsoft.

이를 수행하려면:

* 프로젝트에 NuGet 패키지 VisualStudio를 추가 합니다. 14.0
* 프로젝트에 Microsoft. 사용자의 Uibuildbuilda가 포함 되어 있지 않으면이를 추가 합니다.
* Microsoft.... x m m. x m a. x 버전 이상이 있어야 합니다.

## <a name="update-extension-manifest"></a>확장 매니페스트 업데이트

### <a name="1-installation-targets"></a>1. 설치 대상

VSIX를 빌드하기 위해 대상으로 지정할 버전을 Visual Studio에 알려 주어 야 합니다. 일반적으로 이러한 참조는 버전 14.0 (Visual Studio 2015), 버전 15.0 (Visual Studio 2017) 또는 버전 16.0 (Visual Studio 2019) 중 하나입니다. 이 경우 두 버전 모두에 대 한 확장을 설치 하는 VSIX를 빌드하려고 합니다. 따라서 두 버전을 모두 대상으로 해야 합니다. VSIX를 14.0 이전 버전에서 빌드하고 설치 하려면 이전 버전 번호를 설정 하 여이 작업을 수행할 수 있습니다. 그러나 버전 10.0 및 이전 버전은 더 이상 지원 되지 않습니다.

* Visual Studio에서 *source.extension.vsixmanifest* 파일을 엽니다.
* **설치 대상** 탭을 엽니다.
* **버전 범위** 를 [14.0, 17.0)로 변경 합니다. ' ['는 14.0 및 그 이전의 모든 버전을 포함 하도록 Visual Studio에 지시 합니다. ') '는 Visual Studio에 버전 17.0에 포함 된 모든 버전을 포함 하도록 지시 합니다.
* 모든 변경 내용을 저장 하 고 Visual Studio의 모든 인스턴스를 닫습니다.

![설치 대상 이미지](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. *source.extension.vsixmanifest* 파일에 필수 조건 추가

필수 구성 요소로 Visual Studio 핵심 편집기가 필요 합니다. Visual Studio를 열고 업데이트 된 매니페스트 디자이너를 사용 하 여 필수 구성 요소를 삽입 합니다.

이렇게 하려면 다음을 수행 합니다.

* 파일 탐색기에서 프로젝트 디렉터리로 이동 합니다.
* 텍스트 편집기를 사용 하 여 *source.extension.vsixmanifest* 파일을 엽니다.
* 다음 태그를 추가 합니다.

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* 파일을 저장하고 닫습니다.

> [!NOTE]
> 모든 버전의 Visual Studio 2019 또는 2017과 호환 되도록 필수 구성 요소 버전을 수동으로 편집 해야 할 수도 있습니다. 이는 디자이너가 현재 버전의 Visual Studio (예: 15.0.26208.0)로 최소 버전을 삽입 하기 때문입니다. 그러나 다른 사용자가 이전 버전을 가질 수 있으므로이를 15.0으로 수동으로 편집 하는 것이 좋습니다.

이 시점에서 매니페스트 파일은 다음과 같습니다.

![필수 조건 예제](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>프로젝트 파일 수정 (myproject)

이 단계를 수행 하는 동안 수정 된 .csproj에 대 한 참조를 포함 하는 것이 좋습니다. [여기](https://github.com/Microsoft/VSSDK-Extensibility-Samples)에서 여러 예제를 찾을 수 있습니다. 모든 확장성 샘플을 선택 하 고 참조에 대 한 *.csproj* 파일을 찾은 후 다음 단계를 실행 합니다.

* **파일 탐색기**에서 프로젝트 디렉터리로 이동 합니다.
* 텍스트 편집기를 사용 하 여 *myproject* 파일을 엽니다.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. MinimumVisualStudioVersion 업데이트

* 최소 visual studio 버전을로 설정 하 `$(VisualStudioVersion)` 고이에 대 한 조건문을 추가 합니다. 이러한 태그가 없는 경우 추가 합니다. 태그가 아래와 같이 설정 되었는지 확인 합니다.

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. VsixType 속성을 추가 합니다.

* 속성 그룹에 다음 태그를 추가 `<VsixType>v3</VsixType>` 합니다.

> [!NOTE]
> 태그 아래에이를 추가 하는 것이 좋습니다 `<OutputType></OutputType>` .

### <a name="3-add-the-debugging-properties"></a>3. 디버깅 속성 추가

* 다음 속성 그룹을 추가 합니다.

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* *.Csproj* 파일 및 모든 *.csproj 사용자* 파일에서 다음 코드 예제의 모든 인스턴스를 삭제 합니다.

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. 빌드 도구 가져오기에 조건 추가

* Microsoft... n e t. n e t. n e t 참조가 있는 태그에 조건문을 추가 `<import>` 합니다. `'$(VisualStudioVersion)' != '14.0' And`조건문 앞에 삽입 합니다. 이러한 문은 .csproj 파일의 머리글과 바닥글에 표시 됩니다.

예를 들면 다음과 같습니다.

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* VisualStudio 14.0를 포함 하는 태그에 추가 조건문을 추가 합니다. `<import>` `'$(VisualStudioVersion)' == '14.0' And`조건문 앞에 삽입 합니다. 이러한 문은 .csproj 파일의 머리글과 바닥글에 표시 됩니다.

예를 들면 다음과 같습니다.

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Microsoft... n e t. n e t. n e t 참조가 있는 태그에 조건문을 추가 `<Error>` 합니다. 조건문 앞에를 삽입 하 여이 작업을 수행 `'$(VisualStudioVersion)' != '14.0' And` 합니다. 이러한 문은 .csproj 파일의 바닥글에 표시 됩니다.

예를 들면 다음과 같습니다.

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* VisualStudio 14.0를 포함 하는 태그에 추가 조건문을 추가 합니다. `<Error>` `'$(VisualStudioVersion)' == '14.0' And`조건문 앞에 삽입 합니다. 이러한 문은 .csproj 파일의 바닥글에 표시 됩니다.

예를 들면 다음과 같습니다.

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* .Csproj 파일을 저장 하 고 닫습니다. 
  * 솔루션에 둘 이상의 프로젝트를 사용 하는 경우 프로젝트 상황에 맞는 메뉴에서 "시작 프로젝트로 설정"을 사용 하 여이 프로젝트를 시작 프로젝트로 설정 합니다. 이렇게 하면 프로젝트를 언로드한 후 Visual Studio에서이 프로젝트를 다시 열립니다.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Visual Studio 2015 및 Visual Studio 2019 또는 2017에서 확장 설치 테스트

이 시점에서 프로젝트는 Visual Studio 2015 및 Visual Studio 2017 모두에 설치할 수 있는 VSIXv3 빌드 준비를 해야 합니다.

* Visual Studio 2015에서 프로젝트를 엽니다.
* 프로젝트를 빌드하고 VSIX가 올바르게 빌드되는 출력을 확인 합니다.
* 프로젝트 디렉터리로 이동 합니다.
* *\Bin\debug* 폴더를 엽니다.
* VSIX 파일을 두 번 클릭 하 고 Visual Studio 2015 및 Visual Studio 2019/2017에 확장을 설치 합니다.
* 설치 된 섹션의 **도구**  >  **확장 및 업데이트** 에서 확장을 볼 수 있는지 확인 **Installed** 합니다.
* 확장을 실행/사용 하 여 작동 하는지 확인 합니다.

![VSIX 찾기](media/finding-a-VSIX-example.png)

> [!NOTE]
> 프로젝트에서 **파일을 여는**메시지와 함께 응답이 중지 되는 경우 Visual Studio를 강제로 종료 하 고, 프로젝트 디렉터리로 이동 하 고, 숨겨진 폴더를 표시 하 고, vs 폴더를 삭제 합니다 *.*
