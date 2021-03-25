---
description: 이 메서드는 문서 위치를 디버그 주소 배열에 매핑합니다.
title: 'Idebug Provider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dd3b8fbe65a72ccf937007d19117359859ff29f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087108"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
이 메서드는 문서 위치를 디버그 주소 배열에 매핑합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>매개 변수
`pDocPos`\
진행 문서 위치입니다.

`fStatmentOnly`\
진행 TRUE 이면 디버그 주소를 단일 문으로 제한 합니다.

`ppEnumBegAddresses`\
제한이 이 문이나 줄과 연결 된 시작 디버그 주소에 대 한 열거자를 반환 합니다.

`ppEnumEndAddresses`\
제한이 이 문이나 줄과 연결 된 끝 디버그 주소에 대 한 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 열거자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 문서 위치는 일반적으로 소스 줄의 범위를 나타냅니다. 이 메서드는 이러한 줄과 연결 된 시작 및 종료 디버그 주소를 제공 합니다. 일부 언어에서는 여러 줄에 걸쳐 있는 문이나 둘 이상의 문을 포함 하는 줄을 허용 합니다. 이 메서드는 디버그 주소를 단일 문으로 제한 하는 플래그를 제공 합니다.

 템플릿의 경우와 같이 단일 문에 여러 개의 디버그 주소가 있을 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
