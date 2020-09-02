---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 315af434271d57a8547963f2538ff1b799ef4fd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150018"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램 디버그 데이터베이스 (.pdb) 파일을 사용 하 여 스택을 쉽게 탐색 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>VTable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaStackWalkHelper` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|레지스터의 값을 검색 합니다.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|레지스터의 값을 설정 합니다.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|메모리의 실행 파일 이미지에서 데이터 블록을 읽습니다.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|지정 된 스택 프레임에서 가장 가까운 함수 반환 주소를 검색 합니다.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|지정 된 스택 프레임에서 지정 된 스택 주소 또는 그 근처의 반환 주소를 검색 합니다.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|지정 된 가상 주소를 포함 하는 스택 프레임을 검색 합니다.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|지정 된 가상 주소를 포함 하는 기호를 검색 합니다. **참고:**  기호에는 형식 `SymTagFunctionType` ( [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거형의 값)이 있어야 합니다.|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|지정 된 가상 주소와 연결 된 .PDATA 데이터 블록을 반환 합니다.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|실행 파일의 메모리 공간 어딘가에 가상 주소가 지정 된 경우 실행 파일의 시작 가상 주소를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 프로그램을 실행 하는 동안 스택 프레임 목록을 생성 하는 실행 파일에 대 한 정보를 가져오기 위해 DIA 코드에서 호출 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 클라이언트 응용 프로그램은 프로그램 실행 중에 스택 탐색을 지원 하기 위해이 인터페이스를 구현 합니다. 이 인터페이스의 인스턴스는 [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) 또는 [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 메서드에 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
