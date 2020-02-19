---
title: ParallelCustomBuild 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279258"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild 작업

[CustomBuild 작업](../msbuild/custombuild-task.md)의 병렬 인스턴스를 실행합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **ParallelCustomBuild** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|**BreakOnFirstFailure**|선택적 **bool** 매개 변수입니다.|
|**MaxItemsInBatch**|선택적 **int** 매개 변수입니다.|
|**MaxProcesses**|선택적 **int** 매개 변수입니다.|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|

## <a name="see-also"></a>참조

[작업 참조](../msbuild/msbuild-task-reference.md)