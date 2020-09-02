---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731607"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
소스 파일에서 문자 오프셋으로 위치를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 IDE에서 구현 되며 디버그 엔진에서 사용 됩니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocumentPositionOffset2` .

|메서드|설명|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|현재 문서 위치에 대 한 범위를 검색 합니다.|

## <a name="remarks"></a>설명
 그러면 [Getrange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) 와 동일한 정보를 반환 하지만 `char` 문서의 시작 부분에서 오프셋을 반환 합니다. 이는 일반적으로 반환 되는 줄 및 열 정보가 아니라 1 차원 문자의 디스크에 존재 하는 것과 같은 문서를 제공 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
