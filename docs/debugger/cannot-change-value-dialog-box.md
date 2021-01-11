---
title: 값을 변경할 수 없음 대화 상자 | Microsoft Docs
description: 디버거 창이나 간략한 조사식에서 변수를 잘못된 값으로 변경하려고 하면 Visual Studio에 표시되는 값을 변경할 수 없음 대화 상자를 검토합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf4181d7ff56bd1a5cf3f195bcea5b02aa023629
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729056"
---
# <a name="cannot-change-value-dialog-box"></a>값을 변경할 수 없음 대화 상자
## <a name="error"></a>Error
 `The value of this variable cannot be changed` &#124; `The name` ‘이름’ `does not exist in the current context` &#124; ‘다양한 기타 메시지’ 

 이 메시지 상자는 디버거 창(자동, 조사식 또는 지역 창)이나 간략한 조사식 대화 상자에서 변수의 내용을 잘못된 값으로 변경하려고 할 때 나타납니다. 예를 들어 정수 변수의 값을 문자열로 설정하려고 하면 이 메시지 상자가 나타납니다.

## <a name="solution"></a>솔루션
 디버거 창이나 간략한 조사식 대화 상자에 입력한 값이 설정하려는 변수에 적합한 값인지 확인하십시오.

## <a name="see-also"></a>참조

- [디버거의 식](../debugger/expressions-in-the-debugger.md)