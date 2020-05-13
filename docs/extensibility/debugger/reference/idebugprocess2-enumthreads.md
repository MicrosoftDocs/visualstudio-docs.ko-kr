---
title: IDebugProcess2::에이넘스레드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724063"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
프로세스에서 실행 중인 모든 스레드 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
【아웃】 프로세스의 모든 프로그램의 모든 스레드 목록을 포함하는 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 각 프로그램에서 실행 중인 스레드를 등록 한 다음 스레드의 프로세스 보기로 결합 합니다. 단일 스레드는 여러 프로그램에서 실행될 수 있습니다. 이 메서드는 해당 스레드를 한 번만 등록합니다.

 이 메서드는 중복 없이 프로세스의 스레드 목록을 제공합니다. 그렇지 않으면 특정 프로그램에서 실행 중인 스레드를 열거하려면 [EnumThreads 메서드를](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 사용합니다.

## <a name="see-also"></a>참조
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
