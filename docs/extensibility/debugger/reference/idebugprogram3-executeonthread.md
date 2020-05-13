---
title: 아이디버그프로그램3::실행온스레드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722652"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
디버거 프로그램을 실행합니다. 프로그램을 실행할 때 사용자가 보고 있는 스레드에 대한 디버거 정보를 제공하기 위해 스레드가 반환됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
【인】 [IDebugThread2 개체입니다.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 디버거가 중지한 후 실행을 다시 시작할 수 있는 세 가지 방법이 있습니다.

- 실행: 이전 단계를 취소하고 다음 중단점까지 실행합니다.

- 단계: 이전 단계를 취소하고 새 단계가 완료될 때까지 실행합니다.

- 계속: 다시 실행하고 이전 단계를 활성 상태로 둡니다.

  `ExecuteOnThread` 전달된 스레드는 취소할 단계를 결정할 때 유용합니다. 스레드를 모르는 경우 실행 실행을 실행하면 모든 단계가 취소됩니다. 스레드에 대한 지식으로 활성 스레드의 단계를 취소하기만 하면 됩니다.

## <a name="see-also"></a>참조
- [실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
