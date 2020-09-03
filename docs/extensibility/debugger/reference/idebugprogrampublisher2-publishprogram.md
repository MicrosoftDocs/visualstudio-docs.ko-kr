---
title: IDebugProgramPublisher2::P ublishProgram | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721679"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
이 메서드는 디버그 엔진 (DEs) 및 세션 디버그 관리자에 사용할 수 있는 프로그램을 만듭니다.

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
진행 이 프로그램을 시작 하거나 연결할 수 있는 DEs의 Guid 배열입니다.

`szFriendlyName`\
진행 프로그램의 친숙 한 이름입니다 (사용자에 게 표시 되는 메뉴 또는 대화 상자에 표시).

`pDebuggeeInterface`\
[in] `IUnknown` 프로그램에 대 한 인터페이스입니다 .이 값은 프로그램을 고유 하 게 식별 하는 쿠키로 사용 됩니다 .이 값은 프로그램을 "게시 취소" 하는 데 사용 됩니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 프로그램을 디버깅에 더 이상 사용할 수 없게 하려면 [Unpublishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)을 호출 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
