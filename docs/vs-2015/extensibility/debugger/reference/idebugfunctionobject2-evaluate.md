---
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c25e62dbfc0778fb1bf07c9108c9111f3520d87f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180963"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

함수를 호출 하 고 결과 값을 개체로 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppParams`  
 진행 입력 매개 변수를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다. 이러한 각 매개 변수는이 인터페이스의 Create 메서드 중 하나를 사용 하 여 생성 됩니다.  
  
 `dwParams`  
 진행 배열에 있는 매개 변수의 수 `ppParams` 입니다.  
  
 `dwEvalFlags`  
 진행 계산을 수행 하는 방법을 지정 하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.  
  
 `dwTimeout`  
 진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. 무기한 **대기 하려면 무기한** 을 사용 합니다.  
  
 `ppResult`  
 제한이 함수 값을 개체로 나타내는 **Idebugobject** 를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
