---
title: 'IDebugDocumentPosition2:: IsPositionInDocument | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7950f091d34d03222044455be671e15f5297a747
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200286"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

문서 위치가 지정 된 문서에 포함 되어 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pDoc`  
 진행 포함 하는 문서 후보를 나타내는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 주로 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스에서 중단점을 설정 하는 데 사용 됩니다. 문서가 로드 되 면 문서에이 위치가 포함 되어 있는지 여부를 확인 하기 위해 중단점 위치가 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
