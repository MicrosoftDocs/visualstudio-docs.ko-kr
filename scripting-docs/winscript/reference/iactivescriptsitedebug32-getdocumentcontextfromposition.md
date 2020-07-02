---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835279"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
언어 엔진에서를 위임 하는 데 사용 `IDebugCodeContext::GetSourceContext` 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwSourceContext`  
 진행 또는에 제공 된 소스 콘텐츠 `ParseScriptText` `AddScriptlet` 입니다.  
  
 `uCharacterOffset`  
 진행 스크립트 블록 또는 scriptlet의 시작을 기준으로 하는 문자 오프셋입니다.  
  
 `uNumChars`  
 진행 이 컨텍스트의 문자 수입니다.  
  
 `ppsc`  
 제한이 이 문자 위치 범위에 해당 하는 문서 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는를 반환 `HRESULT` 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했습니다.|  
  
## <a name="remarks"></a>설명  
 언어 엔진은이 메서드를 사용 하 여을 위임 `IDebugCodeContext::GetSourceContext` 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteDebug32 인터페이스](../../winscript/reference/iactivescriptsitedebug32-interface.md)