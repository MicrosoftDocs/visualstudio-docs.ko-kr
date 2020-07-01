---
title: '연습: 코드 조각 만들기'
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f46dc6a1871b6d44c37c1931bf65f1b4a11c9ae
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770785"
---
# <a name="walkthrough-create-a-code-snippet"></a>연습: 코드 조각 만들기

몇 가지 단계로 코드 조각을 만들 수 있습니다. XML 파일을 만들고, 적절한 요소를 입력하고, 코드를 추가하기만 하면 됩니다. 대체 매개 변수와 프로젝트 참조를 선택적으로 활용할 수 있습니다. **코드 조각 관리자**(**도구** > **코드 조각 관리자**)에서 **가져오기** 단추를 사용하여 Visual Studio 설치에 코드 조각을 가져옵니다.

## <a name="snippet-template"></a>코드 조각 템플릿

다음 XML은 기본 코드 조각 템플릿입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

## <a name="create-a-code-snippet"></a>코드 조각 만들기

1. Visual Studio에서 새 XML 파일을 만들고 위에 표시된 템플릿을 추가합니다.

2. Title 요소에 코드 조각의 **제목**을 입력합니다. 제목 **제곱근**을 사용합니다.

3. **Code** 요소의 **Language** 특성에 코드 조각의 언어를 입력합니다. C#의 경우 **CSharp**를, Visual Basic의 경우 **VB**를, C++의 경우 **CPP**를 사용합니다.

   > [!TIP]
   > 사용 가능한 언어 값을 모두 보려면 [코드 조각 스키마 참조](code-snippets-schema-reference.md) 페이지에서 [코드 요소 특성 섹션](code-snippets-schema-reference.md#attributes)으로 이동합니다.

4. **Code** 요소 안의 **CDATA** 섹션에서 조각 코드를 추가합니다.

   C#의 경우:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   또는 Visual Basic의 경우

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > 코드 조각의 **CDATA** 섹션에 있는 코드 줄의 들여쓰기 또는 서식은 지정할 수 없습니다. 삽입 시, 언어 서비스에서 삽입된 코드의 서식을 자동으로 지정합니다.

5. 조각을 *SquareRoot.snippet*으로 저장합니다(어디에서나 저장할 수 있음).

## <a name="import-a-code-snippet"></a>코드 조각 가져오기

1. **코드 조각 관리자**를 사용하여 Visual Studio 설치에 조각을 가져올 수 있습니다. **도구** > **코드 조각 관리자**를 선택하여 엽니다.

2. **가져오기** 단추를 클릭합니다.

3. 이전 절차에서 코드 조각을 저장한 위치로 이동하고, 선택하고, **열기**를 클릭합니다.

4. 오른쪽 창의 선택 항목 중에서 코드 조각을 추가할 위치를 선택하라고 묻는 **코드 조각 가져오기** 대화 상자가 열립니다. 선택 사항 중 하나는 **내 코드 조각**이어야 합니다. **마침**, **확인**을 차례로 선택하고 클릭합니다.

5. 코드 조각은 코드 언어에 따라 다음 위치 중 하나에 복사됩니다.

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. C# 또는 Visual Basic 프로젝트를 열고 코드 조각을 테스트합니다. 편집기에서 코드 파일을 열어둔 상태로 오른쪽 클릭 메뉴에서 **코드 조각** > **코드 조각 삽입**을 선택한 다음, **내 코드 조각**을 선택합니다. **제곱근**이라고 하는 코드 조각이 보여야 합니다. 폴더를 두 번 클릭합니다.

   코드 조각이 코드 파일에 삽입됩니다.

## <a name="description-and-shortcut-fields"></a>설명 및 바로 가기 필드

::: moniker range="vs-2017"

1. 설명 필드는 코드 조각 관리자에서 볼 때 코드 조각에 대한 자세한 정보를 제공합니다. 바로 가기는 코드 조각을 삽입하기 위해 사용자가 입력할 수 있는 태그입니다. 파일 *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# or Visual Basic]\My Code Snippet\SquareRoot.snippet*을 열어 추가한 코드 조각을 편집합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. 설명 필드는 코드 조각 관리자에서 볼 때 코드 조각에 대한 자세한 정보를 제공합니다. 바로 가기는 코드 조각을 삽입하기 위해 사용자가 입력할 수 있는 태그입니다. 파일 *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# or Visual Basic]\My Code Snippet\SquareRoot.snippet*을 열어 추가한 코드 조각을 편집합니다.

::: moniker-end

   > [!TIP]
   > Visual Studio가 배치된 디렉터리에서 파일을 편집하고 있으므로 Visual Studio로 다시 가져올 필요는 없습니다.

2. **Header** 요소에 **Author** 및 **Description** 요소를 추가하고 채웁니다.

3. **Header** 요소는 다음과 비슷합니다.

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. **코드 조각 관리자**를 열고 코드 조각을 선택합니다. 오른쪽 창에서 이제 **Description** 및 **Author** 필드가 채워졌습니다.

   ![코드 조각 관리자에서 코드 조각 설명](media/code-snippet-description-author.png)

5. 바로 가기를 추가하려면 **헤더** 요소 내에서 **바로 가기** 요소를 추가합니다.

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. 코드 조각 파일을 다시 저장합니다.

7. 바로 가기를 테스트하려면 이전에 사용한 프로젝트를 열고 편집기에 **sqrt**를 입력한 후 **Tab**을 누릅니다(Visual Basic은 한 번, C#는 두 번).

   코드 조각이 삽입됩니다.

## <a name="replacement-parameters"></a>대체 매개 변수

사용자가 코드 조각의 부분을 교체하길 원할 수 있습니다. 예를 들어 사용자가 현재 프로젝트의 이름을 변수 이름으로 교체하길 원한다면 두 가지 유형의 대체(리터럴 및 개체)를 제공할 수 있습니다. [Literal 요소](code-snippets-schema-reference.md#literal-element)는 코드 조각에 완전히 포함되어 있으나 코드에 삽입된 후 사용자 지정될 코드 조각의 대체를 식별하는 데 사용됩니다(예: 문자열 또는 숫자값). [Object 요소](code-snippets-schema-reference.md#object-element)는 코드 조각에서 필요하지만 코드 조각 자체의 외부에서 정의될 항목을 식별하는 데 사용됩니다(예: 개체 인스턴스 또는 컨트롤).

1. 사용자가 제곱근을 계산할 숫자를 쉽게 대체할 수 있게 하려면 *SquareRoot.snippet* 파일의 **Snippet** 요소를 다음과 같이 수정하세요.

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   리터럴 대체에는 ID(`Number`)가 부여됩니다. 이 ID는 `$`개 문자로 둘러싸서 코드 조각 내에서 참조됩니다.

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. 코드 조각 파일을 저장합니다.

3. 프로젝트를 열고 코드 조각을 삽입합니다.

   코드 조각이 삽입되고 편집 가능한 리터럴이 대체용으로 강조 표시됩니다. 대체 매개 변수에 마우스를 올려 값에 대한 도구 설명을 확인합니다.

   ![Visual Studio에서 코드 조각 대체 매개 변수 도구 설명](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > 코드 조각에서 둘 이상의 대체 가능한 매개 변수가 있는 경우에는 **Tab**을 눌러 이동하여 값을 변경할 수 있습니다.

## <a name="import-a-namespace"></a>네임스페이스 가져오기

[Imports 요소](code-snippets-schema-reference.md#imports-element)를 포함하여 `using` 지시문(C#) 또는 `Imports` 문(Visual Basic)을 추가하기 위해 코드 조각을 사용할 수 있습니다. .NET Framework 프로젝트의 경우에는 [References 요소](code-snippets-schema-reference.md#references-element)를 사용하여 프로젝트에 참조를 추가할 수도 있습니다.

다음 XML은 System.IO 네임스페이스에서 메서드 `File.Exists`를 사용하고 따라서 System.IO 네임스페이스를 가져오도록 **Imports** 요소를 정의하는 코드 조각을 보여 줍니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>참고 항목

- [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)
