---
title: 작업 압축 풀기 | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631512"
---
# <a name="unzip-task"></a>Unzip 작업

지정된 위치로 *.zip* 보관 압축을 풉니다.

>[!NOTE]
>`Unzip` 작업은 MSBuild 15.8 이상에서만 사용할 수 있습니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `Unzip` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`DestinationFolder`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수<br /><br /> 파일을 압축 해제할 대상 폴더를 지정합니다.|
|`OverwriteReadOnlyFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 읽기 전용 파일을 덮어씁니다. 기본값은 `false`입니다.|
|`SkipUnchangedFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 변경되지 않은 파일의 압축 해제를 건너뜁니다. 기본값은 `true`입니다. 파일 크기가 같고 마지막으로 수정된 시간이 같으면 `Unzip` 작업에서 파일이 변경되지 않은 것으로 간주합니다.|
|`SourceFiles`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 압축을 풀 파일을 하나 이상 지정합니다. 여러 파일을 지정하는 경우 동일한 폴더에 순서대로 압축이 풀립니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 보관 압축을 풀고 모든 읽기 전용 파일을 덮어씁니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
