---
title: 이데버그어레이오브젝트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736235"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 관리되는 배열 개체를 나타내고 식 평가기(EE)가 배열에 대한 기본 인덱스(하한)를 결정할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이것은 관리되는 디버그 엔진(DE)에 의해 구현됩니다.

## <a name="methods"></a>메서드
 이 인터페이스는 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|배열의 차원 수가 주어진 각 인덱스에 대한 기본 인덱스(하한)를 검색합니다.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|배열에 기본 인덱스(하한)가 정의된지 여부를 결정합니다.|

## <a name="remarks"></a>설명
 식 평가기는 이 인터페이스를 사용하여 구문 분석 트리에서 관리되는 배열을 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
