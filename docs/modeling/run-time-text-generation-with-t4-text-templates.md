---
title: T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 344e15b69bf3e8308c62c6fa1074720b0cd7618d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520837"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성

Visual Studio 런타임 텍스트 템플릿을 사용 하 여 응용 프로그램에서 런타임에 텍스트 문자열을 생성할 수 있습니다. 응용 프로그램이 실행 되는 컴퓨터에는 Visual Studio가 필요 하지 않습니다. 컴파일 시간에 템플릿이 런타임에 실행 되는 코드를 생성 하기 때문에 런타임 템플릿을 "전처리 된 텍스트 템플릿"이 라고도 합니다.

각 템플릿은 생성 된 문자열에 표시 되는 텍스트와 프로그램 코드 조각으로 이루어진 조합입니다. 프로그램 조각은 문자열의 변수 부분에 대 한 값을 제공 하 고 조건부 및 반복 되는 부분을 제어 합니다.

예를 들어 다음 템플릿은 HTML 보고서를 만드는 응용 프로그램에서 사용할 수 있습니다.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

템플릿은 변수 부분이 프로그램 코드로 대체 된 HTML 페이지입니다. HTML 페이지의 정적 프로토타입을 작성 하 여 이러한 페이지의 디자인을 시작할 수 있습니다. 그런 다음 테이블 및 기타 변수 부분을 특정 한 경우에 따라 달라 지는 콘텐츠를 생성 하는 프로그램 코드로 바꿀 수 있습니다.

응용 프로그램에서 템플릿을 사용 하면 긴 일련의 write 문과 같이 사용자가 사용할 수 있는 것 보다 최종 형식의 출력을 쉽게 볼 수 있습니다. 출력의 형태를 변경 하는 것이 더 쉽고 안정적입니다.

## <a name="creating-a-run-time-text-template-in-any-application"></a>모든 응용 프로그램에서 런타임 텍스트 템플릿 만들기

### <a name="to-create-a-run-time-text-template"></a>런타임 텍스트 템플릿을 만들려면

1. 솔루션 탐색기의 프로젝트 바로 가기 메뉴에서 **Add**  >  **새 항목**추가를 선택 합니다.

2. **새 항목 추가** 대화 상자에서 **런타임 텍스트 템플릿**을 선택 합니다. (Visual Basic **공통 항목**  >  을 검색 합니다. **일반**.)

3. 템플릿 파일의 이름을 입력 합니다.

    > [!NOTE]
    > 템플릿 파일 이름은 생성 된 코드에서 클래스 이름으로 사용 됩니다. 따라서 공백이 나 문장 부호를 포함 하지 않아야 합니다.

4. **추가**를 선택합니다.

    확장명이 **.tt**인 새 파일이 만들어집니다. 해당 **사용자 지정 도구** 속성은 **Texttemplatingfilepreprocessor**로 설정 됩니다. 여기에는 다음 줄이 포함 됩니다.

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>기존 파일을 런타임 템플릿으로 변환

템플릿을 만드는 좋은 방법은 기존 출력 예제를 변환 하는 것입니다. 예를 들어 응용 프로그램에서 HTML 파일을 생성 하는 경우 일반 HTML 파일을 만들어 시작할 수 있습니다. 제대로 작동 하는지 그리고 모양이 올바른지 확인 합니다. 그런 다음 Visual Studio 프로젝트에 포함 하 고 템플릿으로 변환 합니다.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>기존 텍스트 파일을 런타임 템플릿으로 변환 하려면

1. Visual Studio 프로젝트에 파일을 포함 합니다. 솔루션 탐색기의 프로젝트 바로 가기 메뉴에서 **Add**  >  **기존 항목**추가를 선택 합니다.

2. 파일의 **사용자 지정 도구** 속성을 **Texttemplatingfilepreprocessor**로 설정 합니다. 솔루션 탐색기에서 파일의 바로 가기 메뉴에 있는 **속성**을 선택 합니다.

    > [!NOTE]
    > 속성이 이미 설정 되어 있으면이 속성이 **Texttemplatingfilepreprocessor** 이며 **Texttemplatingfilepreprocessor**가 아닌지 확인 합니다. 이는 확장명이 **.tt**인 파일을 포함 하는 경우에 발생할 수 있습니다.

3. 파일 이름 확장명을 **.tt**로 변경 합니다. 이 단계는 선택 사항 이지만 잘못 된 편집기에서 파일을 여는 것을 방지 하는 데 도움이 됩니다.

4. 파일 이름의 주 부분에서 공백이 나 문장 부호를 제거 합니다. 예를 들어 "My Web Page.tt"는 올바르지 않지만 "MyWebPage.tt"은 올바릅니다. 파일 이름은 생성 된 코드에서 클래스 이름으로 사용 됩니다.

5. 파일의 시작 부분에 다음 줄을 삽입 합니다. Visual Basic 프로젝트에서 작업 하는 경우 "c #"을 "VB"로 바꿉니다.

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>런타임 템플릿의 콘텐츠입니다.

### <a name="template-directive"></a>Template 지시문

파일을 만들 때 템플릿의 첫 번째 줄을 유지 합니다.

`<#@ template language="C#" #>`

Language 매개 변수는 프로젝트의 언어에 따라 달라 집니다.

### <a name="plain-content"></a>일반 콘텐츠

응용 프로그램에서 생성 하려는 텍스트를 포함 하도록 **.tt** 파일을 편집 합니다. 예를 들면 다음과 같습니다.

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>포함 된 프로그램 코드

및 사이에 프로그램 코드를 삽입할 수 있습니다 `<#` `#>` . 예를 들면 다음과 같습니다.

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

문 사이에 문이 삽입 되 `<# ... #>` 고 사이에 식이 삽입 됩니다 `<#= ... #>` . 자세한 내용은 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

## <a name="using-the-template"></a>템플릿 사용

### <a name="the-code-built-from-the-template"></a>템플릿을 기반으로 작성 된 코드

**.Tt** 파일을 저장 하면 자회사 또는 **.vb** 파일이 생성 **됩니다.** **솔루션 탐색기**에서이 파일을 보려면 **.tt** 파일 노드를 확장 합니다. Visual Basic 프로젝트에서 먼저 **솔루션 탐색기** 도구 모음에서 **모든 파일 표시** 를 선택 합니다.

자회사 파일에는 라는 메서드가 포함 된 partial 클래스가 포함 되어 있습니다 `TransformText()` . 응용 프로그램에서이 메서드를 호출할 수 있습니다.

### <a name="generating-text-at-run-time"></a>런타임에 텍스트 생성

응용 프로그램 코드에서 다음과 같은 호출을 사용 하 여 템플릿의 콘텐츠를 생성할 수 있습니다.

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

생성 된 클래스를 특정 네임 스페이스에 놓으려면 텍스트 템플릿 파일의 **사용자 지정 도구 네임 스페이스** 속성을 설정 합니다.

### <a name="debugging-runtime-text-templates"></a>런타임 텍스트 템플릿 디버깅

일반 코드와 동일한 방식으로 런타임 텍스트 템플릿을 디버그 및 테스트 합니다.

텍스트 템플릿에 중단점을 설정할 수 있습니다. Visual Studio에서 디버깅 모드로 응용 프로그램을 시작 하는 경우 코드를 단계별로 실행 하 고 일반적인 방법으로 조사식 식을 평가할 수 있습니다.

### <a name="passing-parameters-in-the-constructor"></a>생성자에 매개 변수 전달

일반적으로 템플릿은 응용 프로그램의 다른 부분에서 일부 데이터를 가져와야 합니다. 이 작업을 쉽게 수행 하기 위해 템플릿으로 작성 된 코드는 partial 클래스입니다. 프로젝트의 다른 파일에 같은 클래스의 다른 부분을 만들 수 있습니다. 이 파일에는 템플릿에 포함 된 코드와 응용 프로그램의 나머지 부분에 모두 액세스할 수 있는 매개 변수, 속성 및 함수를 포함 하는 생성자가 포함 될 수 있습니다.

예를 들어 별도의 파일 **MyWebPageCode.cs**을 만들 수 있습니다.

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

템플릿 파일 **MyWebPage.tt**에서 다음을 작성할 수 있습니다.

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

응용 프로그램에서이 템플릿을 사용 하려면 다음을 수행 합니다.

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic의 생성자 매개 변수

Visual Basic에서 **MyWebPageCode** 의 개별 파일에는 다음이 포함 됩니다.

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

템플릿 파일에는 다음이 포함 될 수 있습니다.

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

이 템플릿은 생성자에서 매개 변수를 전달 하 여 호출할 수 있습니다.

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>템플릿 속성의 데이터 전달

템플릿에 데이터를 전달 하는 다른 방법은 partial 클래스 정의에서 템플릿 클래스에 공용 속성을 추가 하는 것입니다. 응용 프로그램은를 호출 하기 전에 속성을 설정할 수 있습니다 `TransformText()` .

Partial 정의에서 템플릿 클래스에 필드를 추가할 수도 있습니다. 이렇게 하면 템플릿의 연속 실행 간에 데이터를 전달할 수 있습니다.

### <a name="use-partial-classes-for-code"></a>코드에 partial 클래스 사용

많은 개발자가 템플릿에서 코드의 많은 본문을 작성 하지 않으려는 경우를 선호 합니다. 대신 템플릿 파일과 이름이 같은 partial 클래스에서 메서드를 정의할 수 있습니다. 템플릿에서 이러한 메서드를 호출 합니다. 이러한 방식으로 템플릿에서는 대상 출력 문자열의 모양을 보다 명확 하 게 보여 줍니다. 결과의 모양에 대 한 논의는 표시 되는 데이터를 만드는 논리와 구분할 수 있습니다.

### <a name="assemblies-and-references"></a>어셈블리 및 참조

템플릿 코드가 .NET 또는 **System.Xml.dll**와 같은 다른 어셈블리를 참조 하도록 하려면 일반적인 방법으로 프로젝트의 **참조** 에 추가 합니다.

문과 동일한 방법으로 네임 스페이스를 가져오려면 지시문을 사용 하 여 `using` 이 작업을 수행할 수 있습니다 `import` .

```
<#@ import namespace="System.Xml" #>
```

이러한 지시문은 지시문 바로 뒤의 파일 시작 부분에 배치 해야 합니다 `<#@template` .

### <a name="shared-content"></a>공유 콘텐츠

여러 템플릿을 공유 하는 텍스트가 있는 경우이를 별도의 파일에 저장 하 고 표시 되어야 하는 각 파일에 포함할 수 있습니다.

```
<#@include file="CommonHeader.txt" #>
```

포함 된 콘텐츠는 프로그램 코드와 일반 텍스트를 혼합 하 여 포함할 수 있으며 다른 include 지시문 및 기타 지시문을 포함할 수 있습니다.

Include 지시문은 템플릿 파일이 나 포함 된 파일의 텍스트에 있는 모든 위치에서 사용할 수 있습니다.

### <a name="inheritance-between-run-time-text-templates"></a>런타임 텍스트 템플릿 간 상속

추상 일 수 있는 기본 클래스 템플릿을 작성 하 여 런타임 템플릿 간에 콘텐츠를 공유할 수 있습니다. `inherits`지시문의 매개 변수를 사용 `<@#template#>` 하 여 다른 런타임 템플릿 클래스를 참조 합니다.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>상속 패턴: 기본 메서드의 조각

뒤에 나오는 예제에서 사용 된 패턴에서 다음 사항을 확인 합니다.

- 기본 클래스는 `SharedFragments` 클래스 기능 블록 내에서 메서드를 정의 합니다 `<#+ ... #>` .

- 기본 클래스에는 자유 텍스트가 포함 되어 있지 않습니다. 대신 모든 텍스트 블록이 클래스 기능 메서드 내에서 발생 합니다.

- 파생 클래스는에 정의 된 메서드를 호출 합니다 `SharedFragments` .

- 응용 프로그램은 `TextTransform()` 파생 클래스의 메서드를 호출 하지만 기본 클래스를 변환 하지는 않습니다 `SharedFragments` .

- 기본 클래스와 파생 클래스 모두 런타임 텍스트 템플릿입니다. 즉, **사용자 지정 도구** 속성이 **Texttemplatingfilepreprocessor**로 설정 됩니다.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**결과 출력은 다음과 같습니다.**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>상속 패턴: 기본 본문의 텍스트

템플릿 상속 사용에 대 한이 대체 방법에서 텍스트의 대부분은 기본 템플릿에서 정의 됩니다. 파생 된 템플릿은 기본 콘텐츠에 맞는 데이터 및 텍스트 조각을 제공 합니다.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**응용 프로그램 코드:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**결과 출력:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>관련 항목

디자인 타임 템플릿: 템플릿을 사용 하 여 응용 프로그램의 일부가 되는 코드를 생성 하려는 경우 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)을 참조 하세요.

런타임 템플릿은 템플릿 및 해당 콘텐츠가 컴파일 타임에 결정 되는 모든 응용 프로그램에서 사용할 수 있습니다. 런타임에 변경 되는 템플릿에서 텍스트를 생성 하는 Visual Studio 확장을 작성 하려는 경우 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)
- [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)
- [T4 도구 상자](http://olegsych.com/T4Toolbox/)
