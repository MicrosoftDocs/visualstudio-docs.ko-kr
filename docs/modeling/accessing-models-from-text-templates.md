---
title: 텍스트 템플릿에서 모델에 액세스
description: 텍스트 템플릿을 사용하여 도메인별 언어 모델을 기반으로 하는 보고서 파일, 소스 코드 파일 및 기타 텍스트 파일을 만드는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05e21dacfe56f41f1d2c0da51659ab55203db1a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389165"
---
# <a name="access-models-from-text-templates"></a>텍스트 템플릿에서 모델 액세스

텍스트 템플릿을 사용하여 도메인별 언어 모델을 기반으로 하는 보고서 파일, 소스 코드 파일 및 기타 텍스트 파일을 만들 수 있습니다. 텍스트 템플릿에 대한 기본 정보는 [코드 생성 및 T4 텍스트 템플릿을 참조하세요.](../modeling/code-generation-and-t4-text-templates.md) 텍스트 템플릿은 DSL을 디버그할 때 실험적 모드에서 작동하며 DSL을 배포한 컴퓨터에서도 작동합니다.

> [!NOTE]
> DSL 솔루션을 만들 때 샘플 텍스트 템플릿 **\* .tt** 파일이 디버깅 프로젝트에 생성됩니다. 도메인 클래스의 이름을 변경하면 이러한 템플릿이 더 이상 작동하지 않습니다. 그럼에도 불구하고 필요한 기본 지시문을 포함하고 DSL과 일치하도록 업데이트할 수 있는 예제를 제공합니다.

 텍스트 템플릿에서 모델에 액세스하려면 다음을 수행합니다.

- 템플릿 지시문의 inherit 속성을 [Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation으로](/previous-versions/bb893209(v=vs.140))설정합니다. 이렇게 하면 Store에 액세스할 수 있습니다.

- 액세스하려는 DSL에 대한 지시문 프로세서를 지정합니다. 이렇게 하면 DSL에 대한 어셈블리가 로드되므로 텍스트 템플릿의 코드에서 해당 도메인 클래스, 속성 및 관계를 사용할 수 있습니다. 또한 지정한 모델 파일도 로드합니다.

  `.tt`다음 예제와 유사한 파일은 DSL 최소 언어 템플릿에서 새 Visual Studio 솔루션을 만들 때 디버깅 프로젝트에 만들어집니다.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 이 템플릿에 대한 다음 사항을 알아차리세요.

- 템플릿은 DSL 정의에서 정의한 도메인 클래스, 속성 및 관계를 사용할 수 있습니다.

- 템플릿에서 지정한 모델 파일을 로드 합니다 `requires` 속성입니다.

- 의 `this` 속성은 루트 요소를 포함합니다. 이 위치에서 코드는 모델의 다른 요소로 이동할 수 있습니다. 속성의 이름은 일반적으로 DSL의 루트 도메인 클래스와 동일합니다. 이 예제에서는 `this.ExampleModel`입니다.

- 코드 조각이 작성되는 언어는 C#이지만 모든 종류의 텍스트를 생성할 수 있습니다. 또는 지시문에 속성을 추가하여 에서 코드를 작성할 수 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] `language="VB"` `template` 있습니다.

- 템플릿을 디버그하려면 `debug="true"` `template` 지시문에 를 추가합니다. 예외가 발생하면 템플릿이 다른 Visual Studio 인스턴스에서 열립니다. 코드의 특정 지점에서 디버거를 중단하려면 문을 삽입합니다. `System.Diagnostics.Debugger.Break();`

   자세한 내용은 [T4 텍스트 템플릿 디버깅을 참조하세요.](../modeling/debugging-a-t4-text-template.md)

## <a name="about-the-dsl-directive-processor"></a>DSL 지시문 프로세서 정보
 템플릿은 DSL 정의에서 정의한 도메인 클래스를 사용할 수 있습니다. 이는 일반적으로 템플릿의 시작 부근에 나타나는 지시문에 의해 가져옵니다. 이전 예제에서는 다음과 같습니다.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 지시문의 이름( `MyLanguage` 이 예제에서는 )은 DSL 이름에서 파생됩니다. DSL의 일부로 생성되는 *지시문 프로세서를* 호출합니다. **Dsl\GeneratedCode\DirectiveProcessor.cs에서** 해당 소스 코드를 찾을 수 있습니다.

 DSL 지시문 프로세서는 다음 두 가지 주요 작업을 수행합니다.

- DSL을 참조하는 템플릿에 어셈블리 및 가져오기 지시문을 효과적으로 삽입합니다. 이렇게 하면 템플릿 코드에서 도메인 클래스를 사용할 수 있습니다.

- 매개 변수에 지정한 파일을 `requires` 로드하고 로드된 모델의 루트 요소를 참조하는 의 속성을 `this` 설정합니다.

## <a name="validating-the-model-before-running-the-template"></a>템플릿을 실행하기 전에 모델 유효성 검사
 템플릿이 실행되기 전에 모델의 유효성을 검사할 수 있습니다.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 다음에 유의합니다.

1. `filename`및 `validation` 매개 변수는 ";"로 구분되며 다른 구분 기호나 공백이 없어야 합니다.

2. 유효성 검사 범주 목록에 따라 실행할 유효성 검사 메서드가 결정됩니다. 여러 범주를 "&#124;"로 구분해야 하며 다른 구분 기호나 공백이 없어야 합니다.

   오류가 발견되면 오류 창에 보고되고 결과 파일에 오류 메시지가 포함됩니다.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> 텍스트 템플릿에서 여러 모델 액세스

> [!NOTE]
> 이 메서드를 사용하면 동일한 템플릿에서 여러 모델을 읽을 수 있지만 ModelBus 참조는 지원하지 않습니다. ModelBus 참조로 상호 연결된 모델을 읽으려면 [텍스트 템플릿에서 Visual Studio ModelBus 사용을 참조하세요.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 동일한 텍스트 템플릿에서 두 개 이상의 모델에 액세스하려면 각 모델에 대해 생성된 지시문 프로세서를 한 번 호출해야 합니다. 매개 변수에서 각 모델의 파일 이름을 지정해야 `requires` 합니다. 매개 변수에서 루트 도메인 클래스에 사용할 이름을 지정해야 `provides` 합니다. 각 지시문 호출에서 매개 변수에 대해 서로 다른 값을 지정해야 `provides` 합니다. 예를 들어 Library.xyz, School.xyz 및 Work.xyz 라는 세 개의 모델 파일이 있다고 가정합니다. 동일한 텍스트 템플릿에서 액세스하려면 다음과 유사한 세 개의 지시문 호출을 작성해야 합니다.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> 이 예제 코드는 최소 언어 솔루션 템플릿을 기반으로 하는 언어에 대한 것입니다.

 텍스트 템플릿의 모델에 액세스하려면 이제 다음 예제의 코드와 비슷한 코드를 작성할 수 있습니다.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>동적으로 모델 로드
 런타임에 로드할 모델을 확인하려는 경우 DSL 관련 지시문을 사용하는 대신 프로그램 코드에서 모델 파일을 동적으로 로드할 수 있습니다.

 그러나 DSL 관련 지시문의 함수 중 하나는 템플릿 코드가 해당 DSL에 정의된 도메인 클래스를 사용할 수 있도록 DSL 네임스페이스를 가져오는 것입니다. 지시문을 사용하지 않으므로 로드할 수 있는 모든 모델에 대해 및 지시문을 추가해야 **\<assembly>** **\<import>** 합니다. 로드할 수 있는 여러 모델이 모두 동일한 DSL의 인스턴스인 경우 이 방법은 쉽습니다.

 파일을 로드하기 위해 가장 효과적인 방법은 Visual Studio ModelBus 사용하는 것입니다. 일반적인 시나리오에서 텍스트 템플릿은 DSL 관련 지시문을 사용하여 일반적인 방식으로 첫 번째 모델을 로드합니다. 해당 모델에는 다른 모델에 대한 ModelBus 참조가 포함됩니다. ModelBus를 사용하여 참조된 모델을 열고 특정 요소에 액세스할 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 Visual Studio ModelBus 사용을 참조하세요.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 덜 일반적인 시나리오에서는 파일 이름만 있고 현재 Visual Studio 프로젝트에 없을 수 있는 모델 파일을 여는 것이 좋을 수 있습니다. 이 경우 [방법: 프로그램 코드에서 파일에서 모델 열기에](../modeling/how-to-open-a-model-from-file-in-program-code.md)설명된 기술을 사용하여 파일을 열 수 있습니다.

## <a name="generating-multiple-files-from-a-template"></a>템플릿에서 여러 파일 생성
 여러 파일을 생성하려는 경우(예: 모델의 각 요소에 대해 별도의 파일을 생성하려는 경우) 몇 가지 가능한 방법이 있습니다. 기본적으로 각 템플릿 파일에서 하나의 파일만 생성됩니다.

### <a name="splitting-a-long-file"></a>긴 파일 분할
 이 메서드에서는 템플릿을 사용하여 구분 기호로 구분된 단일 파일을 생성합니다. 그런 다음 파일을 해당 부분으로 분할합니다. 두 개의 템플릿이 있습니다. 하나는 단일 파일을 생성하고 다른 하나는 분할합니다.

 **LoopTemplate.t4는** 긴 단일 파일을 생성합니다. **모든 템플릿 변환** 을 클릭할 때 직접 처리하면 안 되므로 파일 확장명 는 ".t4"입니다. 이 템플릿은 세그먼트를 구분하는 구분 기호 문자열을 지정하는 매개 변수를 가져옵니다.

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` 는 `LoopTemplate.t4` 를 호출한 다음 결과 파일을 해당 세그먼트로 분할합니다. 이 템플릿은 모델을 읽지 않으므로 모델링 템플릿일 필요는 없습니다.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
