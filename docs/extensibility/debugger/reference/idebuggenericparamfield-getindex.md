---
title: 'IDebugGenericParamField:: GetIndex | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b31acd57685058795186fcecb73164218d5ad15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727989"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
이 제네릭 매개 변수의 인덱스를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetIndex(
    DWORD* pIndex
);
```

```csharp
int GetIndex(
    out uint pIndex
);
```

## <a name="parameters"></a>매개 변수
`pIndex`\
제한이 이 제네릭 매개 변수의 인덱스 값입니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
예를 들어 사전 (K, V)의 경우 K는 인덱스 0이 고 V는 인덱스 1입니다.

## <a name="example"></a>예
다음 예제에서는 [Idebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 인터페이스를 노출 하는 **CDebugGenericParamFieldType** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );

    IfFalseGo(pIndex, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pIndex = m_index;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );
    return hr;
}
```

## <a name="see-also"></a>추가 정보
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
