---
title: Delete 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634281"
---
# <a name="delete-task"></a>Delete 작업

지정한 파일을 삭제합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `Delete` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`DeletedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 삭제된 파일을 지정합니다.|
|`Files`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 삭제할 파일을 지정합니다.|
|`TreatErrorsAsWarnings`|선택적 `Boolean` 매개 변수<br /><br /> `true`이면 오류가 경고로 기록됩니다. 기본값은 `false`입니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

> [!WARNING]
> `Delete` 작업과 함께 와일드카드를 사용할 때는 주의해야 합니다. 특히 속성이 빈 문자열로 평가되는 경우 `$(SomeProperty)\**\*.*` 또는 `$(SomeProperty)/**/*.*`와 같은 식이 포함된 잘못된 파일을 쉽게 삭제할 수 있습니다. 이 경우 `Files` 매개 변수는 드라이브의 루트로 평가되며 삭제하려 했던 것보다 훨씬 많이 삭제할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 파일 *MyApp.pdb*를 삭제합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
