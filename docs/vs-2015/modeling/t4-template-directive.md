---
title: T4 템플릿 지시문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02ab48e2fcd014508277a9bc361cde65d62ef38c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850784"
---
# <a name="t4-template-directive"></a>T4 템플릿 지시문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적으로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 텍스트 템플릿은 템플릿의 처리 방식을 지정하는 `template` 지시문으로 시작합니다. 하나의 텍스트 템플릿 및 템플릿이 포함된 파일에는 템플릿 지시문이 하나만 있어야 합니다.

 텍스트 템플릿 작성에 대 한 일반적인 개요는 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

## <a name="using-the-template-directive"></a>template 지시문 사용

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

 `template` 지시문에는 변환의 다양한 측면을 지정할 수 있도록 하는 몇 가지 특성이 있습니다. 모든 특성은 선택적입니다.

## <a name="compileroptions-attribute"></a>compilerOptions 특성
 예: `compilerOptions="optimize+"`

 유효한 값: 유효한 모든 컴파일러 옵션입니다. 자세한 내용은 [c # 컴파일러 옵션 범주별 목록](https://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83) 및 [Visual Basic 컴파일러 옵션 범주별 목록](https://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3)을 참조 하세요.

 전처리된 런타임 템플릿의 경우 무시됩니다.

 이 옵션은 템플릿이 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 또는 [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]으로 변환된 경우 적용되며 결과 코드는 컴파일됩니다.

## <a name="culture-attribute"></a>culture 특성
 예: `culture="de-CH"`

 유효한 값: "", 고정 문화권 (기본값)입니다.

 xx-XX 형식의 문자열로 표현된 문화권. 예를 들어 en-US, ja-JP, de-CH, de-DE 등입니다. 자세한 내용은 <xref:System.Globalization.CultureInfo?displayProperty=fullName>를 참조하세요.

 식 블록이 텍스트로 변환될 때 사용할 문화권을 지정하는 culture 특성입니다.

## <a name="debug-attribute"></a>debug 특성
 예:

```
debug="true"
```

 유효한 값은 `true, false` 입니다. 기본값은 False입니다.

 `debug` 특성이 `true`인 경우 중간 코드 파일에 디버거가 중단 또는 예외가 발생한 템플릿의 위치를 정확하게 식별할 수 있도록 하는 정보가 포함됩니다.

 디자인 타임 템플릿의 경우 중간 코드 파일은 **% TEMP%** 디렉터리에 기록 됩니다.

 디버거에서 디자인 타임 템플릿을 실행 하려면 텍스트 템플릿을 저장 한 다음 솔루션 탐색기에서 텍스트 템플릿의 바로 가기 메뉴를 열고 **T4 템플릿 디버그**를 선택 합니다.

## <a name="hostspecific-attribute"></a>hostspecific 특성
 예:

```
hostspecific="true"
```

 유효한 값은 `true, false, trueFromBase` 입니다. 기본값은 False입니다.

 이 특성의 값을 `true`로 설정하면 `Host`라는 속성이 텍스트 템플릿에서 생성된 클래스에 추가됩니다. 속성은 변환 엔진의 호스트에 대 한 참조 이며 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))로 선언 됩니다. 사용자 지정 호스트를 정의한 경우에는 해당 호스트를 사용자 지정 호스트 형식으로 캐스팅할 수 있습니다.

 이 속성의 형식이 호스트의 형식에 따라 달라지기 때문에 이 속성은 특정 호스트에서만 작동하는 텍스트 템플릿을 작성하는 경우에만 유용합니다. [디자인 타임 템플릿에](../modeling/design-time-code-generation-by-using-t4-text-templates.md)는 적용 되지만 [런타임 템플릿에](../modeling/run-time-text-generation-with-t4-text-templates.md)는 적용 되지 않습니다.

 `hostspecific`이 `true`이고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용하고 있는 경우 `this.Host`를 IServiceProvider로 캐스팅하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 기능에 액세스할 수 있습니다. `Host.ResolvePath(filename)`를 사용하여 프로젝트에서 파일의 절대 경로를 가져올 수도 있습니다. 예를 들면 다음과 같습니다.

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

 `inherits`와 `hostspecific` 특성을 함께 사용하는 경우, 파생 클래스에 host="trueFromBase"를 지정하고 기본 클래스에는 host="true"를 지정하십시오. 이렇게 하면 생성된 코드에서 `Host` 속성의 이중 정의를 피할 수 있습니다.

## <a name="language-attribute"></a>language 특성
 예: `language="VB"`

 유효한 값: `C#` (기본값)

 `VB`

 Language 특성은 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] 문 및 식 블록의 소스 코드에 사용할 언어 (또는)를 지정 합니다. 출력이 생성되는 중간 코드 파일에서 이 언어가 사용됩니다. 이 언어는 템플릿에서 생성되는 언어와 관련이 없으며 모든 종류의 텍스트일 수 있습니다.

 예를 들면 다음과 같습니다.

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>

```

## <a name="inherits-attribute"></a>inherits 특성
 템플릿의 프로그램 코드가 텍스트 템플릿에서 생성될 수도 있는 다른 클래스에서 상속하도록 지정할 수 있습니다.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>전처리된 런타임 텍스트 템플릿의 상속
 런타임 텍스트 템플릿 간에 상속을 사용하여 여러 파생 변형이 있는 기본 템플릿을 만들 수 있습니다. 런타임 템플릿은 **사용자 지정 도구** 속성이 **Texttemplatingfilepreprocessor**로 설정 된 템플릿입니다. 런타임 템플릿에서는 애플리케이션에서 호출하여 템플릿에 정의된 텍스트를 만들 수 있는 코드를 생성합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요.

 `inherits` 특성을 지정하지 않으면 기본 클래스 및 파생 클래스가 텍스트 템플릿에서 생성됩니다. `inherits` 특성을 지정하면 파생 클래스만 생성됩니다. 기본 클래스를 직접 작성할 수 있지만 기본 클래스에서 파생 클래스에 사용되는 메서드를 제공해야 합니다.

 또한 전처리된 다른 템플릿을 기본 클래스로 지정하는 것이 더 일반적입니다. 기본 템플릿에서는 파생 템플릿의 텍스트를 인터리브할 수 있는 공통 텍스트 블록을 제공합니다. 클래스 기능 블록 `<#+ ... #>`을 사용하여 텍스트 조각이 들어 있는 메서드를 정의할 수 있습니다. 예를 들어 출력 텍스트의 프레임워크를 기본 템플릿에 둠으로써 파생 템플릿에 재정의할 수 있는 가상 메서드를 제공할 수 있습니다.

 전처리된 런타임 텍스트 템플릿 BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>

```

 전처리된 런타임 텍스트 템플릿 DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>

```

 DerivedTemplate1을 호출할 애플리케이션 코드:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

 결과 출력:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

 서로 다른 프로젝트에서 기본 클래스와 파생 클래스를 빌드할 수 있습니다. 기본 프로젝트 또는 어셈블리를 파생 프로젝트의 참조에 추가해야 합니다.

 직접 작성한 일반 클래스를 기본 클래스로 사용할 수도 있습니다. 기본 클래스는 파생 클래스에 사용되는 메서드를 제공합니다.

> [!WARNING]
> `inherits`와 `hostspecific` 특성을 함께 사용하는 경우, 파생 클래스에 hostspecific="trueFromBase"를 지정하고 기본 클래스에는 host="true"를 지정하십시오. 이렇게 하면 생성된 코드에서 `Host` 속성의 이중 정의를 피할 수 있습니다.

### <a name="inheritance-in-a-design-time-text-template"></a>디자인 타임 텍스트 템플릿의 상속
 디자인 타임 텍스트 템플릿은 **사용자 지정 도구가** **Texttemplatingfilegenerator**로 설정 된 파일입니다. 이 템플릿에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 일부를 구성하는 코드 또는 텍스트의 출력 파일을 생성합니다. 출력 파일을 생성하기 위해 먼저 템플릿이 중간 프로그램 코드 파일로 변환되며, 대개 이 파일은 보이지 않습니다. `inherits` 특성은 이 중간 코드를 위한 기본 클래스를 지정합니다.

 디자인 타임 텍스트 템플릿의 경우에는 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> 클래스에서 파생되는 기본 클래스를 지정할 수 있습니다. `<#@assembly#>` 지시문을 사용하여 기본 클래스가 들어 있는 프로젝트나 어셈블리를 로드합니다.

 자세한 내용은 [Gareth Jones의 블로그에서 "텍스트 템플릿의 상속"](https://blogs.msdn.microsoft.com/garethj/2011/01/03/vs2010-sp1-t4-template-inheritance-part-i-sample-metadata/)을 참조 하세요.

## <a name="linepragmas-attribute"></a>LinePragmas 특성
 예: `linePragmas="false"`

 유효한 값: `true` (기본값)

 `false`

 이 특성을 false로 설정하면 생성된 코드에서 줄 번호를 식별하는 태그가 제거됩니다. 즉, 컴파일러에서 생성된 코드의 줄 번호를 사용하여 모든 오류를 보고하는 것을 의미합니다. 이렇게 하면 텍스트 템플릿 또는 생성된 코드를 디버깅하도록 선택할 수 있어 더 많은 디버깅 옵션을 사용할 있습니다.

 이 특성은 소스 코드 컨트롤에 따라 프로그램에서 산만한 병합을 유발하는 정확한 파일 이름을 찾는 경우 유용할 수 있습니다.

## <a name="visibility-attribute"></a>표시 유형 특성
 예: `visibility="internal"`

 유효한 값: `public` (기본값)

 `internal`

 런타임 텍스트 템플릿에서 생성된 클래스의 표시 유형 특성을 설정합니다. 기본적으로 클래스는 사용자 코드의 공용 API에 속하지만 `visibility="internal"`을 설정하여 사용자의 코드만 텍스트 생성 클래스를 사용할 수 있도록 지정할 수 있습니다.
