---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154199"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호에 포함 된 위치 정보의 종류를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>요소  
 `LocIsNull`  
 위치 정보를 사용할 수 없습니다.  
  
 `LocIsStatic`  
 위치는 정적입니다.  
  
 `LocIsTLS`  
 위치가 스레드 로컬 저장소에 있습니다.  
  
 `LocIsRegRel`  
 위치가 등록 상대 위치입니다.  
  
 `LocIsThisRel`  
 Location은 `this` 상대 경로입니다.  
  
 `LocIsEnregistered`  
 위치가 레지스터에 있습니다.  
  
 `LocIsBitField`  
 위치가 비트 필드에 있습니다.  
  
 `LocIsSlot`  
 Location은 MSIL (Microsoft 중간 언어) 슬롯입니다.  
  
 `LocIsIlRel`  
 위치는 MSIL에 상대적입니다.  
  
 `LocInMetaData`  
 위치가 메타 데이터에 있습니다.  
  
 `LocIsConstant`  
 위치는 상수 값입니다.  
  
 `LocTypeMax`  
 이 열거형의 위치 형식 수입니다.  
  
## <a name="remarks"></a>설명  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 인터페이스에 사용할 수 있는 속성은 이미지 파일 내의 기호 위치에 따라 달라 집니다. 자세한 내용은 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)를 참조 하세요.  
  
 이 열거형의 값은 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) 메서드를 호출 하 여 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)
