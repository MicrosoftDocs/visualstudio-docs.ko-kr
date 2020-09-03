---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722652"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
디버거 프로그램을 실행 합니다. 스레드는 프로그램을 실행할 때 사용자가 보고 있는 스레드에 디버거 정보를 제공 하기 위해 반환 됩니다.

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
진행 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버거를 중지 한 후 실행을 다시 시작할 수 있는 세 가지 방법이 있습니다.

- 실행: 이전 단계를 취소 하 고 다음 중단점까지 실행 합니다.

- 단계: 모든 이전 단계를 취소 하 고 새 단계가 완료 될 때까지 실행 합니다.

- 계속:를 다시 실행 하 고 모든 이전 단계를 활성 상태로 둡니다.

  에 전달 된 스레드는 `ExecuteOnThread` 취소할 단계를 결정할 때 유용 합니다. 스레드를 모르는 경우 실행을 실행 하면 모든 단계가 취소 됩니다. 스레드에 대 한 정보를 사용 하 여 활성 스레드의 단계를 취소 하기만 하면 됩니다.

## <a name="see-also"></a>추가 정보
- [실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
