---
title: 이데버그포인터오브젝트3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725471"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 구문 분석 트리에서 포인터를 나타내고 **IDebugPointerObject** 인터페이스를 확장합니다.

## <a name="syntax"></a>구문

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기(EE)는 이 인터페이스를 구현합니다.

## <a name="methods"></a>메서드
 이 인터페이스는 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|포인터의 주소를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
