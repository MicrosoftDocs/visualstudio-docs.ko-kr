---
title: 메시지 코드 | Microsoft Docs
description: 메시지 뷰의 각 메시지 줄에 표시된 메시지 코드의 의미를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903612"
---
# <a name="message-codes"></a>메시지 코드
[메시지 뷰](../debugger/messages-view.md)에 표시되는 각 메시지 줄에는 'P', 'S', 's' 또는 'R' 코드가 포함됩니다. 이러한 코드에는 다음과 같은 의미가 있습니다.

|코드|의미|
|----------|-------------|
|P|**PostMessage** 함수를 사용하여 메시지를 큐에 게시했습니다. 메시지의 최종 처리와 관련된 정보를 사용할 수 없습니다.|
|S|**SendMessage** 함수를 사용하여 메시지를 보냈습니다. 받는 사람이 메시지를 처리하고 반환할 때까지 보낸 사람은 제어 권한을 다시 얻지 못한다는 것을 나타냅니다. 따라서 받는 사람은 다시 반환 값을 보낸 사람에게 전달할 수 있습니다.|
|s|메시지를 보냈지만 보안 때문에 반환 값에 액세스하지 못합니다.|
|R|각 'S' 줄에는 메시지 반환 값을 나열하는 해당 'R'(반환) 줄이 있습니다. 메시지 호출이 중첩되어 하나의 메시지 처리기가 다른 메시지를 보내는 경우도 있습니다.|