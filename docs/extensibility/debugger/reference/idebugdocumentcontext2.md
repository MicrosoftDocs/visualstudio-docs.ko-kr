---
title: 아이디버그문서컨텍스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731737"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
이 인터페이스는 소스 파일 문서의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 소스 코드 수준 디버깅을 지원하는 작업의 일부로 이 인터페이스를 구현합니다. 이 인터페이스는 소스 코드의 위치 외에도 컨텍스트를 비교하고 소스 코드 문서를 탐색하는 메서드를 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 여러 인터페이스의 메서드(일반적으로 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 및 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 인터페이스)는 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugDocumentContext2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|이 문서 컨텍스트가 포함된 문서를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|이 문서 컨텍스트를 포함하는 문서의 표시 가능한 이름을 가져옵니다.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|이 문서 컨텍스트와 연결된 모든 코드 컨텍스트 목록을 검색합니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|이 문서 컨텍스트와 연결된 언어를 가져옵니다.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|이 문서 컨텍스트의 파일 문 범위를 가져옵니다.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|이 문서 컨텍스트의 파일 소스 범위를 가져옵니다.|
|[비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|이 문서 컨텍스트를 지정된 문서 컨텍스트 배열과 비교합니다.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|지정된 수의 문또는 줄로 문서 컨텍스트를 이동합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
