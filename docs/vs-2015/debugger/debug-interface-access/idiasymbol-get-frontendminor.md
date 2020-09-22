---
title: 'IDiaSymbol:: get_frontEndMinor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12e5956f880a79d7946ff9655ec1ef3d1a79ff22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841883"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프런트 엔드 부 버전 번호를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 Front. end 부 버전 번호를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
> [!NOTE]
> 반환 값은 `S_FALSE` 기호에 대해 속성을 사용할 수 없음을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 컴파일러는 일반적으로 프런트 엔드 (파서) 라는 두 개의 기본 요소로 구성 되며,이는 소스 코드를 중간 형식으로 구문 분석 하는 작업을 처리 하 고, 백 엔드 (코드 생성기)는 중간 형식을 어셈블리로 변환 합니다. 프런트 엔드에서 백 엔드에서 다른 버전을 갖는 것이 일반적이 지 않습니다.  
  
 프런트 엔드 또는 백 엔드 버전 번호는 세 부분으로 구성 됩니다. \<major> \<minor> \<build> 여기서 \<major> 은 주 버전 번호이 고,은 \<minor> 부 버전 번호 이며, \<build> 는 빌드 번호입니다. 예를 들어 13.10.3077.  
  
## <a name="requirements"></a>요구 사항  
  
|요구 사항|Description|  
|-----------------|-----------------|  
|헤더:|dia2.h|  
|버전:|DIA SDK v7.0|  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
