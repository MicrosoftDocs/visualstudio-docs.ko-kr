---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896357"
---
# <a name="addmessage"></a>AddMessage
그래픽 진단 *HUD*(Head-Up Display)에 사용자 지정 메시지를 추가합니다.

## <a name="syntax"></a>구문

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>매개 변수
 `szMessage` HUD에 추가할 메시지입니다.

## <a name="remarks"></a>설명
 그래픽 진단 HUD가 그래픽 진단에서 실행 중인 앱의 왼쪽 위에 표시됩니다. 여기에는 앱 및 그래픽 정보 캡처에 대한 정보, 이 함수를 호출하여 추가되는 메시지가 표시됩니다.

 HUD에 메시지를 추가하려면 그래픽 정보를 캡처하지 않아도 됩니다. 즉, `VsgDbg` 클래스의 인스턴스를 통해 메시지를 추가할 수 있지만 [Init](init.md) 멤버 함수가 먼저 호출되지는 않습니다. 메시지는 HUD에만 표시되고 그래픽 로그 파일에는 기록되지 않습니다.