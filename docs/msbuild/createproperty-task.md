---
title: CreateProperty 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155e8e6b57cc388e8c2981297be8b26ef5444c1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634320"
---
# <a name="createproperty-task"></a>CreateProperty 작업

전달된 값으로 속성을 채웁니다. 이를 통해 하나의 속성 또는 문자열에서 다른 속성 또는 문자열로 값을 복사할 수 있습니다.

## <a name="attributes"></a>특성

다음 표에서는 `CreateProperty` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|------------------| - |
| `Value` | 선택적 `String` 출력 매개 변수입니다.<br /><br /> 새 속성에 복사할 값을 지정합니다. |
| `ValueSetByTask` | 선택적 `String` 출력 매개 변수입니다.<br /><br /> `Value` 매개 변수와 동일한 값을 포함합니다. 출력이 최신 상태이므로 바깥쪽 대상을 건너뛸 때 MSBuild가 출력 속성을 설정하지 않도록 하려는 경우에만 이 매개 변수를 사용합니다. |

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제는 `CreateProperty` 작업을 사용하여 `SourceFilename` 및 `SourceFileExtension` 속성 값의 조합을 사용하는 `NewFile` 속성을 만듭니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

프로젝트를 실행한 후 `NewFile` 속성의 값은 *Module1.vb*입니다.

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)
