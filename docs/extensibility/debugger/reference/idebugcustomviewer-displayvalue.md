---
title: 아이디버그커스텀뷰어::D플레이밸류 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732445"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
이 메서드는 지정된 값을 표시 하기 위해 호출 됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>매개 변수
`hwnd`\
【인】 상위 창

`dwID`\
【인】 두 개 이상의 유형을 지원하는 사용자 지정 뷰어용 ID입니다.

`pHostServices`\
[in] 예약되어 있습니다. 항상 null로 설정합니다.

`pDebugProperty`\
【인】 표시할 값을 검색하는 데 사용할 수 있는 인터페이스입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 필요한 창을 만들고, 값을 표시하고, 입력을 대기하고, 창을 닫은 다음, 호출자에게 돌아가기 전에 "모달"입니다. 즉, 메서드는 출력을 위한 창 만들기에서 사용자 입력 대기, 창 파기까지 속성 값을 표시하는 모든 측면을 처리해야 합니다.

 지정된 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 개체의 값 변경을 지원하려면 값을 문자열로 표현할 수 있는 경우 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 메서드를 사용할 수 있습니다. 그렇지 않으면 `DisplayValue` `IDebugProperty3` 인터페이스를 구현하는 동일한 개체에서 이 메서드를 구현하는 식 계산기전용 사용자 지정 인터페이스를 만들어야 합니다. 이 사용자 지정 인터페이스는 임의의 크기 또는 복잡성의 데이터를 변경하기 위한 메서드를 제공합니다.

## <a name="see-also"></a>참조
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
