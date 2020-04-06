---
title: 아이디버그문서배치2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731642"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
이 인터페이스는 소스 파일의 추상 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 일반적으로 이 인터페이스를 구현합니다. DE는 자체 소스 코드를 제공해야 하는 경우(DE가 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현할 때와 같이) DE(디버그 엔진)도 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [EnumCodeContexts에](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)인수로 전달됩니다. 또한 보류 중인 중단점을 만드는 데 사용되는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조의 일부인 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 공용 구조(특히 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 구조)의 일부로 제공됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugDocumentPosition2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|이 문서 위치를 포함하는 원본 파일의 파일 이름을 가져옵니다.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|포함된 문서를 가져옵니다.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|이 위치가 지정된 문서에 포함되어 있는지 확인합니다.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|이 문서 위치의 범위를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
