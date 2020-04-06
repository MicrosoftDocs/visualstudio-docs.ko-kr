---
title: 아이디버그문서2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731996"
---
# <a name="idebugdocument2"></a>IDebugDocument2
이 인터페이스는 원본 문서를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]일반적으로 이 인터페이스를 구현합니다. 디버그 엔진(DE)은 소스 코드를 제공해야 하고 소스가 디스크에 없는 경우에도 이 인터페이스를 구현할 수 있습니다.  이러한 경우 DE는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 및 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) 인터페이스뿐만 아니라 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 및 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 인터페이스에 대한 몇 가지 추가 메서드도 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 의 메서드는 `IDebugDisassemblyStream2` `IDebugDocumentPosition2`에서 `IDebugActivateDocumentEvent2` , 및 인터페이스는 이 인터페이스를 반환합니다. `IDebugDocumentContext2`

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugDocument2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|여러 형식 중 하나로 문서 이름을 가져옵니다.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|문서의 클래스 식별자를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 DE가 소스 코드를 제공하는 경우에만 구현됩니다. 예를 들어 HTML 페이지에서 스크립트를 디버깅하는 경우 소스가 동적으로 다운로드되거나 생성되고 디스크 파일로 존재하지 않기 때문에 DE는 소스 코드를 제공합니다. C++와 같은 기존 언어를 디버깅할 때이 인터페이스를 구현할 필요가 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
