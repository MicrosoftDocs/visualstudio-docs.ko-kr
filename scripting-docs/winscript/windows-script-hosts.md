---
title: Windows 스크립트 호스트 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51053dec1f8362aa9eef80e4867d2f92a06454cb
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835331"
---
# <a name="windows-script-hosts"></a>Windows 스크립트 호스트
Microsoft Windows 스크립트 호스트를 구현할 때, 호스트에서 다음을 수행하는 경우에 한해 스크립팅 엔진이 기본 스레드의 컨텍스트에서 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스만 호출한다고 간주해도 됩니다.  
  
- 기본 스레드를 선택합니다(일반적으로 메시지 루프를 포함하는 스레드).  
  
- 기본 스레드에서 스크립팅 엔진을 인스턴스화합니다.  
  
- [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 및 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)의 경우와 같이 특별히 허용된 경우를 제외하고 기본 스레드에서만 스크립팅 엔진 메서드를 호출합니다.  
  
- 기본 스레드에서만 스크립팅 엔진의 디스패치 개체를 호출합니다.  
  
- 창 핸들이 제공되는 경우 메시지 루프가 기본 스레드에서 실행되는지 확인합니다.  
  
- 호스트 개체의 개체가 기본 스레드의 소스 이벤트만 모델링하는지 확인합니다.  
  
  이러한 규칙 다음에는 단일 스레드 호스트가 자동으로 옵니다. 위에 설명한 제한된 모델은 적당히 느슨하도록 의도되었으므로 호스트가 다른 스레드(CTRL+BREAK 처리기 등으로 시작)에서 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)를 호출하여 중단 스크립트를 중단하거나 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)을 사용하여 새 스레드에 스크립트를 복제할 수 있습니다.  
  
## <a name="remarks"></a>설명  
 이러한 제한 사항은 자유 스레드 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스와 자유 스레드 개체 모델을 구현하도록 선택하는 호스트에 적용되지 않습니다. 이러한 호스트에서는 제한 없이 모든 스레드의 [IActiveScript](../winscript/reference/iactivescript.md) 인터페이스를 사용할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스](../winscript/windows-script-interfaces.md)