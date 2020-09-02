---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144571"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단 *HUD*(Head-Up Display) 오버레이를 설정하거나 해제합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>설명  
 그래픽 진단 HUD가 그래픽 진단에서 실행 중인 앱의 왼쪽 위에 표시됩니다. 여기에는 앱 및 그래픽 정보 캡처에 대한 런타임 정보, [AddMessage](../debugger/addmessage.md) 멤버 함수를 호출하여 추가되는 메시지가 표시됩니다.  
  
 HUD를 설정하거나 해제하려면 그래픽 정보를 캡처하지 않아도 됩니다. 즉, `VsgDbg` 클래스의 인스턴스를 통해 설정/해제할 수 있지만 [Init](../debugger/init.md) 멤버 함수를 먼저 호출할 필요는 없습니다.
