---
title: IDebugProgram2::쓰기 덤프 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722730"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
파일에 덤프를 씁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>매개 변수
`DumpType`\
【인】 짧거나 긴 예를 들어 덤프 유형을 지정하는 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) 열거형의 값입니다.

`pszDumpUrl`\
【인】 덤프를 작성하는 URL입니다. 일반적으로 이 형식은 `file://c:\path\filename.ext`의 모양이지만 유효한 URL일 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 프로그램 덤프에는 일반적으로 현재 스택 프레임, 스택 자체, 프로그램에서 실행 중인 스레드 목록 및 프로그램이 소유하는 모든 메모리가 포함됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
