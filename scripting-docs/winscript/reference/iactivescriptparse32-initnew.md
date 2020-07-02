---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835708"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
스크립팅 엔진을 초기화 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Return Value  
 `S_OK`성공 하면를 반환 하 고, `E_FAIL` 초기화 하는 동안 오류가 발생 한 경우를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진을 사용 하려면 먼저 `IPersist*::Load` , 또는 메서드 중 하나를 호출 해야 합니다. `IPersist*::InitNew` `IActiveScriptParse32::InitNew` 이 메서드는의 의미 체계는 `IPersistStreamInit::InitNew` 와 동일 합니다 .이 메서드는 스크립팅 엔진 자체를 초기화 하도록 지시 합니다. 또는와를 모두 호출할 수는 없으며, `IPersist*::InitNew` 또는를 두 `IActiveScriptParse32::InitNew` 번 이상 `IPersist*::Load` 호출 하는 것은 유효 `IPersist*::InitNew` `IActiveScriptParse32::InitNew` 하지 않습니다 `IPersist*::Load` .  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)