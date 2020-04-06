---
title: 아이디버그코드컨텍스트3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734194"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
모듈 및 프로세스 인터페이스를 검색할 수 있도록 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스를 확장합니다.

## <a name="syntax"></a>구문

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진에 의해 구현되고 디버그 패키지에서 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 사용됩니다.

## <a name="methods"></a>메서드
 이 인터페이스는 인터페이스의 `IDebugCodeContext2` 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|디버그 모듈의 인터페이스에 대한 참조를 검색합니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|디버그 프로세스의 인터페이스에 대한 참조를 검색합니다.|

## <a name="remarks"></a>설명
 일반적으로 구현할 필요가 없는 선택적 인터페이스입니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
