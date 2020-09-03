---
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733024"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
서버에 디버그 엔진의 인스턴스를 만듭니다.

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
진행 매개 변수에 지정 된 CLSID를 구현 하는 dll의 경로 `clsidObject` 입니다. 인 경우 `NULL` COM의 `CoCreateInstance` 함수가 호출 됩니다.

`wLangId`\
진행 디버그 엔진의 로캘입니다. [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) 메서드를 호출 하지 않아야 하는 경우에는 0이 될 수 있습니다.

`clsidObject`\
진행 만들 디버그 엔진의 CLSID입니다.

`riid`\
진행 클래스 개체에서 검색할 특정 인터페이스의 인터페이스 ID입니다.

`ppvObject`\
[out] `IUnknown` 인스턴스화된 개체의 인터페이스입니다. 이 개체를 원하는 인터페이스로 캐스팅 하거나 마샬링합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
