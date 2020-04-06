---
title: 아이디버그문서텍스트사건2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731373"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
이 인터페이스는 디버그 엔진에서 제공하는 원본 문서의 변경 내용을 Visual Studio에 알리는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 소스 코드를 변경하는 것을 지원하기 위해 이 인터페이스를 구현합니다. 이 인터페이스는 일반적으로 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 구현하는 동일한 개체에서 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]을 사용하계 는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 메서드에 대한 호출을 통해 이 인터페이스를 가져옵니다. 인터페이스는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> 메서드에 대한 호출에서 가져옵니다. 인터페이스는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 메서드를 호출하여 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugDocumentTextEvents2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|전체 문서가 소멸되었음을 나타냅니다.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|텍스트가 문서에 삽입되었음을 디버그 패키지에 지정합니다.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|문서에서 텍스트가 제거되었음을 디버그 패키지에 지정합니다.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|문서에서 텍스트가 대체되었음을 디버그 패키지에 보온합니다.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|문서에서 텍스트 특성이 업데이트되었음을 디버그 패키지에 지정합니다.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|문서 특성이 업데이트되었음을 수신자에게 보전합니다.|

## <a name="remarks"></a>설명
 자체 문서를 제공하는 디버그 엔진만 인터페이스를 `IDebugDocumentTextEvent2` 활용할 수 있습니다. 이 것의 예는 스크립팅 디버그 엔진입니다. 스크립트를 해석하는 과정에서 디스크 파일에 없는 새 소스 코드를 생성할 수 있으며 DE에만 알려져 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
