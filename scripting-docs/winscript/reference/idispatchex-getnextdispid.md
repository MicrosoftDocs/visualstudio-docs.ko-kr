---
title: 'IDispatchEx:: GetNextDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144431"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

개체의 멤버를 열거 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>매개 변수

`grfdex`\
열거할 항목 집합을 결정 합니다. 다음 값을 조합 하 여 사용할 수 있습니다.

|값|의미|
|-----------|-------------|
|fdexEnumDefault|개체가 기본 요소를 열거 하도록 요청 합니다. 개체는 모든 요소 집합을 열거할 수 있습니다.|
|fdexEnumAll|개체가 모든 요소를 열거 하도록 요청 합니다. 개체는 모든 요소 집합을 열거할 수 있습니다.|

`id`\
현재 멤버를 식별 합니다. GetNextDispID는 열거에서 항목을 검색 합니다. GetDispID 또는 GetNextDispID에 대 한 이전 호출을 사용 하 여이 식별자를 가져옵니다. DISPID_STARTENUM 값을 사용 하 여 첫 번째 항목의 첫 번째 식별자를 가져옵니다.

`pid`\
열거형의 다음 항목에 대 한 식별자를 수신 하는 DISPID 변수의 주소입니다.

멤버가 또는에서 삭제 되는 `DeleteMemberByName` 경우 `DeleteMemberByDispID` 은 `DISPID` 에 대해 유효한 상태로 유지 되어야 `GetNextDispID` 합니다.

## <a name="return-value"></a>Return Value

다음 값 중 하나를 반환합니다.

|값|의미|
|-|-|
|`S_OK`|성공|
|`S_FALSE`|열거가 완료 되었습니다.|

## <a name="example"></a>예제

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>참고 항목

- [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)