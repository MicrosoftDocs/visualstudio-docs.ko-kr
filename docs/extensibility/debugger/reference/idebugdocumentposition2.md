---
title: IDebugDocumentPosition2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731642"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
이 인터페이스는 소스 파일의 추상 위치를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 일반적으로이 인터페이스를 구현 합니다. De (디버그 엔진)는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현 하는 경우 처럼 자체 소스 코드를 제공 해야 하는 경우에도이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)에 대 한 인수로 전달 됩니다. 또한이 메서드는 보류 중인 중단점을 만드는 데 사용 되는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조체의 일부인 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 공용 구조체 (특히 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 구조체)의 일부로 제공 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocumentPosition2` .

|메서드|설명|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|이 문서 위치를 포함 하는 소스 파일의 파일 이름을 가져옵니다.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|포함 하는 문서를 가져옵니다.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|이 위치가 지정 된 문서에 포함 되어 있는지 여부를 확인 합니다.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|이 문서 위치에 대 한 범위를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
