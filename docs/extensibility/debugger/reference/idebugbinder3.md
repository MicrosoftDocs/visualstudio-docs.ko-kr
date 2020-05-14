---
title: 이데버그바인더3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735676"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 형식, 별칭 및 사용자 지정 시각화 도우미 서비스에 대한 액세스를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 별칭, 사용자 지정 시각화 도우미 서비스 및 개체 유형 정보에 대한 액세스를 지원하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스는 [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스에서 제공하는 메서드 외에도 다음을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|이 개체가 바인딩된 메모리를 나타내는 메모리 개체를 검색합니다.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|이 개체와 연결된 예외(있는 경우)를 검색합니다.|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|이름이 지정된 별칭을 검색합니다.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|이 개체에 대한 모든 별칭 배열을 검색합니다.|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|이 개체와 연결된 인수 형식의 수를 가져옵니다.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|이 개체와 연결된 인수 유형 목록을 검색합니다.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|시각화 도우미 서비스에 대한 인터페이스를 가져옵니다.|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|개체 위치 또는 64비트 메모리 주소를 메모리 컨텍스트로 변환합니다.|

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
