---
title: 'IDebugProcess2:: CauseBreak | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eaaeb111e5309cb37b934c45000c267a62f88514
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188072"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로세스에서 코드를 실행 하는 다음 프로그램이 중단 하 고 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트 개체를 전송 하도록 요청 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CauseBreak(   
   void  
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
