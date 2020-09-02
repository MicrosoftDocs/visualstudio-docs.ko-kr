---
title: 'IDebugProgramPublisher2:: Un 프로그래밍 노드 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fed7f35b87ec3e4a761b7adc33876affe778d9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423136"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 프로그램 노드를 가용성에서 디버그 엔진 (DEs) 및 세션 디버그 관리자 (SDM)에서 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pProgramNode`  
 진행 제거할 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 제거 되 면 프로그램 정보에 대 한 프로그램 노드를 더 이상 쿼리할 수 없습니다.  
  
 프로그램 노드를 사용 가능 하 게 설정 하려면 [이 메서드를 호출 합니다.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
