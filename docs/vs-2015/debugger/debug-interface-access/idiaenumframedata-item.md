---
title: 'IDiaEnumFrameData:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0db365738e7c41c4a4e9f36b1942c5a64dedada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161254"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

인덱스를 사용 하 여 프레임 데이터 요소를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 인덱스  
 진행 검색할 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체의 인덱스입니다. 인덱스의 범위는 0 ~ `count` -1입니다 `count` . 여기서은 [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) 메서드에서 반환 됩니다.  
  
 section  
 제한이 원하는 프레임 데이터 요소를 나타내는 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
