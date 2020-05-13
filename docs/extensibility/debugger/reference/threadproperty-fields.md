---
title: THREADPROPERTY_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713407"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
스레드에 대한 정보를 검색할 내용을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>필드
 `TPF_ID`\
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 구조의 `dwThreadId` 필드를 초기화/사용합니다.

 `TPF_SUSPENDCOUNT`\
 `THREADPROPERTIE`S 구조의 `dwSuspendCount` 필드를 초기화/사용합니다.

 `TPF_STATE`\
 `THREADPROPERTIE`S 구조의 `dwThreadState` 필드를 초기화/사용합니다.

 `TPF_PRIORITY`\
 `THREADPROPERTIE`S 구조의 `bstrPriority` 필드를 초기화/사용합니다.

 `TPF_NAME`\
 `THREADPROPERTIE`S 구조의 `bstrName` 필드를 초기화/사용합니다.

 `TPF_LOCATION`\
 `THREADPROPERTIE`S 구조의 `bstrLocation` 필드를 초기화/사용합니다.

 `TPF_ALLFIELDS`\
 모든 필드를 지정합니다.

## <a name="remarks"></a>설명
 이러한 값은 [ThreadProperties](../../../extensibility/debugger/reference/threadproperties.md) 구조의 필드를 초기화할 필드를 나타내기 위해 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 메서드에 인수로 전달됩니다.

 이러한 값은 구조의 `dwFields` `THREADPROPERTIES` 구성원에서 사용되는 필드와 유효한 필드를 나타내는 데도 사용됩니다.

 이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
