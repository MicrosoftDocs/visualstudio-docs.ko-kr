---
title: CallTarget 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 831153a734fa88c045f7b8397db0a033e53862c7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634489"
---
# <a name="calltarget-task"></a>CallTarget 작업

프로젝트 파일 내의 지정된 대상을 호출합니다.

## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 `CallTarget` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|---------------------------| - |
| `RunEachTargetSeparately` | 선택적 `Boolean` 입력 매개 변수입니다.<br /><br /> `true`인 경우 MSBuild 엔진이 대상마다 한 번씩 호출됩니다. `false`인 경우 MSBuild 엔진이 한 번씩 호출되어 모든 대상을 빌드합니다. 기본값은 `false`입니다. |
| `TargetOutputs` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 빌드된 모든 대상의 출력을 포함합니다. |
| `Targets` | 선택적 `String[]` 매개 변수입니다.<br /><br /> 빌드할 대상을 지정합니다. |
| `UseResultsCache` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 캐시된 결과(있는 경우)가 반환됩니다.<br /><br /> **참고** MSBuild 작업이 실행되면 해당 출력은 (ProjectFileName, GlobalProperties)[TargetNames] 범위에 빌드 항목의 목록으로 캐시됩니다. |

## <a name="remarks"></a>설명

 `Targets`에 지정된 대상이 실패하고 `RunEachTargetSeparately`가 `true`인 경우 작업이 나머지 대상을 계속 빌드합니다.

 기본 대상을 빌드하려는 경우 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용하고 `$(MSBuildProjectFile)`와 동일한 `Projects` 매개 변수를 설정합니다.

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 `CallOtherTargets` 내에서 `TargetA`를 호출합니다.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [대상](../msbuild/msbuild-targets.md)
