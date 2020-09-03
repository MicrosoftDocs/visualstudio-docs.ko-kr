---
title: 솔루션 전체에서 종속성 매핑 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d70016229ad9599c7ededbefaf08744f2bb6f351
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548085"
---
# <a name="map-dependencies-across-your-solutions"></a>솔루션 전체의 종속성 매핑
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 간의 종속성을 파악하려는 경우 코드 맵을 만들어 해당 코드를 시각화합니다. 그러면 전체 파일과 코드 줄을 확인하지 않고도 여러 코드가 서로 맞는지 파악할 수 있습니다.

 ![솔루션 전체의 종속성 보기](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

 **아래에는 이와 관련한 몇 가지 비디오가 나와 있습니다**.

- [시각화를 통해 코드 종속성 이해](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)

- [변경 영향 시각화](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)

- [코드 맵으로 복잡한 코드 이해하기](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understanding-complex-code-with-Code-Map-ENU)

## <a name="get-started-with-code-maps"></a><a name="GetStarted"></a> 코드 맵 시작
 **코드 맵을 사용하려면 다음이 필요합니다**.

- Visual Studio Enterprise: 코드 편집기, 솔루션 탐색기, 클래스 뷰 또는 개체 브라우저에서 코드 맵을 만듭니다.

- Visual Studio Professional: 코드 맵을 열고, 제한된 편집을 수행하고, 코드를 탐색합니다.

> [!WARNING]
> Visual Studio Enterprise에서 만든 맵을 Visual Studio Professional 사용자와 공유하기 전에 숨겨진 항목, 확장된 그룹 및 그룹 간 링크 등의 모든 항목이 맵에 표시되어 있어야 합니다.

 **다음 언어로 코드에 대한 종속성을 매핑할 수 있습니다**.

- 솔루션이나 어셈블리(.dll 또는 .exe)의 Visual C# .NET 또는 Visual Basic .NET

- Visual C++ 프로젝트의 네이티브 또는 관리되는 C/C++ 코드, 헤더 파일(.h 또는 `#include`) 또는 이진 파일

- Microsoft Dynamics AX용 .NET 모듈의 X++ 프로젝트 및 어셈블리

  **참고:** C# 또는 Visual Basic .NET이 아닌 다른 프로젝트의 경우 코드 맵을 시작하거나 기존 코드 맵에 항목을 추가하는 옵션이 더 적습니다. 예를 들어 C++ 프로젝트의 텍스트 편집기에서는 개체를 마우스 오른쪽 단추로 클릭하여 코드 맵에 추가할 수 없습니다. 그러나 솔루션 탐색기, 클래스 뷰 및 개체 브라우저에서 개별 코드 요소 또는 파일을 끌어서 놓을 수 있습니다.

#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>솔루션 전체의 종속성을 확인하려면

1. **아키텍처** 메뉴를 엽니다.

2. 솔루션을 열었지만 빌드하지 않았거나 마지막으로 빌드한 후 코드가 변경된 경우 **솔루션용 코드 맵 생성**을 선택합니다.

3. 마지막으로 빌드한 후 코드가 변경되지 않은 경우 **빌드하지 않고 솔루션용 코드 맵 생성** 을 선택하여 맵을 더 빠르게 만들 수 있습니다.

4. [전체 종속성을 확인](#SeeOverviewSource) 하여 코드 맵을 통해 솔루션의 전체 종속성을 보는 방법을 알아보세요.

#### <a name="to-see-specific-dependencies-within-your-solution"></a>솔루션 내에서 특정 종속성을 확인하려면

1. 솔루션이 로드되면 **솔루션 탐색기**를 엽니다.

2. 매핑할 모든 프로젝트, 어셈블리 참조, 폴더, 파일, 형식 또는 멤버를 선택합니다.

3. **솔루션 탐색기** 도구 모음에서 **코드 맵에 표시**를 선택 하 여![선택한 노드에서 새 그래프 만들기 단추](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton")를 선택 합니다. 또는 바로 가기 메뉴를 열고 **코드 맵에 표시**를 선택합니다. 클래스 뷰 또는 개체 브라우저에서 신규 또는 기존 코드 맵으로 항목을 끌 수도 있습니다.

4. [특정 종속성을 확인](#SeeSpecificSource) 하여 코드 맵을 통해 솔루션 내의 특정 종속성을 보는 방법을 알아보세요.

### <a name="to-add-a-new-empty-code-map-to-your-solution"></a><a name="CreateEmptyMap"></a> 솔루션에 빈 코드 맵을 새로 추가 하려면

1. **솔루션 탐색기**에서 최상위 솔루션 노드의 바로 가기 메뉴를 엽니다. **추가** , **새 항목**을 차례로 선택합니다.

2. **설치됨**에서 **일반**을 선택합니다.

3. 오른쪽 창에서 **방향이 지정된 그래프 문서** , **추가**를 차례로 선택합니다.

     그러면 빈 맵이 솔루션의 **솔루션 항목** 폴더에 표시됩니다.

#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>솔루션에 추가하지 않고 빈 코드 맵을 새로 만들려면

1. **아키텍처** 메뉴를 열고 **새 코드 맵**을 선택합니다.

     \- 또는 -

2. **파일** 메뉴를 열고 **새로 만들기** , **파일**을 차례로 선택합니다.

3. **설치됨**에서 **일반**을 선택합니다.

4. 오른쪽 창에서 **방향이 지정된 그래프 문서** , **열기**를 차례로 선택합니다.

     그러면 빈 맵이 솔루션의 폴더에 표시되지 않습니다.

## <a name="see-overall-dependencies"></a><a name="SeeOverviewSource"></a> 전체 종속성을 확인

### <a name="see-dependencies-across-your-solution"></a><a name="OverviewSource"></a> 솔루션 전체의 종속성 확인

1. **아키텍처** 메뉴에서 **솔루션용 코드 맵 생성**을 선택합니다.

    ![코드 맵 생성 명령](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")

    최상위 수준 어셈블리와 어셈블리 간의 집계된 링크를 보여 주는 맵이 표시됩니다. 집계 링크의 범위가 넓을수록 해당 링크로 표시되는 종속성의 수도 많습니다.

2. 코드 맵 도구 모음에서 **범례** 단추를 사용하여 프로젝트 형식 아이콘(예: 테스트, 웹, Phone 프로젝트), 코드 항목(예: 클래스, 메서드, 속성) 및 관계 형식(예: 상속 원본, 구현, 호출) 목록을 표시하거나 숨깁니다.

    ![어셈블리의 상위&#45;수준 종속성 그래프](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")

    이 예제에는 솔루션 폴더(**테스트** 및 **구성 요소**), 테스트 프로젝트, 웹 프로젝트 및 어셈블리가 포함됩니다. 기본 적으로 모든 포함 관계는 확장 및 축소할 수 있는 *그룹*으로 나타납니다. **외부** 그룹은 플랫폼 종속성을 포함하여 사용자의 솔루션 외부에 있는 모든 것을 포함합니다. 외부 어셈블리에는 사용된 항목만 표시됩니다. 기본적으로 깔끔하게 표시하기 위해 시스템 기본 형식은 맵에서 숨겨집니다.

3. 맵으로 드릴다운하려면 프로젝트 및 어셈블리를 나타내는 그룹을 확장합니다. **CTRL+A** 를 눌러 모드 노드를 선택하고 바로 가기 메뉴에서 **그룹**, **확장** 을 차례로 선택하는 방식으로 모든 항목을 확장할 수 있습니다.

    ![코드 맵에서 모든 그룹 확장](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")

4. 그러나 이 방법은 큰 솔루션에는 유용하지 않을 수 있습니다. 실제로 복잡한 솔루션의 경우 메모리 제한으로 인해 모든 그룹을 확장하지 못할 수 있습니다. 대신에 개별 노드의 내부를 확인하려면 해당 노드를 확장합니다. 마우스 포인터를 노드 맨 위로 이동하고 펼침 단추(아래쪽 화살표)가 나타나면 단추를 클릭합니다.

    ![코드 맵에서 노드 확장](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

    또는 항목을 선택 하 고 더하기 키 ()를 눌러 키보드를 사용 **+** 합니다. 코드를 더 자세히 살펴보려면 네임스페이스, 형식 및 멤버에 대해 같은 작업을 수행합니다.

   > [!TIP]
   > 마우스, 키보드 및 터치를 사용 하 여 코드 맵으로 작업 하는 방법에 대 한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)을 참조 하세요.

5. 맵을 단순화하고 개별 파트에 포커스를 지정하려면 코드 맵 도구 모음에서 **필터** 를 선택하고 원하는 노드 및 링크의 형식만 선택합니다. 예를 들어 모든 솔루션 폴더 및 어셈블리 컨테이너를 숨길 수 있습니다.

    ![컨테이너를 필터링하여 맵 단순화](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")

    기본 솔루션 코드에 영향을 미치지 않고 맵에서 개별 그룹 및 항목을 숨기거나 제거하여 맵을 단순화할 수도 있습니다.

6. 항목 간 관계를 확인하려면 맵에서 관계를 선택합니다. **범례** 창에 표시된 대로 링크 색은 관계 형식을 나타냅니다.

    ![솔루션 전체의 종속성 보기](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

    이 예제에서 자주색 링크는 호출이고, 점선 링크는 참조이고, 연한 파란색 링크는 필드 액세스입니다. 녹색 링크는 상속이거나, 관계 또는 *범주* 의 형식 두 개 이상을 나타내는 *집합체 링크*일 수 있습니다.

   > [!TIP]
   > 녹색 링크가 표시된다고 해서 단순히 상속 관계만 있는 것은 아닙니다. 메서드 호출도 있을 수 있지만 해당 호출은 상속 관계에 의해 숨겨집니다. 특정 링크 형식을 확인하려면 **필터** 창의 확인란을 사용하여 원하지 않는 형식을 숨깁니다.

7. 항목 또는 링크에 대한 자세한 정보를 확인하려면 도구 설명이 나타날 때까지 포인터를 항목 또는 링크의 맨 위로 이동합니다. 이렇게 하면 링크가 나타내는 코드 요소 또는 범주의 세부 정보가 표시됩니다.

    ![관계의 범주 표시](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")

8. 집합체 링크로 나타내는 항목 및 종속성을 살펴보려면 먼저 링크를 선택하고 바로 가기 메뉴를 엽니다. **영향을 주는 링크 표시** (또는 **새 코드 맵에 영향을 주는 링크 표시**)를 선택합니다. 그러면 그룹이 링크의 양쪽 끝에서 확장되고 링크에 참여하는 항목 및 종속성만 표시됩니다.

9. 맵의 특정 부분에 포커스를 지정하려면 원하지 않는 항목을 계속 제거하면 됩니다. 예를 들어 클래스 및 멤버 뷰를 분석하려면 **필터** 창에서 모든 네임스페이스 노드를 필터링하면 됩니다.

     ![클래스 및 멤버 수준으로 드릴다운](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")

10. 복잡한 솔루션 맵에서 포커스를 지정하는  또 다른 방법은 기존 맵을 기반을 선택한 항목이 포함된 새 맵을 생성하는 것입니다. **CTRL** 키를 누른 채 포커스를 지정할 항목을 선택하고, 바로 가기 메뉴를 열고, **선택 영역의 새 그래프**를 선택합니다.

     ![선택한 항목을 새 코드 맵에 표시](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

11. 포함하는 컨텍스트가 새 맵에 전달됩니다. **필터** 창을 사용하여 표시하지 않을 솔루션 폴더 및 기타 컨테이너를 숨깁니다.

     ![뷰를 단순화하기 위해 컨테이너 필터링](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")

12. 그룹을 확장하고 맵에서 관계를 볼 항목을 선택합니다.

     ![관계를 볼 항목 선택](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")

    참고 항목:

- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)

- [DGML 파일을 편집하여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

- [분석기를 실행](../modeling/find-potential-problems-using-code-map-analyzers.md)하여 코드에서 발생할 수 있는 문제를 찾습니다.

### <a name="see-dependencies-across-assemblies-or-binaries"></a><a name="OverviewCompiled"></a> 어셈블리 또는 이진 파일 간의 종속성 확인

1. [빈 코드 맵을 만들거나](#GetStarted)기존 코드 맵(.dgml 파일)을 엽니다.

2. 어셈블리 또는 이진 파일을 외부 Visual Studio에서 맵으로 끕니다. 예를 들어 Windows 탐색기 또는 파일 탐색기에서 어셈블리 또는 이진 파일을 끕니다.

> [!NOTE]
> Windows 탐색기 또는 파일 탐색기와 Visual Studio를 동일한 UAC(사용자 액세스 제어) 권한 수준에서 실행하는 경우에만 Windows 탐색기 또는 파일 탐색기에서 어셈블리 또는 이진 파일을 끌 수 있습니다. 예를 들어 UAC가 켜져 있고 Visual Studio를 관리자 권한으로 실행하는 경우 Windows 탐색기 또는 파일 탐색기에서 끌기 작업이 차단됩니다. 이 문제를 해결하려면 둘 다 같은 관리자 권한으로 실행하거나 UAC를 해제합니다.

## <a name="see-specific-dependencies"></a><a name="SeeSpecificSource"></a> 특정 종속성 보기
 예를 들어 보류 중인 변경 내용이 있는 일부 파일에서 코드 검토를 수행하려는 경우 변경 내용의 종속성을 확인하려면 해당 파일에서 코드 맵을 만듭니다.

 ![코드 맵에 특성 종속성 표시](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

### <a name="see-specific-dependencies-in-your-solution"></a>솔루션의 특정 종속성 확인

1. **솔루션 탐색기**를 엽니다. 원하는 프로젝트, 어셈블리 참조, 폴더, 파일, 형식 및 멤버를 선택합니다. 형식이나 멤버에 대한 종속성을 포함하는 항목을 찾으려면 **솔루션 탐색기**에서 해당 형식 또는 멤버의 바로 가기 메뉴를 열고 종속성 형식을 선택하고 결과를 선택합니다.

2. 항목 및 해당 멤버를 매핑합니다. **솔루션 탐색기** 도구 모음에서 **코드 맵에 표시**를 클릭 하 여![선택한 노드에서 새 그래프 만들기 단추](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton")를 클릭 합니다.

     ![매핑할 항목 선택](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")

3. 맵에는 포함하는 어셈블리 내에서 선택한 항목이 표시됩니다.

     ![맵에 그룹으로 표시된 선택된 항목](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")

     솔루션 탐색기, 클래스 뷰 또는 개체 브라우저에서 신규 빈 코드 맵이나 기존 코드 맵으로 항목을 끌 수도 있습니다. 빈 맵을 만들려면 [빈 코드 맵 만들기](#GetStarted)를 참조하세요. 항목의 부모 계층 구조를 포함하려면 항목을 끄는 동안 **Ctrl** 키를 누르고 있거나, 코드 맵 도구 모음에서 **프로젝트 포함** 단추를 사용하여 기본 작업을 지정합니다.

    > [!NOTE]
    > Windows Phone 또는 Windows 스토어와 같은 여러 앱에 공유되는 프로젝트에서 항목을 추가할 경우 해당 항목은 현재 활성화된 앱 프로젝트와 함께 맵에 나타납니다. 다른 앱 프로젝트에 대한 컨텍스트를 변경하고 공유 프로젝트의 항목을 추가하면 해당 항목이 새로 활성화된 앱 프로젝트와 함께 나타납니다. 맵의 항목에 수행하는 작업은 동일한 컨텍스트를 공유하는 항목에만 적용됩니다.

4. 항목을 탐색하려면 해당 항목을 확장합니다. 항목을 확장하려면 항목 위로 마우스 포인터를 이동한 다음 펼침 단추(아래쪽 화살표) 아이콘이 나타나면 클릭합니다.

     ![코드 맵에서 노드 확장](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

     모든 항목을 확장하려면 **Ctrl+A**를 눌러 모든 항목을 선택하고 맵에 대한 바로 가기 메뉴를 연 다음 **그룹**, **확장**을 차례로 선택합니다. 그러나 이 옵션은 모든 그룹을 확장할 때 사용할 수 없는 맵 또는 메모리 문제가 발생하는 경우 사용할 수 없습니다.

5. 필요하면 클래스 및 멤버 수준 바로 아래쪽으로 원하는 항목을 계속 확장합니다.

     ![클래스 및 멤버 수준으로 그룹 확장](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")

     코드에 있지만 맵에 표시 되지 않는 멤버를 확인 하려면 그룹의 왼쪽 위 모퉁이에 있는 **다시 페치 자식** 아이콘 ![다시 페치 자식 아이콘](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") 을 클릭 합니다.

6. 맵의 항목과 관련된 추가 항목을 확인하려면 항목을 선택하고, 코드 맵 도구 모음에서 **관련 항목 표시** 를 선택하고, 맵에 추가할 관련 항목 형식을 선택합니다. 또는 항목을 하나 이상 선택하고, 바로 가기 메뉴를 열고, 맵에 추가할 관련 항목 형식에 대한 **표시...** 옵션을 선택합니다. 예를 들면 다음과 같습니다.

     **어셈블리**인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**참조된 어셈블리 표시**|이 어셈블리가 참조하는 어셈블리를 추가합니다. **외부** 그룹에 외부 어셈블리가 나타납니다.|
    |**참조하는 어셈블리 표시**|솔루션에 이 어셈블리를 참조하는 어셈블리를 추가합니다.|

     **네임스페이스**인 경우 **포함하는 어셈블리 표시**를 선택합니다(표시되지 않을 경우).

     **클래스** 또는 **인터페이스**인 경우 다음을 선택합니다.

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

     **메서드**인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**호출된 메서드 표시**|이 메서드가 호출하는 메서드를 추가합니다.|
    |**참조된 필드 표시**|이 메서드가 참조하는 필드를 추가합니다.|
    |**포함하는 형식 표시**|부모 형식을 추가합니다.|
    |**포함하는 형식, 네임스페이스 및 어셈블리 표시**|부모 컨테이너 계층 구조를 추가합니다.|
    |**재정의된 메서드 표시**|다른 메서드를 재정의하거나 인터페이스 메서드를 구현하는 메서드의 경우 재정의된 기본 클래스에 모든 추상 메서드 또는 가상 메서드를 추가하고 구현된 인터페이스 메서드를 추가합니다(있는 경우).|

     **필드** 또는 **속성**인 경우 다음을 선택합니다.

    |옵션|설명|
    |-|-|
    |**포함하는 형식 표시**|부모 형식을 추가합니다.|
    |**포함하는 형식, 네임스페이스 및 어셈블리 표시**|부모 컨테이너 계층 구조를 추가합니다.|

     ![이 멤버에 의해 호출된 메서드 표시](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")

7. 맵에 관계가 표시됩니다. 이 예제에서는 `Find` 메서드를 통해 호출되는 메서드와 솔루션 내부 또는 외부에서 해당 위치를 나타냅니다.

     ![코드 맵에 특성 종속성 표시](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

8. 맵을 단순화하고 개별 파트에 포커스를 지정하려면 코드 맵 도구 모음에서 **필터** 를 선택하고 원하는 노드 및 링크의 형식만 선택합니다. 예를 들어 솔루션 폴더, 어셈블리 및 네임스페이스의 표시를 해제합니다.

     ![필터 창을 사용하여 디스플레이 단순화](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")

## <a name="see-dependencies-between-c-and-c-source-files-and-header-files"></a><a name="SeeSourceHeader"></a> C 및 c + + 소스 파일과 헤더 파일 간의 종속성을 참조 하세요.
 C++ 프로젝트에 대해 보다 완전한 맵을 만들려면 해당 프로젝트에 대해 찾아보기 정보 컴파일러 옵션(**/FR**)을 설정합니다. [/FR, /Fr (Create .Sbr File)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896)를 참조하세요. 그렇지 않으면 메시지가 표시되고 이 옵션을 설정하라는 메시지가 나타납니다. **확인**을 선택하면 현재 맵에 대해서만 옵션이 설정됩니다. 이후 모든 맵에 대해 메시지를 숨기도록 선택할 수 있습니다. 이 메시지를 숨기는 경우 다시 표시되도록 설정할 수 있습니다. 이렇게 하려면 다음 레지스트리 키를 `0` 으로 설정하거나 해당 키를 삭제합니다.

 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**

 Visual C++ 프로젝트가 포함된 솔루션을 열 때 IntelliSense 데이터베이스를 업데이트하는 데 시간이 걸릴 수 있습니다. 이 동안에는 IntelliSense 데이터베이스가 업데이트를 완료할 때까지 헤더 파일(.h 또는 `#include`)에 관한 코드 맵을 만들 수 없습니다. Visual Studio 상태 표시줄에서 업데이트 진행률을 모니터링할 수 있습니다. 특정 IntelliSense 설정을 사용할 수 없으므로 나타나는 문제 또는 메시지를 해결하려면 [C 및 C++ 코드의 맵 문제 해결](#Troubleshooting)을 참조하세요.

- 솔루션의 모든 소스 파일과 헤더 파일 간 종속성을 확인하려면 **아키텍처** 메뉴에서 **포함 파일의 그래프 생성**을 클릭합니다.

     ![네이티브 코드의 종속성 그래프](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")

- 현재 열려 있는 파일과 관련 소스 파일 및 헤더 파일 간의 종속성을 확인하려면 소스 파일이나 헤더 파일을 열고 파일 내 임의의 위치에서 파일 바로 가기 메뉴를 연 다음 **포함 파일의 그래프 생성**을 선택합니다.

     ![.H 파일의 첫 번째&#45;수준 종속성 그래프](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")

### <a name="troubleshoot-maps-for-c-and-c-code"></a><a name="Troubleshooting"></a> C 및 C++ 코드의 맵 문제 해결
 다음 항목은 C 및 C++ 코드에서 지원되지 않습니다.

- 기본 형식은 부모 계층 구조가 포함된 맵에 나타나지 않습니다.

- 대부분의 **표시** 메뉴 항목은 C 및 C++ 코드에 사용할 수 없습니다.

  C 및 C++ 코드의 코드 맵을 만들 때는 다음과 같은 문제가 발생할 수 있습니다.

|**문제점**|**가능한 원인**|**해결 방법**|
|---------------|------------------------|--------------------|
|코드 맵을 생성하지 못했습니다.|솔루션에 프로젝트가 성공적으로 만들어지지 않습니다.|발생한 빌드 오류를 수정하고 맵을 재생성합니다.|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**아키텍처** 메뉴에서 코드 맵을 생성 하려고 하면이 응답 하지 않습니다.|프로그램 데이터베이스 파일(.pdb)이 손상될 수 있습니다.<br /><br /> .pdb 파일에는 형식, 메서드 및 소스 파일 정보와 같은 디버깅 정보가 저장됩니다.|솔루션을 다시 빌드한 다음 다시 시도합니다.|
|IntelliSense 검색 데이터베이스에 대한 특정 설정을 사용할 수 없습니다.|특정 IntelliSense 설정을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**옵션** 대화 상자에서 사용하지 못할 수 있습니다.|설정을 사용할 수 있도록 설정합니다.<br /><br /> [옵션, 텍스트 편집기, C/c + +, 고급을](../ide/reference/options-text-editor-c-cpp-advanced.md)참조 하세요.|
|**알 수 없는 메서드** 라는 메시지가 메서드 노드에 나타납니다.<br /><br /> 이 문제는 메서드의 이름을 확인할 수 없기 때문에 발생합니다.|이진 파일에 기본 재배치 테이블이 없을 수 있습니다.|링커에서 **/FIXED:NO** 옵션을 설정합니다.<br /><br /> [/FIXED (Fixed Base Address)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5)를 참조하세요.|
||프로그램 데이터베이스 파일(.pdb)이 빌드되지 않았을 수 있습니다.<br /><br /> .pdb 파일에는 형식, 메서드 및 소스 파일 정보와 같은 디버깅 정보가 저장됩니다.|링커에서 **/DEBUG** 옵션을 설정합니다.<br /><br /> [/DEBUG (Generate Debug Info)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103)를 참조하세요.|
||.pdb 파일을 열 수 없거나 예상되는 위치에서 찾을 수 없습니다.|.pdb 파일이 예상되는 위치에 있는지 확인합니다.|
||디버그 정보가 .pdb 파일에서 제거되었습니다.|**/PDBSTRIPPED** 옵션이 링커에서 사용된 경우 전체 .pdb 파일을 대신 포함합니다.<br /><br /> [/PDBSTRIPPED (Strip Private Symbols)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55)를 참조하세요.|
||호출자가 함수가 아니며 이진 파일의 썽크이거나 데이터 섹션의 포인터입니다.|호출자가 썽크이면 썽크를 방지하기 위해 `_declspec(dllimport)` 를 사용해 봅니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [일반 규칙 및 제한 사항](https://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [__Declspec를 사용 하 여 함수 호출 가져오기 (dllimport)](https://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](https://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|

## <a name="make-code-maps-render-more-quickly"></a><a name="RenderMoreQuickly"></a> 코드 맵을 더 빠르게 렌더링
 맵을 처음으로 생성하는 경우 Visual Studio는 검색된 모든 종속성을 인덱싱합니다. 특히 대형 솔루션의 경우 이 프로세스에 다소 시간이 걸릴 수도 있지만 이후에는 성능이 개선됩니다. 코드가 변경되면 Visual Studio는 업데이트된 코드만 다시 인덱싱합니다. 맵 렌더링을 완료하는 데 걸리는 시간을 최소화하려면 다음을 고려합니다.

- [원하는 종속성만 매핑합니다.](#SeeSpecificSource)

- 전체 솔루션에 대한 맵을 생성하기 전에 솔루션 범위를 줄입니다.

- 코드 맵 도구 모음에서 **빌드 건너뛰기** 단추를 사용하여 솔루션에 대한 자동 빌드를 해제합니다.

- 코드 맵 도구 모음에서 **부모 포함** 단추를 사용하여 부모 항목의 자동 추가를 해제합니다.

- 코드 맵 파일을 직접 편집하여 필요하지 않은 노드 및 링크를 제거합니다. 맵을 변경해도 기본 코드에 영향을 미치지 않습니다. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

  ![빌드 건너뛰기 및 상위 포함 단추](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")

  Visual Studio는 1GB의 메모리로 실행할 수 있지만, Visual Studio가 코드 인덱스를 만들고 맵을 생성하는 동안 오래 지연되지 않도록 컴퓨터에 최소 2GB의 메모리가 있는 것이 좋습니다.

  프로젝트 항목의 **출력 디렉터리에 복사** 가 **항상 복사**로 설정된 경우 맵을 만들거나 솔루션 탐색기에서 맵으로 항목을 추가하는 데 더 오래 걸릴 수 있습니다. 이 경우 증분 빌드 및 Visual Studio에서 매번 프로젝트를 다시 빌드할 때마다 문제가 발생할 수 있습니다. 성능을 높이려면 이 속성을 **변경된 내용만 복사** 또는 `PreserveNewest`로 변경합니다. [Incremental Builds](../msbuild/incremental-builds.md)를 참조하세요.

  올바르게 빌드된 코드에 대해서만 완료된 맵에 종속성이 표시됩니다. 특성 구성 요소에 대해 빌드 오류가 발생하면 해당 오류가 맵에 나타납니다. 이 맵을 기반으로 아키텍처 관련 사항을 결정하기 전에 구성 요소가 실제로 빌드되는지와 해당 구성 요소에 종속성이 있는지를 확인해야 합니다.

## <a name="share-code-maps"></a><a name="SavingExporting"></a> 코드 맵 공유

### <a name="share-the-map-with-other-visual-studio-users"></a>다른 Visual Studio 사용자와 맵 공유
 **파일** 메뉴를 사용하여 맵을 저장합니다.

 또는

 맵을 특정 프로젝트의 일부로 저장 하려면 맵 도구 모음에서 **공유**, dgml을로 **이동** 을 차례로 선택 하 \<*CodeMapName*> **.dgml into**고 맵을 저장할 프로젝트를 선택 합니다.

 ![맵을 다른 프로젝트로 이동](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")

 Visual Studio는 맵을 Visual Studio Enterprise 및 Visual Studio Professional의 다른 사용자와 공유할 수 있는 .dgml 파일로 저장합니다.

> [!NOTE]
> Visual Studio Professional 사용자와 맵을 공유하기 전에 모든 그룹을 확장하고, 숨겨진 노드와 그룹 간 링크를 표시하고, 삭제된 노드 중 다른 작업자가 맵 상에서 볼 수 있도록 하려는 노드를 검색합니다. 그렇지 않으면 다른 사용자가 이러한 항목을 볼 수 없습니다.
>
> 모델링 프로젝트에 있거나 모델링 프로젝트에서 다른 위치로 복사된 맵을 저장할 때 다음 오류가 발생할 수 있습니다.
>
> "프로젝트 디렉터리 외부에 *fileName* 을 저장할 수 없습니다. 연결된 항목이 지원되지 않습니다."
>
> Visual Studio에서 오류가 표시되지만 저장된 버전이 만들어집니다. 이 오류가 발생하지 않게 하려면 모델링 프로젝트 외부에 맵을 만듭니다. 그런 다음 원하는 위치에 그래프를 저장할 수 있습니다. 파일을 솔루션의 다른 위치에 복사하고 저장해 보는 것으로는 문제가 해결되지 않습니다.

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>맵을 이미지로 내보내면 Microsoft Word나 PowerPoint 같이 다른 애플리케이션으로 그래프를 복사할 수 있습니다.

1. 코드 맵 도구 모음에서 **공유**, **이미지로 메일 보내기** 또는 **이미지 복사**를 선택합니다.

2. 이미지를 다른 애플리케이션에 붙여넣습니다.

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>맵을 XPS 파일로 내보내면 Internet Explorer 같이 XML 또는 XAML 뷰어에서 맵을 확인할 수 있습니다.

1. 코드 맵 도구 모음에서 **공유**, **이미지로 메일 보내기** 또는 **이식 가능한 XPS로 저장**을 선택합니다.

2. 파일을 저장할 위치를 찾습니다.

3. 코드 맵 이름을 지정합니다. 파일 **형식** 상자가 **xps 파일 ( \* .xps)** 로 설정 되어 있는지 확인 합니다. **저장**을 선택합니다.

## <a name="what-else-can-i-do"></a>어떻게 해야 하나요?

- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)

- [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)

- [DGML 파일을 편집하여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
