---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736611"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
해당 범위 또는 컨테이너 내에서 개체와 해당 위치를 설명 하는 구조체를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
[in, out] 이 메서드가 채우는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드에는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조가 전달 되 고,이 메서드에는 적절 한 정보로 채워집니다. 이 정보를 해석 하는 방법은 반환 되는 정보의 종류와 기호 처리기 자체에 따라 달라 집니다. 자세한 내용은 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
