---
title: 'IDebugGenericFieldDefinition:: ConstructInstantiation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352018e50b955ed414af974bc21b62775fd55f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728255"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
형식 인수 배열이 지정 된 경우 필드 인스턴스를 생성 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>매개 변수
`cArgs`\
진행 배열의 인수 개수 `ppArgs` 입니다.

`ppArgs`\
진행 형식 인수를 포함 하는 배열입니다. 형식 인수는 폐쇄형 형식 이어야 합니다 (제네릭이 아닌 또는 완전히 인스턴스화된 제네릭).

`ppConstructedField`\
제한이 새 필드를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 제약 조건은 확인 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
