---
title: T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efdbf1b96e1dc49f5b9c48cebe6cededc9ea7c6e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534149"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디자인 타임 T4 텍스트 템플릿을 사용하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트에서 프로그램 코드 및 기타 파일을 생성할 수 있습니다. 일반적으로 *모델*의 데이터에 따라 생성 되는 코드를 변경 하도록 템플릿을 작성 합니다. 모델은 애플리케이션 요구 사항에 대한 주요 정보를 포함하는 파일 또는 데이터베이스입니다.

 워크플로를 테이블이나 다이어그램으로 정의하는 모델을 예로 들어 보겠습니다. 해당 모델에서 워크플로를 실행하는 소프트웨어를 생성할 수 있습니다. 사용자 요구 사항이 변경되면 사용자와 함께 새 워크플로에 대해 쉽게 논의할 수 있습니다. 워크플로에서 코드를 다시 생성하는 것이 코드를 직접 업데이트하는 것보다 안정적입니다.

> [!NOTE]
> *모델* 은 응용 프로그램의 특정 측면을 설명 하는 데이터 원본입니다. 모든 형태와 종류의 파일 또는 데이터베이스일 수 있으며 UML 모델이나 DSL(Domain-Specific Language) 모델 등의 특정 형태가 아니어도 됩니다. 일반적인 모델은 테이블 또는 XML 파일 형식입니다.

 코드를 생성하는 방법에 대해서는 이미 잘 알고 계실 것입니다. 솔루션의 **.resx** 파일에 리소스를 정의 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 클래스 및 메서드 집합이 자동으로 생성 됩니다. 리소스 파일로 리소스를 편집하는 것이 클래스와 메서드를 편집하는 것보다 훨씬 쉽고 안정적입니다. 텍스트 템플릿을 사용하면 직접 디자인한 소스에서 같은 방식으로 코드를 생성할 수 있습니다.

 텍스트 템플릿에는 생성하려는 텍스트와 텍스트의 변수 부분을 생성하는 프로그램 코드가 혼합되어 있습니다. 프로그램 코드를 사용하면 생성된 텍스트의 일부분을 반복하거나 조건부로 생략할 수 있습니다. 생성된 텍스트 자체는 애플리케이션 부분을 만드는 프로그램 코드일 수 있습니다.

## <a name="creating-a-design-time-t4-text-template"></a>디자인 타임 T4 텍스트 템플릿 만들기

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Visual Studio에서 디자인 타임 T4 텍스트 템플릿을 만들려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]프로젝트를 만들거나 기존 프로젝트를 엽니다.

     예를 들어 **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택 합니다.

2. 텍스트 템플릿 파일을 프로젝트에 추가 하 고 확장명이 **.tt**인 이름을 지정 합니다.

     이렇게 하려면 **솔루션 탐색기**의 프로젝트 바로 가기 메뉴에서 **추가**, **새 항목**을 차례로 선택 합니다. **새 항목 추가** 대화 상자의 가운데 창에서 **텍스트 템플릿** 을 선택 합니다.

     파일의 **사용자 지정 도구** 속성은 **Texttemplatingfilegenerator**입니다.

3. 파일을 엽니다. 다음 지시문이 이미 포함되어 있습니다.

    ```
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    ```

     [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 프로젝트에 템플릿을 추가한 경우 언어 특성은 "`VB`"입니다.

4. 파일 끝에 원하는 텍스트를 추가합니다. 예를 들면 다음과 같습니다.

    ```
    Hello, world!
    ```

5. 파일을 저장합니다.

     템플릿을 실행할지를 확인 하는 **보안 경고** 메시지 상자가 표시 될 수 있습니다. **확인**을 클릭합니다.

6. **솔루션 탐색기**에서 템플릿 파일 노드를 확장 하면 확장명이 **.txt**인 파일이 검색 됩니다. 이 파일에 템플릿에서 생성된 텍스트가 포함되어 있습니다.

    > [!NOTE]
    > 프로젝트가 Visual Basic 프로젝트인 경우 출력 파일을 보려면 **모든 파일 표시** 를 클릭 해야 합니다.

### <a name="regenerating-the-code"></a>코드 다시 생성
 다음과 같은 경우에는 템플릿이 실행되어 보조 파일이 생성됩니다.

- 템플릿을 편집한 다음 다른 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 창으로 포커스를 변경하는 경우

- 템플릿을 저장하는 경우

- **빌드** 메뉴에서 **모든 템플릿 변환** 을 클릭 합니다. 이 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에서 모든 템플릿이 변형됩니다.

- **솔루션 탐색기**의 모든 파일 바로 가기 메뉴에서 **사용자 지정 도구 실행**을 선택 합니다. 선택한 일부 템플릿을 변형하려면 이 방법을 사용합니다.

  템플릿이 읽는 데이터 파일이 변경되면 템플릿이 실행되도록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 설정할 수도 있습니다. 자세한 내용은 [코드 자동 다시 생성](#Regenerating)을 참조 하세요.

## <a name="generating-variable-text"></a>변수 텍스트 생성
 텍스트 템플릿에서는 프로그램 코드를 사용하여 생성된 파일 내용이 바뀌도록 할 수 있습니다.

#### <a name="to-generate-text-by-using-program-code"></a>프로그램 코드를 사용하여 텍스트를 생성하려면

1. `.tt` 파일의 내용을 다음과 같이 변경합니다.

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>

   ```

2. .tt 파일을 저장하고 생성된 .txt 파일을 다시 검사합니다. 숫자 0에서 10까지를 각각 제곱한 값이 표시됩니다.

   위의 코드에서 문은 `<#...#>` 내에 포함되어 있으며 단일 식은 `<#=...#>` 내에 포함되어 있습니다. 자세한 내용은 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

   [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서 생성 코드를 작성하는 경우 `template` 지시문은 `language="VB"`를 포함해야 합니다. `"C#"`은 기본 버전입니다.

## <a name="debugging-a-design-time-t4-text-template"></a>디자인 타임 T4 텍스트 템플릿 디버그
 텍스트 템플릿을 디버그하려면

- 먼저 `debug="true"`를 `template` 지시문에 삽입합니다. 예를 들면 다음과 같습니다.

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- 일반 코드에서와 같은 방식으로 템플릿에 중단점을 설정합니다.

- 솔루션 탐색기에서 텍스트 템플릿 파일의 바로 가기 메뉴에서 **T4 템플릿 디버그** 를 선택 합니다.

  템플릿이 실행된 후 중단점에서 중지됩니다. 일반적인 방식으로 변수를 점검하고 코드를 단계별로 실행할 수 있습니다.

> [!TIP]
> `debug="true"`를 사용하는 경우 생성된 코드에 줄 번호 매기기 지시문이 추가로 삽입되므로 해당 코드가 텍스트 템플릿에 보다 정확하게 매핑됩니다. 이 지시문이 없으면 중단점으로 인해 실행이 잘못된 상태로 중지될 수 있습니다.
>
> 디버그를 수행하지 않을 때도 템플릿 지시문에 절을 그대로 유지해도 됩니다. 이렇게 해도 성능은 아주 약간 낮아질 뿐입니다.

## <a name="generating-code-or-resources-for-your-solution"></a>솔루션의 코드 또는 리소스 생성
 모델에 따라 달라지는 프로그램 파일을 생성할 수 있습니다. 모델은 데이터베이스, 구성 파일, UML 모델, DSL 모델, 기타 소스 등의 입력입니다. 일반적으로는 같은 모델에서 여러 프로그램 파일을 생성합니다. 이렇게 하려면 생성된 각 프로그램 파일에 대해 템플릿 파일을 만들고 모든 템플릿이 같은 모델을 읽도록 합니다.

#### <a name="to-generate-program-code-or-resources"></a>프로그램 코드 또는 리소스를 생성하려면

1. .cs, .vb, .resx, .xml 등 적절한 형식의 파일을 생성하도록 출력 지시문을 변경합니다.

2. 필요한 솔루션 코드를 생성하는 코드를 삽입합니다. 예를 들어 클래스에서 3개 정수 필드 선언을 생성하려는 경우 다음 코드를 삽입합니다.

    ```csharp

              <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. 파일을 저장하고 다음 코드를 포함하는 생성된 파일을 검사합니다.

    ```
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>생성 코드와 생성된 텍스트
 프로그램 코드를 생성할 때는 템플릿에서 실행되는 생성 코드와 그 결과로 생성된, 솔루션의 일부분이 되는 코드를 혼동하지 않아야 합니다. 이 두 코드의 언어는 달라도 됩니다.

 위의 예에는 두 가지 버전이 있습니다. 그 중 한 버전에서는 생성 코드가 C#이고 다른 버전에서는 생성 코드가 Visual Basic입니다. 그러나 두 언어에서 생성된 텍스트는 모두 C# 클래스로 동일합니다.

 마찬가지로 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 템플릿을 사용하여 모든 언어에서 코드를 생성할 수도 있습니다. 생성된 텍스트는 특정 언어가 아니어도 되며 프로그램 코드일 필요도 없습니다.

### <a name="structuring-text-templates"></a>텍스트 템플릿 구조 지정
 실제 프로그래밍에서는 대개 템플릿 코드를 다음의 두 부분으로 구분합니다.

- 변수에서 값은 설정하지만 텍스트 블록은 포함하지 않는 구성(데이터 수집) 부분. 위의 예에서 이 부분은 `properties` 초기화입니다.

   이 부분은 저장소 내 모델을 생성하며 일반적으로 모델 파일을 읽으므로 "모델" 섹션이라고 하는 경우도 있습니다.

- 변수의 값을 사용하는 텍스트 생성 부분. 위의 예에서는 `foreach(...){...}`에 해당합니다.

  코드를 반드시 이와 같이 분리해야 하는 것은 아니지만 이 스타일을 사용하면 텍스트를 포함하는 부분을 보다 단순하게 작성하여 템플릿을 더 쉽게 읽을 수 있습니다.

## <a name="reading-files-or-other-sources"></a>파일 또는 기타 소스 읽기
 모델 파일이나 데이터베이스에 액세스하기 위해 템플릿 코드는 System.XML 등의 어셈블리를 사용할 수 있습니다. 이러한 어셈블리에 액세스하려면 다음과 같은 지시문을 삽입해야 합니다.

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

 `assembly` 지시문은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 참조 섹션과 같은 방식으로 템플릿 코드에서 지정한 어셈블리를 사용할 수 있도록 합니다. System.dll은 자동으로 참조되므로 해당 참조를 포함할 필요는 없습니다. `import` 지시문을 사용하면 일반 프로그램 파일의 `using` 지시문과 같은 방식으로 정규화된 이름을 사용하지 않고도 형식을 사용할 수 있습니다.

 예를 들어 **System.IO**를 가져온 후 다음을 작성할 수 있습니다.

```csharp

      <# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>

```

### <a name="opening-a-file-with-a-relative-pathname"></a>상대 경로 이름을 사용하여 파일 열기
 텍스트 템플릿을 기준으로 하는 위치에서 파일을 로드하려는 경우 `this.Host.ResolvePath()`를 사용하면 됩니다. this.Host를 사용하려면 `hostspecific="true"`에서 `template`를 설정해야 합니다.

```
<#@ template debug="false" hostspecific="true" language="C#" #>

```

 그런 후에 다음과 같은 코드를 작성할 수 있습니다.

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...

```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>

```

 현재 템플릿 파일의 이름을 식별하는 `this.Host.TemplateFile`을 사용할 수도 있습니다.

 여기서 `this.Host`는 VB에서는 `Me.Host`이며, 해당 형식은 `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`와 같습니다.

### <a name="getting-data-from-vsprvs"></a>[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 데이터 가져오기
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 제공되는 서비스를 사용하려면 `hostSpecific` 특성을 설정하고 `EnvDTE` 어셈블리를 로드합니다. 그런 다음 IServiceProvider.GetCOMService()를 사용하여 DTE 및 기타 서비스에 액세스할 수 있습니다. 예를 들면 다음과 같습니다.

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

> [!TIP]
> 텍스트 템플릿은 자체 앱 도메인에서 실행되며 마샬링을 통해 서비스에 액세스합니다. 이 경우에는 GetCOMService()가 GetService()보다 안정적입니다.

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a>자동으로 코드 다시 생성
 일반적으로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션의 여러 파일은 입력 모델 하나를 사용하여 생성됩니다. 각 파일은 자체 템플릿에서 생성되지만 모든 템플릿은 같은 모델을 참조합니다.

 소스 모델이 변경되면 솔루션에서 모든 템플릿을 다시 실행해야 합니다. 이 작업을 수동으로 수행 하려면 **빌드** 메뉴에서 **모든 템플릿 변환** 을 선택 합니다.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK를 설치한 경우 빌드를 수행할 때마다 모든 템플릿이 자동으로 변형되도록 지정할 수 있습니다. 이렇게 하려면 프로젝트 파일(.csproj 또는 .vbproj)을 텍스트 편집기에서 편집하여 파일 끝부분의 다른 `<import>` 문 뒤에 다음 줄을 추가합니다.

```
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 자세한 내용은 [빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)을 참조 하세요.

## <a name="error-reporting"></a>오류 보고
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 창에 오류 및 경고 메시지를 표시하려는 경우 다음 메서드를 사용할 수 있습니다.

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a>기존 파일을 템플릿으로 변환
 템플릿의 유용한 특징 중 하나는 삽입된 일부 프로그램 코드와 함께, 템플릿에서 생성한 파일과 매우 비슷하다는 점입니다. 이로 인해 템플릿을 만드는 유용한 방법이 제공됩니다. 먼저 파일 등의 프로토타입으로 일반 파일을 만든 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 다음, 결과 파일을 변경 하는 생성 코드를 점차적으로 도입 합니다.

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>기존 파일을 디자인 타임 템플릿으로 변환하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 파일에 `.cs`, `.vb`, `.resx` 파일 등 생성하려는 파일 형식을 추가합니다.

2. 새 파일을 테스트하여 작동하는지 확인합니다.

3. 솔루션 탐색기에서 파일 이름 확장명을 **.tt**로 변경 합니다.

4. **.Tt** 파일의 다음 속성을 확인 합니다.

    |속성|Value|
    |-|-|
    |**사용자 지정 도구 =**|**TextTemplatingFileGenerator**|
    |**빌드 작업 =**|**없음**|

5. 파일의 시작 부분에 다음 줄을 삽입합니다.

    ```
    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    ```

     [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서 템플릿의 생성 코드를 작성하려면 `language` 특성을 `"VB"` 대신 `"C#"`로 설정합니다.

     `extension` 특성을 `.cs`, `.resx`, `.xml` 등 생성하려는 파일 형식의 파일 이름 확장명으로 설정합니다.

6. 파일을 저장합니다.

     지정한 확장명으로 보조 파일이 작성됩니다. 이 파일은 해당 파일 형식에 적절한 속성을 포함합니다. 예를 들어 .cs 파일의 **빌드 작업** 속성은 **컴파일**입니다.

     생성된 파일의 내용이 원래 파일과 같은지 확인합니다.

7. 달라지도록 하려는 파일 부분을 확인합니다. 특정 상황에서만 표시되는 부분이나 반복되는 부분, 특정 값이 달라지는 부분을 예로 들 수 있습니다. 생성 코드를 삽입하고 파일을 저장한 다음 보조 파일이 올바르게 생성되는지 확인합니다. 이 단계를 반복합니다.

## <a name="guidelines-for-code-generation"></a>코드 생성 지침
 [T4 텍스트 템플릿 작성에 대 한 지침을](../modeling/guidelines-for-writing-t4-text-templates.md)참조 하세요.

## <a name="next-steps"></a>다음 단계

|다음 단계|항목|
|---------------|-----------|
|보조 함수, 포함된 파일 및 외부 데이터를 사용하는 코드로 고급 텍스트 템플릿을 작성하고 디버그합니다.|[T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)|
|런타임에 템플릿에서 문서를 생성합니다.|[T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 외부에서 텍스트 생성을 실행합니다.|[TextTransform 유틸리티 사용하여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)|
|DSL(Domain-Specific Language) 형식으로 데이터를 변형합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>참고 항목
 [T4 텍스트 템플릿 작성 지침](../modeling/guidelines-for-writing-t4-text-templates.md)
