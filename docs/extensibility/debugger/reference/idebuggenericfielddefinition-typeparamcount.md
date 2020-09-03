---
title: 'IDebugGenericFieldDefinition:: TypeParamCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a488bce2ad5822f875776bdfc4c4de29eee71bbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728230"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
제네릭 필드와 연결 된 형식 매개 변수의 수를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>매개 변수
`pcParams`\
[in, out] 형식 매개 변수 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 목록에서 \<T> 이 메서드는 1을 반환 하 고 list 인 경우 \<T1,T2> 이 메서드는 2를 반환 합니다. 이 메서드는 형식 매개 변수가 없는 경우 0을 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
