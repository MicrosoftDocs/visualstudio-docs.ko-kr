---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537422"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 속성 식별자에 해당 하는 문자열 이름을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cpropid`  
 진행 의 속성 id 수 `rgpropid` 입니다.  
  
 `rgpropid`  
 진행 이름을 가져올 속성 id의 배열입니다 `PROPID` .는 WTypes. h에서로 정의 됩니다 `ULONG` .  
  
 `rglpwstrName`  
 [in, out] 지정 된 속성 id의 속성 이름 배열입니다. 배열은 요청 된 수의 속성 이름을 보유 하기 위해 미리 할당 되어야 하며 적어도 문자열을 보유할 수 있어야 합니다 `cpropid``BSTR` .  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 반환 된 속성 이름은 `SysFreeString` 더 이상 필요 하지 않은 경우 함수를 호출 하 여 해제 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
