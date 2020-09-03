---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736623"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
DE (디버그 엔진)는이 인터페이스를 사용 하 여 로드할 문서를 요청 합니다.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 소스 파일을 열어야 할 때이 인터페이스를 구현 합니다. 이 인터페이스는에서 작동 하거나 스크립트 인터프리터의 일부인 디버그 엔진 에서만 구현 됩니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. 즉, SDM에서 인터페이스에 액세스 하는 데 [QueryInterface](/cpp/atl/queryinterface) 를 사용 합니다 `IDebugEvent2` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 소스 파일을 열어야 하는 경우 DE는이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugActivateDocumentEvent2` .

|메서드|Description|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|활성화할 문서를 가져옵니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|문서 내의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 사용 하는 일반적인 시나리오는 HTML 페이지의 스크립트 코드에서 구문 분석 오류가 발생 하는 경우 스크립트 DE는 구문 분석 오류가 있는 문서를 표시할 수 있도록이 인터페이스를 SDM으로 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
