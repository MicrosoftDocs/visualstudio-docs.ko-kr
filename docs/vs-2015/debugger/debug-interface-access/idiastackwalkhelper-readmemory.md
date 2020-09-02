---
title: 'IDiaStackWalkHelper:: readMemory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150064"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

메모리의 실행 파일 이미지에서 데이터 블록을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `type`  
 진행 읽을 메모리의 형식을 지정 하는 [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md) 열거형의 값입니다.  
  
 va  
 진행 읽기를 시작할 이미지의 가상 주소입니다.  
  
 `cbData`  
 진행 데이터 버퍼의 크기 (바이트)입니다.  
  
 `pcbData`  
 제한이 실제로 읽은 바이트 수를 반환 합니다. `pbData`가 이면 `NULL` 사용 가능한 데이터의 총 바이트 수입니다.  
  
 `pbData`  
 [in, out] 읽은 메모리를 사용 하 여 채워진 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md)
