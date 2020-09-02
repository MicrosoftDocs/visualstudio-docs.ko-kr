---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731373"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
이 인터페이스는 디버그 엔진에서 제공 하는 소스 문서에 대 한 변경 내용을 Visual Studio에 알리는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는이 인터페이스를 구현 하 여 소스 코드를 변경할 수 있도록 지원 합니다. 이 인터페이스는 일반적으로 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현 하는 동일한 개체에서 구현 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 메서드를 호출 하 여이 인터페이스를 가져옵니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> . <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>메서드를 호출 하 여 인터페이스를 가져옵니다 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> . <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>인터페이스는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 메서드를 호출 하 여 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocumentTextEvents2` .

|메서드|설명|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|전체 문서가 소멸 되었음을 나타냅니다.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|텍스트를 문서에 삽입 했음을 디버그 패키지에 알립니다.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|문서에서 텍스트가 제거 되었음을 디버그 패키지에 알립니다.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|문서에서 텍스트가 대체 되었음을 디버그 패키지에 알립니다.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|문서에서 텍스트 특성이 업데이트 되었음을 디버그 패키지에 알립니다.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|문서 특성이 업데이트 되었음을 이벤트를 수신자에 게 알립니다.|

## <a name="remarks"></a>설명
 자체 문서를 제공 하는 디버그 엔진 에서만 인터페이스를 활용 `IDebugDocumentTextEvent2` 합니다. 이에 대 한 예는 스크립팅 디버그 엔진입니다. 스크립트를 해석 하는 과정에서 디스크 파일에 없는 새 소스 코드를 생성할 수 있으며,이는 DE에만 알려집니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
