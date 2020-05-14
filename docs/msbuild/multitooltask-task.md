---
title: MultiToolTask 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d9e8b23492f23d39977b4eb26f8ee633b8463f27
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565216"
---
# <a name="multitooltask-task"></a>MultiToolTask 작업

설명이 없습니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **MultiToolTask** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|선택적 **string[]** 매개 변수입니다.|
|**SemaphoreProcCount**|선택적 **string** 매개 변수입니다.|
|**SchedulerFunction**|선택적 **string** 매개 변수입니다.|
|**SchedulerVerbose**|선택적 **bool** 매개 변수입니다.|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|
|**TaskAssemblyName**|선택적 **string** 매개 변수입니다.|
|**TaskName**|필수 **문자열** 매개 변수입니다.|
|**TrackerLogDirectory**|필수 **문자열** 매개 변수입니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)
