---
title: 빌드 프로세스 확장
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca0c55951d4928347528814d043bb8a7c55be9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633852"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>방법: Visual Studio 빌드 프로세스 확장

Visual Studio 빌드 프로세스는 프로젝트 파일로 가져온 일련의 MSBuild *.targets* 파일로 정의됩니다. 이러한 가져온 파일 중 하나인 *Microsoft.Common.targets*는 빌드 프로세스의 여러 지점에서 사용자 지정 작업을 실행할 수 있도록 확장될 수 있습니다. 이 문서에서는 Visual Studio 빌드 프로세스를 확장하는 데 사용할 수 있는 두 가지 방법을 설명합니다.

- 공통 대상(*Microsoft.Common.targets* 또는 가져오는 파일)에 정의된 미리 정의된 특정 대상을 재정의합니다.

- 공통 대상에 정의된 “DependsOn” 속성을 재정의합니다.
## <a name="override-predefined-targets"></a>미리 정의된 대상 재정의

## <a name="override-predefined-targets"></a>미리 정의된 대상 재정의

공통 대상은 빌드 프로세스의 일부 주요 대상의 전후에 호출되는 미리 정의된 빈 대상 집합을 포함합니다. 예를 들어 MSBuild는 메인 `CoreBuild` 대상 전에 `BeforeBuild` 대상을 호출하고 `CoreBuild` 대상 후에 `AfterBuild` 대상을 호출합니다. 기본적으로 공통 대상의 빈 대상은 아무것도 수행하지 않지만 공통 대상을 가져오는 프로젝트 파일에서 원하는 대상을 정의하여 해당 기본 동작을 재정의할 수 있습니다. 미리 정의된 대상을 재정의하면 MSBuild 작업을 사용하여 빌드 프로세스를 더 세부적으로 제어할 수 있습니다.
공통 대상은 빌드 프로세스의 일부 주요 대상의 전후에 호출되는 미리 정의된 빈 대상 집합을 포함합니다. 예를 들어 MSBuild는 메인 `CoreBuild` 대상 전에 `BeforeBuild` 대상을 호출하고 `CoreBuild` 대상 후에 `AfterBuild` 대상을 호출합니다. 기본적으로 공통 대상의 빈 대상은 아무것도 수행하지 않지만 공통 대상을 가져오는 프로젝트 파일에서 원하는 대상을 정의하여 해당 기본 동작을 재정의할 수 있습니다. 미리 정의된 대상을 재정의하면 MSBuild 작업을 사용하여 빌드 프로세스를 더 세부적으로 제어할 수 있습니다.

> [!NOTE]
> SDK 스타일 프로젝트에는 *프로젝트 파일의 마지막 줄 뒤*에 대상의 암시적 가져오기가 있습니다. 즉, [방법: MSBuild 프로젝트 SDK 사용](how-to-use-project-sdk.md)의 설명대로 가져오기를 수동으로 지정하지 않는 한 기본 대상을 재정의할 수 없습니다.

#### <a name="to-override-a-predefined-target"></a>미리 정의된 대상을 재정의하려면

1. 재정의하려는 공통 대상에서 미리 정의된 대상을 식별합니다. 안전하게 재정의할 수 있는 대상의 전체 목록은 아래 표를 참조하세요.

2. `</Project>` 태그 바로 앞에, 프로젝트 파일의 끝에 하나 이상의 대상을 정의합니다. 예를 들어:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. 프로젝트 파일을 빌드합니다.

다음 표는 안전하게 재정의할 수 있는 공통 대상에서 모든 대상을 표시합니다.

|대상 이름|설명|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|이러한 대상 중 하나에 삽입된 작업은 핵심 컴파일이 완료되기 전이나 후에 실행됩니다. 대부분의 사용자 지정은 이러한 두 개의 대상 중 하나에서 수행됩니다.|
|`BeforeBuild`, `AfterBuild`|이러한 대상 중 하나에 삽입된 작업은 빌드의 모든 작업 전이나 후에 실행됩니다. **참고:**  `BeforeBuild` 및 `AfterBuild` 대상은 프로젝트 파일 대부분의 끝에 삽입된 주석에서 이미 정의되어 있습니다. 따라서 프로젝트 파일에 빌드 전후 이벤트를 쉽게 추가할 수 있습니다.|
|`BeforeRebuild`, `AfterRebuild`|이러한 대상 중 하나에 삽입된 작업은 핵심 다시 빌드 기능이 호출되기 전 또는 후에 실행됩니다. *Microsoft.Common.targets*에서 대상 실행 순서는 차례로 `BeforeRebuild`, `Clean`, `Build` 및 `AfterRebuild`입니다.|
|`BeforeClean`, `AfterClean`|이러한 대상 중 하나에 삽입된 작업은 핵심 정리 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforePublish`, `AfterPublish`|이러한 대상 중 하나에 삽입된 작업은 핵심 게시 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforeResolveReferences`, `AfterResolveReferences`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 참조가 확인되기 전이나 후에 실행됩니다.|
|`BeforeResGen`, `AfterResGen`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 리소스가 생성되기 전이나 후에 실행됩니다.|

## <a name="override-dependson-properties"></a>DependsOn 속성 재정의

미리 정의된 대상 재정의는 빌드 프로세스를 확장하는 쉬운 방법이지만 MSBuild에서 대상의 정의를 순차적으로 평가하므로 프로젝트를 가져오는 다른 프로젝트에서 이미 재정의한 대상을 재정의하는 것을 방지할 방법이 없습니다. 따라서 예를 들어 다른 모든 프로젝트를 가져온 후 프로젝트에서 정의된 마지막 `AfterBuild` 대상은 빌드 중 사용되는 대상이 됩니다.

공통 대상 전체의 `DependsOnTargets` 특성에서 사용되는 DependsOn 속성을 재정의하여 의도하지 않은 대상의 재정의를 방지할 수 있습니다. 예를 들어 `Build` 대상은 `"$(BuildDependsOn)"`의 `DependsOnTargets` 특성 값을 포함합니다. 고려 사항:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

이 XML 조각은 `Build` 대상 전에 실행할 수 있음을 나타내며 `BuildDependsOn` 속성에 지정된 모든 대상은 먼저 실행되어야 합니다. `BuildDependsOn` 속성은 다음으로 정의됩니다.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

프로젝트 파일의 끝에서 `BuildDependsOn`이라는 다른 속성을 선언하여 이 속성 값을 재정의할 수 있습니다. 새 속성에서 이전 `BuildDependsOn` 속성을 포함하여 대상 목록의 시작과 끝에 새 대상을 추가할 수 있습니다. 예를 들어:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

프로젝트 파일을 가져오는 프로젝트는 만든 사용자 지정 항목을 덮어쓰지 않고 이러한 속성을 재정의할 수 있습니다.

#### <a name="to-override-a-dependson-property"></a>DependsOn 속성을 재정의하려면

1. 재정의하려는 공통 대상에서 미리 정의된 DependsOn 속성을 식별합니다. 일반적으로 재정의된 DependsOn 속성의 목록은 아래 표를 참조하세요.

2. 프로젝트 파일의 끝에서 속성의 다른 인스턴스를 정의합니다. 새 속성에 원래 속성을 포함합니다(예: `$(BuildDependsOn)`).

3. 속성 정의 앞 또는 뒤에 사용자 지정 대상을 정의합니다.

4. 프로젝트 파일을 빌드합니다.

### <a name="commonly-overridden-dependson-properties"></a>일반적으로 재정의된 DependsOn 속성

|속성 이름|설명|
|-------------------|-----------------|
|`BuildDependsOn`|전체 빌드 프로세스 앞이나 뒤에 사용자 지정 대상을 삽입하려는 경우 재정의할 속성입니다.|
|`CleanDependsOn`|사용자 지정 빌드 프로세스에서 출력을 정리하려는 경우 재정의할 속성입니다.|
|`CompileDependsOn`|컴파일 단계 앞이나 뒤에 사용자 지정 프로세스를 삽입하려는 경우 재정의할 속성입니다.|

## <a name="see-also"></a>참조

- [Visual Studio 통합](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [.targets 파일](../msbuild/msbuild-dot-targets-files.md)
