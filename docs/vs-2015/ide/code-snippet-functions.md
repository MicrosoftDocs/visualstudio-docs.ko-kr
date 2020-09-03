---
title: 코드 조각 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 92533b90e6a2da9f29a67d13c6e0eee2c31dbcfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620227"
---
# <a name="code-snippet-functions"></a>코드 조각 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

세 가지 함수를 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 코드 조각에 사용할 수 있습니다. 함수는 코드 조각의 [Function](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) 요소에 지정됩니다. 코드 조각을 만드는 방법에 대 한 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조 하세요.

## <a name="functions"></a>Functions
 다음 표에서는 코드 조각의 `Function` 요소에 사용할 수 있는 함수를 설명합니다.

|함수|Description|언어|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|`EnumerationLiteral` 매개 변수로 지정된 열거형 멤버에 대한 switch 문과 case 문 집합을 생성합니다. `EnumerationLiteral` 매개 변수는 열거형 리터럴 또는 열거형 형식에 대한 참조여야 합니다.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`ClassName()`|삽입된 코드 조각을 포함하는 클래스의 이름을 반환합니다.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`SimpleTypeName(` `TypeName` `)`|*TypeName* 매개 변수를 코드 조각이 호출되는 컨텍스트에서 가장 단순한 형태로 줄입니다.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|

## <a name="example"></a>예
 다음 예제에서는 `GenerateSwitchCases` 함수를 사용하는 방법을 보여 줍니다. 이 코드 조각이 삽입되고 열거형이 `$switch_on$` 리터럴에 입력되면 `$cases$` 리터럴은 열거형의 모든 값에 대해 `case` 문을 생성합니다.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>예
 다음 예제에서는 `ClassName` 함수를 사용하는 방법을 보여 줍니다. 이 코드 조각이 삽입되면 `$classname$` 리터럴은 코드 파일의 해당 위치에 있는 바깥쪽 클래스의 이름으로 바뀝니다.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="vjsharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>예
 이 예제는 `SimpleTypeName` 함수를 사용하는 방법을 보여 줍니다. 이 코드 조각이 코드 파일에 삽입되면 코드 조각이 호출된 컨텍스트에서 `$SystemConsole$` 리터럴이 가장 간단한 형태의 <xref:System.Console> 형식으로 바뀝니다.

```
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>관련 항목
 [Function 요소 (Intellisense 코드 조각)](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)
