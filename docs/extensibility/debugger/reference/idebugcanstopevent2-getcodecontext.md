---
description: 이 이벤트의 위치를 설명 하는 코드 컨텍스트를 가져옵니다.
title: 'IDebugCanStopEvent2:: GetCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29863a16d59528e86f7c5a3449e7c321b2dcaf9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173539"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
이 이벤트의 위치를 설명 하는 코드 컨텍스트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>매개 변수
`ppCodeContext`\
제한이 현재 코드 위치를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 대부분의 런타임 아키텍처에서 코드 컨텍스트는 프로그램의 실행 스트림에서 특정 명령을 가리키는 주소로 간주할 수 있습니다.

 소스 코드 줄을 향하는 문서 컨텍스트를 가져오려면 [Getdocumentcontext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
