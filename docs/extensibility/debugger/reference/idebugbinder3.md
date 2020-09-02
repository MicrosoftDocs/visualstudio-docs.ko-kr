---
title: IDebugBinder3 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735676"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 형식, 별칭 및 사용자 지정 시각화 도우미 서비스에 대 한 액세스를 제공 합니다.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진은이 인터페이스를 구현 하 여 별칭, 사용자 지정 시각화 도우미 서비스 및 개체 형식 정보에 대 한 액세스를 지원 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스는 [QueryInterface](/cpp/atl/queryinterface)를 사용 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 인터페이스에서 제공 하는 메서드 외에도이 인터페이스는 다음을 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|이 개체가 바인딩되는 메모리를 나타내는 메모리 개체를 검색 합니다.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|이 개체와 연결 된 예외를 검색 합니다 (있는 경우).|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|이름이 지정 된 별칭을 검색 합니다.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|이 개체에 대 한 모든 별칭의 배열을 검색 합니다.|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|이 개체와 연결 된 인수 형식의 수를 가져옵니다.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|이 개체와 연결 된 인수 형식의 목록을 검색 합니다.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|시각화 도우미 서비스에 대 한 인터페이스를 가져옵니다.|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|개체 위치 또는 64 비트 메모리 주소를 메모리 컨텍스트로 변환 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
