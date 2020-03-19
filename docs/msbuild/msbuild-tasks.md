---
title: MSBuild 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633137"
---
# <a name="msbuild-tasks"></a>MSBuild 작업

빌드 플랫폼에는 빌드 프로세스 중에 동작을 필요한 수만큼 실행할 수 있는 기능이 필요합니다. MSBuild에서는 *작업*을 통해 이러한 동작을 수행합니다. 작업은 MSBuild에서 원자성 빌드 작업을 수행하는 데 사용하는 실행 코드 단위입니다.

## <a name="task-logic"></a>작업 논리

 MSBuild XML 프로젝트 파일 형식은 빌드 작업을 자체적으로 완전히 실행할 수 없으므로 프로젝트 파일 외부에서 작업 논리를 구현해야 합니다.

 작업의 실행 논리는 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 .NET 클래스로 구현됩니다. 이 인터페이스는 <xref:Microsoft.Build.Framework> 네임스페이스에서 정의됩니다.

 또한 작업 클래스는 프로젝트 파일에서 작업에 사용 가능한 입력 및 출력 매개 변수를 정의합니다. 이름이 같은 해당 특성을 [작업](../msbuild/task-element-msbuild.md) 요소에 배치하고 해당 값을 이 문서 뒷부분의 예제에 나온 대로 설정하면 작업 클래스가 표시하는 설정 가능한 모든 공용 비정적/비추상 속성에 값을 부여할 수 있습니다.

 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 관리되는 클래스를 만들어 자체의 작업을 작성할 수 있습니다. 자세한 내용은 [작업 작성](../msbuild/task-writing.md)을 참조하세요.

## <a name="execute-a-task-from-a-project-file"></a>프로젝트 파일에서 작업 실행

 프로젝트 파일에서 작업을 실행하기 전에 먼저 [UsingTask](../msbuild/usingtask-element-msbuild.md) 요소를 사용하여 작업을 구현하는 어셈블리의 형식을 작업 이름에 매핑해야 합니다. 그러면 MSBuild가 프로젝트 파일에서 작업을 찾을 때 작업의 실행 논리를 찾을 위치를 알 수 있습니다.

 MSBuild 프로젝트 파일에서 작업을 실행하려면 작업 이름을 포함하는 요소를 `Target` 요소의 자식으로 만듭니다. 작업이 매개 변수를 수락하면 해당 매개 변수가 요소의 특성으로 전달됩니다.

 MSBuild 항목 목록 및 속성을 매개 변수로 사용할 수 있습니다. 예를 들어 다음 코드는 `MakeDir` 작업을 호출하고 `MakeDir` 개체의 `Directories` 속성 값을 `BuildDir` 속성 값과 동일하게 설정합니다.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 작업은 프로젝트 파일에 정보를 반환할 수도 있으며, 나중에 사용하기 위해 항목이나 속성에 이 정보를 저장할 수 있습니다. 예를 들어 다음 코드는 `Copy` 작업을 호출하고 `CopiedFiles` 출력 속성의 정보를 `SuccessfullyCopiedFiles` 항목 목록에 저장합니다.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>포함된 작업

 MSBuild에는 파일을 복사하는 [Copy](../msbuild/copy-task.md), 디렉터리를 만드는 [MakeDir](../msbuild/makedir-task.md), C# 소스 코드 파일을 컴파일하는 [Csc](../msbuild/csc-task.md) 등의 여러 작업이 포함되어 있습니다. 사용 가능한 작업 및 사용법 정보의 전체 목록은 [작업 참조](../msbuild/msbuild-task-reference.md)를 참조하세요.

## <a name="overridden-tasks"></a>재정의된 작업

 MSBuild는 여러 위치에서 작업을 찾습니다. 첫 번째 위치는 .NET Framework 디렉터리에 저장된 확장명이 *.OverrideTasks*인 파일입니다. 이러한 파일의 작업은 프로젝트 파일의 작업을 비롯하여 이름이 동일한 다른 작업을 재정의합니다. 두 번째 위치는 .NET Framework 디렉터리의 확장명이 *.Tasks*인 파일입니다. 이러한 위치 중 하나에 작업이 없으면 프로젝트 파일의 작업을 사용합니다.

## <a name="see-also"></a>참조

- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [작업 작성](../msbuild/task-writing.md)
- [인라인 작업](../msbuild/msbuild-inline-tasks.md)
