---
title: 값을 변경할 수 없음 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfe275411346e499312ba51c50a3a2ac3f4ed7d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161643"
---
# <a name="cannot-change-value-dialog-box"></a>값을 변경할 수 없음 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124; `The name` ‘이름’ `does not exist in the current context` &#124; ‘다양한 기타 메시지’   
  
 이 메시지 상자는 디버거 창(자동, 조사식 또는 지역 창)이나 간략한 조사식 대화 상자에서 변수의 내용을 잘못된 값으로 변경하려고 할 때 나타납니다. 예를 들어 정수 변수의 값을 문자열로 설정하려고 하면 이 메시지 상자가 나타납니다.  
  
## <a name="solution"></a>솔루션  
 디버거 창이나 간략한 조사식 대화 상자에 입력한 값이 설정하려는 변수에 적합한 값인지 확인하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [디버거의 식](../debugger/expressions-in-the-debugger.md)
