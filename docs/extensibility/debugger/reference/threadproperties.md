---
title: 스레드 속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713428"
---
# <a name="threadproperties"></a>THREADPROPERTIES
스레드의 속성을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>멤버
 `dwFields`\
 이 구조의 어떤 필드가 유효한지 설명하는 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) 열거형의 플래그 조합입니다.

 `dwThreadId`\
 스레드 ID입니다.

 `dwSuspendCount`\
 스레드 일시 중단 카운트입니다.

 `dwThreadState`\
 스레드 [상태](../../../extensibility/debugger/reference/threadstate.md) 열거형의 값으로 운영 스레드의 상태를 나타냅니다.

 `bstrPriority`\
 스레드 우선 순위를 지정하는 문자열입니다. 예를 들어 "정상 이상", "정상" 또는 "시간 중요"를 예로 들 수 있습니다.

 `bstName`\
 스레드 이름입니다.

 `bstrLocation`\
 스레드 위치(일반적으로 최상위 스택 프레임)는 일반적으로 실행이 현재 중지된 메서드의 이름으로 표시됩니다.

## <a name="remarks"></a>설명
 이 구조는 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 메서드에 대 한 호출에 의해 채워져 있습니다. 이렇게 반환되는 정보는 일반적으로 **스레드** 창을 채우는 데 사용됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
