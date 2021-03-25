---
description: 이 프로그램을 디버그할 수 있는 모든 가능한 디버그 엔진 (DE)의 Guid를 반환 합니다.
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a49a0590a1ec2f0b0e7d2be59fe2161b438154a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084209"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
이 프로그램을 디버그할 수 있는 모든 가능한 디버그 엔진 (DE)의 Guid를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>매개 변수
`celtBuffer`\
진행 반환할 대상 Guid 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgguidEngines` .

`rgguidEngines`\
[in, out] 채워질 끝 Guid의 배열입니다.

`pceltEngines`\
제한이 반환 되는 실제 DE Guid 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`버퍼가 충분히 크지 않은 경우 [c + +] 또는 [c #] 0x8007007A를 반환 합니다.

## <a name="remarks"></a>설명
 엔진 수를 확인 하려면 `celtBuffer` 매개 변수를 0으로 설정 하 고 `rgguidEngines` 매개 변수를 null 값으로 설정 하 여이 메서드를 한 번 호출 합니다. 이 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 는 (c #의 경우 0X8007007A)를 반환 하 고 `pceltEngines` 매개 변수는 필요한 버퍼 크기를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
