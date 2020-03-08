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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409011"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017의 디자인에 대한 새로운 기능

## <a name="live-dependency-validation"></a>실시간 종속성 유효성 검사

원치 않는 종속성을 제거 하면 기술적인 문제를 관리 하는 중요 한 부분입니다. Visual Studio는 위치와 같은 문제에 대 한 정확한 정보를 비롯 하 여 종속성에 대 한 실시간 유효성 검사를 제공 합니다. 라이브 종속성 유효성 검사는 오류 목록 및 편집기의 새 기능에 대 한 모든 이점을 제공 합니다.

![작업의 라이브 종속성 유효성 검사](media/dep-validation-whatsnew-01.png)

종속성 유효성 검사를 더욱 쉽게 검색 하 고 더 쉽게 액세스할 수 있도록 제작 환경이 변경 되었습니다. "레이어 다이어그램"에서 "종속성 다이어그램"으로 용어가 변경 되었습니다.

이제 **아키텍처** 메뉴에 종속성 다이어그램을 직접 만드는 명령이 있습니다.

![아키텍처 메뉴의 라이브 종속성 항목](media/dep-validation-whatsnew-02.png)

계층 속성 이름 및 설명이 다음과 같이 좀 더 의미 있도록 변경 되었습니다.

![라이브 종속성 속성 이름 업데이트](media/dep-validation-whatsnew-03.png)

다이어그램을 저장할 때마다 솔루션의 현재 코드에 대 한 분석 결과의 변경 내용에 대 한 영향이 즉시 표시 됩니다. **종속성 유효성 검사** 명령이 완료 될 때까지 기다릴 필요가 없습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)을 참조 하세요.

## <a name="uml-designers-have-been-removed"></a>UML 디자이너 제거 되었습니다.

UML 디자이너가 Visual Studio에서 제거 되었습니다.

* UML 다이어그램 이제 XML 파일로 표시 됩니다.
* UML 모델 탐색기를 더 이상 존재합니다.
* 모델링 프로젝트 참조는 종속성 유효성 검사를 위해 더 이상 사용 됩니다.
* 솔루션 탐색기에서 "레이어 참조" 노드를 더 이상 표시 됩니다.
* 빌드 작업에서 제거 되었습니다-종속성 (레이어) 다이어그램의 "유효성 검사" 빌드 작업을 더 이상 사용
* 버전 간 왕복에 대 한 프로젝트 구조는 유지 관리
* 있습니다 여전히 열기, 만들기, 편집 하 고 수 (계층) 종속성 다이어그램을 XML로 저장
* 디자인 화면에 액세스할 수 없는 (계층) 종속성 다이어그램에 연결 된 TFS 작업 항목
* 더 이상 지원 되지 DSL 또는 계층에서 다시 연결
* Modeling SDK에서 UML 확장은 더 이상 지원

.NET 및 C++ 코드의 아키텍처 시각화에 대 한 지원은 [코드 맵을](map-dependencies-across-your-solutions.md)통해 사용할 수 있습니다.

UML 디자이너의 중요 한 사용자 라면 UML 요구 사항에 맞게 대체 하는 도구를 결정 하는 동안 Visual Studio 2015 또는 이전 버전을 사용 하 여 계속 수 있습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)을 참조 하세요.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a>아키텍처 및 모델링 도구에 대 한 <a name="VersionSupport" />버전 지원

Visual Studio는 여러 버전에서 사용할 수 있습니다. 이러한 일부 아키텍처 및 모델링 도구에 대 한 지원을 제공 합니다. 다음 표에서는 각 도구의 사용 가능 여부를 보여 줍니다.

|**기능**|**Enterprise edition**|**Professional 버전**|**Community edition**|
|-|-|-|-|
|**코드 맵**|예|만 코드 맵 읽기를 지원 필터링 코드 맵, 선택 항목에서 새 전송 그래프를 만들고 새 일반 노드를 추가 합니다.|-|
|**종속성 다이어그램**|예|종속성 다이어그램 읽기 지원만 합니다.|종속성 다이어그램 읽기 지원만 합니다.|
|**방향이** 지정 된 그래프 (DGML 다이어그램)|예|예|예|
|**코드 복제본**|예|-|-|
