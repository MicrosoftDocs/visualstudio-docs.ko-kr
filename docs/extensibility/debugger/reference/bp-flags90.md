---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738052"
---
# <a name="bp_flags90"></a>BP_FLAGS90
선택적 플래그의 유효한 값을 열거 합니다. 선택적 플래그는 중단점을 설정할 때 추가 정보를 지정 하는 데 사용할 수 있습니다. 이 열거형은 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 열거형을 확장 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>필드
`BP90_FLAG_NONE`\
중단점 플래그를 지정 하지 않습니다.

`BP90_FLAG_MAP_DOCPOSITION`\
디버그 엔진 (DE)이 문서 위치를 사용 하 여 중단점을 매핑하도록 지정 합니다. 이는 ASP (Active Server 페이지)와 같은 스크립트 지향 소스 파일에 설정 된 중단점에만 적용 됩니다.

`BP90_FLAG_DONT_STOP`\
디버그 엔진에서 중단점을 처리 해야 하지만 디버그 엔진이 궁극적으로이를 중지 해서는 안 됨을 지정 합니다. 즉, [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 이벤트 개체를 전송 해서는 안 됩니다. 이 플래그는 주로 추적 지점과 함께 사용 하도록 설계 되었습니다.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
네이티브 디버그 엔진에서 단계별 상태를 지워야 하는지 여부를 확인 하는 데 사용 됩니다. 추적 지점에서 매크로를 실행 하는 경우 BP90_FLAG_DONT_STOP 설정 되지 않으므로 BP90_FLAG_DONT_STOP와 다릅니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg90

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
