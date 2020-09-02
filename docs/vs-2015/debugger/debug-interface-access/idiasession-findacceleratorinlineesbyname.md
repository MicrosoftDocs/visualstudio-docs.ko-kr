---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47883395ec12cac60d3a21651432f5ac21cc64a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151748"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 인라인 함수 이름에 해당 하는 인라인 프레임의 기호 열거형을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `name`  
 진행 검색할 인라인 대상 함수 이름입니다.  
  
 `option`  
 진행 에 해당 하는 인라인 프레임을 검색할 때 사용할 이름 검색 옵션 `name` 입니다. 자세한 내용은 [Namesearchoptions 열거](../../debugger/debug-interface-access/namesearchoptions.md)를 참조 하세요.  
  
 `ppResult`  
 제한이 결과를 사용 하 여 `IDiaEnumSymbols` 초기화 되는 인터페이스 포인터에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 함수는 액셀러레이터 키 함수 내 에서만 가진을 검색 합니다. 네이티브 c + + 프로시저 레코드는 무시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
