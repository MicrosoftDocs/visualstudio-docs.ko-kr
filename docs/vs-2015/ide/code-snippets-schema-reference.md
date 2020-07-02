---
title: 코드 조각 스키마 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67bc1a18b4e4cbfdf69fe917c0d0fdff09832983
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545030"
---
# <a name="code-snippets-schema-reference"></a>코드 조각 스키마 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense 코드 조각은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 애플리케이션에 삽입되도록 미리 작성된 코드 부분입니다. 코드 조각을 제공함으로써 반복 코드를 입력하거나 샘플 검색에 드는 시간을 줄여 생산성을 높일 수 있습니다. IntelliSense 코드 조각 XML 스키마를 사용하여 사용자 지정 코드 조각을 만들어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 이미 포함되어 있는 코드 조각에 추가할 수 있습니다.

## <a name="intellisense-code-snippets-schema-elements"></a>IntelliSense 코드 조각 스키마 요소

|요소|요소|요소|
|-|-|-|
|[Assembly 요소](../ide/code-snippets-schema-reference.md#assembly)|[HelpUrl 요소](../ide/code-snippets-schema-reference.md#helpurl)|[References 요소](../ide/code-snippets-schema-reference.md#references)|
|[Author 요소](../ide/code-snippets-schema-reference.md#author)|[ID 요소](../ide/code-snippets-schema-reference.md#id)|[바로 가기 요소](../ide/code-snippets-schema-reference.md#shortcut)|
|[Code 요소](../ide/code-snippets-schema-reference.md#code)|[Import 요소](../ide/code-snippets-schema-reference.md#import)|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|
|[CodeSnippet 요소](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports 요소](../ide/code-snippets-schema-reference.md#imports)|[SnippetType 요소](../ide/code-snippets-schema-reference.md#snippettype)|
|[CodeSnippets 요소](../ide/code-snippets-schema-reference.md#codesnippets)|[Keyword 요소](../ide/code-snippets-schema-reference.md#keyword)|[SnippetTypes 요소](../ide/code-snippets-schema-reference.md#snippettypes)|
|[선언 요소](../ide/code-snippets-schema-reference.md#declarations)|[Keywords 요소](../ide/code-snippets-schema-reference.md#keywords)|[Title 요소](../ide/code-snippets-schema-reference.md#title)|
|[Default 요소](../ide/code-snippets-schema-reference.md#default)|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|[ToolTip 요소](../ide/code-snippets-schema-reference.md#tooltip)|
|[Description 요소](../ide/code-snippets-schema-reference.md#description)|[Namespace 요소](../ide/code-snippets-schema-reference.md#namespace)|[Type 요소](../ide/code-snippets-schema-reference.md#type)|
|[Function 요소](../ide/code-snippets-schema-reference.md#function)|[Object 요소](../ide/code-snippets-schema-reference.md#object)|[Url 요소](../ide/code-snippets-schema-reference.md#url)|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|[Reference 요소](../ide/code-snippets-schema-reference.md#reference)||

## <a name="assembly-element"></a><a name="assembly"></a>Assembly 요소
 코드 조각이 참조하는 어셈블리의 이름을 지정합니다.

> [!NOTE]
> `Assembly` 요소는 Visual Basic 코드 조각에서만 지원됩니다.

 **Assembly** 요소의 텍스트 값은 이 어셈블리의 텍스트 이름(예: `System.dll`)이거나 강력한 이름(예: `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`)입니다.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Reference 요소](../ide/code-snippets-schema-reference.md#reference)|코드 조각에서 필요로 하는 어셈블리 참조에 대한 정보가 포함되어 있습니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각이 참조하는 어셈블리를 지정합니다.

## <a name="author-element"></a><a name="author"></a>Author 요소
 코드 조각 작성자의 이름을 지정합니다. **코드 조각 관리자**에는 코드 조각의 `Author` 요소에 저장된 이름이 표시됩니다.

```xml
<Author>
   Code Snippet Author
</Author>

```

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보가 포함되어 있습니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각의 작성자를 지정합니다.

## <a name="code-element"></a><a name="code"></a>Code 요소
 짧은 코드 블록에 대한 컨테이너를 제공합니다.

 `Code` 요소의 텍스트에는 `$end$` 및 `$selected$`의 두 예약어를 사용할 수 있습니다. `$end$`는 코드 조각을 삽입하고 나서 커서를 놓을 위치를 표시합니다. `$selected$`는 코드 조각을 호출하면 조각으로 삽입되는 문서에서 선택한 텍스트를 나타냅니다. 다음을 포함하는 코드 조각의 예를 들어 보겠습니다.

```xml
$selected$ is a great color.
```

 사용자가 템플릿을 호출할 때 "Blue"라는 단어를 선택하면 결과는 다음과 같이 표시됩니다.

```xml
Blue is a great color.
```

 `$end$` 또는 `$selected$`를 코드 조각 하나에서 두 번 이상 사용할 수는 없습니다. 이렇게 하면 두 번째 인스턴스만 인식됩니다. 이번에는 다음을 포함하는 코드 조각을 살펴보겠습니다.

```
$selected$ is a great color. I love $selected$.
```

 여기서는 "Blue"라는 단어를 선택하면 결과가 다음과 같이 표시됩니다.

```
is a great color. I love Blue.
```

 `$selected$` 및 `is` 사이에 공백이 있기 때문에 첫 번째 항목은 공백으로 표시됩니다.

 다른 모든 `$` 키워드는 `<Literal>` 및 `<Object>` 태그에서 동적으로 정의됩니다.

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

|특성|설명|
|---------------|-----------------|
|`Delimiter`|선택적 특성입니다. 코드의 리터럴 및 개체를 설명하는 데 사용되는 구분 기호를 지정합니다. 기본값으로 사용되는 구분 기호는 `$`입니다.|
|`Kind`|선택적 특성입니다. 코드 조각에 포함되는 코드 종류를 지정하고 코드 조각 컴파일을 위해 해당 코드 조각을 삽입해야 하는 위치를 지정합니다. 사용할 수 있는 값은 `method body`, `method decl`, `type decl`, `file` 및 `any`입니다.|
|`Language`|필수 특성입니다. 코드 조각의 언어를 지정합니다.|

|Kind 특성 값|Description|
|--------------------------|-----------------|
|`method body`|코드 조각이 메서드 본문이므로 메서드 선언 안에 삽입되도록 지정합니다.|
|`method decl`|코드 조각이 메서드이므로 클래스나 모듈 안에 삽입되도록 지정합니다.|
|`type decl`|코드 조각이 형식이므로 클래스, 모듈 또는 네임스페이스 안에 삽입되도록 지정합니다.|
|`file`|코드 조각이 완전한 코드 파일임을 지정합니다. 이러한 코드 조각은 코드 파일이나 네임스페이스 안에 단독으로 삽입될 수 있습니다.|
|`any`|코드 조각이 어디든지 삽입될 수 있도록 지정합니다. 이 태그는 주석과 같이 컨텍스트와 상관없는 코드 조각에 사용됩니다.|

|Language 특성 값|설명|
|------------------------------|-----------------|
|`VB`|Visual Basic 코드 조각을 식별합니다.|
|`CSharp`|C# 코드 조각을 식별합니다.|
|`CPP`|C++ 코드 조각을 식별합니다.|
|`XML`|XML 코드 조각을 식별합니다.|
|`JavaScript`|JavaScript 코드 조각을 식별합니다.|
|`SQL`|SQL 코드 조각을 식별합니다.|
|`HTML`|HTML 코드 조각을 식별합니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|코드 조각에 대한 참조, 가져오기, 선언 및 코드가 포함되어 있습니다.|

 텍스트 값은 필수입니다. 이 텍스트는 이 코드 조각이 프로젝트에 삽입될 때 사용할 수 있는 코드를 리터럴 및 개체와 함께 지정합니다.

## <a name="codesnippet-element"></a><a name="codesnippet"></a>CodeSnippet 요소
 Visual Studio Code 파일에 삽입할 수 있는 여러 IntelliSense 코드 조각 및 제목을 지정할 수 있습니다.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>

```

|특성|설명|
|---------------|-----------------|
|`Format`|필수 특성입니다. 코드 조각의 스키마 버전을 지정합니다. Format 특성은 x.x.x 구문의 문자열이어야 합니다. 여기서 각 "x"는 버전 번호의 숫자 값을 나타냅니다. Visual Studio에서는 이해할 수 없는 `Format` 특성을 갖는 코드 조각을 무시합니다.|

|자식 요소|설명|
|-------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|필수적 요소입니다. 코드 조각에 대한 일반 정보가 포함되어 있습니다. 하나의 코드 조각에는 `Header` 요소가 단 하나만 있어야 합니다.|
|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|필수적 요소입니다. Visual Studio에서 삽입할 코드가 포함되어 있습니다. 하나의 코드 조각에는 `Snippet` 요소가 단 하나만 있어야 합니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[CodeSnippets 요소](../ide/code-snippets-schema-reference.md#codesnippets)|코드 조각 XML 스키마의 루트 요소입니다.|

## <a name="codesnippets-element"></a><a name="codesnippets"></a>CodeSnippets 요소
 [CodeSnippet 요소](../ide/code-snippets-schema-reference.md#codesnippet)를 그룹화합니다. `CodeSnippets` 요소는 코드 조각 XML 스키마의 루트 요소입니다.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>

```

|자식 요소|설명|
|-------------------|-----------------|
|[CodeSnippet 요소](../ide/code-snippets-schema-reference.md#codesnippet)|선택적 요소입니다. 모든 코드 조각 데이터의 부모 요소입니다. `CodeSnippet` 요소에는 `CodeSnippets` 요소가 0개 또는 그 이상 있을 수 있습니다.|

## <a name="declarations-element"></a><a name="declarations"></a>선언 요소
 코드 조각에서 편집할 수 있는 부분을 구성하는 리터럴과 개체를 지정합니다.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>

```

|자식 요소|설명|
|-------------------|-----------------|
|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|선택적 요소입니다. 편집할 수 있는 코드 조각의 리터럴을 정의합니다. `Literal` 요소에는 `Declarations` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|선택적 요소입니다. 편집할 수 있는 코드 조각의 개체를 정의합니다. `Object` 요소에는 `Declarations` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|코드 조각에 대한 참조, 가져오기, 선언 및 코드가 포함되어 있습니다.|

## <a name="default-element"></a><a name="default"></a>Default 요소
 IntelliSense 코드 조각의 리터럴 또는 개체에 대한 기본값을 지정합니다.

```xml
<Default>
    Default value
</Default>

```

|부모 요소|설명|
|--------------------|-----------------|
|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|편집할 수 있는 코드 조각의 리터럴 필드를 정의합니다.|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|편집할 수 있는 코드 조각의 개체 필드를 정의합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 편집할 수 있는 코드 조각의 필드를 채우는 리터럴 또는 개체의 기본값을 지정합니다.

## <a name="description-element"></a><a name="description"></a>Description 요소
 IntelliSense 코드 조각의 콘텐츠에 대한 설명 정보를 지정합니다.

```xml
<Description>
    Code Snippet Description
</Description>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보가 포함되어 있습니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각을 설명합니다.

## <a name="function-element"></a><a name="function"></a>Function 요소
 Visual Studio에서 리터럴 또는 개체가 포커스를 받을 때 실행할 함수를 지정합니다.

> [!NOTE]
> `Function` 요소는 Visual C# 코드 조각에서만 지원됩니다.

```xml
<Function>
    FunctionName
</Function>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|편집할 수 있는 코드 조각의 리터럴 필드를 정의합니다.|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|편집할 수 있는 코드 조각의 개체 필드를 정의합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 Visual Studio에서 리터럴 또는 개체 필드가 포커스를 받을 때 실행할 함수를 지정합니다.

## <a name="header-element"></a><a name="header"></a>Header 요소
 IntelliSense 코드 조각에 대한 일반 정보를 지정합니다.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>

```

|자식 요소|설명|
|-------------------|-----------------|
|[Author 요소](../ide/code-snippets-schema-reference.md#author)|선택적 요소입니다. 코드 조각을 작성한 사람 또는 회사의 이름입니다. `Author` 요소에는 `Header` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[Description 요소](../ide/code-snippets-schema-reference.md#description)|선택적 요소입니다. 코드 조각에 대한 설명입니다. `Description` 요소에는 `Header` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[HelpUrl 요소](../ide/code-snippets-schema-reference.md#helpurl)|선택적 요소입니다. 코드 조각에 대한 추가 정보가 들어 있는 URL입니다. Header 요소에는 `HelpURL` 요소가 0개 또는 그 이상 있을 수 있습니다. **참고:**  Visual Studio에서는 `HelpUrl` 요소를 사용하지 않습니다. 이 요소는 IntelliSense 코드 조각 XML 스키마의 일부이며 이 요소를 포함하는 모든 코드 조각의 유효성이 검사되지만 요소의 값은 사용되지 않습니다.|
|[Keywords 요소](../ide/code-snippets-schema-reference.md#keywords)|선택적 요소입니다. `Keyword` 요소를 그룹화합니다. `Keywords` 요소에는 `Header` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[바로 가기 요소](../ide/code-snippets-schema-reference.md#shortcut)|선택적 요소입니다. 코드 조각을 삽입하는 데 사용할 수 있는 바로 가기 텍스트를 지정합니다. `Shortcut` 요소에는 `Header` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[SnippetTypes 요소](../ide/code-snippets-schema-reference.md#snippettypes)|선택적 요소입니다. `SnippetType` 요소를 그룹화합니다. `SnippetTypes` 요소에는 `Header` 요소가 0개 또는 그 이상 있을 수 있습니다. `SnippetTypes` 요소가 없으면 코드 조각은 항상 유효합니다.|
|[Title 요소](../ide/code-snippets-schema-reference.md#title)|필수적 요소입니다. 코드 조각의 이름입니다. 하나의 `Title` 요소에는 `Header` 요소가 단 하나만 있어야 합니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[CodeSnippet 요소](../ide/code-snippets-schema-reference.md#codesnippet)|모든 코드 조각 데이터의 부모 요소입니다.|

## <a name="helpurl-element"></a><a name="helpurl"></a>HelpUrl 요소
 코드 조각에 대한 자세한 정보를 제공하는 URL을 지정합니다.

> [!NOTE]
> Visual Studio에서는 `HelpUrl` 요소를 사용하지 않습니다. 이 요소는 IntelliSense 코드 조각 XML 스키마의 일부이며 이 요소를 포함하는 모든 코드 조각의 유효성이 검사되지만 요소의 값은 사용되지 않습니다.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>

```

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보가 포함되어 있습니다.|

 텍스트 값은 선택적입니다. 이 텍스트는 코드 조각에 대한 추가 정보를 얻기 위해 방문할 URL을 지정합니다.

## <a name="id-element"></a><a name="id"></a>ID 요소
 `Literal` 또는 `Object` 요소에 대한 고유 식별자를 지정합니다. 같은 코드 조각에서 두 개의 리터럴 또는 개체는 해당 `ID` 요소에 같은 텍스트 값을 가질 수 없습니다. 리터럴과 개체는 end 값을 가진 `ID` 요소를 포함할 수 없습니다. `$end$` 값은 예약되어 있으며, 코드 조각을 삽입하고 나서 커서를 놓을 위치를 표시하는 데 사용됩니다.

```xml
<ID>
    Unique Identifier
</ID>

```

|부모 요소|설명|
|--------------------|-----------------|
|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|편집할 수 있는 코드 조각의 리터럴 필드를 정의합니다.|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|편집할 수 있는 코드 조각의 개체 필드를 정의합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 개체 또는 리터럴의 고유 식별자를 지정합니다.

## <a name="import-element"></a><a name="import"></a>Import 요소
 IntelliSense 코드 조각에서 사용되는 가져온 네임스페이스를 지정합니다.

> [!NOTE]
> `Import` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>

```

|자식 요소|설명|
|-------------------|-----------------|
|[Namespace 요소](../ide/code-snippets-schema-reference.md#namespace)|필수적 요소입니다. 코드 조각에서 사용되는 네임스페이스를 지정합니다. 하나의 `Namespace` 요소에는 `Import` 요소가 단 하나만 있어야 합니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[Imports 요소](../ide/code-snippets-schema-reference.md#imports)|**Import** 요소에 대한 grouping 요소입니다.|

## <a name="imports-element"></a><a name="imports"></a>Imports 요소
 개별 `Import` 요소를 그룹화합니다.

> [!NOTE]
> `Imports` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<Imports>
    <Import>... </Import>
<Imports>
```

|자식 요소|설명|
|-------------------|-----------------|
|[Import 요소](../ide/code-snippets-schema-reference.md#import)|선택적 요소입니다. 코드 조각에 대해 가져온 네임스페이스가 포함되어 있습니다. `Imports` 요소에는 **Import** 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|코드 조각에 대한 참조, 가져오기, 선언 및 코드가 포함되어 있습니다.|

## <a name="keyword-element"></a><a name="keyword"></a>Keyword 요소
 코드 조각에 대한 사용자 지정 키워드를 지정합니다. Visual Studio에서 코드 조각 키워드는 온라인 콘텐츠 공급자가 검색 또는 분류용으로 사용자 지정 키워드를 추가하기 위한 표준 방법을 나타내는 데 사용됩니다.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Keywords 요소](../ide/code-snippets-schema-reference.md#keywords)|개별 `Keyword` 요소를 그룹화합니다.|

 텍스트 값은 필수입니다. 코드 조각에 대한 키워드입니다.

## <a name="keywords-element"></a><a name="keywords"></a>Keywords 요소
 개별 `Keyword` 요소를 그룹화합니다. Visual Studio에서 코드 조각 키워드는 온라인 콘텐츠 공급자가 검색 또는 분류용으로 사용자 지정 키워드를 추가하기 위한 표준 방법을 나타내는 데 사용됩니다.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
<Keywords>
```

|자식 요소|설명|
|-------------------|-----------------|
|[Keyword 요소](../ide/code-snippets-schema-reference.md#keyword)|선택적 요소입니다. 코드 조각에 대한 개별 키워드가 포함되어 있습니다. `Keyword` 요소에는 `Keywords` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보가 포함되어 있습니다.|

## <a name="literal-element"></a><a name="literal"></a>Literal 요소
 편집할 수 있는 코드 조각의 리터럴을 정의합니다. `Literal` 요소는 코드 조각에 완전히 포함되어 있으나 코드에 삽입된 후 사용자 지정될 대체 코드 부분을 식별하는 데 사용됩니다. 예를 들어, 리터럴 문자열, 숫자 값 및 일부 변수 이름은 리터럴로 선언해야 합니다.

 리터럴과 개체는 selected 또는 end 값인 **ID** 요소를 포함할 수 없습니다. 값 `$selected$`는 코드 조각을 호출하면 조각으로 삽입되는 문서에서 선택한 텍스트를 나타냅니다. `$end$`는 코드 조각을 삽입하고 나서 커서를 놓을 위치를 표시합니다.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|특성|설명|
|---------------|-----------------|
|`Editable`|선택적 `Boolean` 특성입니다. 코드 조각을 삽입한 이후에 리터럴을 편집할 수 있는지 여부를 지정합니다. 이 특성의 기본값은 `true`입니다.|

|자식 요소|설명|
|-------------------|-----------------|
|[Default 요소](../ide/code-snippets-schema-reference.md#default)|필수적 요소입니다. 코드 조각을 삽입할 때 리터럴의 기본값을 지정합니다. 하나의 `Default` 요소에는 `Literal` 요소가 단 하나만 있어야 합니다.|
|[Function 요소](../ide/code-snippets-schema-reference.md#function)|선택적 요소입니다. Visual Studio에서 리터럴이 포커스를 받을 때 실행할 함수를 지정합니다. `Function` 요소에는 `Literal` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[ID 요소](../ide/code-snippets-schema-reference.md#id)|필수적 요소입니다. 리터럴의 고유 식별자를 지정합니다. 하나의 `ID` 요소에는 `Literal` 요소가 단 하나만 있어야 합니다.|
|[ToolTip 요소](../ide/code-snippets-schema-reference.md#tooltip)|선택적 요소입니다. 리터럴의 예상 값과 사용법을 설명합니다. `Literal` 요소에는 **Tooltip** 요소가 0개 또는 1개 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[선언 요소](../ide/code-snippets-schema-reference.md#declarations)|편집할 수 있는 코드 조각의 리터럴과 개체가 포함되어 있습니다.|

## <a name="namespace-element"></a><a name="namespace"></a>Namespace 요소
 코드 조각이 컴파일 및 실행될 수 있도록 가져와야 하는 네임스페이스를 지정합니다. `Namespace` 요소에 지정된 네임스페이스가 아직 없는 경우 코드의 시작 부분에 있는 `Imports` 문에 자동으로 추가됩니다.

> [!NOTE]
> `Namespace` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<Namespace>
    Namespace
</Namespace>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Import 요소](../ide/code-snippets-schema-reference.md#import)|지정된 네임스페이스를 가져옵니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각이 가정하는 네임스페이스를 가져오도록 지정합니다.

## <a name="object-element"></a><a name="object"></a>Object 요소
 편집할 수 있는 코드 조각의 개체를 정의합니다. `Object` 요소는 코드 조각에서 필요하지만 코드 조각 자체의 외부에서 정의될 항목을 식별하는 데 사용됩니다. 예를 들어, Windows Forms 컨트롤, ASP.NET 컨트롤, 개체 인스턴스 및 형식 인스턴스는 개체로 선언되어야 합니다. 개체 선언에는 형식이 지정되어야 하며, 이 형식은 `Type` 요소를 사용하여 지정합니다.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|특성|설명|
|---------------|-----------------|
|`Editable`|선택적 `Boolean` 특성입니다. 코드 조각을 삽입한 이후에 리터럴을 편집할 수 있는지 여부를 지정합니다. 이 특성의 기본값은 `true`입니다.|

|자식 요소|설명|
|-------------------|-----------------|
|[Default 요소](../ide/code-snippets-schema-reference.md#default)|필수적 요소입니다. 코드 조각을 삽입할 때 리터럴의 기본값을 지정합니다. 하나의 `Default` 요소에는 `Literal` 요소가 단 하나만 있어야 합니다.|
|[Function 요소](../ide/code-snippets-schema-reference.md#function)|선택적 요소입니다. Visual Studio에서 리터럴이 포커스를 받을 때 실행할 함수를 지정합니다. `Function` 요소에는 `Literal` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[ID 요소](../ide/code-snippets-schema-reference.md#id)|필수적 요소입니다. 리터럴의 고유 식별자를 지정합니다. 하나의 `ID` 요소에는 `Literal` 요소가 단 하나만 있어야 합니다.|
|[ToolTip 요소](../ide/code-snippets-schema-reference.md#tooltip)|선택적 요소입니다. 리터럴의 예상 값과 사용법을 설명합니다. `Literal` 요소에는 **Tooltip** 요소가 0개 또는 1개 있을 수 있습니다.|
|[Type 요소](../ide/code-snippets-schema-reference.md#type)|필수적 요소입니다. 개체의 형식을 지정합니다. 하나의 `Type` 요소에는 `Object` 요소가 단 하나만 있어야 합니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[선언 요소](../ide/code-snippets-schema-reference.md#declarations)|편집할 수 있는 코드 조각의 리터럴과 개체가 포함되어 있습니다.|

## <a name="reference-element"></a><a name="reference"></a>Reference 요소
 코드 조각에 필요한 어셈블리 참조에 대한 정보를 지정합니다.

> [!NOTE]
> `Reference` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|자식 요소|설명|
|-------------------|-----------------|
|[Assembly 요소](../ide/code-snippets-schema-reference.md#assembly)|필수적 요소입니다. 코드 조각이 참조하는 어셈블리 이름이 포함되어 있습니다. 하나의 `Assembly` 요소에는 `Reference` 요소가 단 하나만 있어야 합니다.|
|[Url 요소](../ide/code-snippets-schema-reference.md#url)|선택적 요소입니다. 참조된 어셈블리에 대한 추가 정보를 제공하는 URL이 포함되어 있습니다. `Url` 요소에는 `Reference` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[References 요소](../ide/code-snippets-schema-reference.md#references)|`Reference` 요소에 대한 그룹화 요소입니다.|

## <a name="references-element"></a><a name="references"></a>References 요소
 개별 `Reference` 요소를 그룹화합니다.

> [!NOTE]
> `References` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|자식 요소|설명|
|-------------------|-----------------|
|[Reference 요소](../ide/code-snippets-schema-reference.md#reference)|선택적 요소입니다. 코드 조각의 어셈블리 참조에 대한 정보가 포함되어 있습니다. `Reference` 요소에는 `References` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[조각 요소](../ide/code-snippets-schema-reference.md#snippet)|코드 조각에 대한 참조, 가져오기, 선언 및 코드가 포함되어 있습니다.|

## <a name="shortcut-element"></a><a name="shortcut"></a>바로 가기 요소
 조각을 삽입하는 데 사용되는 바로 가기 텍스트를 지정합니다. `Shortcut` 요소의 텍스트 값에는 영숫자, 하이픈(-) 및 밑줄(_)만 포함될 수 있습니다.

> [!CAUTION]
> C++에서는 코드 조각 바로 가기에 _ 및 – 문자를 지원하지 않습니다.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보가 포함되어 있습니다.|

 텍스트 값은 선택적입니다. 이 텍스트는 코드 조각을 삽입하기 위한 바로 가기로 사용됩니다.

## <a name="snippet-element"></a><a name="snippet"></a>조각 요소
 코드 조각의 참조, 가져오기, 선언 및 코드를 지정합니다.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>

```

|자식 요소|설명|
|-------------------|-----------------|
|[Code 요소](../ide/code-snippets-schema-reference.md#code)|필수적 요소입니다. 설명서 파일에 삽입할 코드를 지정합니다. 하나의 `Code` 요소에는 `Snippet` 요소가 단 하나만 있어야 합니다.|
|[선언 요소](../ide/code-snippets-schema-reference.md#declarations)|선택적 요소입니다. 코드 조각에서 편집할 수 있는 부분을 구성하는 리터럴과 개체를 지정합니다. `Declarations` 요소에는 `Snippet` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[Imports 요소](../ide/code-snippets-schema-reference.md#imports)|선택적 요소입니다. 개별 `Import` 요소를 그룹화합니다. `Imports` 요소에는 `Snippet` 요소가 0개 또는 그 이상 있을 수 있습니다.|
||선택적 요소입니다. 개별 `Reference` 요소를 그룹화합니다. `References` 요소에는 `Snippet` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[CodeSnippet 요소](../ide/code-snippets-schema-reference.md#codesnippet)|Visual Studio Code 파일에 삽입할 수 있는 여러 IntelliSense 코드 조각 및 제목을 지정할 수 있습니다.|

## <a name="snippettype-element"></a><a name="snippettype"></a>SnippetType 요소
 Visual Studio에서 코드 조각을 삽입하는 방법을 지정합니다.

```xml
<SnippetType>
    SurroundsWith/Expansion
<SnippetType>
```

|부모 요소|설명|
|--------------------|-----------------|
|[SnippetTypes 요소](../ide/code-snippets-schema-reference.md#snippettypes)|`SnippetType` 요소를 그룹화합니다.|

 텍스트 값은 다음 값 중 하나여야 합니다.

- `SurroundsWith`: 코드 조각을 선택된 코드 부분 주위에 배치할 수 있습니다.

- `Expansion`: 코드 조각을 커서 위치에 삽입할 수 있습니다.

- `Refactoring`: Visual C# 리팩터링 동안 코드 조각이 사용되도록 지정합니다. 사용자 지정 코드 조각에서는 `Refactoring`을 사용할 수 없습니다.

## <a name="snippettypes-element"></a><a name="snippettypes"></a>SnippetTypes 요소
 개별 `SnippetType` 요소를 그룹화합니다. `SnippetTypes` 요소가 없으면 코드에서 임의의 위치에 코드 조각을 삽입할 수 있습니다.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
<SnippetTypes>
```

|자식 요소|설명|
|-------------------|-----------------|
|[SnippetType 요소](../ide/code-snippets-schema-reference.md#snippettype)|선택적 요소입니다. Visual Studio에서 코드에 코드 조각을 삽입하는 방법을 지정합니다. `SnippetType` 요소에는 `SnippetTypes` 요소가 0개 또는 그 이상 있을 수 있습니다.|

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보를 지정합니다.|

## <a name="title-element"></a><a name="title"></a>Title 요소
 코드 조각의 제목을 지정합니다. 코드 조각의 `Title` 요소에 저장된 제목은 **코드 조각 선택**과 **코드 조각 관리자**의 코드 조각 설명에 표시됩니다.

```xml
<Title>
    Code Snippet Title
<Title>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Header 요소](../ide/code-snippets-schema-reference.md#header)|코드 조각에 대한 일반 정보를 지정합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각의 제목을 지정합니다.

## <a name="tooltip-element"></a><a name="tooltip"></a>ToolTip 요소
 코드 조각에 있는 리터럴 또는 개체의 예상 값 및 사용법을 설명합니다. 이 값은 Visual Studio에서 코드 조각을 프로젝트에 삽입할 때 도구 설명에 표시됩니다. 코드 조각을 삽입하고 나서 마우스를 리터럴이나 개체 위로 가져가면 도구 설명 텍스트가 표시됩니다.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Literal 요소](../ide/code-snippets-schema-reference.md#literal)|편집할 수 있는 코드 조각의 리터럴 필드를 정의합니다.|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|편집할 수 있는 코드 조각의 개체 필드를 정의합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 코드 조각에 있는 개체나 리터럴과 관련된 도구 설명을 지정합니다.

## <a name="type-element"></a><a name="type"></a>Type 요소
 개체의 형식을 지정합니다. `Object` 요소는 코드 조각에서 필요하지만 코드 조각 자체의 외부에서 정의될 항목을 식별하는 데 사용됩니다. 예를 들어, Windows Forms 컨트롤, ASP.NET 컨트롤, 개체 인스턴스 및 형식 인스턴스는 개체로 선언되어야 합니다. 개체 선언에는 형식이 지정되어야 하며, 이 형식은 `Type` 요소를 사용하여 지정합니다.

```xml
<Type>
    Type
</Type>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Object 요소](../ide/code-snippets-schema-reference.md#object)|편집할 수 있는 코드 조각의 개체 필드를 정의합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 개체의 형식을 지정합니다.

## <a name="url-element"></a><a name="url"></a>Url 요소
 참조된 어셈블리에 대한 자세한 정보를 제공하는 URL을 지정합니다.

> [!NOTE]
> `Url` 요소는 Visual Basic 프로젝트에서만 지원됩니다.

```xml
<Url>
    www.microsoft.com
</Url>
```

|부모 요소|설명|
|--------------------|-----------------|
|[Reference 요소](../ide/code-snippets-schema-reference.md#reference)|코드 조각에 필요한 어셈블리 참조를 지정합니다.|

 텍스트 값은 필수입니다. 이 텍스트는 참조된 어셈블리에 대한 추가 정보를 제공하는 URL을 지정합니다. 참조가 프로젝트에 추가될 수 없는 경우 이 URL이 표시됩니다.

## <a name="see-also"></a>참고 항목
 [코드 조각](../ide/code-snippets.md) [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md)
