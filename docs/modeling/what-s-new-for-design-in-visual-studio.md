---
title: Visual Studio 2017의 디자인에 대한 새로운 기능
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301496"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017의 디자인에 대한 새로운 기능

## <a name="live-dependency-validation"></a>라이브 종속성 유효성 검사

원치 않는 종속성을 제거하는 것은 기술 부채를 관리하는 데 중요한 부분입니다. Visual Studio는 종속성이 있는 위치와 같은 문제에 대한 정확한 정보를 포함하여 종속성에 대한 실시간 유효성 검사를 제공합니다. 라이브 종속성 유효성 검사는 오류 목록 및 편집기의 새로운 기능을 최대한 활용합니다.

![라이브 종속성 유효성 검사 작업](media/dep-validation-whatsnew-01.png)

종속성 유효성 검사를 더 쉽게 검색하고 액세스할 수 있도록 작성 환경이 변경되었습니다. 용어가 "레이어 다이어그램"에서 "종속성 다이어그램"으로 변경되었습니다.

이제 **아키텍처** 메뉴에는 종속성 다이어그램을 직접 만드는 명령이 포함되어 있습니다.

![아키텍처 메뉴의 라이브 종속성 항목](media/dep-validation-whatsnew-02.png)

레이어 속성 이름과 설명이 더 의미 있게 변경되었습니다.

![라이브 종속성 업데이트 속성 이름](media/dep-validation-whatsnew-03.png)

다이어그램을 저장할 때마다 솔루션의 현재 코드에 대한 분석 결과에 변경 사항이 미치는 영향을 즉시 확인할 수 있습니다. **종속성 유효성 검사** 명령이 완료될 때까지 기다릴 필요가 없습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)을 참조하세요.

## <a name="uml-designers-have-been-removed"></a>UML 디자이너가 제거되었습니다.

UML 디자이너가 Visual Studio에서 제거되었습니다.

* UML 다이어그램은 이제 XML 파일로 표시됩니다.
* UML 모델 탐색기가 더 이상 존재하지 않습니다.
* 모델링 프로젝트 참조는 종속성 유효성 검사에 더 이상 사용되지 않습니다.
* 솔루션 탐색기의 "레이어 참조" 노드가 더 이상 표시되지 않습니다.
* 종속성(계층) 다이어그램에 대한 "유효성 검사" 빌드 작업이 더 이상 사용되지 않습니다 - 빌드 작업이 제거되었습니다.
* 버전 간 라운드 트립을 위해 프로젝트 구조가 유지됩니다.
* 종속성(계층) 다이어그램을 XML로 열, 생성, 편집 및 저장할 수 있습니다.
* 종속성(레이어) 다이어그램에 연결된 TFS 작업 항목은 설계 표면에서 액세스할 수 없습니다.
* DSL 또는 레이어로의 백 연결이 더 이상 지원되지 않음
* 모델링 SDK의 UML 확장성은 더 이상 지원되지 않습니다.

.NET 및 C++ 코드의 아키텍처 시각화에 대한 지원은 [코드 맵을](map-dependencies-across-your-solutions.md)통해 사용할 수 있습니다.

UML 디자이너의 중요한 사용자인 경우 UML 요구 사항에 대한 대체 도구를 결정하는 동안 Visual Studio 2015 또는 이전 버전을 계속 사용할 수 있습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)을 참조하세요.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />아키텍처 및 모델링 도구에 대한 에디션 지원

비주얼 스튜디오는 여러 버전으로 제공됩니다. 이러한 모든 아키텍처 및 모델링 도구에 대 한 지원을 제공 합니다. 다음 표에서는 각 도구의 사용 가능 여부를 보여 줍니다.

|**기능**|**엔터프라이즈 에디션**|**프로페셔널 에디션**|**커뮤니티 에디션**|
|-|-|-|-|
|**코드 맵**|yes|코드 맵 읽기, 코드 맵 필터링, 새 일반 노드 추가, 선택 항목에서 새 방향 그래프 만들기만 지원합니다.|-|
|**종속성 다이어그램**|yes|읽기 종속성 다이어그램만 지원합니다.|읽기 종속성 다이어그램만 지원합니다.|
|**방향** 그래프(DGML 다이어그램)|yes|yes|yes|
|**코드 복제**|yes|-|-|
