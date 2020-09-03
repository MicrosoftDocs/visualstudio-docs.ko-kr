---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66f499225d2b319f3678c88894a1217d90b10135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162514"
---
# <a name="idebugmodopt"></a>IDebugModOpt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Debug 선택적 한정자를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 클래스 또는 메서드를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에서 가져옵니다.  
  
## <a name="methods"></a>메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|선택적 한정자 목록을 검색 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
