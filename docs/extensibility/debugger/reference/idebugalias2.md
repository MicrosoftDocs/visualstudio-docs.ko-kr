---
title: 이데버그알리아스2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736359"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 변수에 대한 숫자 별칭을 나타내고 식 계산기(EE)가 별칭에 대한 응용 프로그램 도메인을 가져올 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 관리되는 디버그 엔진(DE)에 의해 구현됩니다.

## <a name="methods"></a>메서드
 이 인터페이스는 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|응용 프로그램 도메인의 식별자를 검색합니다.|

## <a name="remarks"></a>설명
 별칭은 문자열 형식의 소수 자릿수이며 # 문자(예: 1001#)가 뒤따릅니다.

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
