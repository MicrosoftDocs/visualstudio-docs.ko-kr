---
title: 명령줄에서 부하 테스트 실행 설정 지정
description: 부하 테스트에는 부하 테스트가 실행되는 방식에 영향을 미치는 속성인 실행 설정이 포함될 수 있습니다. 명령줄에서 실행 설정을 로드하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 290f56ba0f0ca9c6a8f6a6a1ee4e30b86bcfacd7
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440963"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>방법: 명령줄에서 사용할 부하 테스트 실행 설정 선택

부하 테스트에는 부하 테스트가 실행되는 방식에 영향을 미치는 속성인 *실행 설정* 이 포함될 수 있습니다. 실행 설정은 **속성** 창에서 범주별로 구성됩니다. 부하 테스트가 실행될 때 현재 활성 상태로 설정되어 있는 실행 설정이 사용됩니다.

부하 테스트에 실행 설정이 하나만 있는 경우 해당 실행 설정이 항상 활성 노드가 됩니다. 부하 테스트에 여러 실행 설정 노드가 있는 경우에는 명령줄에서 부하 테스트를 실행할 때 사용할 노드 하나를 선택할 수 있습니다. [방법: 부하 테스트에 추가 실행 설정 추가](../test/how-to-add-additional-run-settings-to-a-load-test.md)를 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>명령줄에서 실행 설정을 변경하려면

1. 명령줄에서 다른 실행 설정을 사용하여 컨텍스트 매개 변수 전략을 활용하려면 다음 명령을 사용합니다.

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. mstest를 사용하여 부하 테스트 실행

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [방법: 부하 테스트에 실행 설정 추가](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [방법: 부하 테스트에 대한 활성 실행 설정 선택](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
