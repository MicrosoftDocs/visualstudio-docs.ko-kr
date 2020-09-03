---
title: 'IDebugEngine2:: SetLocale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b071bcc68b383854e1e5a12f3ae2cc08ea86f19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195919"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)의 로캘을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `wLangID`  
 진행 언어 로캘을 지정 합니다. 예를 들어 영어의 경우 1033입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 해제에서 반환 된 문자열이 제대로 지역화 되도록 IDE의 로캘 설정을 전파 하기 위해 세션 디버그 관리자 (SDM)에 의해 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
