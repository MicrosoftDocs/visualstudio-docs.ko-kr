---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717135"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
사용자 지정 특성을 열거 합니다.

## <a name="syntax"></a>Syntax

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 인터페이스를 통해 사용자 지정 특성을 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
- [Enumcustomattributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugCustomAttributes` .

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|열거형 시퀀스에서 지정 된 수의 사용자 지정 특성을 검색 합니다.|
|[skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|열거형 시퀀스에서 지정 된 수의 사용자 지정 특성을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|열거자에 있는 사용자 지정 특성의 수를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
