---
title: 'IDebugGenericFieldInstance:: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0272e86f5c1bbbd840ee222b2048440338302d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728160"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
이 인스턴스에 대 한 형식 매개 변수 인수의 수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>매개 변수
`pcArgs`\
[in, out] 이 인스턴스에 대 한 형식 매개 변수 인수의 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어 List 인 경우 \<int> 이 메서드는 1을 반환 하 고, list 인 경우 \<int,float2> 이 메서드는 2를 반환 합니다. 형식 인수가 없으면이 메서드는 0을 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
