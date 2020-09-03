---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161021"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조를 열거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 현재 호출 스택을 설명 하는 구조체 목록을 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 Visual Studio는 디버깅 중인 프로그램에서 중단점, 예외 또는 중단을 발생 시킬 때마다 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 를 호출 하 여이 인터페이스를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugFrameInfo2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[다음](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|열거형 시퀀스에서 지정 된 수의 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조를 검색 합니다.|  
|[skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|열거형 시퀀스에서 지정 된 수의 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조를 건너뜁니다.|  
|[재설정](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[복제](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|열거자의 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조 수를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 Visual Studio는 디버깅 중인 프로그램에서 중단점, 예외 또는 사용자 생성 일시 중지를 처리 하기 위한 첫 번째 단계로이 인터페이스를 가져옵니다. [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조 목록은 현재 호출 스택을 나타내며 목록의 시작 부분에 현재 함수를 호출 하 고 목록의 끝에서 가장 오래 된 함수 호출을 사용 합니다. 각는 `FRAMEINFO` 스택 프레임, 식이 계산 될 수 있는 컨텍스트 및 지역 변수가 표시 되는 컨텍스트를 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
