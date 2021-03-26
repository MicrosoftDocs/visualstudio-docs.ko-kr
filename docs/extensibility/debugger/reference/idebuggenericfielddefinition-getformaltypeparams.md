---
description: 매개 변수 수를 지정 하 여 형식 매개 변수를 검색 합니다.
title: 'IDebugGenericFieldDefinition:: GetFormalTypeParams | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aba284bab3299bf6ef300f9493c20e9c0d230ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063450"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
매개 변수 수를 지정 하 여 형식 매개 변수를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetFormalTypeParams(
   ULONG32                   cParams,
   IDebugGenericParamField** ppParams,
   ULONG32*                  pcParams
);
```

```csharp
int GetFormalTypeParams(
   uint                          cParams,
   out IDebugGenericParamField[] ppParams,
   ref uint                      pcParams
);
```

## <a name="parameters"></a>매개 변수
`cParams`\
진행 매개 변수 수입니다.

`ppParams`\
제한이 형식 매개 변수의 배열입니다.

`pcParams`\
[in, out] 배열의 매개 변수 수 `ppParams` 입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 형식 매개 변수를 왼쪽에서 오른쪽 순서로 반환 합니다. 예를 들어 사전은 \<K,V> IDebugFormalGenericParameters {K, V}를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
