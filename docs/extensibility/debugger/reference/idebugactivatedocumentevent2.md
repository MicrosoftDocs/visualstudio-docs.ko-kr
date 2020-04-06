---
title: 아이디버그활성화문서Event2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736623"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
DE(디버그 엔진)는 이 인터페이스를 사용하여 로드할 문서를 요청합니다.

## <a name="syntax"></a>구문

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 소스 파일을 열어야 할 때 이 인터페이스를 구현합니다. 이 인터페이스는 스크립트 인터프리터와 함께 작동하거나 스크립트 인터프리터의 일부인 디버그 엔진에 의해서만 구현됩니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 `IDebugEvent2` [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에 액세스합니다).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 소스 파일을 열어야 할 때 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugActivateDocumentEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|메서드|설명|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|활성화할 문서를 가져옵니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|문서 내의 위치를 설명하는 문서 컨텍스트를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스가 사용되는 일반적인 시나리오는 HTML 페이지의 스크립트 코드에서 구문 분석 오류가 발생하는 경우 스크립트 DE가 이 인터페이스를 SDM으로 전송하여 구문 분석 오류가 있는 문서를 표시할 수 있도록 하는 것입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
