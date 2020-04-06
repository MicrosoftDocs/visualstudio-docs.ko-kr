---
title: 메시지 유형 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714496"
---
# <a name="messagetype"></a>MESSAGETYPE
메시지 유형 및 이유를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>필드
 `MT_OUTPUTSTRING`\
 메시지를 출력 창으로 보내야 음을 나타냅니다. 이 값은 `MT_MESSAGEBOX`에서 상호 배타적입니다.

 `MT_MESSAGEBOX`\
 메시지를 메시지 상자에 표시해야 함을 나타냅니다. 이 값은 `MT_OUTPUTSTRING`에서 상호 배타적입니다.

 `MT_TYPE_MASK`\
 메시지의 대상을 격리하는 마스크 값입니다.

 `MT_REASON_EXCEPTION`\
 예외의 결과로 메시지 상자가 표시되고 있음을 나타냅니다. 이 값은 `MT_REASON_TRACEPOINT`에서 상호 배타적입니다.

 `MT_REASON_TRACEPOINT`\
 추적 점을 누르면 메시지 상자가 표시되고 있음을 나타냅니다. 이 값은 에 `MT_REASON_EXCEPTION`대해 상호 배타적입니다.

 `MT_REASON_MASK`\
 메시지가 표시되는 이유를 격리하는 마스크 값입니다.

## <a name="remarks"></a>설명
 이러한 값은 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) 및 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) 메서드에서 반환 됩니다.

 이유 값 중 하나는 비트를 `OR`사용하여 출력 대상 값 중 하나와 결합할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
