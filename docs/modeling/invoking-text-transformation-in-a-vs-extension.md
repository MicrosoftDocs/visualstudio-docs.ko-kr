---
title: VS 확장명에서 텍스트 변형 호출
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ab846d1d7121d0c36c4187d937330d2ade52eb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594593"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Visual Studio 확장에서 텍스트 변환 호출

메뉴 명령 또는 [도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)와 같은 Visual Studio 확장을 작성 하는 경우 텍스트 템플릿 서비스를 사용 하 여 텍스트 템플릿을 변환할 수 있습니다. [Stexttemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) 를 가져와서 [itexttemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))로 캐스팅 합니다.

## <a name="get-the-text-templating-service"></a>텍스트 템플릿 서비스 가져오기

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>템플릿에 매개 변수 전달

 템플릿에 매개 변수를 전달할 수 있습니다. 템플릿 내에서 `<#@parameter#>` 지시문을 사용하여 매개 변수 값을 가져올 수 있습니다.

 매개 변수 형식으로는 serialize 가능하거나 마샬링할 수 있는 형식을 사용해야 합니다. 즉, 매개 변수 형식은 <xref:System.SerializableAttribute>를 사용하여 선언되거나 <xref:System.MarshalByRefObject>에서 파생되어야 합니다. 텍스트 템플릿은 별도의 AppDomain에서 실행되므로 이러한 제한 사항이 필요합니다. **System.string** 및 **system.object** 와 같은 모든 기본 제공 형식은 serialize 할 수 있습니다.

 매개 변수 값을 전달하기 위해 호출 코드에서 값을 `Session` 사전이나 <xref:System.Runtime.Remoting.Messaging.CallContext>에 둘 수 있습니다.

 다음 예제에서는 두 가지 방법을 사용하여 짧은 테스트 템플릿을 변형합니다.

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>오류 보고 및 output 지시문

처리 하는 동안 발생 하는 모든 오류는 Visual Studio 오류 창에 표시 됩니다. 또한 [Itexttemplatingcallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110))을 구현 하는 콜백을 지정 하 여 오류에 대 한 알림이 표시 될 수 있습니다.

결과 문자열을 파일에 기록하려는 경우 템플릿의 `<#@output#>` 지시문에 지정된 파일 확장명과 인코딩을 알아야 할 수 있습니다. 이 정보도 역시 콜백에 전달됩니다. 자세한 내용은 [T4 Output 지시어](../modeling/t4-output-directive.md)를 참조 하세요.

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

다음과 비슷한 템플릿 파일을 사용하여 코드를 테스트할 수 있습니다.

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

컴파일러 경고는 Visual Studio 오류 창에 표시 되 고에 대 한 호출도 생성 됩니다 `ErrorCallback` .

## <a name="reference-parameters"></a>참조 매개 변수

<xref:System.MarshalByRefObject>에서 파생되는 매개 변수 클래스를 사용하여 텍스트 템플릿의 값을 전달할 수 있습니다.

## <a name="related-articles"></a>관련된 문서

전처리 된 텍스트 템플릿에서 텍스트를 생성 하려면: 생성 된 `TransformText()` 클래스의 메서드를 호출 합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요.

Visual Studio 확장 외부에서 텍스트를 생성 하려면: 사용자 지정 호스트를 정의 합니다. 자세한 내용은 [사용자 지정 호스트를 사용 하 여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)를 참조 하세요.

나중에 컴파일 및 실행할 수 있는 소스 코드를 생성 하려면 [Itexttemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110))의 [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) 메서드를 호출 합니다.
