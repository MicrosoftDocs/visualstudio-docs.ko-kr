---
title: 'IDiaEnumSectionContribs:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18bee6cf8f47aeeadd41c7accc1f33566f564898
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189976"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

열거형 시퀀스에서 지정 된 수의 섹션 기여를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 celt  
 진행 검색할 열거자의 섹션 기여 수입니다.  
  
 rgelt  
 제한이 원하는 섹션 기여를 나타내는 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 개체로 채워질 배열입니다.  
  
 pceltFetched  
 제한이 인출 된 열거자의 섹션 기여 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`더 이상 섹션 기여를 하지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
