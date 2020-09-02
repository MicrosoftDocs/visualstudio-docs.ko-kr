---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f5f5c3fa70c022175208cee492f3c0e752826e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144676"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

.Pdb 파일의 정보를 사용 하 여 스택 워크를 수행 하는 메서드를 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaStackWalker` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|X86 플랫폼용 스택 프레임 열거자를 검색 합니다.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|특정 플랫폼 형식에 대 한 스택 프레임 열거자를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 로드 된 모듈의 스택 프레임 목록을 가져오는 데 사용 됩니다. 각 메서드는 스택 프레임 목록을 만드는 데 필요한 정보를 제공 하는 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 개체 (클라이언트 응용 프로그램에서 구현 됨)에 전달 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 `CoCreateInstance` 클래스 식별자 `CLSID_DiaStackWalker` 와의 인터페이스 ID를 사용 하 여 메서드를 호출 하 여 가져옵니다 `IID_IDiaStackWalker` . 이 예제에서는이 인터페이스를 가져오는 방법을 보여 줍니다.  
  
## <a name="example"></a>예  
 이 예제에서는 인터페이스를 가져오는 방법을 보여 줍니다 `IDiaStackWalker` .  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
