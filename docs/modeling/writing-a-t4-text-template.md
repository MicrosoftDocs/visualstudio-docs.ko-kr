---
title: T4 텍스트 템플릿 쓰기
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1990377bffe0c663a70520c07bd3ab60b91f8bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593488"
---
# <a name="writing-a-t4-text-template"></a>T4 텍스트 템플릿 쓰기
텍스트 템플릿은 해당 템플릿에서 생성될 텍스트를 포함합니다. 예를 들어 웹 페이지를 만드는 템플릿에는 "..."가 포함 됩니다. \<html> 및 HTML 페이지의 기타 모든 표준 부분입니다. 템플릿에 삽입 된 *제어 블록*은 프로그램 코드의 조각입니다. 제어 블록은 경우에 따라 다른 값을 제공하여 텍스트 부분을 조건부로/반복 적용할 수 있도록 합니다.

 이 구조에서는 템플릿을 쉽게 개발할 수 있습니다. 생성된 파일의 프로토타입으로 시작한 다음 상황에 따라 다른 결과를 생성하는 제어 블록을 증분 방식으로 삽입할 수 있기 때문입니다.

 텍스트 템플릿은 다음 부분으로 구성됩니다.

- **지시문** -템플릿이 처리 되는 방식을 제어 하는 요소입니다.

- **텍스트 블록** -출력에 직접 복사 되는 콘텐츠입니다.

- **제어 블록** -텍스트에 변수 값을 삽입 하 고 텍스트의 조건부 또는 반복 되는 부분을 제어 하는 프로그램 코드입니다.

이 항목의 예제를 [사용 하려면 T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)에 설명 된 대로 템플릿 파일에 복사 합니다. 템플릿 파일을 편집한 후 저장 한 다음, 출력 **.txt** 파일을 검사 합니다.

## <a name="directives"></a>지시문
 텍스트 템플릿 지시문은 변환 코드 및 출력 파일 생성 방법에 대한 일반 명령을 텍스트 템플릿 생성 엔진에 제공합니다.

 예를 들어 다음 지시문은 출력 파일의 확장명이 .txt여야 하도록 지정합니다.

```
<#@ output extension=".txt" #>
```

 지시문에 대 한 자세한 내용은 [T4 텍스트 템플릿 지시문](../modeling/t4-text-template-directives.md)을 참조 하세요.

## <a name="text-blocks"></a>텍스트 블록
 텍스트 블록은 출력 파일에 텍스트를 직접 삽입합니다. 텍스트 블록에는 특수한 서식이 없습니다. 예를 들어 다음 텍스트 템플릿은 "Hello"라는 단어가 포함된 텍스트 파일을 생성합니다.

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>제어 블록
 제어 블록은 템플릿을 변환하는 데 사용되는 프로그램 코드 섹션입니다. 기본 언어는 C#이지만 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]을 사용하려는 경우 파일 시작 부분에 다음 지시문을 작성하면 됩니다.

```
<#@ template language="VB" #>
```

 제어 블록에서 코드를 작성하는 언어는 생성되는 텍스트의 언어와는 관계가 없습니다.

### <a name="standard-control-blocks"></a>표준 제어 블록
 표준 제어 블록은 출력 파일 부분을 생성하는 프로그램 코드 섹션입니다.

 템플릿 파일에서는 텍스트 블록과 표준 제어 블록을 원하는 수만큼 혼합하여 사용할 수 있습니다. 그러나 제어 블록 내에 제어 블록을 배치할 수는 없습니다. 각 표준 제어 블록은 `<# ... #>` 기호로 구분됩니다.

 예를 들어 다음 제어 블록 및 텍스트 블록을 사용하면 출력 파일에 "0, 1, 2, 3, 4 Hello!" 줄이 포함됩니다.

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 명시적인 `Write()` 문을 사용하는 대신 텍스트와 코드를 인터리빙할 수 있습니다. 다음 예에서는 "Hello!"를 출력 합니다. 네 번:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 코드에서 `Write();` 문이 허용되는 모든 위치에 텍스트 블록을 삽입할 수 있습니다.

> [!NOTE]
> 루프 또는 조건부와 같은 복합 문 내에 텍스트 블록을 포함 하는 경우 항상 중괄호 {...}를 사용 합니다. 텍스트 블록을 포함할입니다.

### <a name="expression-control-blocks"></a>식 제어 블록
 식 제어 블록은 식을 평가한 다음 문자열로 변환합니다. 이 문이 출력 파일에 삽입됩니다.

 식 제어 블록은 `<#= ... #>` 기호로 구분됩니다.

 예를 들어 다음 제어 블록은 출력 파일에 "5"가 포함되도록 지정합니다.

```
<#= 2 + 3 #>
```

 여는 기호에는 "< # =" 라는 3 개의 문자가 있습니다.

 식은 범위 내의 모든 변수를 포함할 수 있습니다. 예를 들어 다음 블록은 숫자가 포함된 줄을 출력합니다.

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>클래스 기능 제어 블록
 클래스 기능 제어 블록은 주 변환에 포함되지 않아야 할 속성, 메서드 또는 기타 코드를 정의합니다. 클래스 기능 블록은 대개 도우미 함수에 사용되며,  일반적으로 클래스 기능 블록은 둘 이상의 텍스트 템플릿에 [포함](#Include) 될 수 있도록 별도의 파일에 배치 됩니다.

 클래스 기능 제어 블록은 `<#+ ... #>` 기호로 구분됩니다.

 예를 들어 다음 템플릿 파일은 메서드를 선언 및 사용합니다.

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 클래스 기능은 작성되는 파일 끝에 배치해야 합니다. 그러나 `<#@include#>` 지시문 뒤에 표준 블록과 텍스트가 있어도 클래스 기능을 포함하는 파일을 `include`할 수 있습니다.

 제어 블록에 대 한 자세한 내용은 [텍스트 템플릿 제어 블록](../modeling/text-template-control-blocks.md)을 참조 하세요.

### <a name="class-feature-blocks-can-contain-text-blocks"></a>텍스트 블록을 포함할 수 있는 클래스 기능 블록
 텍스트를 생성하는 메서드를 작성할 수 있습니다. 예를 들면 다음과 같습니다.

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 따라서 둘 이상의 템플릿에 포함될 수 있는 텍스트를 별도의 파일에 생성하는 메서드를 배치하는 경우 특히 유용합니다.

## <a name="using-external-definitions"></a>외부 정의 사용

### <a name="assemblies"></a>어셈블리
 템플릿의 코드 블록은 System.dll 등 가장 흔히 사용되는 .NET 어셈블리에 대해 정의되는 형식을 사용할 수 있습니다. 또한 기타 .NET 어셈블리나 고유한 어셈블리를 참조할 수도 있습니다. 다음과 같이 어셈블리의 경로 이름 또는 강력한 이름을 제공할 수 있습니다.

```
<#@ assembly name="System.Xml" #>
```

 절대 경로 이름을 사용하거나 경로 이름에 표준 매크로 이름을 사용해야 합니다. 예를 들면 다음과 같습니다.

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Assembly 지시문은 [전처리 된 텍스트 템플릿에](../modeling/run-time-text-generation-with-t4-text-templates.md)는 영향을 주지 않습니다.

 자세한 내용은 [T4 Assembly 지시문](../modeling/t4-assembly-directive.md)을 참조 하세요.

### <a name="namespaces"></a>네임스페이스
 import 지시문은 C#의 경우 `using` 절, Visual Basic의 경우 `imports` 절과 같습니다. 이 지시문을 사용하면 정규화된 이름을 사용하지 않고도 코드에서 형식을 참조할 수 있습니다.

```
<#@ import namespace="System.Xml" #>
```

 지시문 `assembly` 및 `import`은 원하는 수만큼 사용할 수 있습니다. 이러한 지시문은 텍스트 및 제어 블록 앞에 배치해야 합니다.

 자세한 내용은 [T4 Import 지시어](../modeling/t4-import-directive.md)를 참조 하세요.

### <a name="including-code-and-text"></a><a name="Include"></a> 코드 및 텍스트 포함
 `include` 지시문은 다른 템플릿 파일의 텍스트를 삽입합니다. 예를 들어 다음 지시문은 `test.txt`의 내용을 삽입합니다.

```
<#@ include file="c:\test.txt" #>
```

 포함된 내용은 포함하는 텍스트 템플릿의 일부인 것처럼 처리됩니다. 그러나 include 지시문 뒤에 일반 텍스트와 표준 제어 블록이 있어도 클래스 기능 블록 `<#+...#>`이 포함된 파일을 포함할 수 있습니다.

 자세한 내용은 [T4 Include 지시문](../modeling/t4-include-directive.md)을 참조 하세요.

### <a name="utility-methods"></a>유틸리티 메서드
 제어 블록에서 항상 사용할 수 있는 `Write()` 등의 여러 메서드가 있습니다. 여기에는 출력 들여쓰기, 오류 보고 등을 위한 메서드가 포함됩니다.

 원하는 유틸리티 메서드 집합을 직접 작성할 수도 있습니다.

 자세한 내용은 [텍스트 템플릿 유틸리티 메서드](../modeling/text-template-utility-methods.md)를 참조 하세요.

## <a name="transforming-data-and-models"></a>데이터 및 모델 변환
 텍스트 템플릿의 가장 유용한 적용 사례는 모델, 데이터베이스 또는 데이터 파일과 같은 소스의 내용에 따라 자료를 생성하는 것입니다. 템플릿은 데이터를 추출한 다음 서식을 다시 지정합니다. 템플릿 컬렉션은 이러한 소스를 여러 파일로 변환할 수 있습니다.

 소스 파일을 읽는 방식은 다양합니다.

 **텍스트 템플릿에서 파일을 읽습니다**. 이는 데이터를 템플릿으로 가져오는 가장 단순한 방법입니다.

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **탐색 가능한 모델로 파일을 로드**합니다. 즉, 텍스트 템플릿 코드가 탐색할 수 있는 모델로 데이터를 읽는 보다 효율적인 방식을 사용할 수 있습니다. 예를 들어 XML 파일을 로드한 다음 XPath 식을 사용하여 탐색할 수 있습니다. 또한 [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) 를 사용 하 여 XML 데이터를 읽을 수 있는 클래스 집합을 만들 수 있습니다.

 **다이어그램 또는 폼에서 모델 파일을 편집 합니다.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 에서는 모델을 다이어그램 또는 Windows form으로 편집할 수 있는 도구를 제공 합니다. 그러면 생성된 애플리케이션의 사용자와 모델에 대해 보다 쉽게 논의할 수 있습니다. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 또한 모델 구조를 반영 하는 강력한 형식의 클래스 집합을 만듭니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

### <a name="relative-file-paths-in-design-time-templates"></a>디자인 타임 템플릿의 상대 파일 경로
 [디자인 타임 텍스트 템플릿에서](../modeling/design-time-code-generation-by-using-t4-text-templates.md)텍스트 템플릿에 상대적인 위치에 있는 파일을 참조 하려는 경우를 사용 `this.Host.ResolvePath()` 합니다. 또한 `hostspecific="true"` 지시문에서 `template`도 설정해야 합니다.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

호스트가 제공하는 다른 서비스도 가져올 수 있습니다. 자세한 내용은 [템플릿에서 Visual Studio 또는 다른 호스트에 액세스](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))를 참조 하세요.

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>별도의 AppDomain에서 실행되는 디자인 타임 텍스트 템플릿

 [디자인 타임 텍스트 템플릿은](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 주 응용 프로그램과 별도의 AppDomain에서 실행 되는 것을 알고 있어야 합니다. 이러한 방식은 대부분의 경우 중요하지 않지만 복잡한 코드를 사용하는 특정 사례에서는 제한이 적용될 수 있습니다. 예를 들어 별도의 서비스에서 템플릿 내부나 외부로 데이터를 전달하려는 경우 해당 서비스가 serializable API를 제공해야 합니다.

 이는 코드의 나머지 부분과 함께 컴파일되는 코드를 제공 하는 [런타임 텍스트 템플릿에](../modeling/run-time-text-generation-with-t4-text-templates.md)는 적용 되지 않습니다.

## <a name="editing-templates"></a>템플릿 편집
 확장 관리자 온라인 갤러리에서 특수한 텍스트 템플릿 편집기를 다운로드할 수 있습니다. **도구** 메뉴에서 **확장 관리자**를 클릭 합니다. **온라인 갤러리**를 클릭 한 다음 검색 도구를 사용 합니다.

## <a name="related-topics"></a>관련 항목

|Task|항목|
|-|-|
|템플릿을 작성합니다.|[T4 텍스트 템플릿 작성 지침](../modeling/guidelines-for-writing-t4-text-templates.md)|
|프로그램 코드를 사용하여 텍스트를 생성합니다.|[텍스트 템플릿 구조](../modeling/writing-a-t4-text-template.md)|
|Visual Studio 솔루션에서 파일을 생성 합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Visual Studio 외부에서 텍스트 생성을 실행 합니다.|[TextTransform 유틸리티 사용하여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)|
|DSL(Domain-Specific Language) 형식으로 데이터를 변형합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|
