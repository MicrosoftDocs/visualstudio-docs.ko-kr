---
title: 'IDebugExpressionEvaluator:: SetLocale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 730a105b12016ea031bdb4753da009223a5d39f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540526"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 인쇄 가능한 결과를 만드는 데 사용할 언어를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `wLangID`  
 진행 언어 식별자입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 식 계산기 (EE)가 로드 되는 동안 여러 번 호출 될 수 있으므로 EE에서 언어를 즉시 전환할 수 있어야 합니다. EE는이 로캘을 사용 하 여 오류 메시지 및 문자열을 적절 한 언어로 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
