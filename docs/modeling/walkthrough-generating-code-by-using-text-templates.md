---
title: '연습: 텍스트 템플릿을 사용하여 코드 생성'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 181c1ccbeaff0aadee1b3d5ebd255b854b915277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532062"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>연습: 텍스트 템플릿을 사용하여 코드 생성

코드 생성 기능을 사용하면 강력한 형식을 가지고 있지만 소스 모델이 변경될 때 손쉽게 변경할 수 있는 프로그램 코드를 생성할 수 있습니다. 이와 반대로, 구성 파일을 허용하는 완전한 제네릭 프로그램을 작성하는 대체 방식을 사용할 경우에는 좀 더 유연성이 있지만 코드를 읽고 변경하기가 쉽지 않으며 코드의 성능도 그렇게 좋지 않습니다. 이 연습에서는 이러한 이점을 보여 줍니다.

## <a name="typed-code-for-reading-xml"></a>XML 읽기를 위한 형식화된 코드

System.Xml 네임스페이스는 XML 문서를 로드하고 메모리에서 자유롭게 탐색하기 위한 포괄적인 도구를 제공합니다. 아쉽게도 모든 노드에는 동일한 형식인 XmlNode가 있습니다. 따라서 잘못된 형식의 자식 노드 또는 잘못된 특성이 나타나는 등의 프로그래밍 실수가 쉽게 발생할 수 있습니다.

이 예제 프로젝트에서는 템플릿이 샘플 XML 파일을 읽고, 각 노드 형식에 해당하는 클래스를 생성합니다. 직접 작성한 코드에서 이러한 클래스를 사용하여 XML 파일을 탐색할 수 있습니다. 동일한 노드 형식을 사용하는 다른 파일에서 애플리케이션을 실행할 수도 있습니다. 샘플 XML 파일의 목적은 애플리케이션에서 처리하고자 하는 모든 노드 형식의 예를 제공하는 것입니다.

> [!NOTE]
> Visual Studio에 포함 된 응용 프로그램 [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)는 XML 파일에서 강력한 형식의 클래스를 생성할 수 있습니다. 여기에 표시된 템플릿은 예로서 제공됩니다.

샘플 파일은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

이 연습에서 생성하는 프로젝트에서는 다음과 같은 코드를 작성할 수 있습니다. 그러면 입력 시 IntelliSense에서 올바른 특성 및 자식 이름을 입력하라는 메시지가 표시됩니다.

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

이것을 템플릿 없이 작성할 수 있는 형식이 지정되지 않은 코드와 비교해보세요.

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

강력한 형식의 버전에서 XML 스키마를 변경 하면 클래스가 변경 됩니다. 컴파일러는 변경 해야 하는 응용 프로그램 코드의 일부를 강조 표시 합니다. 제네릭 XML 코드를 사용하는 형식화되지 않은 버전에서는 이러한 기능이 지원되지 않습니다.

이 프로젝트에서는 형식이 지정된 버전을 가능하게 하는 클래스를 생성하기 위해 단일 템플릿 파일이 사용됩니다.

## <a name="set-up-the-project"></a>프로젝트 설정

### <a name="create-or-open-a-c-project"></a>C# 프로젝트를 만들거나 엽니다.

모든 코드 프로젝트에 이 방법을 적용할 수 있습니다. 이 연습에서는 C# 프로젝트를 사용하며, 테스트를 목적으로 콘솔 애플리케이션을 사용합니다.

1. **파일** 메뉴에서 **새로 만들기** 를 클릭 한 다음 **프로젝트**를 클릭 합니다.

2. **Visual C#** 노드를 클릭한 다음, **템플릿** 창에서 **콘솔 애플리케이션**을 클릭합니다.

### <a name="add-a-prototype-xml-file-to-the-project"></a>프로토타입 XML 파일을 프로젝트에 추가

이 파일의 목적은 애플리케이션에 읽을 수 있도록 할 XML 노드 형식의 샘플을 제공하는 것입니다. 그러한 샘플은 애플리케이션 테스트에 사용할 파일이 될 수도 있습니다. 템플릿은 이 파일의 각 노드 형식에 대해 C# 클래스를 생성합니다.

파일은 템플릿이 읽을 수 있도록 프로젝트의 일부여야 하지만, 컴파일된 애플리케이션에 빌드되지는 않습니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 클릭 한 다음 **새 항목**을 클릭 합니다.

2. **새 항목 추가** 대화 상자의 **템플릿** 창에서 **XML 파일** 을 선택합니다.

3. 샘플 내용을 파일에 추가합니다.

4. 이 연습에서는 파일 이름을 `exampleXml.xml`로 지정합니다. 이전 섹션에 표시된 XML이 되도록 파일의 내용을 설정합니다.

### <a name="add-a-test-code-file"></a>테스트 코드 파일 추가

C# 파일을 프로젝트에 추가하고, 여기에 원하는 코드의 샘플을 작성합니다. 예:

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

이 단계에서 이 코드를 컴파일하려고 하면 실패합니다. 템플릿을 작성할 때는 성공하도록 허용하는 클래스를 생성하게 됩니다.

좀 더 포괄적인 테스트에서는 예제 XML 파일의 알려진 내용을 기준으로 이 테스트 기능의 출력을 확인할 수 있습니다. 그러나 이 연습에서는 테스트 메서드가 컴파일되는 것까지만 확인합니다.

### <a name="add-a-text-template-file"></a>텍스트 템플릿 파일 추가

텍스트 템플릿 파일을 추가 하 고 출력 확장을 *.cs*로 설정 합니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가**를 클릭한 다음 **새 항목**을 클릭합니다.

2. **새 항목 추가** 대화 상자의 **템플릿** 창에서 **텍스트 템플릿** 을 선택합니다.

    > [!NOTE]
    > 전처리 텍스트 템플릿이 아니라 텍스트 템플릿을 추가하는지 확인합니다.

3. 파일의 템플릿 지시문에서 `hostspecific` 특성을 `true`로 변경합니다.

     이렇게 변경 하면 템플릿 코드가 Visual Studio 서비스에 액세스할 수 있습니다.

4. 템플릿이 C# 파일을 생성할 수 있도록 출력 지시문에서 확장 특성을 ".cs"로 변경합니다. Visual Basic 프로젝트에서는 이를 ".vb"로 변경할 수 있습니다.

5. 파일을 저장합니다. 이 단계에서 텍스트 템플릿 파일에는 다음 줄이 포함됩니다.

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

템플릿 파일의 보조 파일로 솔루션 탐색기에 .cs 파일이 표시되는지 확인합니다. 템플릿 파일의 이름 옆에 있는 [+]를 클릭하여 확인할 수 있습니다. 템플릿 파일을 저장하거나 템플릿 파일에서 포커스를 이동할 때마다 이 파일이 템플릿 파일에서 생성됩니다. 생성된 파일은 프로젝트의 일부로 컴파일됩니다.

템플릿 파일을 개발하는 동안 편의를 위해, 템플릿 파일과 생성된 파일의 창을 나란히 볼 수 있도록 정렬합니다. 이렇게 하면 템플릿의 출력을 즉시 확인할 수 있습니다. 또한 템플릿에서 잘못된 C# 코드를 생성하면 이를 확인할 수 있으며, 오류 메시지 창에 오류가 표시됩니다.

생성된 파일에서 직접 수행한 편집 내용은 템플릿 파일을 저장할 때마다 손실됩니다. 따라서 생성된 파일을 편집하지 않거나 간단한 실험용으로만 편집해야 합니다. IntelliSense가 작동 중일 때 생성된 파일에서 짧은 코드 조각을 시도해본 후 템플릿 파일에 복사하는 것이 더러 도움이 될 수 있습니다.

## <a name="develop-the-text-template"></a>텍스트 템플릿 개발

민첩한 개발을 위한 가장 적합한 방식에 따라, 소수의 몇 단계를 통해 템플릿을 개발하고 테스트 코드가 정확하게 컴파일 및 실행될 때까지 점진적으로 오류를 지워보겠습니다.

### <a name="prototype-the-code-to-be-generated"></a>생성할 코드의 프로토타입

테스트 코드에서는 파일의 각 노드에 대해 클래스를 요구합니다. 따라서 이러한 줄을 템플릿에 추가하고 저장하면 몇 가지 컴파일 오류가 사라집니다.

```csharp
class Catalog {}
class Artist {}
class Song {}
```

이렇게 하면 무엇이 필요한지를 알 수 있지만, 샘플 XML 파일의 노드 형식에서 선언을 생성해야 합니다. 템플릿에서 이러한 실험용 줄을 삭제합니다.

### <a name="generate-application-code-from-the-model-xml-file"></a>모델 XML 파일에서 애플리케이션 코드 생성

XML 파일을 읽고 클래스 선언을 생성하려면 템플릿 내용을 다음 템플릿 코드로 바꿉니다.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

파일 경로를 프로젝트에 대한 올바른 경로로 바꿉니다.

코드 블록 구분 기호는 `<#...#>`입니다. 이러한 구분 기호는 텍스트를 생성하는 프로그램 코드의 조각을 대괄호로 묶습니다. 식 블록 구분 기호 `<#=...#>` 은 문자열로 계산될 수 있는 식을 대괄호로 묶습니다.

애플리케이션에 대한 소스 코드를 생성하는 템플릿을 작성하는 경우 두 개의 별도 프로그램 텍스트를 다루게 됩니다. 코드 블록 구분 기호 내의 프로그램은 템플릿을 저장하거나 다른 창으로 포커스를 이동할 때마다 실행됩니다. 구분 기호 외부에 나타나는, 템플릿에서 생성하는 텍스트는 생성된 파일에 복사되고 애플리케이션 코드의 일부가 됩니다.

`<#@assembly#>` 지시문은 참조처럼 작동하여 어셈블리를 템플릿 코드에 사용할 수 있도록 해 줍니다. 템플릿에서 볼 수 있는 어셈블리의 목록은 애플리케이션 프로젝트에 있는 참조의 목록과 별개입니다.

`<#@import#>` 지시문은 `using` 문의 역할을 하므로, 가져온 네임스페이스에서 클래스의 짧은 이름을 사용할 수 있습니다.

아쉽게도, 이 템플릿은 비록 코드를 생성하지만 예제 XML 파일의 모든 노드에 대해 클래스 선언을 생성하므로, `<song>` 노드의 여러 인스턴스가 있는 경우 클래스 song의 여러 선언이 나타납니다.

### <a name="read-the-model-file-then-generate-the-code"></a>모델 파일을 읽은 다음 코드 생성

많은 텍스트 템플릿은 템플릿의 첫 번째 부분이 소스 파일을 읽고 두 번째 부분이 템플릿을 생성하는 패턴을 따릅니다. 예제 파일 전체를 읽고 여기에 포함된 노드 형식을 요약한 다음 클래스 선언을 생성해야 합니다. `<#@import#>`를 사용하려면 또 다른 `Dictionary<>:`가 필요합니다.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>보조 메서드 추가

클래스 기능 제어 블록은 보조 메서드를 정의할 수 있는 블록입니다. 이 블록은 `<#+...#>` 으로 구분되며 파일의 마지막 블록으로 표시되어야 합니다.

클래스 이름이 대문자로 시작되도록 하려면 템플릿의 마지막 부분을 다음 템플릿 코드로 바꿀 수 있습니다.

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

이 단계에서 생성 된 *.cs* 파일에는 다음 선언이 포함 됩니다.

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

자식 노드에 대한 속성, 특성, 내부 텍스트와 같은 자세한 내용을 동일한 방식으로 추가할 수 있습니다.

### <a name="access-the-visual-studio-api"></a>Visual Studio API에 액세스

`hostspecific`지시문의 특성을 설정 `<#@template#>` 하면 템플릿이 VISUAL Studio API에 대 한 액세스 권한을 얻을 수 있습니다. 템플릿에서는 이 특성을 사용하여 프로젝트 파일의 위치를 가져올 수 있는데, 이렇게 하면 템플릿 코드에서 절대 파일 경로를 사용하지 않아도 됩니다.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>텍스트 템플릿 완료

다음 템플릿 내용은 테스트 코드의 컴파일과 실행을 허용하는 코드를 생성합니다.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>테스트 프로그램 실행

콘솔 애플리케이션의 기본 창에서 다음 줄이 테스트 메서드를 실행합니다. 디버그 모드에서 프로그램을 실행하려면 F5를 누릅니다.

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>응용 프로그램 작성 및 업데이트

이제 제네릭 XML 코드를 사용하는 대신 생성된 클래스를 사용하여 강력한 형식의 스타일로 애플리케이션을 작성할 수 있습니다.

XML 스키마가 변경되면 새 클래스를 쉽게 생성할 수 있습니다. 컴파일러는 애플리케이션 코드를 어디에서 업데이트해야 하는지를 개발자에게 알려 줍니다.

예제 XML 파일이 변경 될 때 클래스를 다시 생성 하려면 **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다.

## <a name="conclusion"></a>결론

이 연습에서는 코드 생성의 몇 가지 방법과 이점에 대해 설명합니다.

- *코드 생성* 이란 *모델*에서 애플리케이션 소스 코드의 일부를 생성하는 것입니다. 모델은 애플리케이션 도메인에 적합한 형식으로 정보를 포함하고 있으며, 애플리케이션의 수명 동안 변경될 수 있습니다.

- 강력한 형식 지정은 코드 생성의 이점 중 하나입니다. 모델은 사용자에게 좀 더 적합한 형식으로 정보를 표현하며, 생성된 코드는 애플리케이션의 다른 부분에서 형식 집합을 사용하여 정보를 처리하도록 허용합니다.

- IntelliSense 및 컴파일러를 사용하면 새 코드를 작성할 때와 스키마를 업데이트할 때 모두 모델의 스키마를 따르는 코드를 생성할 수 있습니다.

- 복잡하지 않은 단일 템플릿 파일을 프로젝트에 추가하면 이러한 혜택을 제공할 수 있습니다.

- 텍스트 템플릿은 증분 방식으로 빠르게 개발 및 테스트할 수 있습니다.

이 연습에서는 애플리케이션이 처리할 XML 파일의 대표적인 예인 모델의 인스턴스에서 실제로 프로그램 코드가 생성됩니다. 좀 더 공식적인 방식에서, XML 스키마는 .xsd 파일 또는 도메인 특정 언어 정의 형식으로 템플릿에 입력될 수 있습니다. 이 방식을 사용하면 템플릿이 관계의 다중성과 같은 특성을 더 쉽게 결정할 수 있습니다.

## <a name="troubleshoot-the-text-template"></a>텍스트 템플릿 문제 해결

**오류 목록**에 템플릿 변환 또는 컴파일 오류가 표시된 경우 또는 출력 파일이 정확히 생성되지 않은 경우 [TextTransform 유틸리티 사용하여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)에 설명된 방법으로 텍스트 템플릿의 문제를 해결할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)
