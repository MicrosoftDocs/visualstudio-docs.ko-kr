---
title: 텍스트 템플릿에서 ModelBus 사용
description: Visual Studio ModelBus 참조가 포함된 모델을 읽는 텍스트 템플릿을 작성하는 경우 대상 모델에 액세스하기 위한 참조를 해결하는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2afe8de66b109793a4e15e8320c3f498a08b25ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388388"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>텍스트 템플릿에서 Visual Studio ModelBus 사용

Visual Studio ModelBus 참조가 포함된 모델을 읽는 텍스트 템플릿을 작성하는 경우 참조를 확인하여 대상 모델에 액세스할 수 있습니다. 이 경우 텍스트 템플릿 및 참조된 DSL(도메인 특정 언어)을 조정해야 합니다.

- 참조의 대상인 DSL에는 텍스트 템플릿에서 액세스하도록 구성된 ModelBus 어댑터가 있어야 합니다. 다른 코드에서도 DSL에 액세스하는 경우 표준 ModelBus 어댑터 외에 다시 구성된 어댑터가 필요합니다.

     어댑터 관리자는 [VsTextTemplatingModelingAdapterManager에서](/previous-versions/ee844317(v=vs.140)) 상속해야 하며 특성이 있어야 `[HostSpecific(HostName)]` 합니다.

- 템플릿은 [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))에서 상속되어야 합니다.

> [!NOTE]
> ModelBus 참조를 포함하지 않는 DSL 모델을 읽으려면 DSL 프로젝트에서 생성된 지시문 프로세서를 사용할 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 모델 액세스를 참조하세요.](../modeling/accessing-models-from-text-templates.md)

텍스트 템플릿에 대한 자세한 내용은 T4 텍스트 템플릿을 [사용하여 디자인 타임 코드 생성을 참조하세요.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>텍스트 템플릿에서 액세스할 수 있도록 Model Bus 어댑터 만들기

텍스트 템플릿에서 ModelBus 참조를 확인하려면 대상 DSL에 호환되는 어댑터가 있어야 합니다. 텍스트 템플릿은 Visual Studio 문서 편집기와는 별도의 AppDomain에서 실행되므로 어댑터는 DTE를 통해 액세스하는 대신 모델을 로드해야 합니다.

1. 대상 DSL 솔루션에 **ModelBusAdapter** 프로젝트가 없는 경우 Modelbus 확장 마법사를 사용하여 만듭니다.

    1. 아직 Visual Studio ModelBus 확장을 다운로드하여 설치합니다. 자세한 내용은 [시각화 및 모델링 SDK를 참조하세요.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

    2. DSL 정의 파일을 엽니다. 디자인 표면을 마우스 오른쪽 단추로 클릭한 다음 **Modelbus 사용을** 클릭합니다.

    3. 대화 상자에서 **이 DSL을 ModelBus 에 노출하려는 경우를** 선택합니다. 이 DSL이 해당 모델을 노출하고 다른 DSL에 대한 참조를 사용하게 하려면 두 옵션을 모두 선택할 수 있습니다.

    4. **확인** 을 클릭합니다. "ModelBusAdapter"라는 새 프로젝트가 DSL 솔루션에 추가됩니다.

    5. **모든 템플릿 변환을 클릭합니다.**

    6. 솔루션을 다시 빌드합니다.

2. 텍스트 템플릿 및 명령과 같은 다른 코드에서 DSL에 액세스하려면 **ModelBusAdapter** 프로젝트를 복제합니다.

    1. Windows 탐색기 **ModelBusAdapter.csproj가** 포함된 폴더를 복사하여 붙여넣습니다.

    2. 프로젝트 파일의 이름을 바꿉니다(예: **T4ModelBusAdapter.csproj).**

    3. **솔루션 탐색기** 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **추가를** 가리킨 다음 **기존 프로젝트** 를 클릭합니다. 새 어댑터 프로젝트 **T4ModelBusAdapter.csproj 를** 찾습니다.

    4. 새 프로젝트의 각 `*.tt` 파일에서 네임스페이스를 변경합니다.

    5. 솔루션 탐색기 새 프로젝트를 **마우스 오른쪽 단추로** 클릭한 다음 **속성을** 클릭합니다. 속성 편집기에서 생성된 어셈블리의 이름과 기본 네임스페이스를 변경합니다.

    6. DslPackage 프로젝트에서 두 어댑터에 대한 참조를 없도록 새 어댑터 프로젝트에 대한 참조를 추가합니다.

    7. DslPackage\source.extension.tt 새 어댑터 프로젝트를 참조하는 줄을 추가합니다.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **모든 템플릿을 변환하고** 솔루션을 다시 빌드합니다. 빌드 오류가 발생하지 않아야 합니다.

3. 새 어댑터 프로젝트에서 다음 어셈블리에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. In AdapterManager.tt:

    - [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))에서 상속되도록 AdapterManagerBase의 선언을 변경합니다.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - 파일의 끝 부근에서 AdapterManager 클래스 앞에 있는 HostSpecific 특성을 바꿉니다. 다음 줄을 제거합니다.

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         다음 줄을 삽입합니다.

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         이 특성은 modelbus 소비자가 어댑터를 검색할 때 사용할 수 있는 어댑터 집합을 필터링합니다.

5. **모든 템플릿을 변환하고** 솔루션을 다시 빌드합니다. 빌드 오류가 발생하지 않아야 합니다.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus 참조를 확인할 수 있는 텍스트 템플릿 작성

일반적으로 "원본" DSL에서 파일을 읽고 생성하는 템플릿으로 시작합니다. 이 템플릿은 원본 DSL 프로젝트에서 생성된 지시문을 사용하여 텍스트 템플릿에서 모델 액세스에 설명된 방식으로 원본 모델 파일을 [읽습니다.](../modeling/accessing-models-from-text-templates.md) 그러나 원본 DSL에는 "대상" DSL에 대한 ModelBus 참조가 포함되어 있습니다. 따라서 참조를 해결하고 대상 DSL에 액세스하기 위해 템플릿 코드를 사용하도록 설정하려고 합니다. 따라서 다음 단계에 따라 템플릿을 조정해야 합니다.

- 템플릿의 기본 클래스를 [ModelBusEnabledTextTransformation으로 변경합니다.](/previous-versions/ee844263(v=vs.140))

- `hostspecific="true"`템플릿 지시문에 를 포함합니다.

- 대상 DSL 및 해당 어댑터에 어셈블리 참조를 추가하고 ModelBus를 사용하도록 설정합니다.

- 대상 DSL의 일부로 생성되는 지시문은 필요하지 않습니다.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 이 텍스트 템플릿이 실행되면 `SourceDsl` 지시문은 파일을 `Sample.source` 로드합니다. 템플릿은 부터 해당 모델의 요소에 액세스할 수 `this.ModelRoot` 있습니다. 코드는 해당 DSL의 도메인 클래스 및 속성을 사용할 수 있습니다.

 또한 템플릿은 ModelBus 참조를 확인할 수 있습니다. 참조가 대상 모델을 가리키는 경우 어셈블리 지시문을 사용하면 코드에서 해당 모델의 DSL의 도메인 클래스 및 속성을 사용할 수 있습니다.

- DSL 프로젝트에서 생성된 지시문을 사용하지 않는 경우 다음도 포함해야 합니다.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- 를 사용하여 `this.ModelBus` ModelBus에 대한 액세스 권한을 얻습니다.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>연습: ModelBus를 사용하는 텍스트 템플릿 테스트
 이 연습에서는 다음 단계를 수행합니다.

1. 두 개의 DSL을 생성합니다. 한 DSL인 *소비자* 에는 `ModelBusReference` 다른 DSL인 *공급자* 를 참조할 수 있는 속성이 있습니다.

2. 공급자에 두 개의 ModelBus 어댑터를 만듭니다. 하나는 텍스트 템플릿으로 액세스하기 위한 어댑터로, 다른 하나는 일반 코드용입니다.

3. 단일 실험적 프로젝트에서 DSL의 인스턴스 모델을 만듭니다.

4. 한 모델에서 도메인 속성을 설정하여 다른 모델을 가리킵니다.

5. 가리킨 모델을 여는 두 번 클릭 처리기를 작성합니다.

6. 첫 번째 모델을 로드하고, 다른 모델에 대한 참조를 따르고, 다른 모델을 읽을 수 있는 텍스트 템플릿을 작성합니다.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>ModelBus에 액세스할 수 있는 DSL 생성

1. 새 DSL 솔루션을 만듭니다. 이 예제에서는 작업 흐름 솔루션 템플릿을 선택합니다. 언어 이름을 로 설정하고 `MBProvider` 파일 이름 확장명을 ".provide"로 설정합니다.

2. DSL 정의 다이어그램에서 맨 위에 있지 않은 다이어그램의 빈 부분을 마우스 오른쪽 단추로 클릭한 다음 **Modelbus 사용을** 클릭합니다.

   **Modelbus 사용이** 표시되지 않으면 VMSDK ModelBus 확장을 다운로드하여 설치합니다.

3. **Modelbus 사용** 대화 상자에서 **이 DSL을 ModelBus 에 노출을** 선택하고 **확인을** 클릭합니다.

    새 프로젝트 가 `ModelBusAdapter` 솔루션에 추가됩니다.

이제 ModelBus를 통해 텍스트 템플릿으로 액세스할 수 있는 DSL이 있습니다. 이에 대한 참조는 명령, 이벤트 처리기 또는 규칙 코드에서 확인할 수 있으며, 모두 모델 파일 편집기의 AppDomain에서 작동합니다. 그러나 텍스트 템플릿은 별도의 AppDomain에서 실행되며 편집할 때 모델에 액세스할 수 없습니다. 텍스트 템플릿에서 이 DSL에 대한 ModelBus 참조에 액세스하려면 별도의 ModelBusAdapter가 있어야 합니다.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>텍스트 템플릿에 대해 구성된 ModelBus 어댑터 만들기

1. 파일 탐색기 *ModelBusAdapter.csproj가* 포함된 폴더를 복사하여 붙여넣습니다.

    폴더 이름을 **T4ModelBusAdapter로 지정합니다.**

    프로젝트 파일의 이름을 *T4ModelBusAdapter.csproj로 바꿉니다.*

2. 솔루션 탐색기 T4ModelBusAdapter를 MBProvider 솔루션에 추가합니다. 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **추가를** 가리킨 다음 **기존 프로젝트** 를 클릭합니다.

3. T4ModelBusAdapter 프로젝트 노드를 마우스 오른쪽 단추로 클릭한 다음 속성을 클릭합니다. 프로젝트 속성 창에서 **어셈블리 이름** 및 **기본 네임스페이스를** 로 변경합니다. `Company.MBProvider.T4ModelBusAdapters`

4. T4ModelBusAdapter의 각 *.tt 파일에서 네임스페이스의 마지막 부분에 "T4"를 삽입하여 줄이 다음과 유사하게 만듭니다.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. 프로젝트에서 `DslPackage` 에 프로젝트 참조를 `T4ModelBusAdapter` 추가합니다.

6. DslPackage\source.extension.tt 아래에 다음 줄을 `<Content>` 추가합니다.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. 프로젝트에서 `T4ModelBusAdapter` **Microsoft.VisualStudio.TextTemplating.Modeling.11.0에** 대한 참조를 추가합니다.

8. T4ModelBusAdapter\AdapterManager.tt 엽니다.

   1. AdapterManagerBase의 기본 클래스를 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))로 변경 합니다. 이 파일의 부분은 이제 다음과 유사 합니다.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. 파일의 끝 부분에서 AdapterManager 클래스 앞에 다음과 같은 추가 특성을 삽입 합니다.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        결과는 다음과 유사 합니다.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. 솔루션 탐색기 제목 표시줄에서 **모든 템플릿 변환** 을 클릭 합니다.

10. **F5** 키를 누릅니다.

11. DSL이 작동 하는지 확인 합니다. 실험적 프로젝트에서를 엽니다 `Sample.provider` . Visual Studio의 실험적 인스턴스를 닫습니다.

    이제이 DSL에 대 한 ModelBus 참조를 텍스트 템플릿 및 일반 코드에서 확인할 수 있습니다.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>ModelBus Reference 도메인 속성을 사용 하 여 DSL 생성

1. 최소 언어 솔루션 템플릿을 사용 하 여 새 DSL을 만듭니다. 언어 이름을 MBConsumer로 설정 하 고 파일 이름 확장명을 "사용"으로 설정 합니다.

2. DSL 프로젝트에서 MBProvider DSL 어셈블리에 대 한 참조를 추가 합니다. 마우스 오른쪽 단추로 클릭 한  `MBConsumer\Dsl\References` 다음 **참조 추가** 를 클릭 합니다. **찾아보기** 탭에서 다음을 찾습니다.`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    이렇게 하면 다른 DSL을 사용 하는 코드를 만들 수 있습니다. 여러 Dsl에 대 한 참조를 만들려는 경우에도 추가 합니다.

3. DSL 정의 다이어그램에서 다이어그램을 마우스 오른쪽 단추로 클릭 한 다음 **ModelBus 사용** 을 클릭 합니다. 대화 상자에서 **이 DSL 사용을 선택 하 여 ModelBus** 를 사용 합니다.

4. 클래스에서 `ExampleElement` 새 도메인 속성을 추가 하 `MBR` 고, 속성 창에서 해당 형식을로 설정 `ModelBusReference` 합니다.

5. 다이어그램에서 도메인 속성을 마우스 오른쪽 단추로 클릭 한 다음 **ModelBusReference 특정 속성 편집** 을 클릭 합니다. 대화 상자에서 **모델 요소** 를 선택 합니다.

    파일 대화 상자 필터를 다음으로 설정 합니다.

    `Provider File|*.provide`

    "&#124;" 뒤의 부분 문자열은 파일 선택 대화 상자에 대 한 필터입니다. *를 사용 하 여 파일을 허용 하도록 설정할 수 있습니다.\*

    **모델 요소 유형** 목록에서 공급자 DSL에 하나 이상의 도메인 클래스 이름을 입력 합니다 (예: 회사. Mbprovider. 작업). 추상 클래스 일 수 있습니다. 목록을 비워 두면 사용자는 모든 요소에 대 한 참조를 설정할 수 있습니다.

6. 대화 상자를 닫고 **모든 템플릿을 변환** 합니다.

   다른 DSL의 요소에 대 한 참조를 포함할 수 있는 DSL을 만들었습니다.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>솔루션의 다른 파일에 대 한 ModelBus 참조 만들기

1. MBConsumer 솔루션에서 CTRL + F5를 누릅니다. **MBConsumer\Debugging** 프로젝트에서 Visual Studio의 실험적 인스턴스가 열립니다.

2. 샘플의 복사본을 추가 합니다. **MBConsumer\Debugging** 프로젝트에를 제공 합니다. ModelBus 참조는 동일한 솔루션에 있는 파일을 참조 해야 하기 때문에이 작업이 필요 합니다.

   1. 디버깅 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 가리킨 다음 **기존 항목** 을 클릭 합니다.

   2. **항목 추가** 대화 상자에서 필터를 **모든 파일 ( \* . \* )** 로 설정 합니다.

   3. 로 이동한 `MBProvider\Debugging\Sample.provide` 다음 **추가** 를 클릭 합니다.

3. `Sample.consume`를 엽니다.

4. 하나의 예제 셰이프를 클릭 하 고 속성 창에서 MBR 속성의 **[...]** 를 클릭 합니다. 대화 상자에서 **찾아보기** 를 클릭 하 고를 선택 `Sample.provide` 합니다. 요소 창에서 형식 작업을 확장 하 고 요소 중 하나를 선택 합니다.

5. 파일을 저장합니다. Visual Studio의 실험적 인스턴스를 아직 닫지 마세요.

   다른 모델의 요소에 대 한 ModelBus 참조를 포함 하는 모델을 만들었습니다.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>텍스트 템플릿에서 ModelBus 참조 확인

1. Visual Studio의 실험적 인스턴스에서 샘플 텍스트 템플릿 파일을 엽니다. 다음과 같이 콘텐츠를 설정 합니다.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     다음 사항을 확인합니다.

    - `hostSpecific` `inherits` 지시문의 및 특성을 `template` 설정 해야 합니다.

    - 소비자 모델은 일반적으로 해당 DSL에서 생성 된 지시문 프로세서를 통해 액세스 됩니다.

    - 어셈블리 및 가져오기 지시문은 ModelBus 및 공급자 DSL의 형식에 액세스할 수 있어야 합니다.

    - 여러 Mbr이 동일한 모델에 연결 되어 있는 경우 CreateAdapter를 한 번만 호출 하는 것이 좋습니다.

2. 템플릿을 저장하는 경우 결과 텍스트 파일이 다음과 유사 하는지 확인 합니다.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>제스처 처리기에서 ModelBus 참조 확인

1. 실행 중인 경우 Visual Studio의 실험적 인스턴스를 닫습니다.

2. *MBConsumer\Dsl\Custom.cs* 라는 파일을 추가 하 고 해당 콘텐츠를 다음으로 설정 합니다.

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. **Ctrl** + **F5** 를 누릅니다.

4. Visual Studio의 실험적 인스턴스에서를 엽니다 `Debugging\Sample.consume` .

5. 한 셰이프를 두 번 클릭 합니다.

    해당 요소에서 MBR을 설정한 경우 참조 된 모델이 열리고 참조 된 요소가 선택 됩니다.

## <a name="see-also"></a>참조

- [Visual Studio Modelbus를 사용하여 모델 통합](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
