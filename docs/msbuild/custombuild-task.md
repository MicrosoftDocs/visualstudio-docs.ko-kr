---
title: CustomBuild 작업 | Microsoft Docs
description: 이 문서에서는 MSBuild에서 C++ 빌드 프로세스 사용자 지정을 지원하는 데 사용되는 MSBuild CustomBuild 작업을 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796552"
---
# <a name="custombuild-task"></a>CustomBuild 작업

Microsoft C++ 컴파일러 도구 cmd.exe를 래핑합니다. 이 클래스는 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)에서 파생되나 파일 종속성 검색을 위해 파일 추적을 사용하지는 않습니다. 증분 빌드가 제대로 작동하려면 모든 종속성은AdditionalDependencies로 명시적으로 지정되어야 합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **CustomBuild** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**BuildSuffix**|선택적 **string** 매개 변수입니다.|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|
|**TrackerLogDirectory**|선택적 **string** 매개 변수입니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)
