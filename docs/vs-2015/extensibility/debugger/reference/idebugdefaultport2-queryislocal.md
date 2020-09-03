---
title: 'IDebugDefaultPort2:: QueryIsLocal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77c521a364b33c1bd6fdde544d27237ead12ca46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196251"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는이 포트가 로컬 컴퓨터에 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Return Value  
 `S_OK`이 포트가 호출자와 같은 컴퓨터에 있는 로컬 이거나 `S_FALSE` 포트가 다른 컴퓨터에 있는 경우를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
