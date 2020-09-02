---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150085"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

가상 주소와 연결 된 .PDATA 데이터 블록을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `va`  
 진행 가져올 데이터의 가상 주소를 지정 합니다.  
  
 `cbData`  
 진행 가져올 데이터의 크기 (바이트)입니다.  
  
 `pcbData`  
 제한이 가져온 데이터의 실제 크기 (바이트)를 반환 합니다.  
  
 `pbData`  
 [in, out] 요청 된 데이터로 채워진 버퍼입니다. `NULL`일 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`지정 된 주소에 대 한 .pdata가 없으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 Compiland의 .PDATA (".pdata" 섹션)은 함수에 대 한 예외 처리에 대 한 정보를 포함 합니다.  
  
 호출자는 반환 되는 데이터의 양을 알고 있으므로 호출자는 사용할 수 있는 데이터의 양을 요청할 필요가 없습니다. 따라서 매개 변수가 인 경우이 메서드를 구현 하 여 오류를 반환할 수 `pbData` `NULL` 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
