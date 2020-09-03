---
title: 'IDebugDisassemblyStream2:: GetCodeContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a98840982d44c2ee2348ca5c321d08cc6c46ffc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196248"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 코드 위치 식별자에 해당 하는 코드 컨텍스트 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `uCodeLocationId`  
 진행 코드 위치 식별자를 지정 합니다. 코드 위치 식별자에 대 한 설명은 [Getcodelocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 메서드에 대 한 설명 섹션을 참조 하세요.  
  
 `ppCodeContext`  
 제한이 연결 된 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 코드 위치 식별자는 [Getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) 메서드 호출에서 반환 될 수 있으며, [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조에 표시 될 수 있습니다.  
  
 코드 컨텍스트를 코드 위치 식별자로 변환 하려면 [Getcodelocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
