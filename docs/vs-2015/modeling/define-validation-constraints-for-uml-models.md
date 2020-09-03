---
title: UML 모델에 대 한 유효성 검사 제약 조건 정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 258fc138f032d34e57df69386b6849fc3a0650a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547591"
---
# <a name="define-validation-constraints-for-uml-models"></a>UML 모델에 대한 유효성 검사 제약 조건 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델이 지정된 조건을 충족하는지 여부를 테스트하는 유효성 검사 제약 조건을 정의할 수 있습니다. 예를 들어 사용자가 상속 관계 루프를 만들지 않도록 제약 조건을 정의할 수 있습니다. 제약 조건은 사용자가 모델을 열거나 저장하려고 할 때 호출되며, 수동으로 호출할 수도 있습니다. 제약 조건이 실패하면 정의한 오류 메시지가 오류 창에 추가됩니다. 이러한 제약 조건을[VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

 데이터베이스와 같은 외부 리소스에 대해 모델의 유효성을 검사하는 제약 조건을 정의할 수도 있습니다. 레이어 다이어그램에 대해 프로그램 코드의 유효성을 검사 하려면 [레이어 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)를 참조 하세요.

 UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="requirements"></a>요구 사항
 [요구 사항](../modeling/extend-uml-models-and-diagrams.md#Requirements)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="applying-validation-constraints"></a>유효성 검사 제약 조건 적용
 유효성 검사 제약 조건은 다음 세 가지 경우에 적용됩니다. 즉, 모델을 저장할 때, 모델을 열 때 및 **아키텍처** 메뉴에서 **UML 모델의 유효성 검사** 를 클릭할 때입니다. 일반적으로 둘 이상의 경우에 적용되도록 각 제약 조건을 정의하지만, 해당 경우에 대해 정의된 제약 조건만 적용됩니다.

 유효성 검사 오류는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 창에 보고되며, 오류를 두 번 클릭하여 오류 상태의 모델 요소를 선택할 수 있습니다.

 유효성 검사를 적용 하는 방법에 대 한 자세한 내용은 [UML 모델 유효성 검사](../modeling/validate-your-uml-model.md)를 참조 하세요.

## <a name="defining-a-validation-extension"></a>유효성 검사 확장 정의
 UML 디자이너에 대한 유효성 검사 확장을 만들려면 유효성 검사 제약 조건을 정의하는 클래스를 만들고 해당 클래스를 VSIX(Visual Studio Integration Extension)에 포함해야 합니다. VSIX는 제약 조건을 설치할 수 있는 컨테이너 역할을 합니다. 유효성 검사 확장을 정의하는 대신 다음 두 가지 방법을 사용할 수 있습니다.

- **프로젝트 템플릿을 사용하여 자체 VSIX에서 유효성 검사 확장을 만듭니다.** 이는 더 빠른 방법입니다. 유효성 검사 제약 조건을 메뉴 명령, 사용자 지정 도구 상자 또는 제스처 처리기와 같은 다른 형식 확장과 결합하지 않으려면 이 방법을 사용합니다. 하나의 클래스에서 여러 제약 조건을 정의할 수 있습니다.

- **별도의 유효성 검사 클래스 및 VSIX 프로젝트를 만듭니다.** 여러 확장 형식을 같은 VSIX로 결합하려면 이 방법을 사용합니다. 예를 들어 메뉴 명령에서 모델이 특정 제약 조건을 따르도록 요구하면 유효성 검사 방법과 동일한 VSIX에 해당 제스처 처리기를 포함할 수 있습니다.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>자체 VSIX에서 유효성 검사 확장을 만들려면

1. **새 프로젝트** 대화 상자의 **모델링 프로젝트**에서 **유효성 검사 확장**을 선택합니다.

2. 새 프로젝트에서 **.cs** 파일을 열고 클래스를 수정하여 유효성 검사 제약 조건을 구현합니다.

    자세한 내용은 [유효성 검사 제약 조건 평가](#Implementing)를 참조하세요.

   > [!IMPORTANT]
   > **.cs** 파일에 다음 `using` 문이 포함되어 있는지 확인합니다.
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. 새 메서드를 정의하여 다른 제약 조건을 추가할 수 있습니다. 메서드를 유효성 검사 메서드로 식별하려면 초기 유효성 검사 메서드와 동일한 방식으로 특성을 사용하여 태그를 지정해야 합니다.

4. F5 키를 눌러 제약 조건을 테스트합니다. 자세한 내용은 [유효성 검사 제약 조건 실행](#Executing)을 참조하세요.

5. 프로젝트에서 빌드된 파일 **bin \\ \* \\ \* . vsix** 를 복사 하 여 다른 컴퓨터에 메뉴 명령을 설치 합니다. 자세한 내용은 [확장 설치 및 제거](#Installing)를 참조하세요.

   다른 **.cs** 파일을 추가하는 경우 일반적으로 다음 `using` 문이 필요합니다.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 다음은 대체 절차입니다.

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>클래스 라이브러리 프로젝트에서 별도 유효성 검사 제약 조건을 만들려면

1. 클래스 라이브러리 프로젝트를 만들어 기존 VSIX 솔루션에 추가하거나 새 솔루션을 만듭니다.

    1. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택합니다.

    2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장하고 가운데 열에서 **클래스 라이브러리**를 선택합니다.

2. 솔루션에 포함되어 있지 않으면 VSIX 프로젝트를 만듭니다.

    1. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서  **추가**, **새 프로젝트**를 선택합니다.

    2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **확장성**을 선택합니다. 가운데 열에서 **VSIX 프로젝트**를 클릭합니다.

3. VSIX 프로젝트를 솔루션의 시작 프로젝트로 설정합니다.

    - 솔루션 탐색기의 VSIX 프로젝트 바로 가기 메뉴에서 **시작 프로젝트로 설정**을 선택 합니다.

4. **source.extension.vsixmanifest**의 **콘텐츠**에서 클래스 라이브러리 프로젝트를 MEF 구성 요소로 추가합니다.

    1. **메타데이터** 탭에서 VSIX 이름을 설정합니다.

    2. **설치 대상** 탭에서 Visual Studio 버전을 대상으로 설정합니다.

    3. **자산** 탭에서 **새로 만들기**를 선택하고 대화 상자에서 다음을 설정합니다.

         **유형**  =  **MEF 구성 요소**

         **원본**  =  **현재 솔루션의 프로젝트**

         **프로젝트**  =  *클래스 라이브러리 프로젝트*

#### <a name="to-define-the-validation-class"></a>유효성 검사 클래스를 정의하려면

1. 유효성 검사 프로젝트 템플릿에서 자체 VSIX를 사용하여 유효성 검사 클래스를 만든 경우에는 이 절차가 필요하지 않습니다.

2. 유효성 검사 클래스 프로젝트에서 다음 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 어셈블리에 대한 참조를 추가합니다.

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. 다음 예제와 비슷한 코드를 포함하는 파일을 클래스 라이브러리 프로젝트에 추가합니다.

    - 각 유효성 검사 제약 조건은 특정 특성으로 표시된 메서드 내에 포함됩니다. 메서드는 모델 요소 형식의 매개 변수를 허용합니다. 유효성 검사가 호출되면 유효성 검사 프레임워크가 해당 매개 변수 형식을 준수하는 모든 모델 요소에 모든 유효성 검사 메서드를 적용합니다.

    - 이러한 메서드는 임의 클래스와 네임스페이스에 배치할 수 있습니다. 원하는 대로 메서드를 변경합니다.

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="executing-a-validation-constraint"></a><a name="Executing"></a> 유효성 검사 제약 조건 실행
 테스트를 위해 디버그 모드에서 유효성 검사 메서드를 실행합니다.

#### <a name="to-test-the-validation-constraint"></a>유효성 검사 제약 조건을 테스트하려면

1. **F5**키를 누르거나, **디버그** 메뉴에서 **디버깅 시작**을 선택합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 시작됩니다.

     **문제 해결**: 새 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 가 시작되지 않는 경우:

    - 프로젝트가 두 개 이상 있으면 VSIX 프로젝트가 솔루션의 시작 프로젝트로 설정되었는지 확인합니다.

    - 솔루션 탐색기의 시작 또는 전용 프로젝트 바로 가기 메뉴에서 **속성**을 선택합니다. 프로젝트 속성 편집기에서 **디버그** 탭을 선택 합니다. **시작 외부 프로그램** 필드의 문자열이 보통 다음과 같은의 전체 경로 이름 인지 확인 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 모델링 프로젝트를 열거나 만들고 모델링 다이어그램을 열거나 만듭니다.

3. 이전 섹션에서 제공된 샘플 제약 조건에 대해 테스트를 설정하려면

    1. 클래스 다이어그램을 엽니다.

    2. 클래스를 만들고 동일한 이름을 가진 두 개의 특성을 추가합니다.

4. 다이어그램에 있는 바로 가기 메뉴에서 **유효성 검사**를 선택합니다.

5. 모델의 모든 오류가 오류 창에 보고됩니다.

6. 오류 보고서를 두 번 클릭합니다. 보고서에 언급된 요소가 화면에 표시되는 경우 강조 표시됩니다.

     **문제 해결**: **유효성 검사** 명령이 메뉴에 표시되지 않는 경우 다음을 확인합니다.

    - 유효성 검사 프로젝트가 VSIX 프로젝트에서 **source.extensions.manifest** 의 **자산** 탭에 MEF 구성 요소로 나열됩니다.

    - 올바른 `Export` 및 `ValidationMethod` 특성이 유효성 검사 메서드에 연결되었습니다.

    - `ValidationCategories.Menu` 는 특성에 대 한 인수에 포함 `ValidationMethod` 되며 LOGICAL OR (&#124;)를 사용 하 여 다른 값으로 구성 됩니다.

    - 모든 `Import` 및 `Export` 특성의 매개 변수가 유효합니다.

## <a name="evaluating-the-constraint"></a><a name="Implementing"></a> 제약 조건 평가
 유효성 검사 메서드는 적용할 유효성 검사 제약 조건이 true 또는 false인지를 확인해야 합니다. true이면 아무 작업도 수행하면 안 됩니다. false이면 `ValidationContext` 매개 변수가 제공하는 메서드를 사용하여 오류를 보고해야 합니다.

> [!NOTE]
> 유효성 검사 메서드는 모델을 변경하면 안 됩니다. 제약 조건을 실행되는 시기 또는 순서에 대한 보장은 없습니다. 유효성 검사 실행 내에서 유효성 검사 메서드의 연속 실행 간에 정보를 전달해야 하는 경우 [여러 유효성 검사 조정](#ContextCache)에서 설명된 컨텍스트 캐시를 사용할 수 있습니다.

 예를 들어 모든 형식(클래스, 인터페이스 또는 열거자)의 이름이 3자 이상인지 확인하려는 경우 다음 메서드를 사용할 수 있습니다.

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 모델을 탐색하고 읽는 데 사용할 수 있는 메서드 및 형식에 대한 자세한 내용은 [Programming with the UML API](../modeling/programming-with-the-uml-api.md) 을 참조하세요.

### <a name="about-validation-constraint-methods"></a>유효성 검사 제약 조건 메서드 정보
 각 유효성 검사 제약 조건은 다음 형식의 메서드에 의해 정의됩니다.

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 모든 유효성 검사 메서드의 특성과 매개 변수는 다음과 같습니다.

|서명|Description|
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|MEF(Managed Extensibility Framework)를 사용하여 메서드를 유효성 검사 제약 조건으로 정의합니다.|
|`[ValidationMethod (ValidationCategories.Menu)]`|유효성 검사를 수행하는 시기를 지정합니다. 둘 이상의 옵션을 결합 하려면 비트 OR (&#124;)를 사용 합니다.<br /><br /> `Menu` = 유효성 검사 메뉴에 의해 호출됩니다.<br /><br /> `Save` = 모델을 저장할 때 호출됩니다.<br /><br /> `Open` = 모델을 열 때 호출됩니다. `Load` = 모델을 저장할 때 호출되지만, 위반이 있을 경우 모델을 다시 열지 못할 수도 있다고 사용자에게 경고합니다. 모델을 구문 분석하기 전에 로드 시에도 호출됩니다.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|제약 조건을 적용할 요소 형식으로 두 번째 매개 변수 `IElement` 를 바꿉니다. 지정한 형식의 모든 요소에 대해 제약 조건 메서드가 호출됩니다.<br /><br /> 메서드 이름은 중요하지 않습니다.|

 두 번째 매개 변수에 다른 형식을 사용하여 유효성 검사 메서드를 원하는 개수만큼 정의할 수 있습니다. 유효성 검사가 호출되면 매개 변수 형식을 준수하는 각 모델 요소에 대해 각 유효성 검사 메서드가 호출됩니다.

### <a name="reporting-validation-errors"></a>유효성 검사 오류 보고
 오류 보고서를 만들려면 `ValidationContext`가 제공하는 메서드를 사용합니다.

 `context.LogError("error string", errorCode, elementsWithError);`

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 목록에 `"error string"`이 표시됩니다.

- `errorCode`는 오류의 고유 식별자여야 하는 문자열입니다.

- `elementsWithError`는 모델의 요소를 식별합니다. 사용자가 오류 보고서를 두 번 클릭하면 이 요소를 나타내는 모양이 선택됩니다.

  `LogError(),``LogWarning()`및는 `LogMessage()` 오류 목록의 서로 다른 섹션에 메시지를 저장 합니다.

## <a name="how-validation-methods-are-applied"></a>유효성 검사 메서드가 적용되는 방법
 유효성 검사는 클래스의 특성 및 작업의 매개 변수와 같은 더 큰 요소의 부분과 관계를 포함하여 모델의 모든 요소에 적용됩니다.

 각 유효성 검사 메서드는 두 번째 매개 변수의 형식에 맞는 각 요소에 적용됩니다. 즉, 예를 들어 `IUseCase` 의 두 번째 매개 변수로 유효성 검사 메서드를 정의하고 상위 형식 `IElement`로 다른 유효성 검사 메서드를 정의하는 경우 모델의 각 사용 사례에 두 메서드가 모두 적용됩니다.

 형식의 계층 구조는 [UML 모델 요소 형식](../modeling/uml-model-element-types.md)으로 요약 됩니다.

 다음 관계를 통해 요소에 액세스할 수도 있습니다. 예를 들어 `IClass`에 유효성 검사 메서드를 정의하는 경우 소유된 속성을 반복할 수 있습니다.

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>모델에서 유효성 검사 메서드 만들기
 각 유효성 검사를 실행하는 동안 유효성 검사 메서드가 한 번 호출되도록 하려는 경우 `IModel`의 유효성을 검사할 수 있습니다.

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>모양 및 다이어그램의 유효성 검사
 유효성 검사 메서드는 모델의 유효성을 검사하는 것이 주요 목적이므로 다이어그램 및 모양과 같은 표시 요소에 대해 호출되지 않습니다. 그러나 다이어그램 컨텍스트를 사용하여 현재 다이어그램에 액세스할 수 있습니다.

 유효성 검사 클래스에서 `DiagramContext` 를 가져온 속성으로 선언합니다.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 유효성 검사 메서드에서 `DiagramContext` 를 사용하여 현재 포커스 다이어그램에 액세스할 수 있습니다(있는 경우).

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 오류를 기록하려면 `LogError`에 모양을 전달할 수 없기 때문에 모양이 나타내는 모델 요소를 가져와야 합니다.

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="coordinating-multiple-validations"></a><a name="ContextCache"></a> 여러 유효성 검사 조정
 예를 들어 사용자가 다이어그램 메뉴에서 유효성 검사를 호출하면 각 유효성 검사 메서드가 각 모델 요소에 적용됩니다. 즉, 유효성 검사 프레임워크의 단일 호출에서 동일한 메서드가 여러 요소에 여러 번 적용될 수 있습니다.

 이 경우 요소 간의 관계를 처리하는 유효성 검사에서 문제가 발생합니다. 예를 들어 사용 사례에서 시작되고 **include** 관계를 트래버스하여 루프가 없는지 확인하는 유효성 검사를 작성할 수 있습니다. 그러나 많은 **include** 링크를 포함하는 모델의 각 사용 사례에 메서드가 적용되는 경우 모델의 동일한 영역을 반복적으로 처리할 가능성이 큽니다.

 이러한 상황을 방지하기 위해 유효성 검사를 실행하는 동안 정보가 유지되는 컨텍스트 캐시가 있습니다. 컨텍스트 캐시를 사용하여 서로 다른 유효성 검사 메서드 실행 간에 정보를 전달할 수 있습니다. 예를 들어 이 유효성 검사 실행에서 이미 처리된 요소 목록을 저장할 수 있습니다. 캐시는 각 유효성 검사 실행을 시작할 때 생성되며, 서로 다른 유효성 검사 실행 간에 정보를 전달하는 데 사용할 수 없습니다.

|구문|Description|
|-|-|
|`context.SetCacheValue<T> (name, value)`|값을 저장합니다.|
|`context.TryGetCacheValue<T> (name, out value)`|값을 가져옵니다. 성공하면 true를 반환합니다.|
|`context.GetValue<T>(name)`|값을 가져옵니다.|
|`Context.GetValue<T>()`|지정된 형식의 값을 가져옵니다.|

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> 확장 설치 및 제거
 사용 중인 컴퓨터 및 다른 컴퓨터에서 모두 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장을 설치할 수 있습니다.

#### <a name="to-install-an-extension"></a>확장을 설치하려면

1. 컴퓨터에서 VSIX 프로젝트를 통해 작성된 **.vsix** 파일을 찾습니다.

    1. **솔루션 탐색기**의 VSIX 프로젝트 바로 가기 메뉴에서 **Windows 탐색기에서 폴더 열기**를 선택합니다.

    2. 파일 ** \\ \* bin \\ **_을 찾습니다_**. vsix**

2. 확장을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

    - 대상 컴퓨터에는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **source.extension.vsixmanifest**에서 지정한 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 엽니다.

     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 시작하거나 다시 시작합니다.

#### <a name="to-uninstall-an-extension"></a>확장을 제거하려면

1. **도구** 메뉴 모음에서 **확장 및 업데이트**를 선택합니다.

2. **설치된 확장**을 확장합니다.

3. 확장을 선택하고 **제거**를 선택합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제 하 여 확장을 제거할 수 있습니다. 여기서 *% LocalAppData%* 는 일반적으로 *DriveName*: \Users \\ *UserName*\AppData\Local입니다.

   *% LocalAppData%* **\Microsoft\VisualStudio \\ [version] \extensions**

## <a name="example"></a><a name="Example"></a> 예제
 이 예제에서는 요소 간 종속성 관계에서 루프를 찾습니다.

 저장 시 및 유효성 검사 메뉴 명령에 의해 유효성을 검사합니다.

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>관련 항목
 [UML API를 사용 하 여](../modeling/programming-with-the-uml-api.md) [모델링 확장 프로그램 정의 및 설치](../modeling/define-and-install-a-modeling-extension.md)
