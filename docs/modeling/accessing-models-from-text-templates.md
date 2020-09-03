---
title: 텍스트 템플릿에서 모델에 액세스
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a66f160d25ccacbdaaaf2238dfc738ade4a4200f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531471"
---
# <a name="access-models-from-text-templates"></a>텍스트 템플릿에서 모델에 액세스

텍스트 템플릿을 사용 하면 도메인별 언어 모델을 기반으로 하는 보고서 파일, 소스 코드 파일 및 기타 텍스트 파일을 만들 수 있습니다. 텍스트 템플릿에 대 한 기본 정보는 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요. DSL을 디버그할 때 텍스트 템플릿은 실험적 모드에서 작동 하 고 DSL을 배포한 컴퓨터 에서도 작동 합니다.

> [!NOTE]
> DSL 솔루션을 만들 때 예제 텍스트 템플릿인 .tt 파일이 디버깅 프로젝트에 생성 됩니다 ** \* .** 도메인 클래스의 이름을 변경 하면 이러한 템플릿이 더 이상 작동 하지 않습니다. 그럼에도 불구 하 고 필요한 기본 지시문을 포함 하 고 DSL과 일치 하도록 업데이트할 수 있는 예제를 제공 합니다.

 텍스트 템플릿에서 모델에 액세스 하려면 다음을 수행 합니다.

- 템플릿 지시문의 inherit 속성을 VisualStudio로 설정 합니다. [vshost.exe로 변환](/previous-versions/bb893209(v=vs.140))합니다. 저장소에 대 한 액세스를 제공 합니다.

- 액세스 하려는 DSL에 대 한 지시문 프로세서를 지정 합니다. 그러면 텍스트 템플릿의 코드에서 해당 도메인 클래스, 속성 및 관계를 사용할 수 있도록 DSL에 대 한 어셈블리가 로드 됩니다. 또한 지정한 모델 파일도 로드 합니다.

  `.tt`다음 예제와 비슷한 파일은 DSL 최소 언어 템플릿에서 새 Visual Studio 솔루션을 만들 때 디버깅 프로젝트에서 만들어집니다.

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

 이 템플릿에 대 한 다음 사항에 유의 하세요.

- 이 템플릿에서는 DSL 정의에 정의 된 도메인 클래스, 속성 및 관계를 사용할 수 있습니다.

- 템플릿은 속성에 지정 된 모델 파일을 로드 합니다 `requires` .

- 의 속성은 `this` 루트 요소를 포함 합니다. 여기에서 코드는 모델의 다른 요소로 이동할 수 있습니다. 속성의 이름은 일반적으로 DSL의 루트 도메인 클래스와 동일 합니다. 이 예제에서는 `this.ExampleModel`입니다.

- 코드 조각이 작성 되는 언어는 c # 이지만 모든 종류의 텍스트를 생성할 수 있습니다. 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 지시문에 속성을 추가 하 여에서 코드를 작성할 수 있습니다 `language="VB"` `template` .

- 템플릿을 디버깅 하려면 `debug="true"` 지시문에를 추가 합니다 `template` . 예외가 발생 하는 경우 템플릿은 Visual Studio의 다른 인스턴스에서 열립니다. 코드의 특정 지점에서 디버거를 중단 하려면 문을 삽입 합니다. `System.Diagnostics.Debugger.Break();`

   자세한 내용은 [T4 텍스트 템플릿 디버깅](../modeling/debugging-a-t4-text-template.md)을 참조 하세요.

## <a name="about-the-dsl-directive-processor"></a>DSL 지시문 프로세서 정보
 템플릿은 DSL 정의에 정의 된 도메인 클래스를 사용할 수 있습니다. 이는 일반적으로 템플릿 시작 부분에 표시 되는 지시문에 의해 수행 됩니다. 이전 예에서는 다음과 같습니다.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 지시문의 이름 ( `MyLanguage` 이 예제에서는)은 DSL의 이름에서 파생 됩니다. DSL의 일부로 생성 된 *지시문 프로세서* 를 호출 합니다. **Dsl\GeneratedCode\DirectiveProcessor.cs**에서 소스 코드를 찾을 수 있습니다.

 DSL 지시문 프로세서는 다음과 같은 두 가지 주요 작업을 수행 합니다.

- DSL을 참조 하는 템플릿에 어셈블리 및 가져오기 지시문을 효과적으로 삽입 합니다. 이렇게 하면 템플릿 코드에서 도메인 클래스를 사용할 수 있습니다.

- 매개 변수에서 지정 하는 파일을 로드 하 `requires` 고 `this` 로드 된 모델의 루트 요소를 참조 하는의 속성을 설정 합니다.

## <a name="validating-the-model-before-running-the-template"></a>템플릿을 실행 하기 전에 모델 유효성 검사
 템플릿이 실행 되기 전에 모델의 유효성을 검사할 수 있습니다.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 다음에 유의합니다.

1. `filename`및 `validation` 매개 변수는 ";"으로 구분 되며 다른 구분 기호 또는 공백이 없어야 합니다.

2. 유효성 검사 범주 목록에 따라 실행 될 유효성 검사 방법이 결정 됩니다. 여러 범주는 "&#124;"로 구분 해야 하며 다른 구분 기호 또는 공백이 없어야 합니다.

   오류가 발견 되 면 오류 창에 보고 되며 결과 파일에는 오류 메시지가 포함 됩니다.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> 텍스트 템플릿에서 여러 모델 액세스

> [!NOTE]
> 이 방법을 사용 하면 동일한 템플릿에서 여러 모델을 읽을 수 있지만 ModelBus 참조는 지원 하지 않습니다. ModelBus 참조를 사용 하 여 interlinked 모델을 읽으려면 [텍스트 템플릿에서 Visual Studio ModelBus 사용](../modeling/using-visual-studio-modelbus-in-a-text-template.md)을 참조 하세요.

 동일한 텍스트 템플릿에서 둘 이상의 모델에 액세스 하려는 경우에는 각 모델에 대해 생성 된 지시문 프로세서를 한 번씩 호출 해야 합니다. 매개 변수에서 각 모델의 파일 이름을 지정 해야 합니다 `requires` . 매개 변수에서 루트 도메인 클래스에 사용할 이름을 지정 해야 합니다 `provides` . `provides`각 지시문 호출에서 매개 변수에 대해 서로 다른 값을 지정 해야 합니다. 예를 들어 Library. xyz, School, .xyz 이라는 세 가지 모델 파일이 있다고 가정 합니다. 동일한 텍스트 템플릿에서 액세스 하려면 다음 세 가지 지시문 호출을 작성 해야 합니다.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> 이 예제 코드는 최소 언어 솔루션 템플릿을 기반으로 하는 언어에 대 한 코드입니다.

 텍스트 템플릿에서 모델에 액세스 하기 위해 이제 다음 예제의 코드와 유사한 코드를 작성할 수 있습니다.

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
 런타임에 로드할 모델을 결정 하려는 경우 DSL 관련 지시문을 사용 하는 대신 프로그램 코드에서 모델 파일을 동적으로 로드할 수 있습니다.

 그러나 dsl 관련 지시문의 함수 중 하나는 dsl 네임 스페이스를 가져오는 것입니다. 그러면 템플릿 코드가 해당 DSL에 정의 된 도메인 클래스를 사용할 수 있습니다. 지시문을 사용 하 고 있지 않기 때문에 **\<assembly>** **\<import>** 로드할 수 있는 모든 모델에 대해 및 지시문을 추가 해야 합니다. 로드할 수 있는 여러 모델이 동일한 DSL의 모든 인스턴스인 경우이 방법은 간단 합니다.

 파일을 로드 하기 위해 가장 효과적인 방법은 Visual Studio ModelBus를 사용 하는 것입니다. 일반적인 시나리오에서 텍스트 템플릿은 DSL 관련 지시문을 사용 하 여 일반적인 방법으로 첫 번째 모델을 로드 합니다. 해당 모델에는 다른 모델에 대 한 ModelBus 참조가 포함 됩니다. ModelBus를 사용 하 여 참조 된 모델을 열고 특정 요소에 액세스할 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 Visual Studio ModelBus 사용](../modeling/using-visual-studio-modelbus-in-a-text-template.md)을 참조 하세요.

 일반적이 지 않은 시나리오에서는 파일 이름만 있고 현재 Visual Studio 프로젝트에 없을 수 있는 모델 파일을 열어야 할 수 있습니다. 이 경우 [방법: 프로그램 코드에서 파일을](../modeling/how-to-open-a-model-from-file-in-program-code.md)사용 하 여 모델 열기에 설명 된 기술을 사용 하 여 파일을 열 수 있습니다.

## <a name="generating-multiple-files-from-a-template"></a>템플릿에서 여러 파일 생성
 여러 파일을 생성 하려는 경우, 예를 들어 모델의 각 요소에 대해 별도의 파일을 생성 하려는 경우 여러 가지 방법을 사용할 수 있습니다. 기본적으로 각 템플릿 파일에서 하나의 파일만 생성 됩니다.

### <a name="splitting-a-long-file"></a>긴 파일 분할
 이 방법에서는 템플릿을 사용 하 여 구분 기호로 구분 된 단일 파일을 생성 합니다. 그런 다음 파일을 파트로 분할 합니다. 두 개의 템플릿이 있습니다. 하나는 단일 파일을 생성 하 고 다른 하나는 분할 하는 데 사용할 수 있습니다.

 **LoopTemplate** 는 긴 단일 파일을 생성 합니다. 파일 확장명은 **모든 템플릿 변환**을 클릭 하면 직접 처리 되지 않으므로 파일 확장명이 "t4"입니다. 이 템플릿은 세그먼트를 구분 하는 구분 기호 문자열을 지정 하는 매개 변수를 사용 합니다.

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

 `LoopSplitter.tt` 는 `LoopTemplate.t4` 를 호출한 다음 결과 파일을 해당 세그먼트로 분할 합니다. 이 템플릿은 모델을 읽지 않기 때문에 모델링 템플릿이 될 필요는 없습니다.

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
