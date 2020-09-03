---
title: 'Idebug Provider:: GetAddressesFromContext | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
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
진행 문서 컨텍스트입니다.

`fStatmentOnly`\
진행 TRUE 이면 디버그 주소를 단일 문으로 제한 합니다.

`ppEnumBegAddresses`\
제한이 이 문이나 줄과 연결 된 시작 디버그 주소에 대 한 열거자를 반환 합니다.

`ppEnumEndAddresses`\
제한이 이 문이나 줄과 연결 된 끝 디버그 주소에 대 한 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 열거자를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 문서 컨텍스트는 일반적으로 소스 줄의 범위를 나타냅니다. 이 메서드는 이러한 줄과 연결 된 시작 및 종료 디버그 주소를 제공 합니다. 일부 언어에서는 여러 줄에 걸쳐 있는 문이나 둘 이상의 문을 포함 하는 줄을 허용 합니다. 이 메서드는 디버그 주소를 단일 문으로 제한 하는 플래그를 제공 합니다.

 템플릿의 경우와 같이 단일 문에 여러 개의 디버그 주소가 있을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
