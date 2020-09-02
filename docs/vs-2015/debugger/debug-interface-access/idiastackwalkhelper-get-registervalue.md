---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4dde30ebcda46d75271b15ec5b7f7c1ac49f384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150108"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

레지스터의 값을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `index`  
 진행 값을 가져올 레지스터를 지정 하 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md) 열거형의 값입니다.  
  
 `pRetVal`  
 제한이 레지스터의 현재 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 매개 변수의 크기에도 불구 하 고 `pRetVal` 구현은 일반적으로 등록에 포함 된 내용만 저장 해야 합니다. 예를 들어 8 비트 레지스터는 지정 된 값의 가장 낮은 8 비트만 보유 합니다. 이 8 비트 값은이 메서드에서 반환 될 때 64 비트로 확장 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e 열거형](../../debugger/debug-interface-access/cv-hreg-e.md)
