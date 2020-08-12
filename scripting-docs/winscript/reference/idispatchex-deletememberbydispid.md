---
title: IDispatchEx::D eleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144638"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
DISPID로 멤버를 삭제 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 멤버 식별자입니다. `GetDispID`또는 `GetNextDispID` 를 사용 하 여 디스패치 식별자를 가져옵니다.  
  
## <a name="return-value"></a>Return Value  
 다음 값 중 하나를 반환합니다.  
  
|값|의미|
|-|-|  
|`S_OK`|성공|  
|`S_FALSE`|멤버가 있지만 삭제할 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 멤버를 삭제 한 경우에는 DISPID가에 대해 유효한 상태를 유지 해야 합니다 `GetNextDispID` .  
  
 지정 된 이름의 멤버를 삭제 하 고 나중에 동일한 이름의 멤버를 다시 만들 경우 DISPID는 동일 해야 합니다. 대/소문자만 다른 멤버 이름이 "동일" 인지 여부는 개체에 따라 달라 집니다.  
  
## <a name="example"></a>예제  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)