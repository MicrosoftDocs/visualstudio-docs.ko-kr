---
title: 뷰 새로 고침 | Microsoft Docs
description: Visual Studio에서 디버그할 때 Spy++ 도구에서 뷰를 새로 고치는 방법을 알아봅니다. Spy++는 시스템 테이블의 스냅샷을 사용하고 이 정보에 따라 뷰를 새로 고칩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- refreshing views
ms.assetid: 2ed0ba66-7259-486b-a518-aab6e45030aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 674eb33418aac8301cf19a0cbbefd15d90e24238
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148873"
---
# <a name="how-to-refresh-the-view"></a>방법: 보기 새로 고침
Spy++는 시스템 테이블의 “스냅샷”을 사용하고 이 정보에 따라 뷰를 새로 고칩니다. 시스템 뷰를 주기적으로 새로 고치는 것이 중요합니다. Spy++ 뷰가 열려 있고 뷰를 새로 고치지 않은 경우에는 이후에 생성되는 프로세스, 스레드 및 창이 표시되지 않습니다. 또한 더 이상 존재하지 않는 항목이 표시될 수도 있습니다. **새로 고침** 명령은 메시지 뷰를 제외한 모든 뷰에서 사용할 수 있습니다.

### <a name="to-refresh-the-currently-active-view"></a>현재 활성 뷰를 새로 고치려면

- **창** 메뉴에서 **새로 고침** 을 선택하거나, 도구 모음에서 **새로 고침** 단추를 클릭합니다.

## <a name="see-also"></a>참조
- [Spy++ 사용](../debugger/using-spy-increment.md)
- [Spy++ 뷰](../debugger/spy-increment-views.md)
- [Spy++ 참조](../debugger/spy-increment-reference.md)