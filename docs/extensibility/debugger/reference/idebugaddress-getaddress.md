---
title: 아이디버그 주소::겟주소 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736611"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
범위 또는 컨테이너 내에서 개체 및 해당 위치를 설명하는 구조를 반환합니다.

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
【인, 아웃】 이 방법으로 채워진 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조는 이 메서드에 전달되어 적절한 정보로 채웁니다. 이 정보를 해석하는 방법은 반환되는 정보의 종류와 기호 처리기 자체에 따라 다릅니다. 자세한 내용은 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 참조하십시오.

## <a name="see-also"></a>참조
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
