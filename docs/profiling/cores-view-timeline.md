---
title: 코어 뷰 시간 표시 막대 | Microsoft Docs
description: 타임라인의 기본 사항으로 특정 시점에 어떤 코어에서 어떤 스레드가 실행되었는지 확인하는 방법과 확대 및 축소 방법을 알아봅니다.
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882897"
---
# <a name="cores-view-timeline"></a>코어 뷰 타임라인
타임라인의 각 행은 프로파일링된 시스템의 논리적 프로세서 코어를 나타냅니다. 각 행의 경우 가로 축은 지정된 시점에 논리 코어에서 실행된 스레드를 보여 줍니다. 타임라인에서 관심 있는 색을 가리켜 스레드를 식별하는 도구 설명으로 돌아갈 수 있습니다. 스레드 식별에 도움이 되도록 창 아래쪽의 범례는 각 색이 나타내는 것을 보여 줍니다. 클릭하고 끌어서 놓거나 CTRL 키를 누르고 마우스 휠을 이동하여 확대/축소하도록 확대/축소 도구를 사용합니다. 확대/축소 일관성은 코어 뷰와 스레드 뷰 사이를 전환할 때 유지 관리됩니다.

## <a name="see-also"></a>참고 항목
- [코어 뷰](../profiling/cores-view.md)
- [확대/축소 컨트롤(스레드 뷰)](../profiling/zoom-control-threads-view.md)