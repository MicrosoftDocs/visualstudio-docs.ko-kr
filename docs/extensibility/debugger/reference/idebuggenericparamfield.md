---
title: 이데버그네네릭파라엠필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727848"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
관리 되는 코드 제네릭 형식에 대 한 매개 변수를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 제네릭 지원에 사용됩니다.

## <a name="methods"></a>메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|이 제네릭 매개 변수와 연결된 제약 조건 수를 반환합니다.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|이 제네릭 매개 변수와 연결된 제약 조건을 검색합니다.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|이 제네릭 매개 변수에 대한 플래그를 검색합니다.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|이 제네릭 매개 변수의 인덱스를 검색합니다.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|이 제네릭 매개 변수의 이름을 검색합니다.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|이 제네릭 매개 변수의 형식 또는 메서드 소유자를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
