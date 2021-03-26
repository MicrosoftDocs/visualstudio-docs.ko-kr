---
description: 이 인터페이스는 소스 파일 문서의 위치를 나타냅니다.
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a20473d2076932987ecc352c8719f1d9133ed198
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066518"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
이 인터페이스는 소스 파일 문서의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 소스 코드 수준 디버깅 지원의 일부로이 인터페이스를 구현 합니다. 이 인터페이스는 소스 코드의 위치 외에도 컨텍스트를 비교 하 고 소스 코드 문서를 탐색 하는 메서드를 제공 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 여러 인터페이스 (일반적으로 [getdocumentcontext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 및 [getdocumentcontext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 인터페이스)의 메서드는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocumentContext2` .

|메서드|Description|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|이 문서 컨텍스트를 포함 하는 문서를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|이 문서 컨텍스트를 포함 하는 문서의 표시할 때 나타나는 이름을 가져옵니다.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|이 문서 컨텍스트와 연결 된 모든 코드 컨텍스트의 목록을 검색 합니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|이 문서 컨텍스트와 연결 된 언어를 가져옵니다.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|이 문서 컨텍스트의 파일 문 범위를 가져옵니다.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|이 문서 컨텍스트의 파일 소스 범위를 가져옵니다.|
|[비교](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|이 문서 컨텍스트를 지정 된 문서 컨텍스트의 배열과 비교 합니다.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|문서 컨텍스트를 지정 된 수의 문이나 줄로 이동 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
