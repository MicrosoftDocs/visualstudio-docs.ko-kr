---
title: 아이디버그소스서버모듈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719919"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
PDB 파일에 포함된 원본 서버 정보를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 디버거 엔진에 의해 구현되고 디버거 UI에서 사용됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugSourceServerModule`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|소스 서버 정보의 배열을 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
