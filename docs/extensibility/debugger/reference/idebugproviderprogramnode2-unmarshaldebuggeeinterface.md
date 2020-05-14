---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720708"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
프로세스 경계를 넘어 지정된 인터페이스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>매개 변수
`riid`\
【인】 얻을 인터페이스의 GUID.

`ppvObject`\
【아웃】 원하는 인터페이스를 구현하는 개체를 반환합니다. [C++]는 원하는 인터페이스 유형으로 직접 캐스팅할 수 있습니다. [C#] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 원하는 인터페이스를 얻기 위해 메서드를 사용합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 디버그 엔진이 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 프로세스 공간에서 실행 중이고 디버깅 중인 프로그램이 자체 프로세스 공간에서 실행중인 경우에 사용됩니다.

## <a name="see-also"></a>참조
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
