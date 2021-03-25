---
description: 프로세스에 대해 검색할 정보의 종류를 지정 합니다.
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1f779352ce6b1217cd8af1e87988cb165b2dddc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079633"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
프로세스에 대해 검색할 정보의 종류를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>필드
 `PIF_FILE_NAME`\
 `bstrFileName` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조체의 필드를 초기화/사용 합니다.

 `PIF_BASE_NAME`\
 `bstrBaseName`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_TITLE`\
 `bstrTitle`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_PROCESS_ID`\
 `ProcessId`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_SESSION_ID`\
 `dwSessionId`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_ATTACHED_SESSION_NAME`\
 `bstrAttachedSessionName`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_CREATION_TIME`\
 `CreationTime`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_FLAGS`\
 `Flags`구조체의 필드를 초기화/사용 `PROCESS_INFO` 합니다.

 `PIF_ALL`\
 모든 필드를 채웁니다.

## <a name="remarks"></a>설명
 초기화할 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조체의 필드를 나타내기 위해 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 메서드에 전달 됩니다.

 또한 `Fields` 구조체의 필드에 사용 `PROCESS_INFO` 되어 사용 되는 필드와 유효한 필드를 표시 합니다.

 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
