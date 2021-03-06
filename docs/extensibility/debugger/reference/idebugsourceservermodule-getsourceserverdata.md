---
description: 원본 서버 정보의 배열을 검색 합니다.
title: 'IDebugSourceServerModule:: GetSourceServerData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35e6f73d74006d4db4135f9202968896a6023cf5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071183"
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
원본 서버 정보의 배열을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSourceServerData(
    ULONG* pDataByteCount,
    BYTE** ppData
);
```

```csharp
public int GetSourceServerData(
    out uint  pDataByteCount,
    out int[] ppData
);
```

## <a name="parameters"></a>매개 변수
`pDataByteCount`\
제한이 데이터 배열의 바이트 수입니다.

`ppData`\
제한이 데이터 배열에 대 한 참조입니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) 인터페이스를 노출 하는 **cmodule** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)
{
    HRESULT hr = S_OK;
    CComPtr<ISymUnmanagedReader> pSymReader;
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;

    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );
    *pDataByteCount = 0;
    *ppData = NULL;

    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );

    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );

Error:

    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)
