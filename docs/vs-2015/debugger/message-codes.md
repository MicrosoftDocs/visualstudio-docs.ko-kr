---
title: 메시지 코드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182958"
---
# <a name="message-codes"></a>메시지 코드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[메시지 뷰](../debugger/messages-view.md)에 표시되는 각 메시지 줄에는 'P', 'S', 's' 또는 'R' 코드가 포함됩니다. 이러한 코드에는 다음과 같은 의미가 있습니다.  
  
|코드|의미|  
|----------|-------------|  
|P|**PostMessage** 함수를 사용하여 메시지를 큐에 게시했습니다. 메시지의 최종 처리와 관련된 정보를 사용할 수 없습니다.|  
|S|**SendMessage** 함수를 사용하여 메시지를 보냈습니다. 받는 사람이 메시지를 처리하고 반환할 때까지 보낸 사람은 제어 권한을 다시 얻지 못한다는 것을 나타냅니다. 따라서 받는 사람은 다시 반환 값을 보낸 사람에게 전달할 수 있습니다.|  
|s|메시지를 보냈지만 보안 때문에 반환 값에 액세스하지 못합니다.|  
|R|각 'S' 줄에는 메시지 반환 값을 나열하는 해당 'R'(반환) 줄이 있습니다. 메시지 호출이 중첩되어 하나의 메시지 처리기가 다른 메시지를 보내는 경우도 있습니다.|
