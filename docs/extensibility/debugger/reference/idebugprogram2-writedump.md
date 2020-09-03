---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722730"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
덤프를 파일에 씁니다.

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
진행 덤프 형식 (예: short 또는 long)을 지정 하는 덤프 [유형](../../../extensibility/debugger/reference/dumptype.md) 열거형의 값입니다.

`pszDumpUrl`\
진행 덤프를 쓸 URL입니다. 일반적으로이 형식은 형식이 며 `file://c:\path\filename.ext` 유효한 모든 URL 일 수 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 프로그램 덤프에는 일반적으로 현재 스택 프레임, 스택 자체, 프로그램에서 실행 중인 스레드 목록 및 프로그램이 소유 하는 모든 메모리가 포함 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
