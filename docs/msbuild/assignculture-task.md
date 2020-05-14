---
title: AssignCulture 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9f7bb47efefa3f7a1d4cf52cbfa5891602956f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634567"
---
# <a name="assignculture-task"></a>AssignCulture 작업

이 작업은 유효한 .NET 문화권 식별자 문자열이 포함되어 있는 항목의 목록을 파일 이름의 일부로 허용하고 해당 문화권 식별자가 포함된 `Culture`라는 메타데이터가 있는 항목을 생성합니다. 예를 들어 *Form1.fr-fr.resx*라는 파일 이름에 포함된 문화권 식별자 “fr-fr”이 있으므로 이 작업은 `Culture`와 같은 `fr-fr` 메타데이터를 포함하는 동일한 파일 이름을 가진 항목을 생성합니다. 태스크는 파일 이름에서 제거된 문화권을 포함하는 파일 이름의 목록도 생성합니다.

## <a name="task-parameters"></a>작업 매개 변수

다음 표에서는 `AssignCulture` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`AssignedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 각 항목에 추가된 `Files` 메타데이터 항목을 포함하여 `Culture` 매개 변수에 수신된 항목 목록이 포함됩니다.<br /><br /> `Files` 매개 변수에서 들어오는 항목에 `Culture` 메타데이터 항목이 포함되는 경우 원래 메타데이터 항목을 사용합니다.<br /><br /> 파일 이름에 유효한 문화권 식별자가 포함되는 경우에만 작업이 `Culture` 메타데이터 항목을 할당합니다. 문화권 식별자는 파일 이름에서 마지막 두 점 사이에 있어야 합니다.|
|`AssignedFilesWithCulture`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> `AssignedFiles` 메타 데이터 항목이 있는 `Culture` 매개 변수에서 항목의 하위 집합이 포함됩니다.|
|`AssignedFilesWithNoCulture`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> `AssignedFiles` 메타 데이터 항목이 없는 `Culture` 매개 변수에서 항목의 하위 집합이 포함됩니다.|
|`CultureNeutralAssignedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 파일 이름에서 제거된 문화권을 제외하고 `AssignedFiles` 매개 변수에서 생성되는 동일한 항목 목록이 포함됩니다.<br /><br /> 작업이 유효한 문화권 식별자인 경우에만 파일 이름에서 문화권을 제거합니다.|
|`Files`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 문화권을 할당할 문화권 이름이 포함된 파일 목록을 지정합니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 `AssignCulture` 항목 컬렉션을 포함하는 `ResourceFiles` 작업을 실행합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

다음 표에서는 작업 실행 이후의 출력 항목 값을 설명합니다. 항목 뒤에 괄호로 묶은 내용이 항목 메타데이터입니다.

|항목 컬렉션입니다.|콘텐츠|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx*(Culture="fr")<br /><br /> *MyResource2.XX.resx*(추가 메타데이터 없음)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx*(Culture="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx*(추가 메타데이터 없음)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx*(Culture="fr")<br /><br /> *MyResource2.XX.resx*(추가 메타데이터 없음)|

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
