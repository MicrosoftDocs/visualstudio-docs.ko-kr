---
title: '연습: 코드 조각 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac188bcf7975b8da1bbc71a90d3b6c34b095d424
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845572"
---
# <a name="walkthrough-creating-a-code-snippet"></a>연습: 코드 조각 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

몇 가지 단계로 코드 조각을 만들 수 있습니다. XML 파일을 만들고, 적절한 요소를 입력하고, 코드를 추가하기만 하면 됩니다. 또한 코드에 참조 및 대체 매개 변수를 추가할 수 있습니다. 코드 조각 관리자(**도구/코드 조각 관리자**)에서 가져오기 단추를 사용하여 Visual Studio 설치에 코드 조각을 추가할 수 있습니다.

> [!TIP]
> 코드 조각을 더 쉽게 작성 하는 방법에 대 한 자세한 내용을 보려면 CodePlex 웹 사이트에서 코드 [조각 편집기](https://snippeteditor.codeplex.com/)와 같은 커뮤니티 도구를 검색 합니다.

## <a name="snippet-template"></a>코드 조각 템플릿
 다음은 기본 코드 조각 템플릿입니다.

```
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>

```

### <a name="to-create-a-code-snippet"></a>코드 조각을 만들려면

1. Visual Studio에서 새 XML 파일을 만들고 위에 표시된 템플릿을 추가합니다.

2. Title 요소에 코드 조각의 제목 (예: "Hello World VB")을 입력 합니다.

3. Code 요소의 언어 특성에 코드 조각의 언어를 입력합니다. 예를 들어 "VB"를 사용합니다.

4. Code 요소 안의 CDATA 섹션에 일부 코드를 추가합니다. 예를 들어 다음과 같습니다.

    ```
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>

    ```

5. VBCodeSnippet.snippet으로 코드 조각을 저장합니다.

### <a name="to-add-a-code-snippet-to-visual-studio"></a>Visual Studio에 코드 조각을 추가하려면

1. 코드 조각 관리자를 사용하여 Visual Studio 설치에 사용자 고유의 코드 조각을 추가할 수 있습니다. 코드 조각 관리자(**도구/코드 조각 관리자**)를 엽니다.

2. **가져오기** 단추를 클릭합니다.

3. 이전 절차에서 코드 조각을 저장한 위치로 이동하고, 선택하고, **열기**를 클릭합니다.

4. 오른쪽 창의 선택 항목 중에서 코드 조각을 추가할 위치를 선택하라고 묻는 **코드 조각 가져오기** 대화 상자가 열립니다. 선택 사항 중 하나는 **내 코드 조각**이어야 합니다. **마침**, **확인**을 차례로 선택하고 클릭합니다.

5. 코드 조각이 다음 위치에 복사됩니다.

     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`

6. Visual Basic 프로젝트를 열고 코드 파일을 열어 코드 조각을 테스트합니다. 파일의 상황에 맞는 메뉴에서 코드 **조각 삽입** 을 클릭 한 다음 **내 코드 조각**을 클릭 합니다. **내 Visual Basic 코드 조각**이라는 코드 조각이 나타납니다. 폴더를 두 번 클릭합니다.

7. 코드에 삽입 됨이 표시 됩니다 `Console.WriteLine("Hello, World!")` .

### <a name="adding-description-and-shortcut-fields"></a>설명 및 바로 가기 필드 추가

1. 설명 필드는 코드 조각 관리자에서 볼 때 코드 조각에 대한 자세한 정보를 제공합니다. 바로 가기는 코드 조각을 삽입하기 위해 사용자가 입력할 수 있는 태그입니다. 파일을 열어 추가한 코드 조각을 편집 `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet` 합니다.

2. Header 요소에 Author 및 Description 요소를 추가하고 채웁니다.

3. Header 요소는 다음과 비슷합니다.

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>

    ```

4. 코드 조각 관리자를 열고 코드 조각을 선택합니다. 오른쪽 창에서 이제 Description 및 Author 필드가 채워졌습니다.

5. 바로 가기를 추가하려면 Author 및 Description 요소와 함께 Shortcut 요소를 추가합니다.

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>

    ```

6. 코드 조각 파일을 다시 저장합니다.

7. 바로 가기를 테스트하려면 Visual Basic 프로젝트를 열고 코드 파일을 엽니다. `hello`파일에를 입력 하 고 tab 키를 누릅니다. 코드 조각 코드를 삽입 해야 합니다.

### <a name="to-add-references-and-imports"></a>참조 및 가져오기를 추가하려면

1. Visual Basic 코드 조각을 사용 하면 References 요소를 사용 하 여 프로젝트에 참조를 추가 하 고 Imports 요소를 사용 하 여 Imports 선언을 추가할 수 있습니다. (다른 언어의 코드 조각에는이 기능이 없습니다.) 예를 들어 `Console.WriteLine` 코드 예제에서을로 변경 하는 경우 `MessageBox.Show` System.Windows.Forms.dll 어셈블리를 프로젝트에 추가 해야 할 수 있습니다.

2. 코드 조각을 엽니다.

3. Snippet 요소 아래에 References 요소를 추가합니다.

    ```
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>

    ```

4. Snippet 요소 아래에 Imports 요소를 추가합니다.

    ```
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>

    ```

5. CDATA 섹션을 다음과 같이 변경합니다.

    ```
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. 코드 조각을 저장합니다.

7. Visual Basic 프로젝트를 열고 코드 조각을 추가합니다.

8. 코드 파일 맨 위에 Imports문이 표시됩니다.

    ```
    Imports System.Windows.Forms

    ```

9. 프로젝트의 속성을 봅니다. References 탭은 System.Windows.Forms.dll에 대한 참조를 포함합니다.

### <a name="adding-replacements"></a>대체 추가

1. 변수를 추가하고 사용자가 현재 프로젝트의 변수로 변수를 교체하도록 하려는 경우 코드 조각의 부분을 사용자가 바꿀 수 있습니다. 두 가지 유형의 대체(리터럴 및 개체)를 제공할 수 있습니다. 리터럴은 일부 형식(문자열 리터럴, 변수 이름 또는 숫자 값의 문자열 표현)의 문자열입니다. 개체는 문자열이 아닌 일부 형식의 인스턴스입니다. 이 절차에서는 리터럴 대체 및 개체 대체를 선언하고 이러한 대체를 참조하도록 코드를 변경합니다.

2. 코드 조각을 엽니다.

3. 이 예제에서는 SQL 연결 문자열을 사용하므로 적절한 참조를 추가하려면 Imports 및 References 요소를 변경해야 합니다.

    ```
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>

    ```

4. SQL 연결 문자열에 대한 리터럴 대체를 선언하려면 Snippet 요소 아래에 Declarations 요소를 추가하고, ID, 도구 설명 및 대체에 대한 기본값에 대한 하위 요소로 Literal 요소를 추가합니다.

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>

    ```

5. SQL 연결에 대한 개체 대체를 선언하려면 Declarations 요소 내에 Object 요소를 추가하고, ID, 개체 유형, 도구 설명 및 기본값에 대한 하위 요소를 추가합니다. 결과 Declarations 요소는 다음과 같이 표시됩니다.

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6. 코드 섹션에서 주변 $ 기호로 대체를 참조합니다(예: `$replacement$`).

    ```
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. 코드 조각을 저장합니다.

8. Visual Basic 프로젝트를 열고 코드 조각을 추가합니다.

9. 코드는 다음과 같아야 합니다. 여기서 대체 `SQL connection string` 및 `dcConnection`은 연한 주황색으로 강조 표시됩니다. TAB 키를 눌러 다른 쪽으로 이동 합니다.

    ```
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection

    ```

## <a name="see-also"></a>관련 항목
 [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)
