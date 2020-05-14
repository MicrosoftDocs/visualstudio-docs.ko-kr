---
title: IDebug 기호 공급자::Get주소컨텍스트에서 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719439"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
이 메서드는 문서 컨텍스트를 디버그 주소 배열에 매핑합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>매개 변수
`pDocContext`\
【인】 문서 컨텍스트입니다.

`fStatmentOnly`\
【인】 TRUE인 경우 디버그 주소를 단일 문으로 제한합니다.

`ppEnumBegAddresses`\
【아웃】 이 명령문 또는 줄과 연결된 시작 디버그 주소에 대한 열거형 기를 반환합니다.

`ppEnumEndAddresses`\
【아웃】 이 명령문 또는 줄과 연관된 종료 디버그 주소에 대해 [IEnumDebug주소](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 열거형기를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 문서 컨텍스트는 일반적으로 소스 줄의 범위를 나타냅니다. 이 메서드는 이러한 줄과 연결된 시작 및 종료 디버그 주소를 제공합니다. 일부 언어에서는 여러 줄에 걸쳐 있는 문 또는 둘 이상의 문을 포함하는 줄을 허용합니다. 이 메서드는 디버그 주소를 단일 문으로 제한하는 플래그를 제공합니다.

 템플릿의 경우와 같이 단일 문에 여러 디버그 주소가 있을 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
