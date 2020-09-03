---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26387618b320ed56ce754e64698fbb1c4223f2f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724315"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
는 코어 서버를 선택 하 고 상호 작용 하는 포트 공급자에 대 한 지원을 제공 합니다.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는 사용할 핵심 서버를 선택할 수 있도록이 인터페이스를 구현 합니다.

## <a name="methods"></a>메서드
 다음 표에서는 **IDebugPortSupplierEx2**의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|포트 공급자에 대 한 핵심 서버를 설정 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
