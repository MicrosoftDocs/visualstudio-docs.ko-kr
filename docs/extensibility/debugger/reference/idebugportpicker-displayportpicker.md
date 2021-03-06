---
description: 사용자가 포트를 선택할 수 있는 지정 된 대화 상자를 표시 합니다.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072314"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
사용자가 포트를 선택할 수 있는 지정 된 대화 상자를 표시 합니다.

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
진행 부모 대화 상자에 대 한 핸들입니다.

`pbstrPortId`\
제한이 포트 식별자 문자열입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 반환 값 `S_FALSE` (또는가로 설정 된의 반환 값 `S_OK` )은 `BSTR` `NULL` 사용자가 **취소** 를 클릭 했음을 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
