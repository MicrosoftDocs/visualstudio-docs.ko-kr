---
title: FormatUrl 작업 | Microsoft Docs
description: MSBuild FormatUrl 작업을 사용하여 입력 URL을 올바른 출력 URL 형식으로 변환하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888097"
---
# <a name="formaturl-task"></a>FormatUrl 작업

URL을 올바른 URL 형식으로 변환합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `FormatUrl` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`InputUrl`|선택적 `String` 매개 변수입니다.<br /><br /> 서식을 지정하려면 URL을 지정합니다.|
|`OutputUrl`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 서식이 지정된 URL을 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)