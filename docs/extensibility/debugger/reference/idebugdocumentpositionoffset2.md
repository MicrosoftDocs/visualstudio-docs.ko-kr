---
title: 아이디버그문서배치오프셋2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731607"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
소스 파일의 위치를 문자 오프셋으로 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 IDE에 의해 구현되고 디버그 엔진에 의해 사용됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugDocumentPositionOffset2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|현재 문서 위치의 범위를 검색합니다.|

## <a name="remarks"></a>설명
 이렇게 하면 [GetRange와](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) 동일한 `char` 정보가 반환되지만 문서의 시작 부분에서 오프셋이 됩니다. 이렇게 하면 일반적으로 반환되는 선 및 열 정보 대신 디스크에 있는 문서, 즉 1차원 문자 배열과 같은 문서가 표시됩니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
