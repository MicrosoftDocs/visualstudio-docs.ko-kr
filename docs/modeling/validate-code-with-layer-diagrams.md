---
title: 종속성 다이어그램을 사용하여 코드 유효성 검사
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80759705"
---
# <a name="validate-code-with-dependency-diagrams"></a>종속성 다이어그램을 사용하여 코드 유효성 검사

## <a name="why-use-dependency-diagrams"></a>종속성 다이어그램을 사용 하는 이유

코드가 디자인과 충돌 하지 않도록 하려면 Visual Studio에서 종속성 다이어그램으로 코드의 유효성을 검사 합니다. 이 경우 다음에 도움이 됩니다.

- 코드의 종속성과 종속성 다이어그램에 대 한 종속성 간의 충돌을 찾습니다.

- 제안된 변경 내용의 영향을 받을 수 있는 종속성을 찾습니다.

   예를 들어 종속성 다이어그램을 편집 하 여 잠재적인 아키텍처 변경을 표시 한 다음 코드의 유효성을 검사 하 여 영향을 받는 종속성을 확인할 수 있습니다.

- 코드를 다른 디자인으로 리팩터링 또는 마이그레이션합니다.

   코드를 다른 아키텍처로 이동할 때 아직 작업이 필요한 코드 또는 종속성을 찾을 수 있습니다.

**요구 사항**

- Visual Studio

  .NET Core 프로젝트에 대 한 종속성 다이어그램을 만들려면 Visual Studio 2019 버전 16.2 이상이 있어야 합니다.

- 종속성 다이어그램이 포함 된 모델링 프로젝트가 있는 솔루션입니다. 이 종속성 다이어그램은 유효성을 검사 하려는 c # 또는 Visual Basic 프로젝트의 아티팩트에 연결 해야 합니다. [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)를 참조 하세요.

이 기능을 지원하는 Visual Studio 버전을 확인하려면 [아키텍처 및 모델링 도구에 대한 에디션 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

Visual Studio 또는 명령 프롬프트에서 열려 있는 종속성 다이어그램에서 수동으로 코드의 유효성을 검사할 수 있습니다. 로컬 빌드 또는 Azure Pipelines 빌드를 실행할 때 자동으로 코드의 유효성을 검사할 수도 있습니다. [Channel 9 비디오: 종속성 다이어그램을 사용 하 여 아키텍처 디자인 및 유효성 검사](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)를 참조 하세요.

> [!IMPORTANT]
> TFS (Team Foundation Server)를 사용 하 여 레이어 유효성 검사를 실행 하려면 빌드 서버에 동일한 버전의 Visual Studio도 설치 해야 합니다.

## <a name="live-dependency-validation"></a>라이브 종속성 유효성 검사

종속성 유효성 검사는 실시간으로 수행 되 고 오류는 **오류 목록**에 즉시 표시 됩니다.

* 실시간 유효성 검사는 c # 및 Visual Basic에 대해 지원 됩니다.

* 라이브 종속성 유효성 검사를 사용할 때 전체 솔루션 분석을 사용 하도록 설정 하려면 **오류 목록**에 표시 되는 황금색 표시줄에서 옵션 설정을 엽니다.

  - 솔루션에서 모든 아키텍처 문제를 보지 않으려는 경우 금색 표시줄을 영구적으로 해제할 수 있습니다.
  - 전체 솔루션 분석을 사용 하지 않는 경우 분석은 편집 중인 파일에 대해서만 수행 됩니다.

* 라이브 유효성 검사를 사용 하도록 프로젝트를 업그레이드 하는 경우 변환 진행률이 대화 상자에 표시 됩니다.

* 라이브 종속성 유효성 검사를 위해 프로젝트를 업데이트 하는 경우 NuGet 패키지의 버전은 모든 프로젝트에 대해 동일 하 게 업그레이드 되며 사용 중인 가장 높은 버전입니다.

* 새 종속성 유효성 검사 프로젝트를 추가 하면 프로젝트 업데이트가 트리거됩니다.

## <a name="see-if-an-item-supports-validation"></a>항목에서 유효성 검사를 지원하는지 확인

여러 앱에서 공유 되는 프로젝트의 웹 사이트, Office 문서, 일반 텍스트 파일 및 파일에 레이어를 연결할 수 있지만, 유효성 검사 프로세스에 포함 되지 않습니다. 별도의 레이어에 연결된 프로젝트 또는 어셈블리의 경우에는 해당 레이어 간에 종속성이 나타나지 않아도 유효성 검사 오류가 나타나지 않습니다. 이러한 참조는 코드에서 사용하지 않는 한 종속성으로 처리되지 않습니다.

1. 종속성 다이어그램에서 계층을 하나 이상 선택 하 고 선택 항목을 마우스 오른쪽 단추로 클릭 한 다음 **링크 보기**를 클릭 합니다.

2. **레이어 탐색기**에서 **유효성 검사 지원** 열을 확인 합니다. 값이 false일 경우 해당 항목은 유효성 검사를 지원하지 않습니다.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>유효성 검사에 다른.NET 어셈블리 및 프로젝트 포함

항목을 종속성 다이어그램으로 끌면 해당 .NET 어셈블리나 프로젝트에 대 한 참조가 모델링 프로젝트의 **Layer references** 폴더에 자동으로 추가 됩니다. 이 폴더에는 유효성 검사 중 분석되는 프로젝트와 어셈블리에 대한 참조가 포함되어 있습니다. 다른 .NET 어셈블리 및 프로젝트를 수동으로 종속성 다이어그램으로 끌어 오지 않고 유효성 검사에 포함할 수 있습니다.

1. **솔루션 탐색기**에서 모델링 프로젝트 또는 **레이어 참조** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **참조 추가**를 클릭 합니다.

2. **참조 추가** 대화 상자에서 어셈블리 또는 프로젝트를 선택한 다음 **확인**을 클릭 합니다.

## <a name="validate-code-manually"></a>수동으로 코드 유효성 검사

솔루션 항목에 연결 된 종속성 다이어그램이 열려 있는 경우 다이어그램에서 바로 가기 **유효성 검사** 명령을 실행할 수 있습니다. 또한 명령 프롬프트를 사용 하 여 **/p: ValidateArchitecture** 사용자 지정 속성을 **True**로 설정 하 여 **msbuild** 명령을 실행할 수 있습니다. 예를 들어, 코드를 변경할 때 종속성 충돌을 빠르게 찾을 수 있도록 레이어 유효성 검사를 정기적으로 수행합니다.

### <a name="validate-code-from-an-open-dependency-diagram"></a>열려 있는 종속성 다이어그램에서 코드 유효성 검사

1. 다이어그램 화면을 마우스 오른쪽 단추로 클릭 한 다음 **아키텍처 유효성 검사**를 클릭 합니다.

    > [!NOTE]
    > 기본적으로 종속성 다이어그램 (. microsoft.visualstudio.teamarchitect.layerdesigner.diagrams.layerdiagram.show) 파일의 **빌드 작업** 속성은 **유효성 검사로 설정 되어 있으므로 다이어그램이** 유효성 검사 프로세스에 포함 됩니다.

     **오류 목록** 창에서 발생 하는 모든 오류를 보고 합니다. 유효성 검사 오류에 대 한 자세한 내용은 [레이어 유효성 검사 문제 해결](#troubleshoot-layer-validation-issues)을 참조 하세요.

2. 각 오류의 소스를 보려면 **오류 목록** 창에서 오류를 두 번 클릭 합니다.

    > [!NOTE]
    > Visual Studio는 오류 원본 대신 코드 맵을 표시할 수 있습니다. 이는 종속성 다이어그램에 지정 되지 않은 어셈블리에 대 한 종속성이 코드에 있거나 종속성 다이어그램에서 지정한 종속성이 코드에 없는 경우에 발생 합니다. 이 경우 코드 맵이나 코드를 검토하여 종속성이 있어야 하는지 여부를 확인합니다. 코드 맵에 대 한 자세한 내용은 [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)을 참조 하세요.

3. 오류를 관리 하려면 [레이어 유효성 검사 오류 해결](#resolve-layer-validation-errors)을 참조 하세요.

### <a name="validate-code-at-the-command-prompt"></a>명령 프롬프트에서 코드 유효성 검사

1. Visual Studio 명령 프롬프트를 엽니다.

2. 다음 중 하나를 선택합니다.

   - 솔루션의 특정 모델링 프로젝트에 대해 코드의 유효성을 검사 하려면 다음 사용자 지정 속성을 사용 하 여 MSBuild를 실행 합니다.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 또는

       모델링 프로젝트 (. .modelproj) 파일 및 종속성 다이어그램이 포함 된 폴더로 이동한 후 다음 사용자 지정 속성을 사용 하 여 MSBuild를 실행 합니다.

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 솔루션의 모든 모델링 프로젝트에 대해 코드 유효성을 검사 하려면 다음 사용자 지정 속성을 사용 하 여 MSBuild를 실행 합니다.

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 또는

       종속성 다이어그램이 포함 된 모델링 프로젝트를 포함 하는 솔루션 폴더로 이동한 후 다음 사용자 지정 속성을 사용 하 여 MSBuild를 실행 합니다.

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     발생하는 모든 오류가 나열됩니다. MSBuild에 대 한 자세한 내용은 [msbuild](../msbuild/msbuild.md) 및 [msbuild 작업](../msbuild/msbuild-task.md)을 참조 하세요.

   유효성 검사 오류에 대 한 자세한 내용은 [레이어 유효성 검사 문제 해결](#troubleshoot-layer-validation-issues)을 참조 하세요.

### <a name="manage-validation-errors"></a>유효성 검사 오류 관리

개발 과정에서 유효성 검사 중 보고된 충돌 문제 중 일부를 표시하지 않을 수 있습니다. 예를 들어 이미 해결되었거나 특정 시나리오와 관계가 없는 오류를 표시하지 않을 수 있습니다. 오류를 표시 하지 않는 경우에는 Team Foundation에서 작업 항목을 기록 하는 것이 좋습니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

#### <a name="create-a-work-item-for-a-validation-error"></a>유효성 검사 오류에 대 한 작업 항목 만들기

- **오류 목록** 창에서 오류를 마우스 오른쪽 단추로 클릭 하 고 **작업 항목 만들기**를 가리킨 다음 만들려는 작업 항목의 형식을 클릭 합니다.

이러한 작업을 사용 하 여 **오류 목록** 창에서 유효성 검사 오류를 관리할 수 있습니다.

|**수행할 작업**|**다음 단계 수행**|
|-|-|
|선택한 오류를 유효성 검사 중에 표시 안 함|하나 또는 여러 개의 선택한 오류를 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **오류 표시 안 함**을 클릭 합니다.<br /><br /> 표시되지 않는 오류는 취소선 서식을 사용하여 나타납니다. 다음에 유효성 검사를 실행하면 이러한 오류가 나타나지 않습니다.<br /><br /> 표시 되지 않는 오류는 해당 종속성 다이어그램 파일에 대 한 비 표시 오류 파일에서 추적 됩니다.|
|선택한 오류 표시 안 함 중지|선택한 억제 된 오류 또는 오류를 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **오류 무시 중지**를 클릭 합니다.<br /><br /> 다음에 유효성 검사를 실행하면 표시하지 않도록 선택한 오류는 나타나지 않습니다.|
|**오류 목록** 창에서 표시 되지 않는 모든 오류 복원|**오류 목록** 창의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **표시 되지 않는 모든 오류 표시**를 클릭 합니다.|
|**오류 목록** 창에서 표시 되지 않는 모든 오류 숨기기|**오류 목록** 창의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 표시 되지 않는 **모든 오류 숨기기**를 클릭 합니다.|

## <a name="validate-code-automatically"></a>자동으로 코드 유효성 검사

로컬 빌드를 실행할 때마다 레이어 유효성 검사를 수행할 수 있습니다. 팀에서 Azure DevOps를 사용 하는 경우 사용자 지정 MSBuild 작업을 만들어 지정할 수 있는 제어 된 체크 인을 사용 하 여 레이어 유효성 검사를 수행 하 고, 빌드 보고서를 사용 하 여 유효성 검사 오류를 수집할 수 있습니다. 제어 된 체크 인 빌드를 만들려면 [TFVC 제어 체크](/azure/devops/pipelines/build/triggers)인을 참조 하세요.

### <a name="to-validate-code-automatically-during-a-local-build"></a>로컬 빌드 중 자동으로 코드의 유효성을 검사하려면

텍스트 편집기를 사용하여 모델링 프로젝트 파일(.modelproj)을 열고 다음 속성을 포함합니다.

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- 또는 -

1. **솔루션 탐색기**에서 종속성 다이어그램 또는 다이어그램이 포함 된 모델링 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. **속성** 창에서 모델링 프로젝트의 **아키텍처 유효성 검사** 속성을 **True**로 설정 합니다.

    이렇게 하면 모델링 프로젝트가 유효성 검사 프로세스에 포함됩니다.

3. **솔루션 탐색기**에서 유효성 검사에 사용할 종속성 다이어그램 (microsoft.visualstudio.teamarchitect.layerdesigner.diagrams.layerdiagram.show) 파일을 클릭 합니다.

4. **속성** 창에서 다이어그램의 **빌드 작업** 속성이 **Validate**로 설정 되어 있는지 확인 합니다.

    여기에는 유효성 검사 프로세스의 종속성 다이어그램이 포함 됩니다.

오류 목록 창에서 오류를 관리 하려면 [레이어 유효성 검사 오류 해결](#resolve-layer-validation-errors)을 참조 하세요.

## <a name="troubleshoot-layer-validation-issues"></a>레이어 유효성 검사 문제 해결

다음 표에서는 레이어 유효성 검사 문제와 해결 방법에 대해 설명합니다. 이 문제는 코드와 디자인 간의 충돌로 인해 발생하는 오류와 다릅니다. 이러한 오류에 대 한 자세한 내용은 [레이어 유효성 검사 문제 해결](#troubleshoot-layer-validation-issues)을 참조 하세요.

|**문제점**|**가능한 원인**|**해결 방법**|
|-|-|-|
|유효성 검사 오류가 예상대로 발생하지 않습니다.|솔루션 탐색기의 다른 종속성 다이어그램에서 복사 되 고 동일한 모델링 프로젝트에 있는 종속성 다이어그램에서는 유효성 검사가 작동 하지 않습니다. 이러한 방식으로 복사 되는 종속성 다이어그램은 원래 종속성 다이어그램과 동일한 참조를 포함 합니다.|모델링 프로젝트에 새 종속성 다이어그램을 추가 합니다.<br /><br /> 소스 종속성 다이어그램에서 새 다이어그램으로 요소를 복사 합니다.|

## <a name="resolve-layer-validation-errors"></a>레이어 유효성 검사 오류 해결

종속성 다이어그램에 대해 코드의 유효성을 검사 하는 경우 코드가 디자인과 충돌 하는 경우 유효성 검사 오류가 발생 합니다. 예를 들어, 다음과 같은 조건에서 유효성 검사 오류가 발생할 수 있습니다.

- 잘못된 레이어에 아티팩트가 할당되었습니다. 이 경우 아티팩트를 이동합니다.

- 클래스 등의 아티팩트가 아키텍처에 맞지 않는 방식으로 다른 클래스를 사용합니다. 이 경우 코드를 리팩터링하여 종속성을 제거합니다.

이러한 오류를 해결하려면 유효성 검사 중 더 이상 오류가 나타나지 않을 때까지 코드를 업데이트합니다. 이 작업은 반복적으로 수행할 수 있습니다.

다음 섹션에서는 이러한 오류에 사용되는 구문과 이러한 오류의 의미를 설명하고 오류의 해결 및 관리 방법을 제안합니다.

|**구문**|**설명**|
|-|-|
|*Artifactn*(*artifacttypen*)|*Artifactn* 은 종속성 다이어그램의 레이어와 연결 된 아티팩트입니다.<br /><br /> *Artifacttypen* 은 **클래스** 또는 **메서드와**같은 *artifactn*의 형식입니다. 예를 들면 다음과 같습니다.<br /><br /> MySolution.MyProject.MyClass.MyMethod(메서드)|
|*NamespaceNameN*|네임스페이스의 이름입니다.|
|*LayerNameN*|종속성 다이어그램의 계층 이름입니다.|
|*DependencyType*|*Artifact1* 와 *Artifact2*간의 종속성 관계 유형입니다. 예를 들어 *Artifact1* 에는 *Artifact2*와의 **호출** 관계가 있습니다.|

| **오류 구문** | **오류 설명** |
|-|-|
| DV0001: **잘못 된 종속성** | 이 문제는 계층에 매핑된 코드 요소 (네임 스페이스, 형식, 멤버)가 다른 레이어에 매핑된 코드 요소를 참조 하지만이 계층을 포함 하는 종속성 유효성 검사 다이어그램에서 이러한 계층 사이에 종속성 화살표가 없는 경우에 보고 됩니다. 이것은 종속성 제약 조건 위반입니다. |
| DV1001: **네임 스페이스 이름이 잘못 되었습니다** . | 이 문제는 "허용 되는 네임 스페이스 이름" 속성에이 코드 요소가 정의 된 네임 스페이스가 포함 되지 않은 계층에 연결 된 코드 요소에서 보고 됩니다. 이것은 명명 제약 조건 위반입니다. "허용 되는 네임 스페이스 이름" 구문은 계층에 연결 된 코드 요소를 정의할 수 있는 네임 스페이스를 세미콜론으로 구분한 목록입니다. |
| DV1002: **참조할 수 없는 네임 스페이스에 대 한 종속성** | 이 문제는 계층에 연결 된 코드 요소에 대해 보고 되 고 계층의 "참조할 수 없는 Namespace" 속성에 정의 된 네임 스페이스에 정의 된 다른 코드 요소를 참조 합니다. 이것은 명명 제약 조건 위반입니다. "참조할 수 없는 네임 스페이스" 속성은이 계층과 연결 된 코드 요소에서 참조 해서는 안 되는 세미콜론으로 구분 된 네임 스페이스 목록으로 정의 됩니다. |
| DV1003: **허용 되지 않는 네임 스페이스 이름** | 이 문제는 계층에 연결 된 코드 요소에서 보고 됩니다. "허용 되지 않는 네임 스페이스 이름" 속성에는이 코드 요소가 정의 된 네임 스페이스가 포함 됩니다. 이것은 명명 제약 조건 위반입니다. "허용 되지 않는 네임 스페이스 이름" 속성은이 레이어와 연결 된 코드 요소를 정의 하면 안 되는 세미콜론으로 구분 된 네임 스페이스 목록으로 정의 됩니다. |
| DV2001: **레이어 다이어그램 상태** | 이 문제는 종속성 다이어그램 파일을 포함 하지 않지만 종속성 유효성 검사 분석기를 참조 하는 프로젝트에서 보고 됩니다. 종속성 유효성 검사를 사용 하지 않은 경우 솔루션 탐색기에서 직접 "DependencyValidation"를 제거 하거나이 경고를 표시 하지 않을 수 있습니다. 종속성 다이어그램을 추가 하려면 [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)를 참조 하세요. |
| DV2002: **매핑되지 않은 형식 기준** | 이 문제는 코드 요소가 계층에 매핑되지 않은 경우에 보고 됩니다. |
| DV3001: **누락 된 링크** | '*LayerName*' 계층은 찾을 수 없는 '*아티팩트*'에 연결 됩니다. 어셈블리 참조가 있는지 확인하세요. |
| DV9001: **아키텍처 분석에서 내부 오류가 발생 했습니다** . | 결과가 불완전할 수 있습니다. 자세한 내용은 상세 빌드 이벤트 로그를 참조하세요. |

## <a name="see-also"></a>참조

- [Visual Studio의 실시간 종속성 유효성 검사](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [개발하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)
- [비디오: 실시간으로 아키텍처 종속성 유효성 검사](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
