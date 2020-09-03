---
title: 'IDebugDisassemblyStream2:: GetSize | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6db80ef9c447f9e08a1332348d2212699d01d8e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203035"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 디스어셈블리 스트림의 명령에 있는 크기를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pnSize`  
 제한이 는의 지침에 따라 크기를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에서 반환 된 값을 사용 하 여 [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 배열을 할당 한 다음이를 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드로 전달할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
