---
title: 'IDebugCanStopEvent2:: GetCodeContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c27418848812b2fbd3c16d4a1546c301fd7db4cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191179"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 이벤트의 위치를 설명 하는 코드 컨텍스트를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppCodeContext`  
 제한이 현재 코드 위치를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 대부분의 런타임 아키텍처에서 코드 컨텍스트는 프로그램의 실행 스트림에서 특정 명령을 가리키는 주소로 간주할 수 있습니다.  
  
 소스 코드 줄을 향하는 문서 컨텍스트를 가져오려면 [Getdocumentcontext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
