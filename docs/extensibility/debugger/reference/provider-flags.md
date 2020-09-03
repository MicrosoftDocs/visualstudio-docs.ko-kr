---
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2333b62f21aa7b2b2bc70bddb50cbb3983cedf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713814"
---
# <a name="provider_flags"></a>PROVIDER_FLAGS
프로그램 공급자에서 가져올 desired 속성을 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="fields"></a>필드
 `PFLAG_NONE`\
 플래그가 지정 되지 않았습니다.

 `PFLAG_REMOTE_PORT`\
 호출자가와 다른 컴퓨터의 프로그램 목록을 원합니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

 `PFLAG_DEBUGGEE`\
 현재이 인스턴스에서 프로세스를 디버깅 하는 중입니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 는 디버깅 중인 프로그램에 연결 되었지만 실행 되지 않았습니다.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 는 이벤트를 감시 합니다.

 `PFLAG_GET_PROGRAM_NODES`\
 호출자는 `ProgramNodes` [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 구조체의 필드를 원합니다.

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 호출자는 `fIsTheDebuggerPresent` 구조체의 필드를 원합니다 `PROVIDER_PROCESS_DATA` .

## <a name="remarks"></a>설명
 이러한 플래그는 다음 메서드에 전달 됩니다.

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
