---
title: 아이디버그문서텍스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731565"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
이 인터페이스는 텍스트 문서를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 제공해야 하는 소스 코드가 텍스트 형식으로 되어 있을 때 이 인터페이스를 구현합니다. 가장 일반적인 경우이므로 DE가 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현하는 경우 `IDebugDocumentText2` 인터페이스도 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 메서드를 `QueryInterface` 사용하여 인터페이스에서 이 `IDebugDocument2` 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 인터페이스의 `IDebugDocument2` 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|문서의 이 위치에서 텍스트 크기를 검색합니다.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|문서의 지정된 위치에서 텍스트를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 구현하는 개체는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) 개체에 대한 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 인터페이스를 제공하는 인터페이스도 구현해야 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
