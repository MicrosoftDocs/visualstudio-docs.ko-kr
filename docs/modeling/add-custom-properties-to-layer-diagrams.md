---
title: 종속성 다이어그램에 사용자 지정 속성 추가
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c68d8a75ca8203a790684506ffd44b3d890648a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546918"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>종속성 다이어그램에 사용자 지정 속성 추가

종속성 다이어그램에 대 한 확장 코드를 작성 하는 경우 종속성 다이어그램의 요소와 함께 값을 저장할 수 있습니다. 값은 다이어그램이 저장되고 다시 열릴 때 유지됩니다. 사용자가 보고 편집할 수 있도록 이러한 속성이 **속성** 창에 표시 될 수도 있습니다. 예를 들어 사용자가 각 레이어에 대한 정규식을 지정하고, 각 레이어의 클래스 이름이 사용자가 지정한 패턴을 따르는지 확인하기 위해 유효성 검사 코드를 작성하도록 허용할 수 있습니다.

## <a name="non-visible-properties"></a>표시 되지 않는 속성

코드에서 종속성 다이어그램의 요소에 값을 연결 하려면 MEF 구성 요소를 정의 하지 않아도 됩니다. `Properties` [Ilayerelement](/previous-versions/ff644511(v=vs.140))에 이라는 사전이 있습니다. 레이어 요소의 사전에 마샬링할 수 값을 추가하기만 하면 됩니다. 종속성 다이어그램의 일부로 저장 됩니다.

## <a name="editable-properties"></a>편집 가능한 속성

**초기 준비**

> [!IMPORTANT]
> 속성이 표시 되도록 하려면 계층 속성을 표시할 각 컴퓨터에서 다음과 같이 변경 합니다.
>
> 1. **관리자 권한으로 실행**을 사용 하 여 메모장을 실행 합니다. *%ProgramFiles%\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*를 엽니다.
> 2. **콘텐츠** 요소 내에 다음을 추가 합니다.
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Visual Studio 응용 프로그램 시작 메뉴의 **Visual Studio Tools** 섹션에서 **개발자 명령 프롬프트**를 엽니다. 다음을 입력합니다.
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Visual Studio를 다시 시작합니다.

**코드가 VSIX 프로젝트에 있는지 확인**

속성이 명령, 제스처 또는 유효성 검사 프로젝트의 일부인 경우에는 아무것도 추가할 필요가 없습니다. 사용자 지정 속성에 대한 코드는 MEF 구성 요소로 정의된 Visual Studio 확장성 프로젝트에 정의되어야 합니다. 자세한 내용은 [종속성 다이어그램에 명령 및 제스처 추가](../modeling/add-commands-and-gestures-to-layer-diagrams.md) 또는 [종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)를 참조 하세요.

**사용자 지정 속성 정의**

사용자 지정 속성을 만들려면 다음과 같이 클래스를 정의합니다.

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

[Ilayerelement](/previous-versions/ff644511(v=vs.140)) 또는 해당 파생 클래스 (다음을 포함)에 대 한 속성을 정의할 수 있습니다.

- `ILayerModel`-모델

- `ILayer`-각 계층

- `ILayerDependencyLink`-레이어 간 링크

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>예제

다음 코드는 일반적인 사용자 지정 속성 설명자입니다. 레이어 모델(`ILayerModel`)에서 사용자가 사용자 지정 유효성 검사 메서드의 값을 제공할 수 있게 해주는 부울 속성을 정의합니다.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>참고 항목

- [종속성 다이어그램 확장](../modeling/extend-layer-diagrams.md)
