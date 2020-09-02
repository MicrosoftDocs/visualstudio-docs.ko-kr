---
title: 'IDiaEnumDebugStreamData:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b80f71b2ca5d718f2de834389b4caab728e1f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197883"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 레코드를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 인덱스  
 진행 검색할 레코드의 인덱스입니다. 인덱스는 0에서-1 사이의 범위에 `count` `count` 있습니다. 여기서은 [IDiaEnumDebugStreamData:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)에 의해 반환 됩니다.  
  
 cbData  
 진행 데이터 버퍼의 크기 (바이트)입니다.  
  
 pcbData  
 제한이 반환 된 바이트 수를 반환 합니다. `data`가 이면는 `NULL` 지정 된 `pcbData` 레코드에서 사용할 수 있는 총 데이터 바이트 수를 포함 합니다.  
  
 data[]  
 제한이 디버그 스트림 레코드 데이터로 채워진 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 는 `E_INVALIDARG` 잘못 된 매개 변수를 반환 하 고 `index` 매개 변수가 범위를 벗어나면를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData:: Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)
