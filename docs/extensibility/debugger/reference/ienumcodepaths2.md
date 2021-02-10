---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69a65488d38fe2562392be152e448369ff081915
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962160"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
이 인터페이스는 코드 경로 목록을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)은이 인터페이스를 구현 하 여 코드 경로 목록을 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Enumcodepaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumCodePaths2` .

|메서드|Description|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|열거형 시퀀스에서 지정 된 수의 코드 경로를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|열거형 시퀀스에서 지정 된 수의 코드 경로를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|열거자의 코드 경로 수를 가져옵니다.|

## <a name="remarks"></a>설명
 코드 경로는 프로그램의 분기 또는 함수 호출을 나타냅니다. 코드 경로 목록은 코드 실행이 수행 된 경로를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
