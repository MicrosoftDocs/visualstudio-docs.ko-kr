---
title: IDebugSourceServer모듈::겟소스서버데이터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0388e4a1916a16f7e429fa4f32c45ed62fdb02e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719922"
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
소스 서버 정보의 배열을 검색합니다.

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
【아웃】 데이터 배열의 바이트 수입니다.

`ppData`\
【아웃】 데이터 배열에 대한 참조입니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugServerServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) 인터페이스를 노출 하는 **CModule** 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

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
