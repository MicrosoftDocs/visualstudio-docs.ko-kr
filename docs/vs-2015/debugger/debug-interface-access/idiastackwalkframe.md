---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150145"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[IDiaFrameData:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 메서드의 호출 사이에 스택 컨텍스트를 유지 관리 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaStackWalkFrame` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|레지스터의 값을 검색 합니다.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|레지스터의 값을 설정 합니다.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|이미지에서 메모리를 읽습니다.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|지정 된 스택 프레임에서 가장 가까운 함수 반환 주소를 검색 합니다.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|지정 된 주소 또는 그 근처의 반환 주소에 대해 지정 된 스택 프레임을 검색 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 레지스터를 읽고 쓰는 작업 뿐만 아니라 메모리에 액세스 하 고 반환 주소를 찾기 위해 프로그램을 실행 하는 동안 사용 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 클라이언트 응용 프로그램은이 인터페이스를 구현 하 고 인터페이스의 인스턴스를 [IDiaFrameData:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 메서드에 전달 합니다. 이 인터페이스의 동일한 인스턴스를 다시 사용 하 여 메서드를 호출할 때마다 레지스터의 상태를 유지 합니다 `execute` . `execute`또한이 메서드는이 인터페이스를 사용 하 여 반환 주소를 확인 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
