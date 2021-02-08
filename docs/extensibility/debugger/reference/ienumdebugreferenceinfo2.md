---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14b5bdc8a8be5734da765f0396fb96830042969f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842227"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
이 인터페이스는 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체를 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 메모리의 개체에 대 한 참조 지원의 일부로이 인터페이스를 구현 합니다. 참조가 지원 되는 경우에만이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 Visual Studio는 [Enumchildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 을 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugReferenceInfo2` .

|메서드|Description|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|열거형 시퀀스에서 지정 된 수의 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|열거형 시퀀스에서 지정 된 수의 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|열거자의 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체 수를 가져옵니다.|

## <a name="remarks"></a>설명
 참조는 기본적으로 형식 및 주소 이지만 속성은 이름, 형식 및 주소입니다. 참조는 참조 하는 개체가 메모리에 존재 하는 한 지속 됩니다. 자세한 내용은 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
