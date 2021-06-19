---
title: T4 매개 변수 지시문
description: Visual Studio 매개 변수 지시문은 외부 컨텍스트에서 전달된 값에서 초기화된 템플릿 코드의 속성을 선언합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386100"
---
# <a name="t4-parameter-directive"></a>T4 매개 변수 지시문

Visual Studio 텍스트 템플릿에서 `parameter` 지시문은 외부 컨텍스트에서 전달된 값에서 초기화된 템플릿 코드의 속성을 선언합니다. 텍스트 변환을 호출하는 코드를 작성하는 경우 이러한 값을 설정할 수 있습니다.

## <a name="using-the-parameter-directive"></a>매개 변수 지시문 사용

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`지시문은 외부 컨텍스트에서 전달된 값에서 초기화된 템플릿 코드의 속성을 선언합니다. 텍스트 변환을 호출하는 코드를 작성하는 경우 이러한 값을 설정할 수 있습니다. 값은 사전 또는 에서 전달할 수 `Session` <xref:System.Runtime.Remoting.Messaging.CallContext> 있습니다.

 모든 remotable 형식의 매개 변수를 선언할 수 있습니다. 즉, 형식을 로 선언하거나 <xref:System.SerializableAttribute> 에서 파생되어야 <xref:System.MarshalByRefObject> 합니다. 이렇게 하면 템플릿이 처리되는 AppDomain에 매개 변수 값을 전달할 수 있습니다.

 예를 들어 다음 내용이 있는 텍스트 템플릿을 작성할 수 있습니다.

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>템플릿에 매개 변수 값 전달
 메뉴 명령 또는 이벤트 처리기와 같은 Visual Studio 확장을 작성하는 경우 텍스트 템플릿 서비스를 사용하여 템플릿을 처리할 수 있습니다.

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>호출 컨텍스트에서 값 전달
 또는 에서 값을 논리 데이터로 전달할 수 <xref:System.Runtime.Remoting.Messaging.CallContext> 있습니다.

 다음 예제에서는 두 메서드를 모두 사용하여 값을 전달합니다.

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Run-Time(전처리) 텍스트 템플릿에 값 전달
 일반적으로 `<#@parameter#>` 런타임(전처리) 텍스트 템플릿과 함께 지시문을 사용할 필요는 없습니다. 대신 매개 변수 값을 전달하는 생성된 코드에 대한 추가 생성자 또는 settable 속성을 정의할 수 있습니다. 자세한 내용은 [T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조하세요.

 그러나 런타임 템플릿에서 를 사용하려는 경우 `<#@parameter>` 세션 사전을 사용하여 값을 전달할 수 있습니다. 예를 들어 파일을 라는 전처리된 템플릿으로 만들었다고 `PreTextTemplate1` 가정합니다. 다음 코드를 사용하여 프로그램에서 템플릿을 호출할 수 있습니다.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>TextTemplate.exe 인수 얻기

> [!IMPORTANT]
> `parameter`지시문은 유틸리티의 매개 변수에 설정된 값을 검색하지 `-a` `TextTransform.exe` 않습니다. 이러한 값을 얻으려면 지시문에서 를 설정하고 `hostSpecific="true"` `template` 를 `this.Host.ResolveParameterValue("","","argName")` 사용합니다.
