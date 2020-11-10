---
title: Move 작업 | Microsoft Docs
description: 새 위치로 파일을 이동하는 MSBuild Move 작업의 매개 변수 및 설정을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8714108f7c537d9a50fda453050a54802f14e335
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903553"
---
# <a name="move-task"></a>Move 작업

새 위치로 파일을 이동합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `Move` 작업의 매개 변수를 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`DestinationFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 소스 파일을 이동할 파일의 목록을 지정합니다. 이 목록은 `SourceFiles` 매개 변수에 지정된 목록에 대한 일대일 매핑이어야 합니다. 즉, `SourceFiles`에 지정된 첫 번째 파일이 `DestinationFiles` 등에 지정된 첫 번째 위치에 이동됩니다.|
|`DestinationFolder`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 파일을 이동하려는 디렉터리를 지정합니다.|
|`MovedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 성공적으로 이동된 항목을 계산합니다.|
|`OverwriteReadOnlyFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 파일이 읽기 전용으로 표시되더라도 파일을 덮어씁니다.|
|`SourceFiles`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 이동할 파일을 지정합니다.|

## <a name="remarks"></a>설명

 `DestinationFolder` 매개 변수 또는 `DestinationFiles` 매개 변수 중 하나(둘 다가 아닌)를 지정해야 합니다. 둘 다를 지정하는 경우 작업이 실패하고 오류가 기록됩니다.

 `Move` 작업은 원하는 대상 파일의 필요에 따라 폴더를 만듭니다.

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
