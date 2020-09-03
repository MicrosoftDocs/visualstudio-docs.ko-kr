---
title: UML 확장에서 단위 테스트 실행 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f634f028dafea3260a69537893513f13cc0ebe83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74292545"
---
# <a name="run-unit-tests-on-uml-extensions"></a>UML 확장에서 단위 테스트 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

변경을 연속으로 수행할 때 코드를 안정적으로 유지하려면 단위 테스트를 작성하여 정기적인 빌드 프로세스의 일부분으로 수행하는 것이 좋습니다. 자세한 내용은 [코드 단위 테스트](../test/unit-test-your-code.md)를 참조하세요. Visual Studio 모델링 확장용 테스트를 설정하려면 몇 가지 주요 정보가 필요합니다. 요약하면 다음과 같습니다.

- [VSIX 확장용 단위 테스트 설정](#Host)

   VS IDE 호스트 어댑터를 사용하여 테스트를 실행합니다. 각 테스트 메서드 앞에 `[HostType("VS IDE")]`를 접두사로 지정합니다. 테스트를 실행할 때 이 호스트 어댑터는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 시작합니다.

- [DTE 및 ModelStore 액세스](#DTE)

   일반적으로는 테스트 초기화 시 모델과 다이어그램을 열고 `IModelStore` 에 액세스해야 합니다.

- [모델 다이어그램 열기](#Opening)

   `EnvDTE.ProjectItem` 에 대해 `IDiagramContext`를 캐스트할 수 있습니다.

- [UI 스레드에서 변경 수행](#UiThread)

   모델 저장소를 변경하는 테스트는 UI 스레드에서 수행해야 합니다. 이 테스트에 `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` 를 사용할 수 있습니다.

- [명령, 제스처 및 기타 MEF 구성 요소 테스트](#MEF)

   MEF 구성 요소를 테스트하려면 가져온 속성을 값에 명시적으로 연결해야 합니다.

  다음 섹션에서 이러한 요소에 대해 보다 자세히 설명합니다.

## <a name="requirements"></a>요구 사항
 [요구 사항](../modeling/extend-uml-models-and-diagrams.md#Requirements)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="setting-up-a-unit-test-for-vsix-extensions"></a><a name="Host"></a> VSIX 확장에 대 한 단위 테스트 설정
 모델링 확장의 메서드는 보통 이미 열려 있는 다이어그램에서 작동합니다. 이 메서드는 **IDiagramContext** , **ILinkedUndoContext**등의 MEF 가져오기를 사용합니다. 테스트를 실행하기 전에 테스트 환경에서 이 컨텍스트를 설정해야 합니다.

#### <a name="to-set-up-a-unit-test-that-executes-in-vsprvs"></a>[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 실행되는 단위 테스트를 설정하려면

1. UML 확장 프로젝트와 단위 테스트 프로젝트를 만듭니다.

    1. **UML 확장 프로젝트.** 일반적으로는 명령 제스처 또는 유효성 검사 프로젝트 템플릿을 사용하여 이 프로젝트를 만듭니다. 예를 들어 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

    2. **단위 테스트 프로젝트.** 자세한 내용은 [코드 단위 테스트](../test/unit-test-your-code.md)를 참조하세요.

2. UML 모델링 프로젝트가 포함된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 만듭니다. 이 솔루션을 테스트 초기 상태로 사용합니다. 이 솔루션은 UML 확장 및 해당 단위 테스트를 작성하는 솔루션과는 다른 별개의 솔루션이어야 합니다. 자세한 내용은 [UML 모델링 프로젝트 및 다이어그램 만들기](../modeling/create-uml-modeling-projects-and-diagrams.md)를 참조 하세요.

3. **UML 확장 프로젝트**에서 .csproj 파일을 텍스트로 편집하고 다음 줄에 `true`가 표시되는지 확인합니다.

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     .csproj 파일을 텍스트로 편집하려면 솔루션 탐색기의 프로젝트 바로 가기 메뉴에서 **프로젝트 언로드** 를 선택합니다. 그런 다음 **….csproj 편집**을 선택합니다. 텍스트를 편집한 후 **프로젝트 다시 로드**를 선택합니다.

4. UML 확장 프로젝트에서 **Properties\AssemblyInfo.cs**에 다음 줄을 추가합니다. 그러면 단위 테스트가 테스트할 메서드에 액세스할 수 있습니다.

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **단위 테스트 프로젝트**에서 다음 어셈블리 참조를 추가합니다.

    - *UML 확장 프로젝트*

    - **EnvDTE.dll**

    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**

    - **Microsoft.VisualStudio.Uml.Interfaces.dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. 초기화 메서드를 포함한 각 테스트 메서드에 `[HostType("VS IDE")]` 특성을 접두사로 지정합니다.

     그러면 Visual Studio의 실험적 인스턴스에서 테스트가 실행됩니다.

## <a name="accessing-dte-and-modelstore"></a><a name="DTE"></a> DTE 및 ModelStore 액세스
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 모델링 프로젝트를 여는 메서드를 작성합니다. 일반적으로는 각 테스트 실행 시 솔루션을 한 번만 엽니다. 메서드를 한 번만 실행하려면 메서드에 `[AssemblyInitialize]` 특성을 접두사로 지정합니다. 또한 각 테스트 메서드에 [HostType("VS IDE")] 특성도 추가해야 합니다.  예를 들면 다음과 같습니다.

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 인스턴스가 <xref:EnvDTE.Project?displayProperty=fullName> 모델링 프로젝트를 나타내는 경우이를 [Imodelingproject](/previous-versions/ee789474(v=vs.140))로 캐스팅할 수 있습니다.

## <a name="opening-a-model-diagram"></a><a name="Opening"></a> 모델 다이어그램 열기
 일반적으로 각 테스트 또는 테스트 클래스는 열려 있는 다이어그램에 대해 수행합니다. 다음 예에서는 이 테스트 클래스의 다른 메서드보다 먼저 이 메서드를 실행하는 `[ClassInitialize]` 특성을 사용합니다. 여기서도 각 테스트 메서드에 [HostType("VS IDE")] 특성을 추가해야 합니다.

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="perform-model-changes-in-the-ui-thread"></a><a name="UiThread"></a> UI 스레드에서 모델 변경 수행
 테스트 또는 테스트 중인 메서드로 인해 모델 저장소가 변경되는 경우에는 사용자 인터페이스 스레드에서 해당 테스트나 메서드를 실행해야 합니다. 그렇지 않으면 `AccessViolationException`이 표시될 수 있습니다. 테스트 메서드의 코드를 호출할 Invoke 호출 내에 다음과 같이 포함하세요.

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="testing-command-gesture-and-other-mef-components"></a><a name="MEF"></a> 명령, 제스처 및 기타 MEF 구성 요소 테스트
 MEF 구성 요소는 `[Import]` 특성을 포함하며 해당 값이 호스트에 의해 설정되는 속성 선언을 사용합니다. 일반적으로 이러한 속성은 IDiagramContext, SVsServiceProvider, ILinkedUndoContext 등입니다. 이러한 속성을 사용하는 메서드를 테스트할 때는 테스트 대상 메서드를 실행하기 전에 해당 값을 설정해야 합니다. 예를 들어 다음 코드와 같은 명령 확장을 작성한 경우

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 가져온 속성을 다음과 같이 설정할 수 있습니다.

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 가져온 속성을 매개 변수로 사용하는 메서드를 테스트하려는 경우에는 속성을 테스트 클래스로 가져온 다음 테스트 인스턴스에 `SatisfyImportsOnce` 를 적용하면 됩니다. 예를 들면 다음과 같습니다.

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 이 예에서는 편의상 각 테스트 메서드의 두 특성을 한 줄에 결합했습니다.

## <a name="access-from-tests-to-private-methods-and-variables"></a>테스트에서 private 메서드 및 변수에 액세스
 테스트 대상 메서드를 실행하기 전이나 실행한 후에 private 메서드를 테스트하거나 private 필드의 상태를 확인하려는 경우가 있습니다. 그러나 테스트는 테스트 중인 클래스에 대한 별도의 어셈블리에 포함되어 있으므로 이와 같은 작업을 수행하기가 어렵습니다. 이러한 경우에는 다음을 포함한 몇 가지 방법을 고려해 볼 수 있습니다.

 공용 및 내부 항목만 사용 하 여 테스트는 공용 (또는 내부) 클래스와 멤버만 사용 하도록 테스트를 작성 합니다. 이 방법이 가장 효과적입니다. 이 경우에는 테스트 중인 어셈블리의 내부 구현을 리팩터링해도 테스트가 계속 작동합니다. 변경 전과 후에 같은 테스트를 적용하면 변경으로 인해 어셈블리 동작이 바뀌지 않도록 할 수 있습니다.

 이렇게 하려면 코드 구조를 바꿔야 할 수 있습니다. 예를 들어 일부 메서드를 다른 클래스로 분리해야 할 수 있습니다.

 이 방식을 면밀하게 고려하면 코드를 보다 쉽게 읽고 변경할 수 있으며 변경을 수행해야 할 때 오류 가능성을 줄일 수 있습니다.

 테스트할 프로젝트의 **Properties\AssemblyInfo.cs** 에 특성을 추가하면 테스트 어셈블리가 내부 항목에 액세스하도록 허용할 수 있습니다.

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 테스트 인터페이스 정의 테스트할 클래스의 public 멤버와 테스트에서 사용할 수 있도록 하려는 전용 멤버에 대 한 추가 속성 및 메서드를 모두 포함 하는 인터페이스를 정의 합니다. 그리고 테스트할 프로젝트에 이 인터페이스를 추가합니다. 예를 들면 다음과 같습니다.

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 테스트할 클래스에 메서드를 추가하여 접근자 메서드를 명시적으로 구현합니다. 이러한 추가 메서드는 별도 파일의 partial 클래스 정의에 작성하여 주 클래스와 분리합니다. 예를 들면 다음과 같습니다.

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 테스트 중인 어셈블리에 다음 특성을 추가하여 테스트 어셈블리가 테스트 인터페이스를 사용하도록 허용합니다.

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 단위 테스트 메서드에서 테스트 인터페이스를 사용합니다. 예를 들면 다음과 같습니다.

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 리플렉션을 사용 하 여 접근자를 정의 합니다 .이는 최소 권장 방법입니다. 이전 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전에서는 각 private 메서드에 대해 접근자 메서드를 자동으로 만드는 유틸리티를 제공했습니다. 이 유틸리티는 편리하긴 하지만 사용하는 경우 단위 테스트가 테스트 중인 애플리케이션의 내부 구조에 밀접하게 연결되는 것으로 확인되었습니다. 그러면 요구 사항이나 아키텍처가 변경될 때 구현과 함께 테스트도 변경해야 하므로 추가 작업을 수행해야 합니다. 또한 구현 디자인의 잘못된 가정이 테스트에도 기본적으로 적용되므로 테스트가 오류를 찾지 못합니다.

## <a name="see-also"></a>관련 항목
 [단위 테스트 분석](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
