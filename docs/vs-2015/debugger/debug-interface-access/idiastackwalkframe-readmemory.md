---
title: 'IDiaStackWalkFrame:: readMemory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150170"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이미지에서 메모리를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `type`  
 진행 액세스할 메모리 종류를 지정 하는 [MemoryTypeEnum 열거형](../../debugger/debug-interface-access/memorytypeenum.md) 열거형 값 중 하나입니다.  
  
 `va`  
 진행 읽기를 시작할 이미지의 가상 주소 위치입니다.  
  
 `cbData`  
 진행 데이터 버퍼의 크기 (바이트)입니다.  
  
 `pcbData`  
 제한이 반환 된 바이트 수를 반환 합니다. `data`가 이면는 `NULL` `pcbData` 사용할 수 있는 데이터의 총 바이트 수를 포함 합니다.  
  
 `data`  
 제한이 지정 된 위치의 데이터로 채워질 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
