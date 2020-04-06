---
title: 아이디버그포트공급업체로컬레2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98444ca60937d40262c92d89b8a6c48ed1a0b7ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724294"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
포트 공급자에 대 한 로캘 지원을 제공 합니다.

## <a name="syntax"></a>구문

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 로캘을 설정합니다.

## <a name="methods"></a>메서드
 다음 표에서는 **IDebugPortSupplierLocale2의 메서드를**보여 주며 있습니다.

|방법|설명|
|------------|-----------------|
|[Setlocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|포트 공급자에 대한 로캘을 설정합니다.|

## <a name="requirements"></a>요구 사항
 헤더: 포트프리브.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
