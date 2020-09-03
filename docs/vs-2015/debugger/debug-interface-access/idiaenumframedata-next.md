---
title: 'IDiaEnumFrameData:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe8735511e9830542ce8622a6d984a0a817671
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161226"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

열거형 시퀀스에서 지정 된 수의 프레임 데이터 요소를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 celt  
 진행 검색할 열거자의 프레임 데이터 요소 수입니다.  
  
 rgelt  
 제한이 요청 된 프레임 데이터 요소로 채울 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체의 배열입니다.  
  
 pceltFetched  
 제한이 인출 된 열거자의 프레임 데이터 요소 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`레코드가 더 이상 없으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
