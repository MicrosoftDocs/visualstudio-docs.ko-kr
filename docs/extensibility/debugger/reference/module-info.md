---
title: MODULE_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714309"
---
# <a name="module_info"></a>MODULE_INFO
특정 모듈(DLL, EXE 또는 어셈블리)에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>멤버
 `dwValidFields`\
 입력할 필드를 지정하는 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 열거형의 플래그 조합입니다.

 `m_bstrName`\
 모듈 이름입니다.

 `m_bstrUrl`\
 모듈 URL입니다.

 `m_bstrVersion`\
 모듈 버전입니다.

 `m_bstrDebugMessage`\
 모듈에 대한 선택적 메시지(예: "기호를 로드할 수 없습니다.").

 `m_addrLoadAddress`\
 모듈 로드 주소입니다.

 `m_addrPreferredLoadAddress`\
 모듈의 기본 로드 주소입니다.

 `m_dwSize`\
 모듈 크기입니다.

 `m_dwLoadOrder`\
 모듈 로드 순서입니다.

 `m_TimeStamp`\
 기호 파일이 마지막으로 수정된 시간입니다.

 `m_bstrUrlSymbolLocation`\
 모듈에 지정된 기호 파일의 위치(예:\\".")입니다. 모듈의 기호를 찾기 위한 시작 위치로 사용됩니다.

 `m_dwModuleFlags`\
 모듈을 설명하는 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) 열거형의 플래그 조합입니다.

## <a name="remarks"></a>설명
 이 구조는 채워진 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 메서드에 전달됩니다.

 이 구조는 모듈 창에 나열된 각 모듈에 **해당합니다.**

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
