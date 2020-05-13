---
title: 아이디버그프로그램2::에이넘코드패스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723037"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
소스 파일에서 지정된 위치에 대한 코드 경로 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>매개 변수
`pszHint`\
【인】 IDE의 **소스** 또는 **디스어셈블리** 뷰의 커서 아래에 있는 단어입니다.

`pStart`\
【인】 현재 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

`pFrame`\
【인】 현재 중단점과 연결된 스택 프레임을 나타내는 [IDebugStackFrameFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.

`fSource`\
【인】 비영`TRUE`() 소스 **뷰에** 있는`FALSE`경우, 또는 0 () **디스어셈블리 뷰에** 있는 경우.

`ppEnum`\
【아웃】 코드 경로 목록을 포함하는 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 개체를 반환합니다.

`ppSafety`\
【아웃】 선택한 코드 경로를 건너뛰는 경우 중단점으로 설정할 추가 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환합니다. 예를 들어 단락된 부울 식의 경우 이러한 일이 발생할 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 코드 경로는 프로그램 실행의 현재 지점에 도달하기 위해 호출된 메서드 또는 함수의 이름을 설명합니다. 코드 경로 목록은 호출 스택을 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
