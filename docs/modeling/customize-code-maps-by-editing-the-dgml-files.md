---
title: Customize code maps by editing the DGML files
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24afbfcfe31de52ac51329bb67df41cc59dd6f1e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547279"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Customize code maps by editing the DGML files

코드 맵을 사용자 지정 하려면 해당 사용자의 지시 된 Graph Markup Language (.dgml) 파일을 편집 하면 됩니다. 예를 들어 요소를 편집하여 사용자 지정 스타일을 지정하거나, 코드 요소와 링크에 속성 및 범주를 할당하거나, 코드 요소 또는 링크에 문서 또는 URL을 연결할 수 있습니다. DGML 요소에 대 한 자세한 내용은 [dgml (방향이 지정 된 그래프 태그 언어) 참조](../modeling/directed-graph-markup-language-dgml-reference.md)를 참조 하세요.

텍스트 또는 XML 편집기에서 코드 맵의 .dgml 파일을 편집합니다. 맵이 Visual Studio 솔루션의 일부인 경우 **솔루션 탐색기**에서 선택 하 고 바로 가기 메뉴를 연 다음 **연결 프로그램**, **XML (텍스트) 편집기**를 선택 합니다.

> [!NOTE]
> 코드 맵을 만들려면 Visual Studio Enterprise edition이 있어야 합니다. Visual Studio에서 코드 맵을 편집하는 경우 .dgml 파일을 저장할 때 사용되지 않는 DGML 요소와 특성이 삭제되어 정리됩니다. 또한 수동으로 새 링크를 추가하는 경우 자동으로 코드 요소가 생성됩니다. .dgml 파일을 저장하면 사용자가 요소에 추가한 특성이 사전순으로 자동으로 재배열됩니다.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a>그룹 코드 요소
 새 그룹을 추가하거나 기존 노드를 그룹으로 변환할 수 있습니다.

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 코드 요소를 그룹으로 변환하려면 해당 코드 요소에 대한 `<Node/>` 요소를 찾습니다.

    \- 또는 -

    새 그룹을 추가하려면 `<Nodes>` 섹션을 찾습니다. 새 `<Node/>` 요소를 추가합니다.

3. `<Node/>` 요소에 `Group` 특성을 추가하여 그룹을 확장된 상태로 표시할지 축소된 상태로 표시할지를 지정합니다. 예를 들면 다음과 같습니다.

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. `<Links>` 섹션에서 그룹 코드 요소와 자식 코드 요소 간의 각 관계에 대해 다음 특성을 가진 `<Link/>` 요소가 있는지 확인합니다.

   - 그룹 코드 요소를 지정하는 `Source` 특성

   - 자식 코드 요소를 지정하는 `Target` 특성

   - 그룹 코드 요소와 자식 코드 요소 간의 `Category` 관계를 지정하는 `Contains` 특성

     예를 들면 다음과 같습니다.

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    특성에 대 한 자세한 내용은 `Category` [코드 요소 및 링크에 범주 할당](#AssignCategories)을 참조 하세요.

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a>지도의 스타일 변경
 맵의 .dgml 파일을 편집하여 맵의 배경색과 테두리 색을 변경할 수 있습니다. 코드 요소 및 링크 스타일을 변경 하려면 [코드 요소 및 링크 스타일 변경](#Highlight)을 참조 하세요.

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. `<DirectedGraph>` 요소에 다음 특성을 추가하여 그래프 스타일을 변경합니다.

     배경색

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     테두리 색

    ```xml
    Stroke="StrokeValue"
    ```

     예를 들면 다음과 같습니다.

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a>코드 요소 및 링크 스타일 변경

### <a name="CreateCustomStyles"></a>
 다음 코드 요소에 사용자 지정 스타일을 적용할 수 있습니다.

- 단일 코드 요소 및 링크

- 코드 요소 및 링크 그룹

- 특정 조건을 기반으로 한 코드 요소 및 링크 그룹

> [!TIP]
> 스타일이 여러 코드 요소 또는 링크에서 반복되는 경우 코드 요소 또는 링크에 범주를 적용한 다음 해당 범주에 스타일을 적용하는 것이 좋습니다. 자세한 내용은 [코드 요소 및 링크에 범주 할당](#AssignCategories) 및 [코드 요소 및 링크에 속성 할당](#AssignProperties)을 참조 하세요.

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>단일 코드 요소에 사용자 지정 스타일을 적용하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 코드 요소의 `<Node/>` 요소를 찾습니다. 다음 특성을 추가하여 스타일을 사용자 지정합니다.

     배경색

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     윤곽선

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     윤곽선 두께

    ```xml
    StrokeThickness="StrokeValue"
    ```

     텍스트 색

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     아이콘

    ```xml
    Icon="IconFilePathLocation"
    ```

     텍스트 크기

    ```xml
    FontSize="FontSizeValue"
    ```

     텍스트 형식

    ```xml
    FontFamily="FontFamilyName"
    ```

     텍스트 두께

    ```xml
    FontWeight="FontWeightValue"
    ```

     텍스트 스타일

    ```xml
    FontStyle="FontStyleName"
    ```

     예를 들어 텍스트 스타일로 `Italic`을 지정할 수 있습니다.

     질감

    ```xml
    Style="Glass"
    ```

     - 또는

    ```xml
    Style="Plain"
    ```

     셰이프

     모양을 아이콘으로 바꾸려면 `Shape` 속성을 `None`으로 설정하고 `Icon` 속성을 아이콘 파일 경로로 설정합니다.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     예를 들면 다음과 같습니다.

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>단일 링크에 사용자 지정 스타일을 적용하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 소스 코드 요소의 이름과 대상 코드 요소의 이름을 둘 다 포함하는 `<Link/>` 요소를 찾습니다.

3. `<Link/>` 요소에 다음 특성을 추가하여 노드 스타일을 사용자 지정합니다.

     개요 및 화살표 색

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     윤곽선 두께

    ```xml
    StrokeThickness="StrokeValue"
    ```

     윤곽선 스타일

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     예를 들면 다음과 같습니다.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>코드 요소 또는 링크 그룹에 사용자 지정 스타일을 적용하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. `<Styles></Styles>` 요소가 없으면 `<DirectedGraph></DirectedGraph>` 요소 아래의 `<Links></Links>` 요소 다음에 이 요소를 추가합니다.

3. `<Styles></Styles>` 요소의 `<Style/>` 요소 아래에서 다음 특성을 지정합니다.

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     모든 대상 유형에 사용자 지정 스타일을 적용하려면 조건을 사용하지 않습니다.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>코드 요소 또는 링크 그룹에 조건부 스타일을 적용하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. `<Style/>` 요소에 `<Condition/>` 특성이 포함된 `Expression` 요소를 추가하여 부울 값을 반환하는 식을 지정합니다.

    예를 들면 다음과 같습니다.

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - 또는

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - 또는

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    이 식에서는 다음과 같은 BNF(Backus-Naur Form) 구문을 사용합니다.

    \<Expression>:: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124;\<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression>::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-"\<Expression>

    \<Operator>:: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "또는" &#124; "및" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings>:: = \<MemberBindings> &#124; \<MemberBinding> "."\<MemberBinding>

    \<MemberBinding>:: = \<MethodCall> &#124;\<PropertyGet>

    \<MethodCall>::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet>:: = 식별자

    \<MethodArgs>:: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124;\<empty>

    \<Identifier>::= [^. ]*

    \<Literal>:: = 작은따옴표 또는 큰따옴표로 묶은 문자열 리터럴입니다.

    \<Number>:: = 선택적 소수점이 있는 숫자 문자열

    `<Condition/>`스타일을 적용 하려면 모두 true 여야 하는 여러 요소를 지정할 수 있습니다.

3. `<Condition/>` 요소의 다음 줄에서 한 개 또는 여러 개의 `<Setter/>` 요소를 추가하여 조건을 만족하는 맵, 코드 요소 또는 링크에 적용할 `Property` 특성과 고정 `Value` 특성 또는 계산된 `Expression` 특성을 지정합니다.

    예를 들면 다음과 같습니다.

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   이러한 단계를 모두 보여 주는 간단한 예로, 다음 조건은 코드 요소의 `Passed` 범주가 `True`로 설정되었는지 `False`로 설정되었는지에 따라 코드 요소가 녹색 또는 빨간색으로 나타나도록 지정합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 다음 표에는 사용할 수 있는 조건의 몇 가지 예가 나와 있습니다.

 글꼴 크기를 코드 줄 수의 함수로 설정합니다. 이 경우 코드 요소 크기도 변경됩니다. 이 예제에서는 단일 조건식을 사용하여 여러 속성, 즉 `FontSize`와 `FontFamily`를 설정합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 `Coverage` 속성에 따라 코드 요소의 배경색을 설정합니다. 스타일은 `if-else` 문과 마찬가지로 나타나는 순서대로 확인됩니다.

 이 예제에서:

1. `Coverage`가 > 80 이면 `Background` 속성을 녹색으로 설정 합니다.

2. Else `Coverage` 가 50 > 경우 속성 `Background` 의 값을 기준으로 속성을 주황색 음영으로 설정 합니다 `Coverage` .

3. 또한 `Background` 속성은 `Coverage` 속성 값에 따라 빨간색 음영으로 설정합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 모양이 아이콘으로 대체되도록 `Shape` 속성을 `None`으로 설정합니다. `Icon` 속성을 사용하여 아이콘 위치를 지정합니다.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a>코드 요소 및 링크에 속성 할당
 속성을 할당하여 코드 요소 및 링크를 구성할 수 있습니다. 예를 들어 속성에 따라 코드 요소를 그룹화하거나, 스타일을 변경하거나, 숨길 수 있도록 특정 속성을 가진 코드 요소를 선택할 수 있습니다.

#### <a name="to-assign-a-property-to-a-code-element"></a>코드 요소에 속성을 할당하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 해당 코드 요소에 대한 `<Node/>` 요소를 찾습니다. 속성 이름 및 해당 값을 지정합니다. 예를 들면 다음과 같습니다.

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. `<Property/>` 섹션에 `<Properties>` 요소를 추가하여 표시 이름 및 데이터 형식 등의 특성을 지정합니다.

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>링크에 속성을 할당하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 소스 코드 요소의 이름과 대상 코드 요소의 이름을 둘 다 포함하는 `<Link/>` 요소를 찾습니다.

3. `<Node/>` 요소에서 속성 이름 및 해당 값을 지정합니다. 예를 들면 다음과 같습니다.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. `<Property/>` 섹션에 `<Properties>` 요소를 추가하여 표시 이름 및 데이터 형식 등의 특성을 지정합니다.

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a>코드 요소 및 링크에 범주 할당
 다음 섹션에서는 코드 요소에 범주를 할당하여 구성하는 방법 및 코드 요소 구성에 도움이 되는 계층적 범주를 만들고 상속을 사용하여 자식 범주에 특성을 추가하는 방법을 보여 줍니다.

#### <a name="to-assign-a-category-to-a-code-element"></a>코드 요소에 범주를 할당하려면

- 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

- 원하는 코드 요소에 대한 `<Node/>` 요소를 찾습니다.

- `<Node/>` 요소에 `Category` 특성을 추가하여 범주 이름을 지정합니다. 예를 들면 다음과 같습니다.

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     `<Category/>` 특성을 사용하여 범주의 표시 텍스트를 지정할 수 있도록 `<Categories>` 섹션에 `Label` 요소를 추가합니다.

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>링크에 범주를 할당하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 소스 코드 요소의 이름과 대상 코드 요소의 이름을 둘 다 포함하는 `<Link/>` 요소를 찾습니다.

3. `<Link/>` 요소에 `Category` 특성을 추가하여 범주 이름을 지정합니다. 예를 들면 다음과 같습니다.

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. `<Category/>` 특성을 사용하여 범주의 표시 텍스트를 지정할 수 있도록 `<Categories>` 섹션에 `Label` 요소를 추가합니다.

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>계층적 범주를 만들려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 부모 범주에 대한 `<Category/>` 요소를 추가한 다음 자식 범주의 `BasedOn` 요소에 `<Category/>` 특성을 추가합니다.

     예를 들면 다음과 같습니다.

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     이 예제에서 `MyFirstNode`의 `Category` 특성은 `Background`의 `MyParentCategory` 특성을 상속하므로 이 노드의 배경은 녹색입니다.

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a>코드 요소 및 링크에 문서 또는 Url 연결
 맵의 .dgml 파일을 편집하고 코드 요소에 대한 `Reference` 요소 또는 링크에 대한 `<Node/>` 요소에 `<Link/>` 특성을 추가하여 코드 요소 또는 링크에 문서 또는 URL을 연결할 수 있습니다. 그런 다음 코드 요소 또는 링크에서 해당 콘텐츠를 열고 볼 수 있습니다. `Reference` 특성은 해당 내용의 경로를 지정합니다. 이 경로는 .dgml 파일의 위치를 기준으로 하는 상대 경로이거나 절대 경로일 수 있습니다.

> [!CAUTION]
> 상대 경로를 사용할 경우 .dgml 파일을 다른 위치로 이동하면 해당 경로가 더 이상 확인되지 않습니다. 링크된 콘텐츠를 열고 보려고 시도하면 콘텐츠를 볼 수 없다는 오류가 발생합니다.

 예를 들어 다음과 같은 코드 요소를 연결할 수 있습니다.

- 클래스에 대한 변경 내용을 설명하기 위해 작업 코드 요소, 문서 또는 다른 .dgml 파일의 URL을 클래스의 코드 요소에 연결할 수 있습니다.

- 소프트웨어의 논리 아키텍처에서 레이어를 나타내는 그룹 코드 요소에 종속성 다이어그램을 연결할 수 있습니다.

- 인터페이스를 노출하는 구성 요소에 대한 자세한 정보가 표시되도록 해당 인터페이스의 코드 요소에 구성 요소 다이어그램을 연결할 수 있습니다.

- Team Foundation Server 작업 항목, 버그 또는 코드 요소와 관련된 다른 정보에 코드 요소를 연결합니다.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>코드 요소에 문서 또는 URL을 연결하려면

1. 텍스트 또는 XML 편집기에서 .dgml 파일을 엽니다.

2. 원하는 코드 요소에 대한 `<Node/>` 요소를 찾습니다.

3. 다음 표의 작업 중 하나를 수행합니다.

    단일 코드 요소

   - `<Node/>` 또는 `<Link/>` 요소에서 `Reference` 특성을 추가하여 코드 요소 위치를 지정합니다.

     > [!NOTE]
     > `Reference` 특성은 요소마다 하나씩만 있을 수 있습니다.

     예를 들면 다음과 같습니다.

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    여러 코드 요소

   1. `<Node/>` 또는 `<Link/>` 요소에 새 특성을 추가하여 각 참조의 위치를 지정합니다.

   2. `<Properties>` 섹션에서 다음 작업을 수행합니다.

      1. 각각의 새 참조 형식에 대해 `<Property/>` 요소를 추가합니다.

      2. `Id` 특성을 새 참조 특성의 이름으로 설정합니다.

      3. 특성을 추가 하 `IsReference` 고로 설정 `True` 하 여 해당 참조가 코드 요소의 **참조로 이동** 바로 가기 메뉴에 표시 되도록 합니다.

      4. 특성을 사용 `Label` 하 여 코드 요소의 **참조로 이동** 바로 가기 메뉴에서 표시 텍스트를 지정 합니다.

      예를 들면 다음과 같습니다.

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    맵에서 코드 요소 이름은 밑줄이 그어진 상태로 표시됩니다. 코드 요소 또는 링크에 대 한 바로 가기 메뉴를 열면 선택할 연결 된 코드 요소를 포함 하는 **참조로 이동** 바로 가기 메뉴가 표시 됩니다.

4. `ReferenceTemplate` 특성을 사용하여 URL 등의 일반 문자열을 지정합니다. 이 특성은 여러 참조에서 해당 문자열을 반복하는 대신 사용됩니다.

    `ReferenceTemplate` 특성은 참조 값의 자리 표시자를 지정합니다. 다음 예제에서는 `{0}` 특성의 `ReferenceTemplate` 자리 표시자가 `MyFirstReference` 요소의 `MySecondReference` 및 `<Node/>` 특성 값으로 바뀌어 전체 경로를 생성합니다.

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. 참조된 코드 요소 또는 맵의 코드 요소를 보려면 코드 요소 또는 링크에 대한 바로 가기 메뉴를 엽니다. **참조로 이동** 을 선택 하 고 코드 요소를 선택 합니다.

## <a name="see-also"></a>참조

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
- [DGML(Directed Graph Markup Language) 참조](../modeling/directed-graph-markup-language-dgml-reference.md)
