---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573016"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 메서드는 지정 된 지역 변수의 값을 원시 바이트로 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pInstance`  
 진행 `IDiaLVarInstance` 값을 가져올 지역 변수의 인스턴스를 나타내는 개체입니다.  
  
 `cbDataMax`  
 진행 가 가리키는 버퍼의 최대 바이트 수 `pbData` 입니다. 최대 8 바이트 ()를 사용할 수 있습니다 `sizeof(ULONGLONG)` .  
  
 `pcbData`  
 제한이 버퍼에 저장 된 실제 바이트 수를 반환 합니다.  
  
 `pbData`  
 제한이 데이터로 채울 버퍼입니다. 이는 `NULL`이 될 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
