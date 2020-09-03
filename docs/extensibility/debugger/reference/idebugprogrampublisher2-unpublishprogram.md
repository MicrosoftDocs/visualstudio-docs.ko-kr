---
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721592"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
프로그램을 디버그할 수 없게 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>매개 변수
`pDebuggeeInterface`\
진행 `IUnknown` 프로그램에 대 한 인터페이스입니다. 이 값은 # [program](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) 메서드에 제공 되는 값과 같으며 제거 되는 프로그램을 고유 하 게 식별 합니다. 즉, 쿠키로 사용 됩니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진 및 세션 디버그 관리자가 프로그램을 사용할 수 있도록 하려면 # [program](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) 메서드를 사용 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
