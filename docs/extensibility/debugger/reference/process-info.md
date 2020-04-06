---
title: PROCESS_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713878"
---
# <a name="process_info"></a>PROCESS_INFO
프로세스에 대한 정보를 포함합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>멤버
 `Fields`\
 채워지는 필드를 지정하는 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) 열거형의 플래그 조합입니다.

 `bstrFileName`\
 프로세스의 전체 경로 이름입니다. 매개 변수를 `GN_FILENAME`사용하여 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 메서드를 호출하는 것과 같습니다.

 `bstrBaseName`\
 프로세스의 파일 이름 및 확장입니다. 매개 변수를 `IDebugProcess2::Getname` `GN_BASENAME`사용하여 메서드를 호출하는 것과 같습니다.

 `bstrTitle`\
 프로세스의 제목(있는 경우)입니다. 매개 변수를 `IDebugProcess2::Getname` `GN_TITLE`사용하여 메서드를 호출하는 것과 같습니다.

 `ProcessId`\
 프로세스를 식별하는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다. [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) 메서드를 호출 하는 것과 같습니다.

 `dwSessionId`\
 이 프로세스가 실행 중인 디버그 세션의 식별자입니다.

 `bstrAttachedSessionName`\
 첨부된 세션 이름입니다. [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) 메서드를 호출 하는 것과 같습니다.

 `CreationTime`\
 프로세스가 만들어진 시간입니다.

 `Flags`\
 프로세스의 속성을 지정하는 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) 열거형의 플래그 조합입니다.

## <a name="remarks"></a>설명
 이 구조는 채워진 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 메서드에 전달됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
