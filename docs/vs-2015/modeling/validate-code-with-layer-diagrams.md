---
title: 레이어 다이어그램을 사용 하 여 코드 유효성 검사 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45b82ece15cfef4d313764027c0220453a6d4849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845435"
---
# <a name="validate-code-with-layer-diagrams"></a>레이어 다이어그램에 대해 코드 유효성 검사
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드가 디자인과 충돌하지 않는지 확인하기 위해 Visual Studio에서 레이어 다이어그램을 사용하여 코드의 유효성을 검사할 수 있습니다. 이 경우 다음에 도움이 됩니다.

- 코드의 종속성과 레이어 다이어그램의 종속성 사이의 충돌을 찾을 수 있습니다.

- 제안된 변경 내용의 영향을 받을 수 있는 종속성을 찾습니다.

   예를 들어 레이어 다이어그램을 편집하여 잠재적인 아키텍처 변경을 나타낸 다음, 코드의 유효성을 검사하여 영향을 받는 종속성을 확인할 수 있습니다.

- 코드를 다른 디자인으로 리팩터링 또는 마이그레이션합니다.

   코드를 다른 아키텍처로 이동할 때 아직 작업이 필요한 코드 또는 종속성을 찾을 수 있습니다.

  **요구 사항**

- Visual Studio

- Team Foundation Build를 사용하여 자동으로 코드의 유효성을 검사하는 Team Foundation Build 서버의 Visual Studio

- 레이어 다이어그램을 사용하는 모델링 프로젝트가 포함된 솔루션 이 레이어 다이어그램은 유효성 검사를 하려는 Visual C# .NET 또는 Visual Basic .NET 프로젝트의 아티팩트에 연결해야 합니다. [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)를 참조 하세요.

  이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

  Visual Studio의 열린 레이어 다이어그램 또는 명령 프롬프트에서 코드 유효성 검사를 수동으로 수행할 수 있습니다. 또한 로컬 빌드 또는 Team Foundation Build를 실행할 때 자동으로 코드 유효성 검사를 실행할 수도 있습니다. [Channel 9 비디오: 레이어 다이어그램을 사용 하 여 아키텍처 디자인 및 유효성 검사](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)를 참조 하세요.

> [!IMPORTANT]
> Team Foundation Build를 사용하여 레이어 유효성 검사를 실행하려면 빌드 서버에 동일한 버전의 Visual Studio를 설치해야 합니다.

- [항목에서 유효성 검사를 지원하는지 확인](#SupportsValidation)

- [유효성 검사에 다른.NET 어셈블리 및 프로젝트 포함](#IncludeReferences)

- [수동으로 코드 유효성 검사](#ValidateManually)

- [자동으로 코드 유효성 검사](#ValidateAuto)

- [레이어 유효성 검사 문제 해결](#TroubleshootingValidation)

- [레이어 유효성 검사 오류 이해 및 해결](#UnderstandingValidationErrors)

## <a name="see-if-an-item-supports-validation"></a><a name="SupportsValidation"></a> 항목에서 유효성 검사를 지원 하는지 확인
 레이어를 웹 사이트, Office 문서, 일반 텍스트 파일 및 여러 앱에서 공유되는 프로젝트의 파일에 연결할 수는 있지만, 유효성 검사 프로세스에는 레이어가 포함되지 않습니다. 별도의 레이어에 연결된 프로젝트 또는 어셈블리의 경우에는 해당 레이어 간에 종속성이 나타나지 않아도 유효성 검사 오류가 나타나지 않습니다. 이러한 참조는 코드에서 사용하지 않는 한 종속성으로 처리되지 않습니다.

1. 레이어 다이어그램에서 하나 이상의 레이어를 선택 하 고 선택 항목을 마우스 오른쪽 단추로 클릭 한 다음 **링크 보기**를 클릭 합니다.

2. **레이어 탐색기**에서 **유효성 검사 지원** 열을 확인 합니다. 값이 false일 경우 해당 항목은 유효성 검사를 지원하지 않습니다.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a><a name="IncludeReferences"></a> 유효성 검사를 위한 다른 .NET 어셈블리 및 프로젝트 포함
 항목을 레이어 다이어그램으로 끌면 해당 하는 .NET 어셈블리 또는 프로젝트에 대 한 참조가 모델링 프로젝트의 **Layer references** 폴더에 자동으로 추가 됩니다. 이 폴더에는 유효성 검사 중 분석되는 프로젝트와 어셈블리에 대한 참조가 포함되어 있습니다. 유효성을 검사할 다른 .NET 어셈블리와 프로젝트는 수동으로 레이어 다이어그램으로 끌어 놓지 않고도 포함할 수 있습니다.

1. **솔루션 탐색기**에서 모델링 프로젝트 또는 **레이어 참조** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **참조 추가**를 클릭 합니다.

2. **참조 추가** 대화 상자에서 어셈블리 또는 프로젝트를 선택한 다음 **확인**을 클릭 합니다.

## <a name="validate-code-manually"></a><a name="ValidateManually"></a> 수동으로 코드 유효성 검사
 솔루션 항목에 연결 된 열린 레이어 다이어그램이 있는 경우 다이어그램에서 바로 가기 **유효성 검사** 명령을 실행할 수 있습니다. 또한 명령 프롬프트를 사용 하 여 **/p: ValidateArchitecture** 사용자 지정 속성을 **True**로 설정 하 여 **msbuild** 명령을 실행할 수 있습니다. 예를 들어, 코드를 변경할 때 종속성 충돌을 빠르게 찾을 수 있도록 레이어 유효성 검사를 정기적으로 수행합니다.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>열려 있는 레이어 다이어그램에서 코드 유효성을 검사하려면

1. 다이어그램 화면을 마우스 오른쪽 단추로 클릭 한 다음 **아키텍처 유효성 검사**를 클릭 합니다.

    > [!NOTE]
    > 기본적으로 레이어 다이어그램 (. microsoft.visualstudio.teamarchitect.layerdesigner.diagrams.layerdiagram.show) 파일의 **빌드 작업** 속성은 **유효성 검사로 설정 되어 있으므로 다이어그램이** 유효성 검사 프로세스에 포함 됩니다.

     **오류 목록** 창에서 발생 하는 모든 오류를 보고 합니다. 유효성 검사 오류에 대 한 자세한 내용은 [레이어 유효성 검사 오류 이해 및 해결](#UnderstandingValidationErrors)을 참조 하세요.

2. 각 오류의 소스를 보려면 **오류 목록** 창에서 오류를 두 번 클릭 합니다.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류의 원본 대신 코드 맵을 표시할 수 있습니다. 레이어 다이어그램에 지정되지 않은 어셈블리에 대한 종속성이 코드에 있거나 레이어 다이어그램에 지정된 종속성이 코드에 없는 경우 종속성 그래프가 표시됩니다. 이 경우 코드 맵이나 코드를 검토하여 종속성이 있어야 하는지 여부를 확인합니다. 코드 맵에 대 한 자세한 내용은 [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)을 참조 하세요.

3. 오류를 관리 하려면 [유효성 검사 오류 관리](#ManageErrors)를 참조 하세요.

#### <a name="to-validate-code-at-the-command-prompt"></a>명령 프롬프트에서 코드 유효성을 검사하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트를 엽니다.

2. 다음 중 하나를 선택합니다.

   - 솔루션의 특정 모델링 프로젝트를 기준으로 코드 유효성을 검사하려면 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - 또는

       모델링 프로젝트 파일(.modelproj)과 레이어 다이어그램이 포함된 폴더로 이동한 후 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - 솔루션의 모든 모델링 프로젝트를 기준으로 코드 유효성을 검사하려면 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다.

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - 또는

       솔루션 폴더로 이동한 후 다음 사용자 지정 속성을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행합니다. 이 솔루션 폴더에는 레이어 다이어그램이 포함된 모델링 프로젝트가 들어 있어야 합니다.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     발생하는 모든 오류가 나열됩니다. 에 대 한 자세한 내용은 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] [Msbuild](../msbuild/msbuild.md) 및 [msbuild 작업](../msbuild/msbuild-task.md)을 참조 하세요.

   유효성 검사 오류에 대 한 자세한 내용은 [레이어 유효성 검사 오류 이해 및 해결](#UnderstandingValidationErrors)을 참조 하세요.

### <a name="manage-validation-errors"></a><a name="ManageErrors"></a> 유효성 검사 오류 관리
 개발 과정에서 유효성 검사 중 보고된 충돌 문제 중 일부를 표시하지 않을 수 있습니다. 예를 들어 이미 해결되었거나 특정 시나리오와 관계가 없는 오류를 표시하지 않을 수 있습니다. 오류를 표시하지 않는 경우에는 [!INCLUDE[esprfound](../includes/esprfound-md.md)]에 작업 항목을 기록하는 것이 좋습니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>유효성 검사 오류에 대한 작업 항목을 만들려면

- **오류 목록** 창에서 오류를 마우스 오른쪽 단추로 클릭 하 고 **작업 항목 만들기**를 가리킨 다음 만들려는 작업 항목의 형식을 클릭 합니다.

  이러한 작업을 사용 하 여 **오류 목록** 창에서 유효성 검사 오류를 관리할 수 있습니다.

|**수행할 작업**|**다음 단계 수행**|
|------------|----------------------------|
|선택한 오류를 유효성 검사 중에 표시 안 함|하나 또는 여러 개의 선택한 오류를 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **오류 표시 안 함**을 클릭 합니다.<br /><br /> 표시되지 않는 오류는 취소선 서식을 사용하여 나타납니다. 다음에 유효성 검사를 실행하면 이러한 오류가 나타나지 않습니다.<br /><br /> 표시되지 않는 오류는 해당하는 레이어 다이어그램 파일의 .suppressions 파일에서 추적됩니다.|
|선택한 오류 표시 안 함 중지|선택한 억제 된 오류 또는 오류를 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **오류 무시 중지**를 클릭 합니다.<br /><br /> 다음에 유효성 검사를 실행하면 표시하지 않도록 선택한 오류는 나타나지 않습니다.|
|**오류 목록** 창에서 표시 되지 않는 모든 오류 복원|**오류 목록** 창의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 **표시 되지 않는 모든 오류 표시**를 클릭 합니다.|
|**오류 목록** 창에서 표시 되지 않는 모든 오류 숨기기|**오류 목록** 창의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **유효성 검사 오류 관리**를 가리킨 다음 표시 되지 않는 **모든 오류 숨기기**를 클릭 합니다.|

## <a name="validate-code-automatically"></a><a name="ValidateAuto"></a> 자동으로 코드 유효성 검사
 로컬 빌드를 실행할 때마다 레이어 유효성 검사를 수행할 수 있습니다. 팀에서 Team Foundation Build를 사용하는 경우, 사용자 지정 MSBuild 작업을 생성하여 지정할 수 있는 제어된 체크 인을 사용하여 유효성 검사를 수행하고 빌드 보고서를 사용하여 유효성 검사 오류를 수집할 수 있습니다. 제어 된 체크 인 빌드를 만들려면 [제어 된 체크 인 빌드 프로세스를 사용 하 여 변경 내용 유효성 검사](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)를 참조 하세요.

#### <a name="to-validate-code-automatically-during-a-local-build"></a>로컬 빌드 중 자동으로 코드의 유효성을 검사하려면

- 텍스트 편집기를 사용하여 모델링 프로젝트 파일(.modelproj)을 열고 다음 속성을 포함합니다.

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- 또는 -

1. **솔루션 탐색기**에서 레이어 다이어그램이 포함 된 모델링 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. **속성** 창에서 모델링 프로젝트의 **아키텍처 유효성 검사** 속성을 **True**로 설정 합니다.

    이렇게 하면 모델링 프로젝트가 유효성 검사 프로세스에 포함됩니다.

3. **솔루션 탐색기**에서 유효성 검사에 사용할 레이어 다이어그램 (microsoft.visualstudio.teamarchitect.layerdesigner.diagrams.layerdiagram.show) 파일을 클릭 합니다.

4. **속성** 창에서 다이어그램의 **빌드 작업** 속성이 **Validate**로 설정 되어 있는지 확인 합니다.

    이렇게 하면 레이어 다이어그램이 유효성 검사 프로세스에 포함됩니다.

   오류 목록 창에서 오류를 관리 하려면 [유효성 검사 오류 관리](#ManageErrors)를 참조 하세요.

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Team Foundation Build 중 자동으로 코드의 유효성을 검사하려면

1. **팀 탐색기**에서 빌드 정의를 두 번 클릭 한 다음 **처리**를 클릭 합니다.

2. **빌드 프로세스 매개 변수**에서 **컴파일**을 확장 하 고 **MSBuild 인수** 매개 변수에 다음을 입력 합니다.

    `/p:ValidateArchitecture=true`

   유효성 검사 오류에 대 한 자세한 내용은 [레이어 유효성 검사 오류 이해 및 해결](#UnderstandingValidationErrors)을 참조 하세요. [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]에 대한 자세한 내용은 다음을 참조하세요.

- [애플리케이션 빌드](/azure/devops/pipelines/index)

- [빌드 프로세스에 기본 템플릿 사용](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [UpgradeTemplate .xaml을 기반으로 하는 레거시 빌드를 수정 합니다.](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [빌드 프로세스 템플릿 사용자 지정](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [실행 중인 빌드의 진행률 모니터링](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="troubleshoot-layer-validation-issues"></a><a name="TroubleshootingValidation"></a> 레이어 유효성 검사 문제 해결
 다음 표에서는 레이어 유효성 검사 문제와 해결 방법에 대해 설명합니다. 이 문제는 코드와 디자인 간의 충돌로 인해 발생하는 오류와 다릅니다. 이러한 오류에 대 한 자세한 내용은 [레이어 유효성 검사 오류 이해 및 해결](#UnderstandingValidationErrors)을 참조 하세요.

|**문제점**|**가능한 원인**|**해결 방법**|
|---------------|------------------------|--------------------|
|유효성 검사 오류가 예상대로 발생하지 않습니다.|같은 모델링 프로젝트에 있는 레이어 다이어그램과 솔루션 탐색기의 다른 다이어그램에서 복사한 레이어 다이어그램에 대해서는 유효성 검사가 수행되지 않습니다. 이렇게 복사한 레이어 다어어그램은 원본 레이어 다이어그램과 동일한 참조를 포함합니다.|모델링 프로젝트에 새 레이어 다이어그램을 추가합니다.<br /><br /> 소스 레이어 다이어그램에서 새 다이어그램으로 요소를 복사합니다.|

## <a name="understanding-and-resolving-layer-validation-errors"></a><a name="UnderstandingValidationErrors"></a> 레이어 유효성 검사 오류 이해 및 해결
 레이어 다이어그램에서 코드의 유효성을 검사할 때 코드가 디자인과 충돌하면 유효성 검사 오류가 발생합니다. 예를 들어, 다음과 같은 조건에서 유효성 검사 오류가 발생할 수 있습니다.

- 잘못된 레이어에 아티팩트가 할당되었습니다. 이 경우 아티팩트를 이동합니다.

- 클래스 등의 아티팩트가 아키텍처에 맞지 않는 방식으로 다른 클래스를 사용합니다. 이 경우 코드를 리팩터링하여 종속성을 제거합니다.

  이러한 오류를 해결하려면 유효성 검사 중 더 이상 오류가 나타나지 않을 때까지 코드를 업데이트합니다. 이 작업은 반복적으로 수행할 수 있습니다.

  다음 섹션에서는 이러한 오류에 사용되는 구문과 이러한 오류의 의미를 설명하고 오류의 해결 및 관리 방법을 제안합니다.

|**구문**|**설명**|
|----------------|---------------------|
|*Artifactn*(*artifacttypen*)|*Artifactn* 은 레이어 다이어그램의 레이어와 연결 된 아티팩트입니다.<br /><br /> *Artifacttypen* 은 **클래스** 또는 **메서드와**같은 *artifactn*의 형식입니다. 예를 들면 다음과 같습니다.<br /><br /> MySolution.MyProject.MyClass.MyMethod(메서드)|
|*NamespaceNameN*|네임스페이스의 이름입니다.|
|*LayerNameN*|레이어 다이어그램에 있는 레이어의 이름입니다.|
|*DependencyType*|*Artifact1* 와 *Artifact2*간의 종속성 관계 유형입니다. 예를 들어 *Artifact1* 에는 *Artifact2*와의 **호출** 관계가 있습니다.|

|**오류 구문**|**오류 설명**|
|----------------------|---------------------------|
|AV0001: 잘못 된 종속성: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> 레이어: *LayerName1*, *LayerName2* &#124; 종속성: *DependencyType*|*LayerName1* 에는 *LayerName2에 대*한 직접적인 종속성이 없으므로 *LayerName1* 의 *Artifact1* 는 *LayerName2* 의 *Artifact2* 에 대 한 종속성이 없어야 합니다.|
|AV1001: 잘못 된 네임 스페이스: *아티팩트*<br /><br /> 계층: *LayerName* &#124; 필수 네임 스페이스: *NamespaceName1* &#124; 현재 네임 스페이스: *NamespaceName2*|*LayerName* 를 사용 하려면 연결 된 아티팩트가 *NamespaceName1*에 속해야 합니다. *아티팩트가* *NamespaceName1*가 아닌 *NamespaceName2*에 있습니다.|
|AV1002: 사용할 수 없는 네임 스페이스에 종속: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> 계층: *LayerName* &#124; 사용할 수 없는 네임 스페이스: *NamespaceName* &#124; 종속성: *DependencyType*|*LayerName* 를 사용 하려면 연결 된 아티팩트가 *NamespaceName*에 종속 되지 않아야 합니다. *Artifact2* 가 *NamespaceName*에 있으므로 *Artifact1* 은 *Artifact2* 에 종속 될 수 없습니다.|
|AV1003: 사용할 수 없는 네임 스페이스: *아티팩트*(*artifacttype*)<br /><br /> 계층: *LayerName* &#124; 사용할 수 없는 네임 스페이스: *NamespaceName*|*LayerName* 를 사용 하려면 연결 된 아티팩트가 *NamespaceName*에 속할 수 없습니다. *아티팩트가* *NamespaceName*에 속합니다.|
|AV3001: 누락 된 링크: '*LayerName*' 계층이 찾을 수 없는 '*아티팩트*'에 연결 되어 있습니다. 어셈블리 참조가 있는지 확인하세요.|*LayerName* 찾을 수 없는 아티팩트에 대 한 링크입니다. 예를 들어 모델링 프로젝트에 클래스가 포함된 어셈블리에 대한 참조가 없어서 해당 클래스에 대한 링크가 없을 수 있습니다.|
|AV9001: 아키텍처 유효성 검사에서 내부 오류가 발생했습니다. 결과가 불완전할 수 있습니다. 자세한 내용은 상세 빌드 이벤트 로그를 참조하세요.|자세한 내용은 빌드 이벤트 로그 또는 출력 창을 참조하세요.|

## <a name="security"></a>보안

## <a name="see-also"></a>관련 항목
 [개발하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)
