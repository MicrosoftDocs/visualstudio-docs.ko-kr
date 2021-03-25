---
description: 소스 파일에서 지정 된 위치에 대 한 코드 경로 목록을 검색 합니다.
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 057089c8c7b68fd1109c31bbfc0014f49a71368c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076045"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
소스 파일에서 지정 된 위치에 대 한 코드 경로 목록을 검색 합니다.

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
진행 IDE의 **소스** 또는 **디스어셈블리** 뷰에서 커서 아래의 단어입니다.

`pStart`\
진행 현재 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

`pFrame`\
진행 현재 중단점과 연결 된 스택 프레임을 나타내는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.

`fSource`\
진행 `TRUE` **소스** 뷰에는 0이 아닌 ()이 고, 디스어셈블리 뷰에서는 0 ( `FALSE` )입니다. 

`ppEnum`\
제한이 코드 경로 목록을 포함 하는 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 개체를 반환 합니다.

`ppSafety`\
제한이 선택한 코드 경로를 건너뛰는 경우 중단점으로 설정할 추가 코드 컨텍스트를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다. 이는 short-circuit 부울 식의 경우에 발생할 수 있습니다 (예:).

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 코드 경로는 프로그램 실행에서 현재 지점으로 가져오기 위해 호출 된 메서드 또는 함수의 이름을 설명 합니다. 코드 경로 목록은 호출 스택을 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
