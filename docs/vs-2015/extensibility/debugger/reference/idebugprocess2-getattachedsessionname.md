---
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3acc40e2b906bd46b832d9fa11578de346014042
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841467"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로세스를 디버깅 하는 세션의 이름을 가져옵니다. IDE는 특정 컴퓨터에서 특정 프로세스를 디버깅 하는 사용자에 게이 정보를 표시할 수 있습니다.  
  
> [!NOTE]
> 이 메서드는 더 이상 사용 되지 않으며 구현에서 항상를 반환 해야 `E_NOTIMPL` 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrSessionName`  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 항상를 반환 해야 합니다 `E_NOTIMPL` .  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
