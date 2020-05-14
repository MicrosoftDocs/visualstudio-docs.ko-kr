---
title: 아이디버그코어서버3:만들기인스턴스인서버 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733024"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
서버에서 디버그 엔진의 인스턴스를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>매개 변수
`szDll`\
【인】 매개 변수에 지정된 CLSID를 구현하는 dll에 대한 경로입니다. `clsidObject` 이 `NULL`경우 COM의 `CoCreateInstance` 함수가 호출됩니다.

`wLangId`\
【인】 디버그 엔진의 로캘입니다. [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) 메서드를 호출하지 않아야 하는 경우 0이 될 수 있습니다.

`clsidObject`\
【인】 디버그 엔진의 CLSID를 작성합니다.

`riid`\
【인】 클래스 개체에서 검색할 특정 인터페이스의 인터페이스 ID입니다.

`ppvObject`\
【아웃】 `IUnknown` 인스턴스화된 개체의 인터페이스입니다. 이 개체를 원하는 인터페이스로 캐스팅하거나 마샬링합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
