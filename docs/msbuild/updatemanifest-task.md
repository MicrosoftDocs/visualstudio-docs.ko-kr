---
title: UpdateManifest 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631344"
---
# <a name="updatemanifest-task"></a>UpdateManifest 작업

매니페스트에서 선택한 속성을 업데이트하고 다시 서명합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `UpdateManifest` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`ApplicationManifest`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 애플리케이션 매니페스트를 지정합니다.|
|`ApplicationPath`|필수 `String` 매개 변수입니다.<br /><br /> 애플리케이션 매니페스트의 경로를 지정합니다.|
|`InputManifest`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 업데이트할 매니페스트를 지정합니다.|
|`OutputManifest`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 업데이트된 속성이 포함된 매니페스트를 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [Task 기본 클래스](../msbuild/task-base-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)