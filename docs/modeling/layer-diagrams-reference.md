---
title: 종속성 다이어그램 참조
description: Visual Studio 종속성 다이어그램을 사용하여 시스템의 높은 수준의 논리적 아키텍처를 시각화할 수 있다는 것을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb138164cfab44778c932a4bcb93572a3053a70
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391038"
---
# <a name="dependency-diagrams-reference"></a>종속성 다이어그램: 참조

Visual Studio *종속성 다이어그램을* 사용하여 시스템의 높은 수준의 논리적 아키텍처를 시각화할 수 있습니다. 종속성 다이어그램은 시스템의 물리적 아티팩트 를 레이어라는 논리적 추상 그룹으로 *구성합니다.* 이들 레이어는 아티팩트가 수행하는 주요 작업 또는 시스템의 주요 구성 요소를 설명합니다. 각 레이어에는 더 세부적인 작업을 설명하는 중첩된 레이어가 포함될 수도 있습니다.

이 기능을 지원하는 Visual Studio 버전을 확인하려면 [아키텍처 및 모델링 도구에 대한 에디션 지원](../modeling/analyze-and-model-your-architecture.md#VersionSupport)을 참조하세요.

> [!NOTE]
> .NET Core 프로젝트에 대한 종속성 다이어그램은 Visual Studio 2019 버전 16.2부터 지원됩니다.

레이어 간에 의도한 종속성이나 기존 종속성을 지정할 수 있습니다. 이와 같이 화살표로 나타내는 종속성은 다른 레이어가 나타내는 기능을 어느 레이어가 사용할 수 있는지 또는 현재 어느 레이어가 사용하고 있는지를 나타냅니다. 시스템을 고유한 역할 및 함수를 설명하는 계층으로 구성하면 종속성 다이어그램을 통해 코드를 보다 쉽게 이해하고, 다시 사용하며, 유지 관리하도록 할 수 있습니다.

종속성 다이어그램을 사용하여 다음 작업을 수행할 수 있습니다.

- 시스템의 기존 또는 의도한 논리적 아키텍처를 전달합니다.

- 기존 코드와 의도한 아키텍처 간 충돌을 검색합니다.

- 시스템을 리팩터링, 업데이트하거나 발전시킬 때 변경이 의도한 아키텍처에 미치는 영향을 시각화합니다.

- 체크 인 및 빌드 작업을 통해 유효성 검사를 포함하여 개발 및 유지 관리 중에 의도한 아키텍처를 보강합니다.

이 항목에서는 종속성 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다. 종속성 다이어그램을 만들고 그리는 방법에 대한 자세한 내용은 [종속성 다이어그램: 지침을 참조하세요.](../modeling/layer-diagrams-guidelines.md) 레이어링 패턴에 대한 자세한 내용은 [패턴 & 사례 사이트를 방문하세요.](https://archive.codeplex.com/?p=apparch)

## <a name="reading-dependency-diagrams"></a>종속성 다이어그램 읽기

![종속성 다이어그램의 요소](../modeling/media/uml_layerrefreading.png)

다음 표에서는 종속성 다이어그램에서 사용할 수 있는 요소에 대해 설명합니다.

|**셰이프**|**요소**|**설명**|
|-|-|-|
|1|**계층**|시스템에 있는 물리적 아티팩트의 논리적 그룹입니다. 이들 아티팩트는 네임스페이스, 프로젝트, 클래스, 메서드 등에 해당할 수 있습니다.<br /><br /> 계층에 연결된 아티팩트 를 보려면 계층의 바로 가기 메뉴를 열고 **링크 보기를** 선택하여 레이어 **탐색기를** 엽니다.<br /><br /> 자세한 내용은 계층 탐색기 를 [참조하세요.](#Explorer)<br /><br /> -   사용할 수 **없는 네임스페이스 Dependencies** - 이 계층과 연결된 아티팩트에서 지정된 네임스페이스에 의존할 수 없으면 을 지정합니다.<br />-   **사용할 수 없는 네임스페이스** - 이 계층과 연결된 아티팩트에서 지정된 네임스페이스에 속하지 않도록 지정합니다.<br />-   **필수 네임스페이스** - 이 계층과 연결된 아티팩트에서 지정된 네임스페이스 중 하나에 속하도록 지정합니다.|
|2|**종속성**|한 레이어에서 다른 레이어의 기능을 사용할 수 있지만 반대의 경우는 불가능함을 나타냅니다.<br /><br /> -   **방향** - 종속성의 방향을 지정합니다.|
|3|**양방향 종속성**|한 레이어에서 다른 레이어의 기능을 사용할 수 있고 반대의 경우도 가능함을 나타냅니다.<br /><br /> -   **방향** - 종속성의 방향을 지정합니다.|
|4|**설명**|다이어그램 또는 다이어그램의 요소에 일반적인 메모를 추가하려면 사용합니다.|
|5|**주석 링크**|다이어그램의 요소에 주석을 연결하려면 사용합니다.|

## <a name="layer-explorer"></a><a name="Explorer"></a> 계층 탐색기

솔루션에서 각 레이어를 프로젝트, 클래스, 네임스페이스, 프로젝트 파일 및 기타 소프트웨어 파트와 같은 아티팩트에 연결할 수 있습니다. 레이어의 숫자는 해당 레이어에 연결된 아티팩트의 수를 나타냅니다. 그러나 레이어의 아티팩트 수를 읽을 때 다음을 고려하세요.

- 레이어가 직접 연결되지 않은 다른 아티팩트를 포함하는 아티팩트에 연결된 경우 연결된 아티팩트만 숫자에 포함됩니다. 그러나 레이어 유효성 검사 중에는 직접 연결되지 않은 다른 아티팩트도 분석을 위해 포함됩니다.

     예를 들어 레이어가 단일 네임스페이스에 연결된 경우 해당 네임스페이스에 클래스가 들어 있더라도 연결된 아티팩트의 수는 1입니다. 레이어가 네임스페이스의 각 클래스에도 연결되어 있으면 연결된 클래스가 숫자에 포함됩니다.

- 레이어가 아티팩트에 연결된 다른 레이어를 포함하면 컨테이너 레이어가 이 아티팩트에도 연결됩니다. 단, 컨테이너 레이어의 숫자에는 이러한 아티팩트가 포함되지 않습니다.

레이어 및 아티팩트 연결에 대한 자세한 내용은 다음을 참조하세요.

- [종속성 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)

- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>연결된 아티팩트 검사

종속성 다이어그램에서 하나 이상의 계층에 대한 바로 가기 메뉴를 열고 **링크 보기를** 선택합니다.

**계층 탐색기가** 열리고 선택한 계층에 연결된 아티팩트도 표시됩니다. **계층 탐색기에는** 아티팩트 링크의 각 속성을 보여 주는 열이 있습니다.

> [!NOTE]
> 이러한 속성을 모두 볼 수 없는 경우 **계층 탐색기** 창을 확장합니다.

|**레이어 탐색기의 열**|**설명**|
|-|-|
|**범주**|클래스, 네임스페이스, 소스 파일 등의 아티팩트 종류|
|**계층**|아티팩트에 연결되는 레이어|
|**유효성 검사 지원**|**True이면** 레이어 유효성 검사 프로세스에서 프로젝트가 이 요소에 대한 의존성을 준수하는지 확인할 수 있습니다.<br /><br /> **False이면** 링크가 계층 유효성 검사 프로세스에 참여하지 않습니다.<br /><br /> 자세한 내용은 [종속성 다이어그램: 지침을 참조하세요.](../modeling/layer-diagrams-guidelines.md)|
|**식별자**|연결된 아티팩트에 대한 참조|

## <a name="see-also"></a>참조

- [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
