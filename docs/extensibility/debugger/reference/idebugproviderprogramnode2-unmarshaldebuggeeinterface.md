---
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1449141885a51b3557f8c626b309fcc64c7fb268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909835"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
프로세스 경계를 넘어 지정 된 인터페이스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>매개 변수
`riid`\
진행 가져올 인터페이스의 GUID입니다.

`ppvObject`\
제한이 원하는 인터페이스를 구현 하는 개체를 반환 합니다. [C + +] 원하는 인터페이스 형식으로 직접 캐스팅할 수 있습니다. [C #] 메서드를 사용 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 하 여 원하는 인터페이스를 가져옵니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 디버그 엔진이 프로세스 공간에서 실행 중이 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 고 디버깅 중인 프로그램이 자체 프로세스 공간에서 실행 되는 경우에 사용 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
