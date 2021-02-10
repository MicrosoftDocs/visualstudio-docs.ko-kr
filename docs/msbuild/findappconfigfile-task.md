---
title: FindAppConfigFile 작업 | Microsoft Docs
description: MSBuild FindAppConfigFile 작업을 사용하여 제공된 목록에서 app.config 파일(있는 경우)을 찾는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff26ee3505671d29df610278d701803b816d30f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877137"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile 작업

제공된 목록에서 *app.config* 파일(있는 경우)을 찾습니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `FindAppConfigFile` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`AppConfigFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 있는 경우 목록에서 처음 일치 항목을 지정합니다.|
|`PrimaryList`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 검색할 기본 목록을 지정합니다.|
|`SecondaryList`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 검색할 보조 목록을 지정합니다.|
|`TargetPath`|필수 `String` 매개 변수입니다.<br /><br /> 메타데이터로 추가할 값을 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
