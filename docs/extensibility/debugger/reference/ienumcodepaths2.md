---
title: 아이넘코드패스2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717724"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
이 인터페이스는 코드 경로 목록을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE버그 엔진(DE)은 코드 경로 목록을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 얻으려면 [EnumCodePaths를 호출합니다.](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumCodePaths2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|열거 순서에서 지정된 수의 코드 경로를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|열거 순서에서 지정된 수의 코드 경로를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|열거형의 코드 경로 수를 가져옵니다.|

## <a name="remarks"></a>설명
 코드 경로는 프로그램의 분기점 또는 함수 호출을 나타냅니다. 코드 경로 목록은 코드 실행이 수행된 경로를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
