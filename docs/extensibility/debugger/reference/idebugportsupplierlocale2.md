---
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d59f46bdde06addf5454700eb45e64c3b452d78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874285"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
포트 공급자에 대 한 로캘을 지원 합니다.

## <a name="syntax"></a>구문

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 로캘을 설정 합니다.

## <a name="methods"></a>메서드
 다음 표에서는 **IDebugPortSupplierLocale2** 의 메서드를 보여 줍니다.

|메서드|Description|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|포트 공급자에 대 한 로캘을 설정 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
