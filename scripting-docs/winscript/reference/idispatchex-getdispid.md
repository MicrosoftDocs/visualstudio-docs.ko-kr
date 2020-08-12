---
title: 'IDispatchEx:: GetDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144535"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
단일 멤버 이름을 해당 DISPID에 매핑한 다음에 대 한 후속 호출에서 사용할 수 있습니다 `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bstrName`  
 매핑할 이름이 전달 되었습니다.  
  
 `grfdex`  
 멤버 식별자를 가져오기 위한 옵션을 결정 합니다. 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|fdexNameCaseSensitive|대/소문자 구분 방식으로 이름 조회를 수행 하도록 요청 합니다. 대/소문자를 구분 하는 조회를 지원 하지 않는 개체에서 무시 될 수 있습니다.|  
|fdexNameEnsure|아직 존재 하지 않는 경우 멤버를 만들도록 요청 합니다. 값을 사용 하 여 새 멤버를 만들어야 합니다 `VT_EMPTY` .|  
|fdexNameImplicit|기본 개체가 명시적으로 지정 되지 않은 경우 호출자가 특정 이름의 멤버에 대 한 개체를 검색 하 고 있음을 나타냅니다.|  
|fdexNameCaseInsensitive|대/소문자를 구분 하지 않는 방식으로 이름 조회를 수행 하도록 요청 합니다. 대/소문자를 구분 하지 않는 조회를 지원 하지 않는 개체에서 무시 될 수 있습니다.|  
  
 `pid`  
 DISPID 결과를 받을 호출자가 할당 하는 위치에 대 한 포인터입니다. 오류가 발생 하면 `pid` DISPID_UNKNOWN 포함 됩니다.  
  
## <a name="return-value"></a>Return Value  
 다음 값 중 하나를 반환합니다.  
  
|값|의미|
|-|-|  
|`S_OK`|성공|  
|`E_OUTOFMEMORY`|메모리가 부족 합니다.|  
|`DISP_E_UNKNOWNNAME`|이름을 알 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 `GetDispID`대신를 사용 하 여 `GetIDsOfNames` 지정 된 멤버의 DISPID를 가져올 수 있습니다.  
  
 에서는 `IDispatchEx` 멤버를 추가 및 삭제할 수 있으므로 dispid 집합은 개체의 수명 동안 일정 하 게 유지 되지 않습니다.  
  
 에서 사용 되지 않는 `riid` 매개 변수가 `IDispatch::GetIDsOfNames` 제거 되었습니다.  
  
## <a name="example"></a>예제  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)