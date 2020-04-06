---
title: IDebugWindows컴퓨터 포트2::GetComputerInfo | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 420e963b70846b4d7251c3f1b6c7f5b224c9fdb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718267"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
디버거가 실행 중인 컴퓨터에 대한 정보를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetComputerInfo(
   COMPUTER_INFO * pInfo
);
```

```csharp
public int GetComputerInfo(
   out COMPUTER_INFO[] pInfo
);
```

## <a name="parameters"></a>매개 변수
`pInfo`\
【아웃】 컴퓨터 정보가 포함된 구조를 참조합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)
- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)
