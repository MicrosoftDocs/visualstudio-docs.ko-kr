---
title: DGML(Directed Graph Markup Language) 참조
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2363e5131dd499dd85a5822ed15e2bfe473f1e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596638"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>DGML(Directed Graph Markup Language) 참조

DGML(Directed Graph Markup Language)은 시각화에 사용되고 복잡성 분석을 수행하는 데 사용되는 정보를 설명하며, Visual Studio에서 코드 맵을 지속하는 데 사용되는 형식입니다. 단순 XML을 사용하여 순환 및 비순환 방향이 지정된 그래프를 설명합니다. 방향이 지정된 그래프는 링크 또는 가장자리로 연결되는 노드의 집합입니다. 노드 및 링크를 사용하여 소프트웨어 프로젝트의 요소와 같은 네트워크 구조를 나타낼 수 있습니다.

일부 버전의 Visual Studio에서는 DGML 기능의 하위 집합만 지원 합니다. [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

> [!NOTE]
> .dgml 파일을 편집하는 경우 IntelliSense를 사용하면 각 요소 및 요소 값에 사용할 수 있는 특성을 식별할 수 있습니다. 특성에 색을 지정하려면 "Blue"와 같은 일반적인 색의 이름 또는 "#ffa0b1c3"과 같은 ARGB 16진수 값을 사용합니다. DGML은 WPF(Windows Presentation Foundation) 색 정의 형식의 일부를 사용합니다. 자세한 내용은 [Colors 클래스](/dotnet/api/system.windows.media.colors?view=netframework-4.8)를 참조 하세요.

## <a name="dgml-syntax"></a><a name="DGML"></a> DGML 구문

다음 표에서는 DGML에서 사용되는 요소 종류에 대해 설명합니다.

- `<DirectedGraph></DirectedGraph>`

   이 요소는 코드 맵(.dgml) 문서의 루트 요소입니다. 다른 모든 DGML 요소는 이 요소의 범위 내에 나타납니다.

   다음 목록에서는 포함할 수 있는 선택적 특성에 대해 설명합니다.

   `Background` -지도 배경의 색입니다.

   `BackgroundImage` -지도 배경으로 사용할 이미지 파일의 위치입니다.

   `GraphDirection` -맵이 트리 레이아웃 ()으로 설정 되 면 `Sugiyama` 대부분의 링크가 지정 된 방향, 즉,, 또는로 흐르도록 노드를 정렬 `TopToBottom` `BottomToTop` `LeftToRight` `RightToLeft` 합니다. [지도 레이아웃 변경](../modeling/browse-and-rearrange-code-maps.md#Selecting)을 참조 하세요.

   `Layout` -지도를 `None` , `Sugiyama` (트리 레이아웃), `ForceDirected` (빠른 클러스터) 또는 레이아웃으로 설정 `DependencyMatrix` 합니다. [지도 레이아웃 변경](../modeling/browse-and-rearrange-code-maps.md#Selecting)을 참조 하세요.

   `NeighborhoodDistance` -맵이 트리 레이아웃 또는 빠른 클러스터 레이아웃으로 설정 되 면 선택한 노드에서 지정 된 링크 수 (1-7) 만큼 떨어진 노드만 표시 합니다. [지도 레이아웃 변경](../modeling/browse-and-rearrange-code-maps.md#Selecting)을 참조 하세요.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   이 요소는 맵의 노드를 정의하는 `<Node/>` 요소 목록을 포함하는 선택적 요소입니다. 자세한 내용은 `<Node/>` 요소를 참조하십시오.

  > [!NOTE]
  > `<Link/>` 요소에서 정의되지 않은 노드를 참조하는 경우 맵에서 `<Node/>` 요소를 자동으로 만듭니다.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   이 요소는 단일 노드를 정의합니다. 또한 `<Nodes><Nodes/>` 요소 목록 내에 나타납니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Id` - `Label` 별도의 특성을 지정 하지 않은 경우 노드의 고유 이름과 특성의 기본값입니다 `Label` . 이 이름은 노드를 참조하는 링크의 `Source` 또는 `Target` 특성과 일치해야 합니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` -노드의 표시 이름입니다.

   스타일 특성. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   `Category` -이 특성을 공유 하는 요소를 식별 하는 범주 이름입니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   `Property` -속성 값이 동일한 요소를 식별 하는 속성의 이름입니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   `Group` - 노드에 다른 노드가 포함된 경우 이 특성을 `Expanded` 또는 `Collapsed`로 설정하여 노드의 내용을 표시하거나 숨길 수 있습니다. `<Link/>` 특성을 포함하고, 부모 노드와 자식 노드를 각각 소스 노드와 대상 노드로 지정하는 `Category="Contains"` 요소가 있어야 합니다. [그룹 코드 요소](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes)를 참조 하세요.

   `Visibility` -이 특성을 `Visible` , 또는로 설정 `Hidden` `Collapsed` 합니다. `System.Windows.Visibility`를 사용합니다. [노드 및 링크 숨기기 또는 표시를](../modeling/browse-and-rearrange-code-maps.md#HidingShowing)참조 하세요.

   `Reference` - 이 특성을 문서 또는 URL에 대한 링크로 설정합니다. [코드 요소 및 링크에 문서 또는 Url 링크를](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences)참조 하세요.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   이 요소에는 노드 간의 링크를 정의하는 `<Link>` 요소 목록이 포함됩니다. 자세한 내용은 `<Link/>` 요소를 참조하십시오.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   이 요소는 소스 노드를 대상 노드에 연결하는 단일 링크를 정의합니다. 또한 `<Links></Links>` 요소 목록 내에 나타납니다.

  > [!NOTE]
  > 이 요소가 정의되지 않은 노드를 참조하는 경우 맵 문서에서는 지정된 특성을 포함하는 노드를 자동으로 만듭니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Source` -링크의 소스 노드입니다.

   `Target` - 링크의 대상 노드입니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` -링크의 표시 이름

   스타일 특성. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   `Category` -이 특성을 공유 하는 요소를 식별 하는 범주 이름입니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   `Property` -속성 값이 동일한 요소를 식별 하는 속성의 이름입니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   이 요소에는 `<Category/>` 요소 목록이 포함됩니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   이 요소는 이 특성을 공유하는 요소를 식별하는 데 사용되는 `Category` 특성을 정의합니다. `Category` 특성을 사용하면 맵 요소를 구성하고, 공유된 특성을 상속을 통해 제공하거나 추가 메타데이터를 정의할 수 있습니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Id` - `Label` 특성이 별도로 지정되지 않은 경우 `Label` 특성의 기본값 및 범주의 고유 이름입니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` - 읽기 쉬운 형식의 범주 이름입니다.

   `BasedOn` -현재 요소의이 상속 되는 부모 범주 `<Category/>` 입니다.

   이 요소의 예제에서 `FailedTest` 범주는 `Stroke` 범주에서 `PassedTest` 특성을 상속합니다. [DGML 파일을 편집 하 여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)에서 "계층적 범주를 만들려면"을 참조 하세요.

   또한 범주는 노드 및 링크가 맵에 표시되는 모양을 제어하는 몇 가지 기본적인 템플릿 동작을 제공합니다. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   이 요소에는 `<Property/>` 요소 목록이 포함됩니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   이 요소는 범주 및 기타 속성을 포함하여 DGML 요소 또는 특성에 값을 할당할 때 사용할 수 있는 `Property` 특성을 정의합니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

  - `Id` - `Label` 별도의 특성을 지정 하지 않은 경우 속성의 고유 이름과 특성의 기본값입니다 `Label` .

  - `DataType` -속성에 의해 저장 되는 데이터의 형식입니다.

    **속성을 속성 창에** 표시 하려면 속성을 사용 하 여 속성 `Label` 의 표시 이름을 지정 합니다.

    [코드 요소 및 링크에 범주 할당을](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories)참조 하세요.

    예:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="aliases-for-commonly-used-paths"></a><a name="AddAlias"></a> 일반적으로 사용 되는 경로에 대 한 별칭

일반적으로 사용되는 경로를 별칭으로 바꾸면 .dgml 파일의 크기뿐만 아니라 파일을 로드하거나 저장하는 데 필요한 시간을 줄일 수 있습니다. 별칭을 만들려면 .dgml 파일의 끝에 `<Paths></Paths>` 섹션을 추가합니다. 다음과 같이 이 섹션에서 `<Path/>` 요소를 추가하여 경로의 별칭을 정의합니다.

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

.Dgml 파일의 요소에서 별칭을 참조 하려면 `Id` \<Path/> 요소의를 달러 기호 ($) 및 괄호 (())로 묶습니다.

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>참조

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)
