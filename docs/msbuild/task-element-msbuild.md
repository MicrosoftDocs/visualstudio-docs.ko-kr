---
title: Target의 Task 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a4ec2203430045c083b46b2eea8d3e884a4b794
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263177"
---
# <a name="task-element-of-target-msbuild"></a>Target의 Task 요소(MSBuild)

MSBuild 작업의 인스턴스를 만들고 실행합니다. 생성된 작업 이름에 따라 요소 이름이 결정됩니다.

 \<프로젝트> \<대상>

## <a name="syntax"></a>구문

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Condition`|선택적 특성입니다. 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|
|`ContinueOnError`|선택적 특성입니다. 다음 값 중 하나를 포함할 수 있습니다.<br /><br /> -   **WarnAndContinue** 또는 **true**. 작업이 실패할 경우 [Target](../msbuild/target-element-msbuild.md) 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 경고로 처리됩니다.<br />-   **ErrorAndContinue**. 작업이 실패할 경우 `Target` 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 오류로 처리됩니다.<br />-   **ErrorAndStop** 또는 **false**(기본값). 작업이 실패할 경우 `Target` 요소의 나머지 작업이 실행되지 않고 전체 `Target` 요소와 빌드가 실패한 것으로 간주됩니다.<br /><br /> .NET Framework 4.5 이전 버전은 `true` 및 `false` 값만 지원합니다.<br /><br /> 자세한 내용은 [방법: 작업의 오류 무시](../msbuild/how-to-ignore-errors-in-tasks.md)를 참조하세요.|
|`Parameter`|작업 클래스에 `[Required]` 특성으로 레이블이 지정된 하나 이상의 속성이 포함된 경우 필수입니다.<br /><br /> 값으로 매개 변수 값을 포함하는 사용자 정의 작업 매개 변수입니다. `Task` 요소에는 여러 매개 변수가 있을 수 있으며 각 특성은 작업 클래스의 .NET 속성에 매핑됩니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[출력](../msbuild/output-element-msbuild.md)|프로젝트 파일의 작업에서 출력을 저장합니다. 작업에는 `Output` 요소가 없을 수도 있고 하나 이상 있을 수도 있습니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [Target](../msbuild/target-element-msbuild.md) | MSBuild 작업의 컨테이너 요소입니다. |

## <a name="remarks"></a>설명

 MSBuild 프로젝트 파일의 `Task` 요소는 작업의 인스턴스를 생성하며 작업에 대한 속성을 설정하고 작업을 실행합니다. `Output` 요소는 프로젝트 파일의 다른 곳에서 사용될 속성이나 항목에 출력 매개 변수를 저장합니다.

 작업의 상위 `Target` 요소에 [OnError](../msbuild/onerror-element-msbuild.md) 요소가 있는 경우 작업이 실패하고 `ContinueOnError`에 `false` 값이 있으면 계속 평가됩니다. 작업에 대한 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

## <a name="example"></a>예제

 다음 코드 예제에서는 [Csc task](../msbuild/csc-task.md) 클래스의 인스턴스를 만들고 6개의 속성을 설정하며 작업을 실행합니다. 실행한 후에는 개체의 `OutputAssembly` 속성 값이 `FinalAssemblyName`이라는 항목 목록에 배치됩니다.

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
