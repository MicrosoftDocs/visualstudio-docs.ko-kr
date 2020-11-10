---
title: UpdateManifest 작업 | Microsoft Docs
description: MSBuild가 UpdateManifest 작업을 사용하여 매니페스트에서 선택한 속성을 업데이트하고 다시 서명하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4fab3844b21e12edceb83da310e9069199578ef6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046854"
---
# <a name="updatemanifest-task"></a>UpdateManifest 작업

매니페스트에서 선택한 속성을 업데이트하고 다시 서명합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `UpdateManifest` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
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