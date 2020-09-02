---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538085"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

현재 속성 집합에서 지정 된 속성을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cpspec`  
 진행 배열에 지정 된 속성의 수 `rgpspec` 입니다. 0 인 경우 메서드는 속성을 반환 하지 않고 `S_OK` 성공 코드로 반환 됩니다.  
  
 `rgpspec`  
 진행 읽을 속성의 배열입니다. 속성은 속성 ID 또는 선택적 문자열 이름으로 지정할 수 있습니다. 배열의 특정 순서로 속성을 지정할 필요는 없습니다. 배열에 중복 된 속성이 포함 될 수 있으며,이로 인해 단순 속성에 대해 반환 되는 속성 값이 중복 됩니다. 단순 하지 않은 속성은 두 번째로 열 때 액세스 거부를 반환 해야 합니다. 배열에는 속성 Id와 문자열 Id를 혼합 하 여 포함할 수 있습니다. 이 배열에는 적어도 `cpspec` 속성 값 수가 있어야 합니다.  
  
 `rgvar`  
 [in, out] `PROPVARIANT` 각 속성에 대 한 값으로 채워질 구조체의 배열 (VisualStudio 네임 스페이스)입니다. 배열의 크기는 이상 이어야 합니다 `cpspec` . 호출자는 배열의 값을 초기화할 필요가 없습니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`하나 이상의 속성을 찾을 수 없는 경우을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 속성을 찾을 수 없는 경우 배열의 해당 항목에는 `rgvar` 형식이 인이 포함 `VARIANT` `VT_EMPTY` 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
