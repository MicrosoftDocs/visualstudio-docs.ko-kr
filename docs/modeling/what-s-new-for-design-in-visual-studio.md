---
title: Visual Studio 2017의 디자인에 대한 새로운 기능
description: Visual Studio 2017에서 사용할 수 있는 라이브 종속성 유효성 검사와 같은 코드 디자인에 대 한 새로운 기능에 대해 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 00a72f52b67e1e55bcc0699a3daf7da4dcfbc57d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924014"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Visual Studio 2017의 디자인에 대한 새로운 기능

## <a name="live-dependency-validation"></a>라이브 종속성 유효성 검사

원치 않는 종속성을 제거 하는 것은 기술적 부채를 관리 하는 데 중요 한 부분입니다. Visual Studio는 위치와 같은 문제에 대 한 정확한 정보를 비롯 하 여 종속성에 대 한 실시간 유효성 검사를 제공 합니다. 라이브 종속성 유효성 검사는 오류 목록 및 편집기의 새 기능에 대 한 모든 이점을 제공 합니다.

![실시간 종속성 유효성 검사 실행](media/dep-validation-whatsnew-01.png)

종속성 유효성 검사를 더욱 쉽게 검색 하 고 더 쉽게 액세스할 수 있도록 제작 환경이 변경 되었습니다. "레이어 다이어그램"에서 "종속성 다이어그램"으로 용어가 변경 되었습니다.

이제 **아키텍처** 메뉴에 종속성 다이어그램을 직접 만드는 명령이 있습니다.

![아키텍처 메뉴의 라이브 종속성 항목](media/dep-validation-whatsnew-02.png)

계층 속성 이름 및 설명이 다음과 같이 좀 더 의미 있도록 변경 되었습니다.

![라이브 종속성 업데이트 된 속성 이름](media/dep-validation-whatsnew-03.png)

다이어그램을 저장할 때마다 솔루션의 현재 코드에 대 한 분석 결과의 변경 내용에 대 한 영향이 즉시 표시 됩니다. **종속성 유효성 검사** 명령이 완료 될 때까지 기다릴 필요가 없습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)을 참조하세요.

## <a name="uml-designers-have-been-removed"></a>UML 디자이너가 제거 되었습니다.

UML 디자이너가 Visual Studio에서 제거 되었습니다.

* 이제 UML 다이어그램이 XML 파일로 제공 됩니다.
* UML 모델 탐색기가 더 이상 존재 하지 않습니다.
* 모델링 프로젝트 참조는 더 이상 종속성 유효성 검사에 사용 되지 않습니다.
* 솔루션 탐색기의 "계층 참조" 노드가 더 이상 표시 되지 않습니다.
* 종속성 (레이어) 다이어그램의 "유효성 검사" 빌드 작업이 더 이상 사용 되지 않습니다. 빌드 작업이 제거 되었습니다.
* 프로젝트 구조는 버전 간 라운드트립에 대해 유지 관리 됩니다.
* 종속성 (레이어) 다이어그램을 XML로 계속 열고 만들고 편집 하 고 저장할 수 있습니다.
* 종속성 (레이어) 다이어그램에 연결 된 TFS 작업 항목은 디자인 화면에서 액세스할 수 없습니다.
* 에서 DSL 또는 계층으로의 역방향 연결은 더 이상 지원 되지 않습니다.
* 모델링 SDK의 UML 확장성은 더 이상 지원 되지 않습니다.

.NET 및 c + + 코드의 아키텍처 시각화 지원은 [코드 맵을](map-dependencies-across-your-solutions.md)통해 사용할 수 있습니다.

UML 디자이너의 중요 한 사용자 인 경우 UML 요구 사항에 대 한 대체 도구를 결정 하는 동안 Visual Studio 2015 이전 버전을 계속 사용할 수 있습니다.

자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)을 참조하세요.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />아키텍처 및 모델링 도구에 대 한 버전 지원

Visual Studio는 여러 버전에서 사용할 수 있습니다. 이러한 모든 것이 아키텍처 및 모델링 도구에 대 한 지원을 제공 하는 것은 아닙니다. 다음 표에서는 각 도구의 사용 가능 여부를 보여 줍니다.

|**기능**|**Enterprise edition**|**Professional 버전**|**Community edition**|
|-|-|-|-|
|**코드 맵**|예|는 코드 맵 읽기, 코드 맵 필터링, 새 제네릭 노드 추가 및 선택 영역에서 새 방향 그래프 만들기만 지원 합니다.|-|
|**종속성 다이어그램**|예|는 종속성 다이어그램 읽기만 지원 합니다.|는 종속성 다이어그램 읽기만 지원 합니다.|
|**방향이** 지정 된 그래프 (DGML 다이어그램)|예|예|예|
|**코드 복제본**|예|-|-|
