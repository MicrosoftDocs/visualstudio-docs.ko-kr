---
title: 코드 맵을 통해 dependencies 시각화
description: 코드 맵을 통해 파일 및 코드 줄을 읽지 않고 코드가 어떻게 함께 맞는지 확인하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d33e3d882d25045802f2c015c88b87b970d9d04e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390439"
---
# <a name="map-dependencies-with-code-maps"></a>코드 맵을 통해 의존성 매핑

이 문서에서는 코드 맵을 사용하여 코드 전체의 dependencies를 시각화하는 방법을 알아봅니다.

## <a name="what-are-code-maps"></a>코드 맵이란?

Visual Studio 코드 맵을 사용하면 파일 및 코드 줄을 읽지 않고도 프로그램 코드가 어떻게 결합되는지 더 빠르게 확인할 수 있습니다.  이러한 맵을 사용하면 코드의 구조 및 해당 의존성, 업데이트 방법 및 제안된 변경 비용 예측 등 코드에서 조직 및 관계를 볼 수 있습니다.

![Visual Studio 코드 맵을 통해 dependencies 보기](../modeling/media/codemapsmainintro.png)

다음 언어로 코드에 대한 종속성을 매핑할 수 있습니다.

- 솔루션 또는 어셈블리의 Visual C# 또는 *Visual Basic(.dll* 또는 *.exe*)

- Visual C++ 프로젝트, 헤더 파일(*.h* 또는 ) 또는 이진 파일의 네이티브 또는 관리되는 C 또는 C++ 코드 `#include`

- Microsoft Dynamics AX용 .NET 모듈의 X++ 프로젝트 및 어셈블리

> [!NOTE]
> C# 또는 Visual Basic 이외의 프로젝트의 경우 코드 맵을 시작하거나 기존 코드 맵에 항목을 추가하는 옵션이 더 적습니다. 예를 들어 C++ 프로젝트의 텍스트 편집기에서는 개체를 마우스 오른쪽 단추로 클릭하여 코드 맵에 추가할 수 없습니다. 그러나 솔루션 탐색기 **,** **클래스 뷰** 및 **개체 브라우저** 에서 개별 코드 요소 또는 파일을 끌어서 놓을 수 있습니다.

## <a name="prerequisites"></a>필수 조건

Visual Studio 코드 맵을 만들려면 먼저 [ **코드 맵** 및 **라이브 종속성 유효성 검사** 구성 요소를 설치합니다.](install-architecture-tools.md)

코드 맵을 만들고 편집하려면 **Visual Studio Enterprise 버전이** 필요합니다. 그러나 Visual Studio Community 및 Professional 버전에서는 Enterprise Edition에서 생성된 다이어그램을 열 수 있지만 편집할 수는 없습니다.

> [!NOTE]
> Visual Studio Enterprise 만든 맵을 Visual Studio Professional 사용하는 다른 사용자와 공유하기 전에 맵의 모든 항목(예: 숨겨진 항목, 확장된 그룹 및 그룹 간 링크)이 표시되는지 확인합니다.

## <a name="add-a-code-map"></a>코드 맵 추가

빈 코드 맵을 만들고 어셈블리 참조, 파일 및 폴더를 포함하여 항목을 이 맵으로 끌거나 솔루션의 전체 또는 일부에 대한 코드 맵을 생성할 수 있습니다.

빈 코드 맵을 추가하려면 다음을 수행합니다.

1. **솔루션 탐색기** 에서 최상위 솔루션 노드의 바로 가기 메뉴를 엽니다.   >  **새 항목** 추가를 선택합니다.

2. 새 **항목 추가** 대화 상자의 **설치된** 에서 **일반** 범주를 선택합니다.

3. **Directed Graph Document(.dgml)** 템플릿을 선택한 다음, **추가를** 선택합니다.

   > [!TIP]
   > 이 템플릿은 사전순으로 표시되지 않을 수 있으므로 표시되지 않으면 템플릿 목록의 맨 아래로 스크롤합니다.

   솔루션의 **솔루션 항목** 폴더에 빈 맵이 표시됩니다.

마찬가지로 아키텍처 새 코드 맵 또는 파일 새 파일을 선택하여 솔루션에 추가하지 않고  >  **새 코드 맵** 파일을 만들 수  >    >  있습니다.

자세한 정보:
- [코드 맵 공유](share-code-maps.md)
- [C++용 코드 맵 만들기](code-maps-for-cpp.md)
- [코드 맵 성능 향상](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>솔루션에 대한 코드 맵 생성

솔루션의 모든 의존도를 보려면 다음을 수행합니다.

1. 메뉴 모음에서   >  **아키텍처 솔루션에 대한 코드 맵 생성을** 선택합니다. 코드를 마지막으로 빌드한 이후 코드가 변경되지 않은 경우 아키텍처   >  **빌드하지 않고 솔루션에 대한 코드 맵 생성을** 대신 선택할 수 있습니다.

   ![코드 맵 생성 명령](../modeling/media/codemapsarchitecturemenu.png)

   최상위 어셈블리와 어셈블리 간의 집계된 링크를 보여 주는 맵이 생성됩니다. 집계 링크의 범위가 넓을수록 해당 링크로 표시되는 종속성의 수도 많습니다.

2. 코드 맵 도구 모음에서 **범례** 단추를 사용하여 프로젝트 형식 아이콘(예: 테스트, 웹, Phone 프로젝트), 코드 항목(예: 클래스, 메서드, 속성) 및 관계 형식(예: 상속 원본, 구현, 호출) 목록을 표시하거나 숨깁니다.

   ![어셈블리의 최상위 종속성 그래프](../modeling/media/dependencygraph_toplevelassemblies.png)

   이 예제에는 솔루션 폴더(**테스트** 및 **구성 요소**), 테스트 프로젝트, 웹 프로젝트 및 어셈블리가 포함됩니다. 기본 적으로 모든 포함 관계는 확장 및 축소할 수 있는 *그룹* 으로 나타납니다. **외부** 그룹은 플랫폼 종속성을 포함하여 사용자의 솔루션 외부에 있는 모든 것을 포함합니다. 외부 어셈블리에는 사용된 항목만 표시됩니다. 기본적으로 깔끔하게 표시하기 위해 시스템 기본 형식은 맵에서 숨겨집니다.

3. 맵으로 드릴다운하려면 프로젝트 및 어셈블리를 나타내는 그룹을 확장합니다. **CTRL+A** 를 눌러 모드 노드를 선택하고 바로 가기 메뉴에서 **그룹**, **확장** 을 차례로 선택하는 방식으로 모든 항목을 확장할 수 있습니다.

   ![코드 맵에서 모든 그룹 확장](../modeling/media/codemapsexpandallgroups.png)

4. 그러나 이 방법은 큰 솔루션에는 유용하지 않을 수 있습니다. 실제로 복잡한 솔루션의 경우 메모리 제한으로 인해 모든 그룹을 확장하지 못할 수 있습니다. 대신에 개별 노드의 내부를 확인하려면 해당 노드를 확장합니다. 마우스 포인터를 노드 맨 위로 이동하고 펼침 단추(아래쪽 화살표)가 나타나면 단추를 클릭합니다.

   ![코드 맵에서 노드 확장](../modeling/media/dependencygraph_containment.png)

   또는 항목을 선택한 다음 더하기 키( )를 눌러 키보드를 **+** 사용합니다. 코드를 더 자세히 살펴보려면 네임스페이스, 형식 및 멤버에 대해 같은 작업을 수행합니다.

   > [!TIP]
   > 마우스, 키보드 및 터치를 사용하여 코드 맵 작업에 대한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬을 참조하세요.](../modeling/browse-and-rearrange-code-maps.md)

5. 맵을 단순화하고 개별 파트에 포커스를 지정하려면 코드 맵 도구 모음에서 **필터** 를 선택하고 원하는 노드 및 링크의 형식만 선택합니다. 예를 들어 모든 솔루션 폴더 및 어셈블리 컨테이너를 숨길 수 있습니다.

   ![컨테이너를 필터링하여 맵 단순화](../modeling/media/codemapsfilterfoldersassemblies.png)

   기본 솔루션 코드에 영향을 미치지 않고 맵에서 개별 그룹 및 항목을 숨기거나 제거하여 맵을 단순화할 수도 있습니다.

6. 항목 간 관계를 확인하려면 맵에서 관계를 선택합니다. **범례** 창에 표시된 대로 링크 색은 관계 형식을 나타냅니다.

   ![솔루션 전체의 종속성 보기](../modeling/media/codemapsmainintro.png)

   이 예제에서 자주색 링크는 호출이고, 점선 링크는 참조이고, 연한 파란색 링크는 필드 액세스입니다. 녹색 링크는 상속이거나, 관계 또는 *범주* 의 형식 두 개 이상을 나타내는 *집합체 링크* 일 수 있습니다.

   > [!TIP]
   > 녹색 링크가 표시된다고 해서 단순히 상속 관계만 있는 것은 아닙니다. 메서드 호출도 있을 수 있지만 해당 호출은 상속 관계에 의해 숨겨집니다. 특정 유형의 링크를 보려면 필터 창의 **확인란을** 사용하여 관심 없는 형식을 숨깁니다.

7. 항목 또는 링크에 대한 자세한 정보를 확인하려면 도구 설명이 나타날 때까지 포인터를 항목 또는 링크의 맨 위로 이동합니다. 이렇게 하면 링크가 나타내는 코드 요소 또는 범주의 세부 정보가 표시됩니다.

   ![관계의 범주 표시](../modeling/media/codemapsshowlinkcatgories.png)

8. 집합체 링크로 나타내는 항목 및 종속성을 살펴보려면 먼저 링크를 선택하고 바로 가기 메뉴를 엽니다. **영향을 주는 링크 표시** (또는 **새 코드 맵에 영향을 주는 링크 표시**)를 선택합니다. 그러면 그룹이 링크의 양쪽 끝에서 확장되고 링크에 참여하는 항목 및 종속성만 표시됩니다.

9. 맵의 특정 부분에 집중하기 위해 관심 없는 항목을 계속 제거할 수 있습니다. 예를 들어 클래스 및 멤버 뷰를 분석하려면 **필터** 창에서 모든 네임스페이스 노드를 필터링하면 됩니다.

   ![클래스 및 멤버 수준으로 드릴다운](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. 복잡한 솔루션 맵에서 포커스를 지정하는  또 다른 방법은 기존 맵을 기반을 선택한 항목이 포함된 새 맵을 생성하는 것입니다. **Ctrl 키를** 누른 채 포커스를 맞출 항목을 선택하고 바로 가기 메뉴를 열고 **선택 항목 에서 새 그래프를 선택합니다.**

    ![선택한 항목을 새 코드 맵에 표시](../modeling/media/codemapsshowonnewmap.png)

11. 포함하는 컨텍스트가 새 맵에 전달됩니다. 필터 창을 사용하여 솔루션 폴더 및 표시하지 않으려는 다른 **컨테이너를** 숨깁니다.

    ![뷰를 단순화하기 위해 컨테이너 필터링](../modeling/media/codemapsexpandnewgroups.png)

12. 그룹을 확장하고 맵에서 관계를 볼 항목을 선택합니다.

    ![관계를 볼 항목 선택](../modeling/media/codemapsviewnewrelationships.png)

또한 다음을 참조하세요.

- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
- [DGML 파일을 편집하여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [분석기를 실행하여](../modeling/find-potential-problems-using-code-map-analyzers.md) 코드에서 잠재적인 문제 찾기

## <a name="view-dependencies"></a>Dependencies 보기

보류 중인 변경 내용이 있는 일부 파일에서 수행할 코드 검토가 있다고 가정합니다. 변경 내용의 종속성을 확인하려면 해당 파일에서 코드 맵을 만듭니다.

   ![코드 맵에 특성 종속성 표시](../modeling/media/codemapsspecificdependenciesintro.png)

1. **솔루션 탐색기** 에서 매핑할 프로젝트, 어셈블리 참조, 폴더, 파일, 형식 또는 멤버를 선택합니다.

   ![매핑할 항목 선택](../modeling/media/codemapsselectinsolutionexplorer.png)

1. **솔루션 탐색기** 도구 모음에서 **코드 맵에 표시** 선택한 ![ 노드에서 새 그래프 만들기 단추 를 ](../modeling/media/createnewgraphfromselectedbutton.gif) 선택합니다. 또는 하나 또는 항목 그룹에 대한 바로 가기 메뉴를 열고 **코드 맵에 표시를** 선택합니다.

   솔루션 탐색기 **,** **클래스 뷰** 또는 **개체 브라우저** 에서 [새](#add-a-code-map) 코드 맵 또는 기존 코드 맵으로 항목을 끌 수도 있습니다. 항목의 부모 계층을 포함하려면 항목을 끄는 동안 **Ctrl** 키를 누른 채 누르거나 코드 맵 도구 모음에서 **부모 포함** 단추를 사용하여 기본 작업을 지정합니다. Windows 탐색기 와 같은 Visual Studio 외부에서 어셈블리 파일을 끌 수도 **있습니다.**

   > [!NOTE]
   > Windows Phone 또는 Microsoft Store 같은 여러 앱에서 공유되는 프로젝트에서 항목을 추가하면 해당 항목이 현재 활성 앱 프로젝트와 함께 맵에 표시됩니다. 다른 앱 프로젝트에 대한 컨텍스트를 변경하고 공유 프로젝트의 항목을 추가하면 해당 항목이 새로 활성화된 앱 프로젝트와 함께 나타납니다. 맵의 항목에 수행하는 작업은 동일한 컨텍스트를 공유하는 항목에만 적용됩니다.

3. 맵에는 포함하는 어셈블리 내에서 선택한 항목이 표시됩니다.

   ![맵에 그룹으로 표시된 선택된 항목](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. 항목을 탐색하려면 해당 항목을 확장합니다. 항목을 확장하려면 항목 위로 마우스 포인터를 이동한 다음 펼침 단추(아래쪽 화살표) 아이콘이 나타나면 클릭합니다.

   ![코드 맵에서 노드 확장](../modeling/media/dependencygraph_containment.png)

   모든 항목을 확장하려면 **Ctrl** A를 사용하여 항목을 선택한 + 다음, 맵의 바로 가기 메뉴를 열고 **그룹**  >  **확장을** 선택합니다. 그러나 이 옵션은 모든 그룹을 확장할 때 사용할 수 없는 맵 또는 메모리 문제가 발생하는 경우 사용할 수 없습니다.

5. 필요한 경우 클래스 및 멤버 수준 바로 아래로 관심 있는 항목을 계속 확장합니다.

   ![클래스 및 멤버 수준으로 그룹 확장](../modeling/media/codemapsexpandtoclassandmember.png)

   코드에 있지만 맵에 표시되지 않는 멤버를 보려면 그룹의 왼쪽 위 모서리에 있는 **자식** 다시 참조 아이콘 자식 다시 만들기 ![ ](../modeling/media/dependencygraph_deletednodesicon.png) 아이콘을 클릭합니다.

6. 맵의 항목과 관련된 추가 항목을 확인하려면 항목을 선택하고, 코드 맵 도구 모음에서 **관련 항목 표시** 를 선택하고, 맵에 추가할 관련 항목 형식을 선택합니다. 또는 하나 이상의 항목을 선택하고 바로 가기 메뉴를 연 다음 맵에 추가할 관련 항목 유형에 대해 **표시** 옵션을 선택합니다. 예를 들면 다음과 같습니다.

    **어셈블리** 인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**참조된 어셈블리 표시**|이 어셈블리가 참조하는 어셈블리를 추가합니다. **외부** 그룹에 외부 어셈블리가 나타납니다.|
    |**참조하는 어셈블리 표시**|솔루션에 이 어셈블리를 참조하는 어셈블리를 추가합니다.|

    **네임스페이스** 인 경우 **포함하는 어셈블리 표시** 를 선택합니다(표시되지 않을 경우).

    **클래스** 또는 **인터페이스** 인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**기본 형식 표시**|클래스의 경우 기본 클래스 및 구현된 인터페이스를 추가합니다.<br /><br /> 인터페이스의 경우 기본 인터페이스를 추가합니다.|
    |**파생 형식 표시**|클래스의 경우 파생된 클래스를 추가합니다.<br /><br /> 인터페이스의 경우 파생된 인터페이스와 구현 클래스 또는 구조체를 추가합니다.|
    |**참조된 형식 표시**|이 클래스가 사용하는 모든 클래스와 해당 멤버를 추가합니다.|
    |**참조하는 형식 표시**|이 클래스를 사용하는 모든 클래스와 해당 멤버를 추가합니다.|
    |**포함하는 네임스페이스 표시**|부모 네임스페이스를 추가합니다.|
    |**포함하는 네임스페이스 및 어셈블리 표시**|부모 컨테이너 계층 구조를 추가합니다.|
    |**모든 기본 형식 표시**|기본 클래스 또는 인터페이스 계층 구조를 재귀적으로 추가합니다.|
    |**모든 파생 형식 표시**|클래스의 경우 파생 클래스를 재귀적으로 추가합니다.<br /><br /> 인터페이스의 경우 파생된 모든 인터페이스와 구현 클래스 또는 구조체를 재귀적으로 추가합니다.|

     **메서드** 인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**호출된 메서드 표시**|이 메서드가 호출하는 메서드를 추가합니다.|
    |**참조된 필드 표시**|이 메서드가 참조하는 필드를 추가합니다.|
    |**포함하는 형식 표시**|부모 형식을 추가합니다.|
    |**포함하는 형식, 네임스페이스 및 어셈블리 표시**|부모 컨테이너 계층 구조를 추가합니다.|
    |**재정의된 메서드 표시**|다른 메서드를 재정의하거나 인터페이스 메서드를 구현하는 메서드의 경우 재정의된 기본 클래스에 모든 추상 메서드 또는 가상 메서드를 추가하고 구현된 인터페이스 메서드를 추가합니다(있는 경우).|

     **필드** 또는 **속성** 인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**포함하는 형식 표시**|부모 형식을 추가합니다.|
    |**포함하는 형식, 네임스페이스 및 어셈블리 표시**|부모 컨테이너 계층 구조를 추가합니다.|

    ![이 멤버에 의해 호출된 메서드 표시](../modeling/media/codemapsshowrelatedmethods.png)

7. 맵에 관계가 표시됩니다. 이 예제에서 맵은 메서드에 의해 호출된 메서드와 솔루션 내 또는 외부의 해당 위치를 보여 `Find` 있습니다.

   ![코드 맵에 특성 종속성 표시](../modeling/media/codemapsspecificdependenciesintro.png)

8. 맵을 단순화하고 개별 파트에 포커스를 지정하려면 코드 맵 도구 모음에서 **필터** 를 선택하고 원하는 노드 및 링크의 형식만 선택합니다. 예를 들어 솔루션 폴더, 어셈블리 및 네임스페이스의 표시를 해제합니다.

   ![필터 창을 사용하여 디스플레이 단순화](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>참조

- [코드 맵 공유](share-code-maps.md)
- [C++용 코드 맵 만들기](code-maps-for-cpp.md)
- [코드 맵 성능 향상](code-maps-performance.md)
- [동영상: Visual Studio 2015 코드 맵을 사용하여 코드에서 디자인 이해](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [동영상: Visual Studio 2015 코드 맵을 사용하여 코드에서 디자인 이해](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
- [DGML 파일을 편집하여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
