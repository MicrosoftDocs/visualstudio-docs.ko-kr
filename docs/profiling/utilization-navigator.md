---
title: 사용률 탐색기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e2562e86af36d935679916c2bfb9669be1758d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62823489"
---
# <a name="utilization-navigator"></a>사용률 탐색기
동시성 시각화 도우미의 사용률 탐색기를 사용하면 추적에서 시간 간격을 선택할 수 있습니다. 동시성 시각화 도우미는 시간 경과에 따라 대상 프로세스의 CPU 코어 사용률을 보여줍니다. 그러면 CPU 사용률 패턴을 쉽게 검토할 수 있으며, 사용률 데이터와 다른 보기의 데이터를 비교할 수 있습니다. 사용률 탐색기는 동시성 시각화 도우미에서 모든 보기의 맨 위에 나타납니다. 다음 그림은 사용률 탐색기를 보여줍니다.

 ![선택한 기간을 나타내는 사용률 탐색기](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") 사용률 탐색기 및 선택한 기간

 그림에서 선택한 기간은 *위치 조정*이라는 빨간색 직사각형으로 정의됩니다.

 사용률 탐색기를 사용해서 표시된 시간 범위를 조작하는 방법은 다음과 같습니다.

- 엄지 단추를 왼쪽 또는 오른쪽으로 끌어서 이동할 수 있습니다. (키보드: 엄지 단추에 포커스를 이동한 다음, 왼쪽 또는 오른쪽 화살표 키를 누릅니다.)

- 핸들 중 하나를 끌어서 간격을 변경할 수 있습니다. (키보드: 핸들에 포커스를 이동한 다음, 왼쪽 또는 오른쪽 화살표 키를 누릅니다.)

  다른 동시성 시각화 도우미 확대/축소 컨트롤을 사용하여 간격을 변경하면 사용률 탐색기가 변경 내용을 반영하도록 업데이트됩니다.