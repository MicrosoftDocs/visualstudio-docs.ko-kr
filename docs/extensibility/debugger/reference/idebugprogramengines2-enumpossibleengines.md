---
title: IDebugProgramEngines2::에이넘가능한엔진 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722436"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
이 프로그램을 디버깅할 수 있는 가능한 모든 DEBug 엔진(DE)에 대한 GUID를 반환합니다.

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
【인】 반환할 DE GUID의 수입니다. 또한 배열의 최대 크기를 지정합니다. `rgguidEngines`

`rgguidEngines`\
【인, 아웃】 채울 DE GUID의 배열입니다.

`pceltEngines`\
【아웃】 반환되는 실제 DE GUID 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 버퍼가 충분히 크지 않은 경우 [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 또는 [C#] 0x8007007A를 반환합니다.

## <a name="remarks"></a>설명
 얼마나 많은 엔진이 있는지 확인하려면 매개 변수를 `celtBuffer` 0으로 설정하고 `rgguidEngines` 매개 변수를 null 값으로 설정하여 이 메서드를 한 번 호출합니다. 이렇게 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 하면(C#의 경우 0x8007007A) `pceltEngines` 매개 변수가 버퍼의 필요한 크기를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
