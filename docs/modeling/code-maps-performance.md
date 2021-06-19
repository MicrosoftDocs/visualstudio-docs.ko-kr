---
title: 코드 맵이 느림
description: 코드 맵 성능을 향상시키는 방법과 렌더링을 완료하는 데 필요한 시간을 최소화하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5a279a04b1bd76933df335bc0b2527ab4b2418f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389646"
---
# <a name="improve-performance-for-code-maps"></a>코드 맵의 성능 향상

맵을 처음으로 생성하는 경우 Visual Studio는 검색된 모든 종속성을 인덱싱합니다. 이 프로세스는 특히 대규모 솔루션의 경우 다소 시간이 걸릴 수 있지만 이후 성능을 향상시킵니다. 코드가 변경되면 Visual Studio는 업데이트된 코드만 다시 인덱싱합니다. 맵이 렌더링을 완료하는 데 걸린 시간을 최소화하려면 다음 제안을 고려하세요.

- 원하는 종속성만 매핑합니다.

- 전체 솔루션에 대한 맵을 생성하기 전에 솔루션 범위를 줄입니다.

- 코드 맵 도구 모음에서 **빌드 건너뛰기** 를 선택하여 솔루션에 대한 자동 빌드를 해제합니다.

- 코드 맵 도구 모음에서 부모 **포함을** 선택하여 부모 항목의 자동 추가를 해제합니다.

   ![빌드 건너뛰기 및 상위 포함 단추](../modeling/media/codemapsfilterskipbuildicons.png)

- 코드 맵 파일을 직접 편집하여 필요하지 않은 노드 및 링크를 제거합니다. 맵을 변경해도 기본 코드에 영향을 미치지 않습니다. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

프로젝트 항목의 **출력 디렉터리로 복사** 속성이 **항상 복사로** 설정된 **경우 솔루션 탐색기** 맵을 만들거나 맵에 항목을 추가하는 데 더 많은 시간이 걸릴 수 있습니다. 성능을 높이려면 이 속성을 **변경된 내용만 복사** 또는 `PreserveNewest`로 변경합니다. [증분 빌드 를 참조하세요.](../msbuild/incremental-builds.md)

완료된 맵은 성공적으로 빌드된 코드에 대한만의 의존도를 표시합니다. 특성 구성 요소에 대해 빌드 오류가 발생하면 해당 오류가 맵에 나타납니다. 이 맵을 기반으로 아키텍처 관련 사항을 결정하기 전에 구성 요소가 실제로 빌드되는지와 해당 구성 요소에 종속성이 있는지를 확인해야 합니다.
