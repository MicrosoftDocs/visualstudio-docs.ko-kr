---
title: 'IDiaSession:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0711c95310d4d3613d8b82bccbecab122bf19ef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196355"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

해당 태그 값이 지정 된 경우이 메서드는 지정 된 상대 가상 주소에서 지정 된 부모 액셀러레이터 키 함수에 포함 된 기호의 열거형을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `parent`  
 진행 `IDiaSymbol` 검색할 액셀러레이터 스텁 함수에 해당 하는입니다.  
  
 `tagValue`  
 진행 포인터 태그 값입니다.  
  
 `rva`  
 진행 상대 가상 주소입니다.  
  
 `ppResult`  
 제한이 결과를 사용 하 여 `IDiaEnumSymbols` 초기화 되는 인터페이스 포인터에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 `IDiaSymbol`액셀러레이터 키 함수에 해당 하는 인터페이스에 대해서만이 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
