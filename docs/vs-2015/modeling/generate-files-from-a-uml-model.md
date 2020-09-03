---
title: UML 모델에서 파일 생성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666141"
---
# <a name="generate-files-from-a-uml-model"></a>UML 모델에서 파일 생성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 모델에서 프로그램 코드, 스키마, 문서, 리소스 및 모든 종류의 기타 아티팩트를 생성할 수 있습니다. UML 모델에서 텍스트 파일을 생성 하는 편리한 방법 중 하나는 [텍스트 템플릿을](../modeling/code-generation-and-t4-text-templates.md)사용 하는 것입니다. 텍스트 템플릿을 사용하면 생성하려는 텍스트 내에 프로그램 코드를 포함할 수 있습니다.

 다음 세 가지 주요 시나리오가 있습니다.

- [메뉴 명령 또는 제스처에서 파일 생성](#Command) UML 모델에서 사용할 수 있는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령을 정의합니다.

- [응용 프로그램에서 파일을 생성](#Application)합니다. UML 모델을 읽고 파일을 생성하는 애플리케이션을 작성합니다.

- [디자인 타임에 생성](#Design) 모델을 사용하여 애플리케이션의 기능 중 일부를 정의하고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션 내에서 코드, 리소스 등을 생성합니다.

  이 항목에서는 [텍스트 생성을 사용 하는 방법](#What)에 대해 설명 합니다. 자세한 내용은 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요.

## <a name="generating-files-from-a-menu-command"></a><a name="Command"></a> 메뉴 명령에서 파일 생성
 UML 메뉴 명령 내에서 전처리 텍스트 템플릿을 사용할 수 있습니다. 텍스트 템플릿의 코드 내에서 또는 별도의 partial 클래스에서 다이어그램에 표시되는 모델을 읽을 수 있습니다.

 이러한 기능에 대한 자세한 내용은 다음 항목을 참조하세요.

- [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [UML 모델 탐색](../modeling/navigate-the-uml-model.md)

  다음 예제에 설명된 접근 방식은 모델 다이어그램 중 하나에서 작업을 시작하는 경우 단일 모델에서 텍스트를 생성하는 데 적합합니다. 별도의 컨텍스트에서 모델을 처리 하려면 [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md) 를 사용 하 여 모델 및 해당 요소에 액세스 하는 것이 좋습니다.

### <a name="example"></a>예
 이 예제를 실행하려면 VSIX([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension) 프로젝트를 만듭니다. 이 예제에서 사용 되는 프로젝트 이름은 `VdmGenerator` 입니다. **Source.extension.vsixmanifest** 파일에서 **콘텐츠 추가** 를 클릭 하 고 형식 필드를 **MEF 구성 요소** 및 현재 프로젝트를 참조 하는 원본 경로로 설정 합니다. 이러한 형식의 프로젝트를 설정 하는 방법에 대 한 자세한 내용은 [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)를 참조 하세요.

 다음 코드를 포함하는 C# 파일을 프로젝트에 추가합니다. 이 클래스는 UML 클래스 다이어그램에 표시되는 메뉴 명령을 정의합니다.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace VdmGenerator
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  public class GenerateVdmFromClasses : ICommandExtension
  {
    [Import] public IDiagramContext DiagramContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      // Initialize the template with the Model Store.
      VdmGen generator = new VdmGen(
             DiagramContext.CurrentDiagram.ModelStore);
      // Generate the text and write it.
      System.IO.File.WriteAllText
        (System.IO.Path.Combine(
            Environment.GetFolderPath(
                Environment.SpecialFolder.Desktop),
            "Generated.txt")
         , generator.TransformText());
    }
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }
    public string Text
    { get { return "Generate VDM"; } }
  }
}
```

 다음 파일은 텍스트 템플릿입니다. 모델의 각 UML 클래스에 대한 텍스트 줄과 각 클래스의 각 특성에 대한 줄을 생성합니다. 모델을 읽는 코드는 `<# ... #>`로 구분되어 텍스트에 포함됩니다.

 이 파일을 만들려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 항목**을 클릭 합니다. **전처리 텍스트 템플릿을**선택 합니다. 이 예의 파일 이름은 **VdmGen.tt**여야 합니다. 파일의 **사용자 지정 도구** 속성은 **Texttemplatingfilepreprocessor**여야 합니다. 전처리 된 텍스트 템플릿에 대 한 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요.

```
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#
   foreach (IClass classElement in store.AllInstances<IClass>())   {
#>
Type <#= classElement.Name #> ::
<#
     foreach (IProperty attribute in classElement.OwnedAttributes)     {
#>
       <#= attribute.Name #> : <#=
           attribute.Type == null ? ""
                                  : attribute.Type.Name #>
<#
     }   }
#>
```

 텍스트 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 일부가 되는 C# partial 클래스를 생성합니다. 별도 파일에서 동일한 클래스의 다른 부분 선언을 추가합니다. 이 코드는 UML 모델 저장소에 액세스할 수 있는 권한을 템플릿에 제공합니다.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
namespace VdmGenerator
{
    public partial class VdmGen
    {
        private IModelStore store;
        public VdmGen(IModelStore s)
        { store = s; }
    }
}
```

 프로젝트를 테스트 하려면 **f5**키를 누릅니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 새 인스턴스가 시작됩니다. 이 인스턴스에서 클래스 다이어그램을 포함하는 UML 모델을 열거나 만듭니다. 다이어그램에 일부 클래스를 추가하고 각 클래스에 일부 특성을 추가합니다. 다이어그램을 마우스 오른쪽 단추로 클릭 한 다음 예제 명령을 클릭 `Generate VDM` 합니다. 이 명령은 파일을 만듭니다 `C:\Generated.txt` . 이 파일을 검사합니다. 파일 내용은 다음 텍스트와 비슷하지만 자체 클래스 및 특성을 나열합니다.

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="generating-files-from-an-application"></a><a name="Application"></a> 응용 프로그램에서 파일 생성
 UML 모델을 읽는 애플리케이션에서 파일을 생성할 수 있습니다. 이러한 목적을 위해 모델 및 해당 요소에 액세스 하는 가장 유연 하 고 강력한 방법은 [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md)입니다.

 기본 API를 사용하여 모델을 로드하고, 이전 섹션과 동일한 기술을 사용하여 텍스트 템플릿에 모델을 전달할 수도 있습니다. 모델을 로드 하는 방법에 대 한 자세한 내용은 [프로그램 코드에서 UML 모델 읽기](../modeling/read-a-uml-model-in-program-code.md)를 참조 하세요.

## <a name="generating-files-at-design-time"></a><a name="Design"></a> 디자인 타임에 파일 생성
 프로젝트에 UML을 코드로 해석하는 표준 방법이 있는 경우 UML 모델에서 프로젝트 내의 코드를 생성할 수 있게 해주는 텍스트 템플릿을 만들 수 있습니다. 일반적으로 UML 모델 프로젝트 및 애플리케이션 코드에 대한 하나 이상의 프로젝트를 포함하는 솔루션이 있습니다. 각 코드 프로젝트는 모델의 내용에 따라 프로그램 코드, 리소스 및 구성 파일을 생성하는 여러 템플릿을 포함할 수 있습니다. 개발자는 솔루션 탐색기 도구 모음에서 **모든 템플릿 변환** 을 클릭 하 여 모든 템플릿을 실행할 수 있습니다. 프로그램 코드는 일반적으로 수동으로 작성된 파트를 쉽게 통합할 수 있도록 partial 클래스 형식으로 생성됩니다.

 모든 팀 멤버가 동일한 방식으로 모델에서 코드를 생성하는 프로젝트를 만들 수 있도록 이러한 종류의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 템플릿 형식으로 배포할 수 있습니다. 일반적으로 템플릿은 생성 코드의 사전 조건이 충족되었는지 확인하기 위해 모델에 대한 유효성 검사 제약 조건을 포함하는 확장 패키지의 일부입니다.

### <a name="outline-procedure-for-generating-files"></a>파일 생성 절차 개요

- 프로젝트에 템플릿을 추가 하려면 새 파일 추가 대화 상자에서 **텍스트 템플릿** 을 선택 합니다. 대부분의 프로젝트 형식에 템플릿을 추가할 수 있지만 모델링 프로젝트에는 추가할 수 없습니다.

- 템플릿 파일의 사용자 지정 도구 속성은 **Texttemplatingfilegenerator**여야 하 고 파일 이름 확장명은 .tt 여야 합니다.

- 템플릿에는 최소한 다음과 같은 출력 지시문이 있어야 합니다.

     `<#@ output extension=".cs" #>`

     프로젝트의 언어에 따라 확장 필드를 설정합니다.

- 템플릿의 생성 코드가 모델에 액세스할 수 있게 하려면 UML 모델을 읽는 데 필요한 어셈블리에 대해 `<#@ assembly #>` 지시문을 작성합니다. `ModelingProject.LoadReadOnly()`를 사용하여 모델을 엽니다. 자세한 내용은 [프로그램 코드에서 UML 모델 읽기](../modeling/read-a-uml-model-in-program-code.md)를 참조 하세요.

- 템플릿을 저장 하 고 솔루션 탐색기 도구 모음에서 **모든 템플릿 변환** 을 클릭 하면 템플릿이 실행 됩니다.

- 이러한 형식의 템플릿에 대 한 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)을 참조 하세요.

- 일반적인 프로젝트에는 동일한 모델에서 서로 다른 파일을 생성하는 여러 템플릿이 있습니다. 모든 템플릿의 첫 번째 부분은 동일합니다. 이러한 중복을 줄이려면 공통 부분을 별도 텍스트 파일로 이동한 다음 각 템플릿에 `<#@include file="common.txt"#>` 지시문을 사용하여 호출합니다.

- 텍스트 생성 프로세스에 매개 변수를 제공할 수 있게 해주는 특수화된 지시문 프로세서를 정의할 수도 있습니다. 자세한 내용은 [T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)을 참조 하세요.

### <a name="example"></a>예
 이 예제에서는 소스 모델의 각 UML 클래스에 대해 C# 클래스를 생성합니다.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>이 예제에 대해 Visual Studio 솔루션을 설정하려면

1. 새 솔루션의 모델링 프로젝트에서 UML 클래스 다이어그램을 만듭니다.

   1. **아키텍처** 메뉴에서 **새 다이어그램**을 클릭 합니다.

   2. **UML 클래스 다이어그램**을 선택 합니다.

   3. 프롬프트에 따라 새 솔루션과 모델링 프로젝트를 만듭니다.

   4. 도구 상자에서 UML 클래스 도구를 끌어 다이어그램에 일부 클래스를 추가합니다.

   5. 파일을 저장합니다.

2. 동일한 솔루션에서 C# 또는 Visual Basic 프로젝트를 만듭니다.

   - 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 프로젝트**를 클릭 합니다. **설치 된 템플릿**에서 **Visual Basic** 또는 **Visual c #을** 클릭 한 다음 **콘솔 응용 프로그램과**같은 프로젝트 형식을 선택 합니다.

3. C# 또는 Visual Basic 프로젝트에 일반 텍스트 파일을 추가합니다. 이 파일에는 여러 텍스트 템플릿을 작성하려는 경우 공유되는 코드가 포함됩니다.

   - 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 항목**을 클릭합니다. **텍스트 파일**을 선택 합니다.

     다음 섹션에 표시된 텍스트를 삽입합니다.

4. C# 또는 Visual Basic 프로젝트에 텍스트 템플릿 파일을 추가합니다.

   - 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 항목**을 클릭합니다. **텍스트 템플릿**을 선택 합니다.

     텍스트 템플릿 파일에 다음 코드를 삽입합니다.

5. 텍스트 템플릿 파일을 저장합니다.

6. 보조 파일의 코드를 검사합니다. 모델의 각 UML 클래스에 대한 클래스를 포함해야 합니다.

   1. Visual Basic 프로젝트의 솔루션 탐색기 도구 모음에서 **모든 파일 표시** 를 클릭 합니다.

   2. 솔루션 탐색기에서 템플릿 파일 노드를 확장합니다.

#### <a name="content-of-the-shared-text-file"></a>공유 텍스트 파일의 내용
 이 예제에서 파일 이름은 SharedTemplateCode.txt이고 텍스트 템플릿과 동일한 폴더에 있습니다.

```
<# /* Common material for inclusion in my model templates */ #>
<# /* hostspecific allows access to the Visual Studio API */ #>
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>
<#+  // Note this is a Class Feature Block
///<summary>
/// Text templates are run in a common AppDomain, so
/// we can cache the model store that we find.
///</summary>
private IModelStore StoreCache
{
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }
}
private bool CacheIsOld()
{
    DateTime? dt = AppDomain.CurrentDomain
           .GetData("latestAccessTime") as DateTime?;
    DateTime t = dt.HasValue ? dt.Value : new DateTime();
    DateTime now = DateTime.Now;
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);
    return now.Subtract(t).Seconds > 3;
}

///<summary>
/// Find the UML modeling project in this solution,
/// and load the model.
///</summary>
private IModelStore ModelStore
{
  get
  {
    // Avoid loading the model for every template:
    if (StoreCache == null || CacheIsOld())
    {
      // Use Visual Studio API to find modeling project:
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
      EnvDTE.Project project = null;
      foreach (EnvDTE.Project p in dte.Solution.Projects)
      {
        if (p.FullName.EndsWith(".modelproj"))
        {
          project = p;
          break;
        }
      }
      if (project == null) return null;

      // Load UML model into this AppDomain
      // and access model store:
      IModelingProjectReader reader =
           ModelingProject.LoadReadOnly(project.FullName);
      StoreCache = reader.Store;
    }
    return StoreCache;
  }
}
#>
```

#### <a name="content-of-the-text-template-file"></a>텍스트 템플릿 파일의 내용
 다음 텍스트는 **.tt** 파일에 배치 됩니다. 이 예제에서는 모델의 UML 클래스에서 C# 파일의 클래스를 생성합니다. 그러나 임의 형식의 파일을 생성할 수 있습니다. 생성된 파일의 언어는 텍스트 템플릿 코드가 작성된 언어와 관련이 없습니다.

```
<#@include file="SharedTemplateCode.txt"#>
<#@ output extension=".cs" #>
namespace Test{
<#
      foreach (IClass c in ModelStore.AllInstances<IClass>())
      {
#>
   public partial class <#=c.Name#>
   {   }
<#
      }
#>
}
```

## <a name="how-to-use-text-generation"></a><a name="What"></a> 텍스트 생성을 사용 하는 방법
 모델링의 진정한 가치는 모델을 사용하여 요구 사항 또는 아키텍처 수준에서 디자인할 때 나타납니다. 텍스트 템플릿을 사용하여 전반적인 아이디어를 코드로 변환하는 작업의 일부를 수행할 수 있습니다. 대부분의 경우 이로 인해 UML 모델의 요소와 프로그램 코드의 클래스 또는 다른 파트 간에 일 대 일 대응이 발생하지는 않습니다.

 또한 변환은 문제 도메인에 따라 달라집니다. 모델과 코드 간의 범용 매핑은 없습니다.

 모델에서 코드를 생성하는 몇 가지 예는 다음과 같습니다.

- **제품 라인**. Fabrikam, i n c .는 공항 수하물 처리 시스템을 빌드하고 설치 합니다. 대부분의 소프트웨어는 설치마다 매우 유사하지만, 설치된 수하물 처리 기계 및 이러한 파트가 컨베이어 벨트에 의해 상호 연결된 방식에 따라 소프트웨어 구성이 달라집니다. 계약을 시작할 때 Fabrikam 분석가는 공항 경영진과 요구 사항을 논의하고 UML 동작 다이어그램을 사용하여 하드웨어 계획을 캡처합니다. 개발 팀은 이 모델에서 구성 파일, 프로그램 코드, 계획 및 사용자 문서를 생성합니다. 코드를 수동으로 추가 및 조정하여 작업을 완료합니다. 각 작업에서 축적된 경험을 통해 생성된 자료의 범위를 확장합니다.

- **패턴**. Contoso, Ltd의 개발자는 자주 웹 사이트를 빌드하고 UML 클래스 다이어그램을 사용하여 탐색 체계를 디자인합니다. 각 웹 페이지는 클래스로 표현되고 연결은 탐색 링크를 나타냅니다. 개발자는 모델에서 웹 사이트의 코드를 대부분 생성합니다. 각 웹 페이지는 여러 클래스 및 리소스 파일 항목에 해당합니다.  이 방법은 각 페이지의 구성이 단일 패턴을 준수하므로 직접 작성한 코드보다 안정적이고 유연하다는 이점이 있습니다. 패턴은 생성 템플릿에 있고 모델은 가변 측면을 캡처하는 데 사용됩니다.

- **스키마**. Humongous Insurance는 전 세계에 수천 대의 시스템이 있습니다. 이러한 시스템은 서로 다른 데이터베이스, 언어 및 인터페이스를 사용합니다. 중앙 아키텍처 팀은 내부적으로 비즈니스 개념 및 프로세스의 모델을 게시합니다. 로컬 팀은 이러한 모델에서 데이터베이스 파트를 생성하고 스키마, 프로그램 코드의 선언 등을 교환합니다. 모델의 그래픽 표시는 팀이 제안을 논의하는 데 도움이 됩니다. 팀은 다양한 비즈니스 영역에 적용되는 모델의 하위 집합을 표시하는 여러 다이어그램을 만듭니다. 또한 색을 사용하여 변경될 수 있는 영역을 강조 표시합니다.

## <a name="important-techniques-for-generating-artifacts"></a>아티팩트를 생성하기 위한 중요한 기술
 앞의 예제에서 모델은 다양한 비즈니스 종속 용도에 사용되며, 클래스 및 동작과 같은 모델링 요소의 해석이 애플리케이션마다 달라집니다. 다음 기술은 모델에서 아티팩트를 생성하는 경우에 유용합니다.

- **프로필**. 한 비즈니스 영역 내에서도 요소 형식의 해석이 달라질 수 있습니다. 예를 들어 웹 사이트 다이어그램에서 일부 클래스는 웹 페이지를 나타내고 다른 클래스는 콘텐츠 블록을 나타낼 수 있습니다. 사용자가 이러한 차이를 쉽게 기록할 수 있도록 스테레오타입을 정의합니다. 스테레오타입을 통해 해당 종류의 요소에 적용되는 추가 속성을 연결할 수도 있습니다. 스테레오타입은 프로필 내에 패키징됩니다. 자세한 내용은 [프로필을 정의 하 여 UML 확장](../modeling/define-a-profile-to-extend-uml.md)을 참조 하세요.

     템플릿 코드에서 개체에 정의된 스테레오타입에 쉽게 액세스할 수 있습니다. 예를 들면 다음과 같습니다.

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **제약 된 모델**. 만들 수 있는 모든 모델이 모든 용도에 유효한 것은 아닙니다. 예를 들어 Fabrikam의 공항 수하물 모델에서 나가는 컨베이어가 없는 체크 인 데스크를 포함하면 잘못된 것입니다. 사용자가 이러한 제약 조건을 준수하는 데 도움이 되는 유효성 검사 함수를 정의할 수 있습니다. 자세한 내용은 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)를 참조 하세요.

- **수동 변경 내용을 유지**합니다. 솔루션 파일 중 일부만 모델에서 생성할 수 있습니다. 대부분의 경우 생성된 콘텐츠를 직접 추가하거나 조정할 수 있어야 합니다. 그러나 템플릿 변환을 다시 실행할 때 이러한 수동 변경 내용이 유지되도록 해야 합니다.

     템플릿이 언어에서 코드를 생성 하는 위치에서 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 개발자가 메서드 및 코드를 추가할 수 있도록 partial 클래스를 생성 해야 합니다. 메서드를 포함하는 추상 기본 클래스 및 생성자만 포함하는 상속 클래스의 쌍으로 각 클래스를 생성하는 것도 유용합니다. 이렇게 하면 개발자가 메서드를 재정의할 수 있습니다. 초기화를 재정의할 수 있도록 생성자가 아니라 별도 메서드에서 수행됩니다.

     템플릿이 XML 및 기타 형식의 출력을 생성하는 경우 생성된 콘텐츠와 별도로 수동 콘텐츠를 유지하는 것이 더 어려울 수 있습니다. 한 가지 방법은 두 파일을 결합하는 작업을 빌드 프로세스에 만드는 것입니다. 다른 방법은 개발자가 생성 템플릿의 로컬 복사본을 조정하는 것입니다.

- **코드를 별도의 어셈블리로 이동**합니다. 템플릿에서 큰 코드 본문을 작성하지 않는 것이 좋습니다. 생성된 콘텐츠를 계산과 별도로 유지하는 것이 좋으며, 텍스트 템플릿은 코드 편집 작업에 대해 완전히 지원되지 않습니다.

     대신, 텍스트를 생성하기 위해 상당히 많은 계산을 수행해야 하는 경우 별도 어셈블리에 해당 함수를 빌드하고 템플릿에서 해당 메서드를 호출합니다.
