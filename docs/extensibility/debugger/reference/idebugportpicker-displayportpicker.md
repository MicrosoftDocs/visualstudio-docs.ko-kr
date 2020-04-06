---
title: 이데버그포트피커::D이스플레이포트피커 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724895"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
사용자가 포트를 선택할 수 있도록 지정된 대화 상자를 표시합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>매개 변수
`hwndParentDialog`\
【인】 상위 대화 상자에 대한 핸들입니다.

`pbstrPortId`\
【아웃】 포트 식별자 문자열입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. `S_FALSE` 반환 값(또는 `S_OK` `BSTR` 집합이 있는 반환 값)은 `NULL`사용자가 **Cancel을**클릭했음을 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
