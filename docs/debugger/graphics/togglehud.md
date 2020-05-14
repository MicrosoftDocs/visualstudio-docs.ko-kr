---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848466"
---
# <a name="togglehud"></a>ToggleHUD
그래픽 진단 *HUD*(Head-Up Display) 오버레이를 설정하거나 해제합니다.

## <a name="syntax"></a>구문

```C++
void ToggleHUD();
```

## <a name="remarks"></a>설명
 그래픽 진단 HUD가 그래픽 진단에서 실행 중인 앱의 왼쪽 위에 표시됩니다. 여기에는 앱 및 그래픽 정보 캡처에 대한 런타임 정보, [AddMessage](addmessage.md) 멤버 함수를 호출하여 추가되는 메시지가 표시됩니다.

 HUD를 설정하거나 해제하려면 그래픽 정보를 캡처하지 않아도 됩니다. 즉, `VsgDbg` 클래스의 인스턴스를 통해 설정/해제할 수 있지만 [Init](init.md) 멤버 함수를 먼저 호출할 필요는 없습니다.