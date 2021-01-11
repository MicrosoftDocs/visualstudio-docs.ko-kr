---
title: 코드 메트릭-유지 관리 인덱스 범위 및 의미
ms.date: 1/8/2021
description: Visual Studio의 코드 메트릭에 대 한 유지 관리 인덱스 범위 메트릭에 대해 알아봅니다.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14bee6dcb522b7c1dd0475ca309b829a09c0d4ec
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069559"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>코드 메트릭-유지 관리 인덱스 범위 및 의미

질문: 유지 관리 인덱스는 0과 100 사이에서 다시 설정 되었습니다. 이 작업을 수행 하는 방법 및 이유

메트릭은 원래 다음과 같이 계산 됩니다. `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

이 수식의 사용은 171에서 제한 되지 않은 음수로의 값을 의미 합니다.  코드가 0으로 경향이 코드를 유지 관리 하기가 명확 하 고 코드의 차이는 0이 고 일부 음수 값은 유용 하지 않았습니다.  음수를 줄이고 메트릭을 가능한 한 명확 하 게 유지 하려는 경우 0 개 이하의 인덱스를 모두 0으로 처리 한 다음 171 또는 less 범위의 주소를 0에서 100으로 지정 하도록 결정 했습니다. 따라서 사용 하는 수식은 다음과 같습니다.

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

그 외에도 임계값을 신중 하 게 결정 했습니다.  인덱스에 red가 표시 되는 경우 코드에 문제가 있다는 것을 의미 하는 것입니다.  이렇게 하면 다음과 같은 임계값이 제공 됩니다.

임계값에 대해이 0-100 범위 80-20를 세분화 하 여 노이즈 수준 낮은 상태를 유지 하 고 의심 스러운 코드에만 플래그를 지정 하기로 결정 했습니다. 다음 임계값을 사용 했습니다.

- 0-9 = 빨강
- 10-19 = 노랑
- 20-100 = 녹색
