---
title: '[이디버그디스어셈블리스트림2::검색 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732077"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
디스어셈블리 스트림에서 읽기 포인터를 지정된 위치에 대해 지정된 수의 명령을 이동합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>매개 변수
`dwSeekStart`\
【인】 검색 프로세스를 시작할 상대 위치를 지정하는 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) 열거형의 값입니다.

`pCodeContext`\
【인】 검색 작업이 상대적인 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다. 이 매개 변수는 `dwSeekStart`  =  `SEEK_START_CODECONTEXT`다음과 같은 경우에만 사용됩니다. 그렇지 않으면 이 매개 변수는 무시되고 null 값이 될 수 있습니다.

`uCodeLocationId`\
【인】 검색 작업이 상대적인 코드 위치 식별자입니다. 이 매개 변수는 다음과 같은 경우에 `dwSeekStart`  =  `SEEK_START_CODELOCID`사용됩니다. 그렇지 않으면 이 매개 변수가 무시되고 0으로 설정할 수 있습니다. 코드 위치 식별자에 대한 설명은 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 메서드의 비고 섹션을 참조하십시오.

`iInstructions`\
【인】 에 지정된 위치를 기준으로 이동할 수 `dwSeekStart`있는 명령 수입니다. 이 값은 뒤로 이동하면 음수일 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 `S_OK`를 반환합니다. 검색 `S_FALSE` 위치가 사용 가능한 지침 목록 이외의 지점에 있는 경우 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 검색이 목록의 시작 전에 위치에 있는 경우 읽기 위치는 목록의 첫 번째 명령으로 설정됩니다. 목록이 끝난 후 참조가 위치에 있는 경우 읽기 위치는 목록의 마지막 명령으로 설정됩니다.

## <a name="see-also"></a>참조
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
