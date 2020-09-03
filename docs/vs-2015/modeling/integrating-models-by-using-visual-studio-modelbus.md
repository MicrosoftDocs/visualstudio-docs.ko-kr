---
title: Modelbus를 사용 하 여 모델 통합 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 77b29fe82b3203228b194d34d82444c4b62415fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851498"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Visual Studio Modelbus를 사용하여 모델 통합
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus는 모델과 다른 도구에서 모델로 링크를 만드는 방법을 제공 합니다. 예를 들어 DSL(Domain-Specific Language) 모델과 UML 모델을 연결할 수 있으며 통합 DSL 집합을 만들 수 있습니다.

 ModelBus에서는 모델 또는 모델 내의 특정 요소에 대한 고유 참조를 만들 수 있습니다. 이 참조는 다른 모델의 요소 등 모델 외부에 저장할 수 있습니다. 나중에 도구에서 요소에 액세스해야 하면 ModelBus 인프라에서 적절한 모델을 로드하고 요소를 반환합니다. 원하는 경우 사용자에게 모델을 표시할 수 있습니다. 이전 위치에서 파일에 액세스할 수 없으면 ModelBus에서 사용자에게 파일을 찾으라는 메시지를 표시합니다. 사용자가 파일을 찾으면 해당 파일에 대한 모든 참조가 수정됩니다.

> [!NOTE]
> ModelBus의 최신 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 구현에서 연결되는 모델은 같은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에 있는 항목이어야 합니다.

 추가 정보와 샘플 코드는 다음 항목을 참조하세요.

- [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Visual Studio 용 모델링 SDK](https://www.microsoft.com/download/details.aspx?id=48148)

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> DSL에 대 한 액세스 제공
 모델이나 모델의 요소에 대한 ModelBus 참조를 만들려면 DSL에 대해 ModelBusAdapter를 정의해야 합니다. 가장 쉽게 정의하는 방법은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus 확장을 사용하는 것입니다. 이 확장은 DSL 디자이너에 명령을 추가합니다.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> 모델 버스에 DSL 정의를 노출 하려면

1. Visual Studio ModelBus 확장을 이미 설치하지 않은 경우 다운로드하여 설치합니다. 자세한 내용은 [시각화 및 모델링 SDK](https://www.visualstudio.com/)를 참조 하세요.

2. DSL 정의 파일을 엽니다. 디자인 화면을 마우스 오른쪽 단추로 클릭 한 다음 **Modelbus 사용**을 클릭 합니다.

3. 대화 상자에서 **ModelBus에이 DSL을 노출**하려고 합니다 .를 선택 합니다. 이 DSL을 모델에 표시하는 동시에 다른 DSL에 대한 참조도 사용하려는 경우 두 옵션을 모두 선택하면 됩니다.

4. **확인**을 클릭합니다. "ModelBusAdapter"라는 새 프로젝트가 DSL 솔루션에 추가됩니다.

5. 텍스트 템플릿에서 DSL에 액세스하려면 새 프로젝트에서 AdapterManager.tt를 수정해야 합니다. 명령 및 이벤트 처리기와 같은 기타 코드에서 DSL에 액세스하려면 이 단계를 생략합니다. 자세한 내용은 [텍스트 템플릿에서 Visual Studio ModelBus 사용](../modeling/using-visual-studio-modelbus-in-a-text-template.md)을 참조 하세요.

   1. AdapterManagerBase의 기본 클래스를 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))로 변경 합니다.

   2. 파일 끝부분의 AdapterManager 클래스 앞에 다음 추가 특성을 삽입합니다.

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. ModelBusAdapter 프로젝트의 참조에서 **VisualStudio**를 추가 합니다.

      텍스트 템플릿과 기타 코드에서 모두 DSL에 액세스하려면 어댑터 두 개(수정된 어댑터와 수정되지 않은 어댑터)가 필요합니다.

6. **모든 템플릿 변환**을 클릭 합니다.

7. 솔루션을 다시 빌드합니다.

   이제 ModelBus에서 이 DSL의 인스턴스를 열 수 있습니다.

   `ModelBusAdapters\bin\*` 폴더에는 `Dsl` 프로젝트와 `ModelBusAdapters` 프로젝트에서 작성한 어셈블리가 포함됩니다. 다른 DSL에서 이 DSL을 참조하려면 이러한 어셈블리를 가져와야 합니다.

### <a name="making-sure-that-elements-can-be-referenced"></a>요소를 참조할 수 있는지 확인
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus 어댑터는 기본적으로 요소의 guid를 사용 하 여 식별 합니다. 따라서 이러한 식별자를 모델 파일에 영구적으로 저장해야 합니다.

##### <a name="to-ensure-that-element-ids-are-persisted"></a>요소 ID가 영구적으로 저장되었는지 확인하려면

1. DslDefinition.dsl을 엽니다.

2. DSL 탐색기에서 **Xml 직렬화 동작**을 확장 한 다음 **클래스 데이터**를 확장 합니다.

3. ModelBus 참조를 만들 각 클래스에 대해 다음 작업을 수행합니다.

    클래스 노드를 클릭 하 고 속성 창에서 **Serialize Id** 가로 설정 되어 있는지 확인 `true` 합니다.

   또는 GUID가 아닌 요소 이름을 사용하여 요소를 식별하려는 경우에는 생성된 어댑터 부분을 재정의할 수 있습니다. 어댑터 클래스에서 다음 메서드를 재정의합니다.

- 사용하려는 식별자를 반환하도록 `GetElementId`를 재정의합니다. 참조를 만들 때 이 메서드를 호출합니다.

- ModelBus 참조에서 올바른 요소를 찾도록 `ResolveElementReference`를 재정의합니다.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> 다른 DSL에서 DSL 액세스
 DSL의 도메인 속성에 ModelBus 참조를 저장할 수 있으며 해당 참조를 사용하는 사용자 지정 코드를 작성할 수 있습니다. 사용자가 모델 파일과 파일 내의 요소를 선택하여 ModelBus 참조를 만들도록 할 수도 있습니다.

 DSL에서 다른 DSL에 대 한 참조를 사용할 수 있도록 하려면 먼저 모델 버스 참조의 *소비자* 로 설정 해야 합니다.

#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>DSL이 표시된 DSL에 대한 참조를 사용하도록 설정하려면

1. DSL 정의 다이어그램에서 다이어그램의 주 부분을 마우스 오른쪽 단추로 클릭 한 다음 **Modelbus 사용**을 클릭 합니다.

2. 대화 상자에서 **이 모델을 사용 하 여 모델 버스 참조를 사용 하도록 설정**합니다 .를 선택 합니다.

3. 참조를 사용하는 DSL의 DSL 프로젝트에서 프로젝트 참조에 다음 어셈블리를 추가합니다. 노출 된 DSL의 ModelBusAdapter\bin * 디렉터리에서 이러한 어셈블리 (.dll 파일)를 찾을 수 있습니다 \\ .

    - 표시 되는 DSL 어셈블리 (예: **Fabrikam.FamilyTree.Dsl.dll**

    - 노출 된 모델 버스 어댑터 어셈블리 (예: **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. 참조를 사용하는 DSL 프로젝트의 프로젝트 참조에 다음 .NET 어셈블리를 추가합니다.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>ModelBus 참조를 도메인 속성에 저장하려면

1. 참조를 사용하는 DSL의 DSL 정의에서 도메인 클래스에 도메인 속성을 추가하고 해당 이름을 설정합니다.

2. 속성 창에서 도메인 속성을 선택 하 고 **유형** 을로 설정 `ModelBusReference` 합니다.

   이 단계에서 프로그램 코드가 속성 값을 설정할 수 있지만 해당 값은 속성 창에서 읽기 전용입니다.

   사용자가 특수한 ModelBus 참조 편집기를 사용하여 속성을 설정하도록 허용할 수 있습니다. 이 편집기 또는 선택기에는 두 가지 버전이 있습니다 *.* 하나는 사용자가 모델 파일을 선택할 수 있게 하 고 다른 하나는 사용자가 모델 파일 및 모델 내의 요소를 선택할 수 있도록 합니다.

#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>사용자가 도메인 속성에서 ModelBus 참조를 설정하도록 허용하려면

1. 도메인 속성을 마우스 오른쪽 단추로 클릭 한 다음 **ModelBusReference 특정 속성 편집**을 클릭 합니다. 그러면 *모델 버스 선택*입니다.

2. 모델 또는 모델 내의 요소에 대 한 적절 한 **종류의 ModelBusReference**를 선택 합니다.

3. 파일 대화 상자의 필터 문자열에 `Family Tree files |*.ftree` 등의 문자열을 입력합니다. 표시된 DSL의 파일 확장명을 바꿉니다.

4. 모델의 요소를 참조하려는 경우 Company.FamilyTree.Person과 같이 사용자가 선택할 수 있는 형식의 목록을 추가할 수 있습니다.

5. **확인**을 클릭 한 다음 솔루션 탐색기 도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다.

    > [!WARNING]
    > 올바른 모델이나 엔터티를 선택하지 않은 경우 확인 단추가 사용 가능한 것처럼 표시될 수 있지만 클릭해도 아무런 변화가 없습니다.

6. Company.FamilyTree.Person과 같은 대상 형식 목록을 지정한 경우에는 Company.FamilyTree.Dsl.dll과 같은 대상 DSL의 DLL을 참조하는 어셈블리 참조를 DSL 프로젝트에 추가해야 합니다.

#### <a name="to-test-a-model-bus-reference"></a>ModelBus 참조를 테스트하려면

1. 표시되는 SDL과 참조를 사용하는 DSL을 모두 작성합니다.

2. F5 키나 Ctrl+F5를 눌러 실험 모드에서 DSL 중 하나를 실행합니다.

3. 디버깅 프로젝트의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험 인스턴스에서 각 DSL의 인스턴스인 파일을 추가합니다.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus는 동일한 솔루션에 있는 항목 모델에 대 한 참조만 확인할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 예를 들어 파일 시스템의 다른 부분에 있는 모델 파일에 대한 참조를 만들 수는 없습니다.

4. 표시되는 DSL의 인스턴스에서 요소와 링크를 몇 개 만들고 해당 DSL을 저장합니다.

5. 참조를 사용하는 DSL의 인스턴스를 열고 ModelBus 참조 속성이 포함된 모델 요소를 선택합니다.

6. 속성 창에서 ModelBus 참조 속성을 두 번 클릭합니다. 선택 대화 상자가 열립니다.

7. **찾아보기** 를 클릭 하 고 노출 된 DSL의 인스턴스를 선택 합니다.

     요소 관련 ModelBus 참조 종류를 지정한 경우에는 선택을 통해 모델의 항목을 선택할 수도 있습니다.

## <a name="creating-references-in-program-code"></a>프로그램 코드에서 참조 만들기
 모델 또는 모델 내 요소에 대한 참조를 저장하려면 `ModelBusReference`를 만듭니다. `ModelBusReference`에는 모델 참조와 요소 참조의 두 가지 종류가 있습니다.

 모델 참조를 만들려면 모델이 인스턴스인 DSL의 AdapterManager와 모델의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 항목 또는 파일 이름이 필요합니다.

 요소 참조를 만들려면 모델 파일의 어댑터와 참조할 요소가 필요합니다.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus에서는 같은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션의 항목에 대한 참조만 만들 수 있습니다.

### <a name="import-the-exposed-dsl-assemblies"></a>표시되는 DSL 어셈블리 가져오기
 참조를 사용하는 프로젝트에서 DSL에 대한 프로젝트 참조 및 표시되는 DSL의 ModelBusAdapter 어셈블리를 추가합니다.

 MusicLibrary DSL의 요소에 ModelBus 참조를 저장하려는 경우를 예로 들어 보겠습니다. 여기서 ModelBus 참조는 FamilyTree DSL의 요소를 참조합니다. 이 경우 MusicLibrary 솔루션 `Dsl` 프로젝트의 참조 노드에 다음 어셈블리에 대한 참조를 추가합니다.

- Fabrikam.FamilyTree.Dsl.dll - 표시되는 DSL입니다.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - 표시되는 DSL의 ModelBus 어댑터입니다.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  이러한 어셈블리는 표시되는 DSL `ModelBusAdapters` 프로젝트의 `bin\*`에서 확인할 수 있습니다.

  일반적으로는 참조를 만들 코드 파일에서 다음 네임스페이스를 가져와야 합니다.

```
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>모델에 대한 참조를 만들려면
 모델 참조를 만들려면 표시되는 DSL의 AdapterManager에 액세스한 다음 AdapterManager를 사용하여 모델에 대한 참조를 만듭니다. 파일 경로나 `EnvDTE.ProjectItem`을 지정할 수 있습니다.

 AdapterManager에서는 모델의 개별 요소에 대한 액세스 권한을 제공하는 어댑터를 가져올 수 있습니다.

> [!NOTE]
> 어댑터는 사용한 후 삭제해야 합니다. 어댑터를 삭제하는 가장 편리한 방법은 `using` 문을 사용하는 것입니다. 다음은 이에 대한 예입니다.

```
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter

```

 나중에 `modelReference`를 사용하려는 경우 외부 형식이 `ModelBusReference`인 도메인 속성에 저장하면 됩니다.

```
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

 사용자가 이 도메인 속성을 편집하도록 허용하려면 편집기 특성의 매개 변수로 `ModelReferenceEditor`를 사용합니다. 자세한 내용은 [사용자가 참조를 편집 하도록 허용](#editRef)을 참조 하세요.

### <a name="to-create-a-reference-to-an-element"></a>요소에 대한 참조를 만들려면
 모델용으로 만든 어댑터를 사용하여 참조를 만들고 확인할 수 있습니다.

```
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

 나중에 `elementReference`를 사용하려는 경우 외부 형식이 `ModelBusReference`인 도메인 속성에 저장하면 됩니다. 사용자가 해당 참조를 편집하도록 허용하려면 편집기 특성의 매개 변수로 `ModelElementReferenceEditor`를 사용합니다. 자세한 내용은 [사용자가 참조를 편집 하도록 허용](#editRef)을 참조 하세요.

### <a name="resolving-references"></a>참조 확인
 MBR(`ModelBusReference`)이 있는 경우 MBR이 참조하는 모델이나 모델 요소를 가져올 수 있습니다. 요소가 다이어그램이나 다른 뷰에 표시되어 있으면 해당 뷰를 열고 요소를 선택할 수 있습니다.

 MBR에서 어댑터를 만들 수 있으며 해당 어댑터에서 모델의 루트를 가져올 수 있습니다. 또한 모델 내의 특정 요소를 참조하는 MBR을 확인할 수도 있습니다.

```
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>텍스트 템플릿에서 ModelBus 참조를 확인하려면

1. 액세스하려는 DSL에는 텍스트 템플릿이 액세스하도록 구성된 ModelBus 어댑터가 있어야 합니다. 자세한 내용은 [DSL에 대 한 액세스 제공](#provide)을 참조 하세요.

2. 일반적으로는 소스 DSL에 저장된 MBR(ModelBus 참조)을 사용하여 대상 DSL에 액세스합니다. 따라서 템플릿에는 소스 DSL의 지시문과 MBR을 해석하는 코드가 포함됩니다. 텍스트 템플릿에 대 한 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>

   ```

   자세한 내용 및 연습에 대해서는 [텍스트 템플릿에서 Visual Studio ModelBus 사용](../modeling/using-visual-studio-modelbus-in-a-text-template.md) 을 참조 하세요.

## <a name="serializing-a-modelbusreference"></a>ModelBusReference serialize
 문자열 형식으로 MBR(`ModelBusReference`)을 저장하려는 경우 MBR을 serialize하면 됩니다.

```
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

 이러한 방식으로 serialize한 MBR은 컨텍스트의 영향을 받지 않습니다. 단순 파일 기반 ModelBus 어댑터를 사용하는 경우 MBR에는 절대 파일 경로가 포함됩니다. 인스턴스 모델 파일을 이동하지 않으려는 경우에는 이 경로만 사용해도 충분합니다. 그러나 모델 파일은 대개 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 항목입니다. 사용자는 전체 프로젝트를 파일 시스템의 다른 부분으로 이동할 수 있어야 합니다. 또한 프로젝트의 소스를 제어하고 다른 컴퓨터에서 프로젝트를 열 수 있어야 합니다. 그러므로 파일이 포함된 프로젝트의 위치를 기준으로 하여 경로 이름을 serialize해야 합니다.

### <a name="serializing-relative-to-a-specified-file-path"></a>지정된 파일 경로를 기준으로 serialize
 `ModelBusReference`는 참조를 serialize할 기준이 되는 파일 경로 등의 정보를 저장할 수 있는 사전인 `ReferenceContext`를 포함합니다.

 특정 경로를 기준으로 serialize하려면 다음 코드를 사용합니다.

```
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

 문자열에서 참조를 검색하려면 다음 코드를 사용합니다.

```
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>다른 어댑터를 통해 만든 ModelBusReference
 어댑터를 직접 만들려는 경우에는 다음 정보가 유용합니다.

 MBR(`ModelBusReference`)은 두 부분으로 구성되는데, 그 중 하나는 ModelBus를 통해 역직렬화되는 MBR 헤더이고 다른 하나는 특정 어댑터 관리자를 통해 처리되는 어댑터 관련 부분입니다. 따라서 어댑터 serialization 형식을 직접 지정할 수 있습니다. 예를 들어 파일이 아닌 데이터베이스를 참조하거나 어댑터 참조에 추가 정보를 저장할 수 있습니다. 고유한 어댑터를 사용하는 경우 `ReferenceContext`에 추가 정보가 저장될 수 있습니다.

 MBR을 역직렬화할 때는 ReferenceContext를 제공해야 합니다. 이 ReferenceContext는 MBR 개체에 저장됩니다. MBR을 serialize할 때 어댑터는 저장된 ReferenceContext를 사용하여 문자열을 생성합니다. 역직렬화된 문자열에 ReferenceContext의 모든 정보가 포함되는 것은 아닙니다. 예를 들어 단순 파일 기반 어댑터에서 ReferenceContext에는 포함되는 루트 파일 경로가 serialize된 MBR 문자열에는 저장되지 않습니다.

 MBR은 두 단계로 역직렬화됩니다.

- `ModelBusReferencePropertySerializer` 는 MBR 헤더를 처리 하는 표준 serializer입니다. 이 항목은 `SerializationContext` 키를 사용하여 `ReferenceContext`에 저장되는 표준 DSL `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` 속성 모음을 사용합니다. 특히 `SerializationContext`는 `ModelBus` 인스턴스를 포함해야 합니다.

- ModelBus 어댑터는 MBR의 어댑터 관련 부분을 처리하며 MBR의 ReferenceContext에 저장된 추가 정보를 사용할 수 있습니다. 단순 파일 기반 어댑터는 및 키를 사용 하 여 루트 파일 경로를 유지 합니다 `FilePathLoadContextKey` `FilePathSaveContextKey` .

     모델 파일의 어댑터 참조는 사용할 때만 역직렬화됩니다.

## <a name="to-create-a-model"></a>모델을 만들려면

### <a name="creating-opening-and-editing-a-model"></a>모델 만들기, 열기 및 편집
 다음 코드 조각은 VMSDK 웹 사이트의 상태 시스템 샘플에서 가져온 것으로, ModelBusReference를 사용해 모델을 만들고 여는 방법과 모델에 연결된 다이어그램을 가져오는 방법을 보여줍니다.

 이 샘플에서 대상 DSL의 이름은 StateMachine입니다. 이 이름에서 모델 클래스의 이름과 ModelBusAdapter의 이름 등 여러 이름이 파생됩니다.

```
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>참조 유효성 검사
 BrokenReferenceDetector는 ModelBusReference를 포함할 수 있는 저장소 내의 모든 도메인 속성을 테스트하며, 작업이 발견되는 위치를 제공하는 작업을 호출합니다. 이러한 방식은 특히 유효성 검사 메서드에 유용합니다. 다음 유효성 검사 메서드는 모델 저장 시도 시 저장소를 테스트하고 손상된 참조를 오류 창에서 보고합니다.

```
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>ModelBus 확장이 수행하는 작업
 아래 정보는 반드시 확인해야 하는 것은 아니지만 ModelBus를 광범위하게 사용하는 경우 유용할 수 있습니다.

 ModelBus 확장을 사용하면 DSL 솔루션에서 다음과 같은 변경을 수행할 수 있습니다.

 DSL 정의 다이어그램을 마우스 오른쪽 단추로 클릭 하 고 **Modelbus 사용**을 클릭 한 다음 **이 DSL을 사용 하도록 설정**을 선택 하 여 Modelbus를 사용 합니다.

- DSL 프로젝트에서 참조가에 추가 됩니다 **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- DSL 정의에서 외부 형식 참조(`Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`)가 추가됩니다.

   **DSL 탐색기**의 **도메인 유형**아래에서 참조를 볼 수 있습니다. 외부 형식 참조를 수동으로 추가하려면 루트 노드를 마우스 오른쪽 단추로 클릭합니다.

- 새 템플릿 파일 ( **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**)이 추가 됩니다.

  도메인 속성의 유형을 ModelBusReference로 설정 하 고 속성을 마우스 오른쪽 단추로 클릭 한 다음 **modelbusreference 특정 속성 사용**을 클릭 합니다.

- 여러 CLR 특성이 도메인 속성에 추가됩니다. 속성 창의 사용자 지정 특성 필드에서 해당 특성을 확인할 수 있습니다. **Dsl\GeneratedCode\DomainClasses.cs**에서 속성 선언에 대 한 특성을 볼 수 있습니다.

  ```
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

  DSL 정의 다이어그램을 마우스 오른쪽 단추로 클릭 하 고 **ModelBus 사용**을 클릭 한 다음 **이 DSL을 ModelBus에**표시를 선택 합니다.

- 새 프로젝트(`ModelBusAdapter`)가 솔루션에 추가됩니다.

- `ModelBusAdapter`에 대한 참조가 `DslPackage` 프로젝트에 추가됩니다. `ModelBusAdapter` 에는 프로젝트에 대 한 참조가 있습니다 `Dsl` .

- **DslPackage\source.extention.tt**에서 `|ModelBusAdapter|` 는 MEF 구성 요소로 추가 됩니다.

## <a name="see-also"></a>관련 항목
 [방법: 프로그램 코드에서 파일을 사용 하 여 모델 열기](../modeling/how-to-open-a-model-from-file-in-program-code.md) [UML 모델을 다른 모델 및 도구와 통합](../modeling/integrate-uml-models-with-other-models-and-tools.md) 방법: [텍스트 템플릿에서 Visual Studio ModelBus를 사용 하 여](../modeling/using-visual-studio-modelbus-in-a-text-template.md) [끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)
