---
title: GetOutputFileName 작업 | Microsoft Docs
description: MSBuild GetOutputFileName 도우미 작업을 사용하여 cl.exe 및 기타 도구의 출력 파일 이름 옵션을 지정합니다.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436786"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName 작업

출력 디렉터리 또는 전체 파일 이름만 지정하거나 아무것도 지정하지 않는 cl 및 기타 도구에 대한 출력 파일 이름을 가져오는 도우미 작업입니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **GetOutputFileName** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**OutputExtension**|필수 **문자열** 매개 변수입니다.|
|**OutputFile**|선택적 **string** 출력 매개 변수입니다.|
|**OutputPath**|선택적 **string** 매개 변수입니다.|
|**SourceFile**|필수 **문자열** 매개 변수입니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)
