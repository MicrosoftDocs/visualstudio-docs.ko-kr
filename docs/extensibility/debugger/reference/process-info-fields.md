---
title: PROCESS_INFO_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714006"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
프로세스에 대해 검색할 정보의 종류를 지정했습니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조의 `bstrFileName` 필드를 초기화/사용합니다.

 `PIF_BASE_NAME`\
 `PROCESS_INFO` 구조의 `bstrBaseName` 필드를 초기화/사용합니다.

 `PIF_TITLE`\
 `PROCESS_INFO` 구조의 `bstrTitle` 필드를 초기화/사용합니다.

 `PIF_PROCESS_ID`\
 `PROCESS_INFO` 구조의 `ProcessId` 필드를 초기화/사용합니다.

 `PIF_SESSION_ID`\
 `PROCESS_INFO` 구조의 `dwSessionId` 필드를 초기화/사용합니다.

 `PIF_ATTACHED_SESSION_NAME`\
 `PROCESS_INFO` 구조의 `bstrAttachedSessionName` 필드를 초기화/사용합니다.

 `PIF_CREATION_TIME`\
 `PROCESS_INFO` 구조의 `CreationTime` 필드를 초기화/사용합니다.

 `PIF_FLAGS`\
 `PROCESS_INFO` 구조의 `Flags` 필드를 초기화/사용합니다.

 `PIF_ALL`\
 모든 필드를 채웁니다.

## <a name="remarks"></a>설명
 [getInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 메서드에 전달되어 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조의 필드를 초기화할 필드를 나타냅니다.

 또한 `Fields` `PROCESS_INFO` 구조의 필드에서 사용되는 필드와 유효한 필드를 나타내는 데 사용됩니다.

 이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
