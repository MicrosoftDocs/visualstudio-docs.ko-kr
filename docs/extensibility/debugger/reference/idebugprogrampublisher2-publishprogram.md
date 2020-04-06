---
title: 아이디버그프로그램출판사2::Publish프로그램 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20de162bdc3be2cc4771c9746b13c40a1e140a96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721679"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
이 메서드는 디버그 엔진(DEs) 및 세션 디버그 관리자에 대한 프로그램을 사용할 수 있게 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>매개 변수
`Engines`\
【인】 이 프로그램을 시작하거나 연결할 수 있는 DEs용 GUID 배열입니다.

`szFriendlyName`\
【인】 프로그램의 친숙한 이름(사용자에게 표시되는 메뉴 또는 대화 상자에 나타납니다).

`pDebuggeeInterface`\
【인】 `IUnknown` 프로그램에 대한 인터페이스(이 값은 프로그램을 고유하게 식별하는 쿠키로 사용되며, 이 값은 프로그램을 "게시 취소"하는 데 사용됩니다.)

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 디버깅에 더 이상 프로그램을 사용할 수 없게 하려면 [게시 취소 프로그램](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>참조
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
