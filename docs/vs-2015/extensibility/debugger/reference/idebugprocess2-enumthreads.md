---
title: 'IDebugProcess2:: EnumThreads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188026"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스에서 실행 되는 모든 스레드 목록을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppEnum`  
 제한이 프로세스에 있는 모든 프로그램의 모든 스레드 목록을 포함 하는 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 각 프로그램에서 실행 중인 스레드를 열거 한 다음 스레드의 프로세스 뷰로 결합 합니다. 단일 스레드를 여러 프로그램에서 실행할 수 있습니다. 이 메서드는 스레드를 한 번만 열거 합니다.  
  
 이 메서드는 중복 없이 프로세스의 스레드 목록을 표시 합니다. 그렇지 않고 특정 프로그램에서 실행 중인 스레드를 열거 하려면 [enumthreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 메서드를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
