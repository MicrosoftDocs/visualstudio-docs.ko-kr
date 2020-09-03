---
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcec6af2b8e7b1acfdc9c3cf38cb18654be78c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145006"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 문서 컨텍스트의 소스 코드 범위를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pBegPosition`  
 [in, out] 시작 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.  
  
 `pEndPosition`  
 [in, out] 끝 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 소스 범위는 현재 문에서 코드를 제공한 이전 문 바로 다음에 오는 전체 소스 코드 범위입니다. 소스 범위는 일반적으로 주석을 포함 하 여 소스 문과 디스어셈블리 창의 코드를 혼합 하는 데 사용 됩니다.  
  
 이 문서 컨텍스트 내에 포함 된 코드 문의 범위를 가져오려면 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
