---
title: 코드 맵의 속도가 느립니다.
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28cb2c4fd74716aa876c57517bb440fda513de5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590542"
---
# <a name="improve-performance-for-code-maps"></a>코드 맵의 성능 향상

맵을 처음으로 생성하는 경우 Visual Studio는 검색된 모든 종속성을 인덱싱합니다. 이 프로세스는 특히 대기업의 경우에는 다소 시간이 걸릴 수 있지만 이후 성능을 향상 시킵니다. 코드가 변경되면 Visual Studio는 업데이트된 코드만 다시 인덱싱합니다. 맵에 렌더링을 완료 하는 데 걸리는 시간을 최소화 하려면 다음 제안 사항을 고려 합니다.

- 원하는 종속성만 매핑합니다.

- 전체 솔루션에 대한 맵을 생성하기 전에 솔루션 범위를 줄입니다.

- 코드 맵 도구 모음에서 **빌드 건너뛰기** 를 선택 하 여 솔루션에 대 한 자동 빌드를 해제 합니다.

- 코드 맵 도구 모음에서 부모 **포함** 을 선택 하 여 부모 항목의 자동 추가를 해제 합니다.

   ![빌드 건너뛰기 및 상위 포함 단추](../modeling/media/codemapsfilterskipbuildicons.png)

- 코드 맵 파일을 직접 편집하여 필요하지 않은 노드 및 링크를 제거합니다. 맵을 변경해도 기본 코드에 영향을 미치지 않습니다. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

프로젝트 항목의 **출력 디렉터리에 복사** 속성이 **항상 복사**로 설정 된 경우 맵을 만들거나 **솔루션 탐색기** 에서 맵에 항목을 추가 하는 데 더 많은 시간이 걸릴 수 있습니다. 성능을 높이려면 이 속성을 **변경된 내용만 복사** 또는 `PreserveNewest`로 변경합니다. [증분 빌드](../msbuild/incremental-builds.md)를 참조 하세요.

완료 된 맵은 성공적으로 작성 된 코드에 대 한 종속성만 보여 줍니다. 특성 구성 요소에 대해 빌드 오류가 발생하면 해당 오류가 맵에 나타납니다. 이 맵을 기반으로 아키텍처 관련 사항을 결정하기 전에 구성 요소가 실제로 빌드되는지와 해당 구성 요소에 종속성이 있는지를 확인해야 합니다.
