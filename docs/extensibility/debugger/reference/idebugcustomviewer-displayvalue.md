---
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732445"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
이 메서드는 지정 된 값을 표시 하기 위해 호출 됩니다.

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
진행 부모 창

`dwID`\
진행 둘 이상의 유형을 지 원하는 사용자 지정 뷰어의 ID입니다.

`pHostServices`\
[in] 예약되어 있습니다. 항상 null로 설정 합니다.

`pDebugProperty`\
진행 표시할 값을 검색 하는 데 사용할 수 있는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 호출자에 게 반환 하기 전에 필요한 창을 만들고, 값을 표시 하 고, 입력을 대기 하 고, 창을 닫을 때마다 "모달"로 표시 됩니다. 즉, 메서드는 출력 창 만들기, 사용자 입력 대기, 창 소멸까지 속성 값을 표시 하는 모든 측면을 처리 해야 합니다.

 지정 된 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 개체의 값 변경을 지원 하기 위해 값을 문자열로 표현할 수 있는 경우 [Setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 메서드를 사용할 수 있습니다. 그렇지 않은 경우에는 `DisplayValue` 인터페이스를 구현 하는 동일한 개체에서이 메서드를 구현 하는 식 계산기로만 사용자 지정 인터페이스를 만들어야 `IDebugProperty3` 합니다. 이 사용자 지정 인터페이스는 임의의 크기나 복잡성의 데이터를 변경 하는 메서드를 제공 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
