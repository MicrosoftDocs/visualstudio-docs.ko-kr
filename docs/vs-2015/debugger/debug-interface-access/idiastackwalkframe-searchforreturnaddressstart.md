---
title: 'IDiaStackWalkFrame:: searchForReturnAddressStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2d34c4f10679d6f0702dead5352ddf088704b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150176"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 주소 또는 그 근처의 반환 주소에 대해 지정 된 스택 프레임을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `frame`  
 진행 현재 스택 프레임을 나타내는 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 개체입니다.  
  
 `startAddress`  
 진행 검색을 시작할 가상 메모리 주소입니다.  
  
 `returnAddress`  
 제한이 가장 가까운 함수 반환 주소를로 반환 합니다 `startAddress` .  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
