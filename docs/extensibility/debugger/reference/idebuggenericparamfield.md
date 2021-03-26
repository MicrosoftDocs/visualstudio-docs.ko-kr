---
description: 관리 코드 제네릭 형식에 대 한 매개 변수를 나타냅니다.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091931"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
관리 코드 제네릭 형식에 대 한 매개 변수를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 제네릭을 지 원하는 데 사용 됩니다.

## <a name="methods"></a>메서드
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|이 제네릭 매개 변수와 연결 된 제약 조건 수를 반환 합니다.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|이 제네릭 매개 변수와 연결 된 제약 조건을 검색 합니다.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|이 제네릭 매개 변수에 대 한 플래그를 검색 합니다.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|이 제네릭 매개 변수의 인덱스를 검색 합니다.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|이 제네릭 매개 변수의 이름을 검색 합니다.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|이 제네릭 매개 변수의 형식 또는 메서드 소유자를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
