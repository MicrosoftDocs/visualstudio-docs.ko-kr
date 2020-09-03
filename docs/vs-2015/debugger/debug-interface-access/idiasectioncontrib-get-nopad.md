---
title: 'IDiaSectionContrib:: get_nopad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3044deb31214aae9c37ef7bb1f84324857ffb7d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151900"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

섹션을 다음 메모리 경계로 패딩 하지 않아야 하는지 여부를 나타내는 플래그를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 `TRUE` 섹션을 다음 메모리 경계로 패딩 하지 않아야 하면이 고, 그렇지 않으면를 반환 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 이 속성은 일반적으로 이전 파일 에서만 표시 되는 속성입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
