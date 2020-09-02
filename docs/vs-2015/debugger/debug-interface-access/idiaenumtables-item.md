---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9eec94a5a02eda8fe9b1b3bf8f76f5050ab1e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423870"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

인덱스 또는 이름을 사용 하 여 테이블을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `index`  
 진행 검색할 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 의 인덱스 또는 이름입니다. 정수 variant를 사용 하는 경우 0에서-1 사이의 범위에 있어야 합니다 `count` `count` . 여기서은 [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) 메서드에서 반환 됩니다.  
  
 `table`  
 제한이 원하는 테이블을 나타내는 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 문자열 변형이 지정 된 경우 문자열은 특정 테이블의 이름을 지정 합니다. 이름은 [상수 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)에 정의 된 테이블 이름 중 하나 여야 합니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [상수(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
