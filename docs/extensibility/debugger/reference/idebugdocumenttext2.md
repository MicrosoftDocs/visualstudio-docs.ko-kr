---
description: 이 인터페이스는 텍스트 문서를 나타냅니다.
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1c5928362616466985a6f88102ffcbf4377444
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154212"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
이 인터페이스는 텍스트 문서를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 제공 해야 하는 소스 코드가 텍스트 형식이 면이 인터페이스를 구현 합니다. 이는 가장 일반적인 사례 이므로 DE가 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현 하는 경우 인터페이스도 구현 해야 합니다 `IDebugDocumentText2` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 `QueryInterface`인터페이스에서이 인터페이스를 가져오려면 메서드를 사용 `IDebugDocument2` 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 인터페이스의 메서드 외에도 `IDebugDocument2` 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|문서의이 위치에 있는 텍스트의 크기를 검색 합니다.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|문서의 지정 된 위치에서 텍스트를 검색 합니다.|

## <a name="remarks"></a>설명
 또한이 인터페이스를 구현 하는 개체는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) 개체에 대 한 인터페이스를 제공 하는 인터페이스를 구현 해야 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
