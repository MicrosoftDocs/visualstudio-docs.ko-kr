---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3efe97518b0952c1207eac97fe9151f36c686f43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846558"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
검색할 스레드에 대 한 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_THREADPROPERTY_FIELDS { 
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
public enum enum_THREADPROPERTY_FIELDS { 
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
 `dwThreadId` [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) 구조의 필드를 초기화/사용 합니다.

 `TPF_SUSPENDCOUNT`\
 `dwSuspendCount`S 구조체의 필드를 초기화/사용 `THREADPROPERTIE` 합니다.

 `TPF_STATE`\
 `dwThreadState`S 구조체의 필드를 초기화/사용 `THREADPROPERTIE` 합니다.

 `TPF_PRIORITY`\
 `bstrPriority`S 구조체의 필드를 초기화/사용 `THREADPROPERTIE` 합니다.

 `TPF_NAME`\
 `bstrName`S 구조체의 필드를 초기화/사용 `THREADPROPERTIE` 합니다.

 `TPF_LOCATION`\
 `bstrLocation`S 구조체의 필드를 초기화/사용 `THREADPROPERTIE` 합니다.

 `TPF_ALLFIELDS`\
 모든 필드를 지정 합니다.

## <a name="remarks"></a>설명
 이러한 값은 초기화할 [threadproperties](../../../extensibility/debugger/reference/threadproperties.md) 구조의 필드를 나타내기 위해 [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) 메서드에 인수로 전달 됩니다.

 이러한 값은 `dwFields` 구조체의 멤버 에서도 사용 되며 `THREADPROPERTIES` 유효한 필드를 표시 하는 데 사용 됩니다.

 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
