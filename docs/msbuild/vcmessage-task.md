---
title: VCMessage 작업 | Microsoft Docs
description: MSBuild가 VCMessage 작업을 사용하여 C++ 프로젝트 빌드 중에 경고 및 오류 메시지를 기록하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046753"
---
# <a name="vcmessage-task"></a>VCMessage 작업

빌드 중에 경고 및 오류 메시지를 로깅합니다.

## <a name="remarks"></a>설명

 이 작업은 C++ 프로젝트용 MSBuild 구현에 도움이 되며, 사용자가 호출할 수 없습니다. 자세한 내용은 <xref:Microsoft.Build.Utilities.TaskLoggingHelper>를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 **VCMessage** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**인수**|선택적 **문자열** 매개 변수입니다.<br /><br /> 표시할 메시지의 세미콜론으로 구분된 목록입니다.|
|**코드**|필수 **String** 매개 변수입니다.<br /><br /> 메시지를 정규화하는 오류 번호입니다.|
|**형식**|선택적 **문자열** 매개 변수입니다.<br /><br /> 내보낼 메시지의 종류를 지정합니다. 경고 메시지를 내보내려면 “Warning”을 지정하고 오류 메시지를 내보내려면 “Error”를 지정합니다.|

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
