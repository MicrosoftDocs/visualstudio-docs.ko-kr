---
title: 속성 창 사용자 지정
description: Visual Studio DSL(도메인별 언어)에서 속성 창의 모양과 동작을 사용자 지정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385801"
---
# <a name="customize-the-properties-window"></a>속성 창 사용자 지정

Visual Studio DSL(도메인별 언어)에서 속성 창의 모양과 동작을 사용자 지정할 수 있습니다. DSL 정의에서 각 도메인 클래스에 도메인 속성을 정의합니다. 기본적으로 다이어그램 또는 모델 탐색기에서 클래스의 인스턴스를 선택하면 모든 도메인 속성이 속성 창에 나열됩니다. 이렇게 하면 다이어그램의 셰이프 필드에 매핑하지 않은 경우에도 도메인 속성의 값을 보고 편집할 수 있습니다.

## <a name="names-descriptions-and-categories"></a>이름, 설명 및 범주

**이름 및 표시 이름 입니다.** 도메인 속성 정의에서 속성의 표시 이름은 속성 창에서 런타임에 표시되는 이름입니다. 반면, Name은 속성을 업데이트하는 프로그램 코드를 작성할 때 사용됩니다. 이름은 올바른 CLR 영숫자 이름이어야 하지만 표시 이름에는 공백이 포함될 수 있습니다.

DSL 정의에서 속성의 이름을 설정하면 해당 표시 이름이 자동으로 이름 복사본으로 설정됩니다. "FuelGauge"와 같은 파스칼식 대/소문자 이름을 작성하면 표시 이름에 "연료 계기"라는 공백이 자동으로 포함됩니다. 그러나 표시 이름을 명시적으로 다른 값으로 설정할 수 있습니다.

**설명**. 도메인 속성에 대한 설명은 다음 두 위치에 표시됩니다.

- 사용자가 속성을 선택할 때 속성 창의 아래쪽에 있습니다. 속성이 나타내는 내용을 사용자에게 설명하는 데 사용할 수 있습니다.

- 생성된 프로그램 코드에서. 설명서 기능을 사용하여 API 설명서를 추출하는 경우 API에서 이 속성에 대한 설명으로 표시됩니다.

**범주**. 범주는 속성 창 제목입니다.

## <a name="expose-style-features"></a>스타일 기능 노출

그래픽 요소의 동적 기능 중 일부는 도메인 속성으로 표시하거나 *노출할* 수 있습니다. 이러한 방식으로 노출된 기능은 사용자가 업데이트할 수 있으며 프로그램 코드에서 더 쉽게 업데이트할 수 있습니다.

DSL 정의에서 셰이프 클래스를 마우스 오른쪽 단추로 클릭하고 **노출된 추가를** 가리킨 다음, 기능을 선택합니다.

셰이프에서 **FillColor,** **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** 및 **FillGradientMode** 속성을 노출할 수 있습니다. 커넥터에서 **Color** `,` **TextColor,** **DashStyle** 및 **Thickness** 속성을 노출할 수 있습니다. 다이어그램에서 **FillColor** 및 **TextColor** 속성을 노출할 수 있습니다.

## <a name="forwarding-display-properties-of-related-elements"></a>전달: 관련 요소의 속성 표시

DSL 사용자가 모델의 요소를 선택하면 해당 요소의 속성이 속성 창에 표시됩니다. 그러나 지정된 관련 요소의 속성을 표시할 수도 있습니다. 이는 함께 작동하는 요소 그룹을 정의한 경우에 유용합니다. 예를 들어 주 요소와 선택적 플러그 인 요소를 정의할 수 있습니다. 주 요소가 셰이프에 매핑되고 다른 요소가 매핑되지 않은 경우 모든 속성을 한 요소에 있는 것처럼 보는 것이 유용합니다.

이 효과는 *속성 전달이라고* 하며, 여러 경우에 자동으로 발생합니다. 다른 경우에는 도메인 형식 설명자를 정의하여 속성 전달을 달성할 수 있습니다.

### <a name="default-property-forwarding-cases"></a>기본 속성 전달 사례

사용자가 탐색기에서 셰이프 또는 커넥터 또는 요소를 선택하면 다음 속성이 속성 창 표시됩니다.

- 기본 클래스에 정의된 속성을 포함하여 모델 요소의 도메인 클래스에 정의된 도메인 속성입니다. 단, 검색 가능 을 로 설정한 도메인 **속성은 예외입니다.** `False`

- 복합성이 0..1인 관계를 통해 연결된 요소의 이름입니다. 관계에 대한 커넥터 매핑을 정의하지 않은 경우에도 필요에 따라 연결된 요소를 보는 편리한 방법을 제공합니다.

- 요소를 대상으로 하는 포함 관계의 도메인 속성입니다. 포함 관계는 일반적으로 명시적으로 표시되지 않으므로 사용자는 해당 속성을 볼 수 있습니다.

- 선택한 셰이프 또는 커넥터에 정의된 도메인 속성입니다.

### <a name="add-property-forwarding"></a>속성 전달 추가

속성을 전달하려면 도메인 유형 설명자를 정의합니다. 두 도메인 클래스 간에 도메인 관계가 있는 경우 도메인 유형 설명자를 사용하여 첫 번째 클래스의 도메인 속성을 두 번째 도메인 클래스의 도메인 속성 값으로 설정할 수 있습니다. 예를 들어 **Book** 도메인 클래스와 **Author** 도메인 클래스 간에 관계가 있는 경우 도메인 유형 설명자를 사용하여 사용자가 Book을 선택할 때 책 작성자의 **Name** 속성이 속성 창 **표시되도록** 할 수 있습니다.

> [!NOTE]
> 속성 전달은 사용자가 모델을 편집할 때 속성 창 영향을 미칩니다. 받는 클래스에 도메인 속성을 정의하지 않습니다. DSL 정의의 다른 부분이나 프로그램 코드에서 전달된 도메인 속성에 액세스하려면 전달 요소에 액세스해야 합니다.

다음 절차에서는 DSL을 만들었다고 가정합니다. 처음 몇 단계에서는 필수 구성요소가 요약됩니다.

#### <a name="forward-a-property-from-another-element"></a>다른 요소에서 속성 전달

1. 두 개 이상의 클래스를 포함하는 솔루션을 만듭니다. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 이 예제에서는 **Book** 및 **Author라고** 합니다. **Book과** **Author** 간에는 두 종류의 관계가 있어야 합니다.

    원본 **역할(책** 쪽의 역할)의 복합성은 0..1 또는 1..1이어야 하므로 각 **도서에는** 하나의 **작성자** 가 있어야 합니다.

2. **DSL 탐색기에서** **Book** 도메인 클래스를 마우스 오른쪽 단추로 클릭한 다음 **새 DomainTypeDescriptor 추가를** 클릭합니다.

    **사용자 지정 속성 설명자의 경로라는** 노드가 **사용자 지정 형식 설명자** 노드 아래에 나타납니다.

3. 사용자 지정 **형식 설명자** 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 PropertyPath 추가를** 클릭합니다.

    사용자 지정 속성 설명자의 경로 노드 아래에 새 **속성 경로가** 나타납니다.

4. 새 속성 경로를 선택하고 **속성** 창에서 **Path to Property를** 적절한 모델 요소의 경로로 설정합니다.

    이 속성의 오른쪽에 있는 아래쪽 화살표를 클릭하여 트리 뷰에서 경로를 편집할 수 있습니다. 도메인 경로에 대한 자세한 내용은 [도메인 경로 구문을 참조하세요.](../modeling/domain-path-syntax.md) 편집한 경우 경로는 **BookReferencesAuthor.Author/! 작성자입니다.**

5. **속성을** **Author** 의 **Name** 도메인 속성으로 설정합니다.

6. **표시 이름을** **작성자 이름으로** 설정합니다.

7. 모든 템플릿 변환, DSL 빌드 및 실행

8. 모델 다이어그램에서 책과 저자를 만들고 참조 관계를 사용하여 연결합니다. 책 요소를 선택하면 속성 창 책의 속성 외에도 Author Name이 표시됩니다. 연결된 저자의 이름을 변경하거나 책을 다른 저자에게 연결하고 책의 저자 이름이 변경되는 것을 관찰합니다.

## <a name="custom-property-editors"></a>사용자 지정 속성 편집기

속성 창은 각 도메인 속성의 유형에 대한 적절한 기본 편집 환경을 제공합니다. 예를 들어 열거형 형식의 경우 드롭다운 목록이 표시되고 숫자 속성의 경우 사용자가 숫자를 입력할 수 있습니다. 이는 기본 제공 형식에 대해서만 해당됩니다. 외부 형식을 지정하면 사용자는 속성의 값을 볼 수 있지만 편집할 수는 없습니다.

그러나 다음 편집기 및 형식을 지정할 수 있습니다.

1. 표준 형식과 함께 사용되는 다른 편집기입니다. 예를 들어 문자열 속성에 대한 파일 경로 편집기를 지정할 수 있습니다.

2. 도메인 속성에 대한 외부 형식 및 해당 편집기입니다.

3. 파일 경로 편집기 같은 .NET 편집기 또는 사용자 고유의 사용자 지정 속성 편집기를 만들 수 있습니다.

   기본 편집기가 있는 문자열과 같은 형식과 외부 형식 간의 변환입니다.

   DSL에서 외부 *형식은* 단순 형식(예: Boolean 또는 Int32) 또는 String 중 하나가 아닌 모든 형식입니다.

### <a name="define-a-domain-property-that-has-an-external-type"></a>외부 형식의 도메인 속성 정의

1. **솔루션 탐색기** Dsl 프로젝트에서 외부 형식이 포함된 어셈블리(DLL)에 대한 참조를 **추가합니다.**

    어셈블리는 .NET 어셈블리 또는 제공한 어셈블리일 수 있습니다.

2. 도메인 **유형** 목록에 유형을 추가합니다(이미 수행하지 않은 경우).

   1. DslDefinition.dsl을 열고 **DSL 탐색기에서** 루트 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 외부 형식 추가를** 클릭합니다.

        **도메인 유형** 노드 아래에 새 항목이 나타납니다.

       > [!WARNING]
       > 메뉴 항목이 도메인 유형 노드가 아닌 DSL 루트 노드에 **있습니다.**

   2. 속성 창 새 형식의 이름과 네임스페이스를 설정합니다.

3. 일반적인 방식으로 도메인 클래스에 도메인 속성을 추가합니다.

    속성 창 형식 필드의 드롭다운 목록에서 외부 **형식을** 선택합니다.

   이 단계에서 사용자는 속성 값을 볼 수 있지만 편집할 수는 없습니다. 표시된 값은 `ToString()` 함수에서 얻습니다. 예를 들어 명령 또는 규칙에서 속성 값을 설정하는 프로그램 코드를 작성할 수 있습니다.

### <a name="set-a-property-editor"></a>속성 편집기 설정

다음 형식으로 도메인 속성에 CLR 특성을 추가 합니다.

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

속성 창의 **사용자 지정 특성** 항목을 사용 하 여 속성의 특성을 설정할 수 있습니다.

의 형식은 `AnEditor` 두 번째 매개 변수에 지정 된 형식에서 파생 되어야 합니다. 두 번째 매개 변수는 또는 중 하나 여야 합니다 <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.ComponentEditor> . 자세한 내용은 <xref:System.ComponentModel.EditorAttribute>를 참조하세요.

사용자 고유의 편집기 또는 .NET 편집기 (예: 또는)를 지정할 수 있습니다 <xref:System.Windows.Forms.Design.FileNameEditor> <xref:System.Drawing.Design.ImageEditor> . 예를 들어, 사용자가 파일 이름을 입력할 수 있는 속성을 사용 하려면 다음 절차를 수행 합니다.

#### <a name="define-a-file-name-domain-property"></a>파일 이름 도메인 속성 정의

1. DSL 정의에서 도메인 클래스에 도메인 속성을 추가 합니다.

2. 새 속성을 선택 합니다. 속성 창의 **사용자 지정 특성** 필드에 다음 특성을 입력 합니다. 이 특성을 입력 하려면 줄임표 **[...]** 를 클릭 한 다음 특성 이름 및 매개 변수를 개별적으로 입력 합니다.

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. 도메인 속성의 형식을 기본 **문자열** 설정으로 그대로 둡니다.

4. 편집기를 테스트 하려면 사용자가 파일 이름 편집기를 열어서 도메인 속성을 편집할 수 있는지 확인 합니다.

    1. CTRL + F5 또는 F5 키를 누릅니다. 디버깅 솔루션에서 테스트 파일을 엽니다. 도메인 클래스의 요소를 만들고 선택 합니다.

    2. 속성 창에서 도메인 속성을 선택 합니다. 값 필드에는 줄임표 **[...]** 가 표시 됩니다.

    3. 줄임표를 클릭 합니다. 파일 대화 상자가 나타납니다. 파일을 선택 하 고 대화 상자를 닫습니다. 이제 파일 경로는 도메인 속성의 값입니다.

### <a name="define-your-own-property-editor"></a>고유한 속성 편집기 정의

사용자 고유의 편집기를 정의할 수 있습니다. 이렇게 하면 사용자가 정의한 형식을 편집 하거나 특수 한 방법으로 표준 형식을 편집할 수 있습니다. 예를 들어 사용자가 수식을 나타내는 문자열을 입력 하도록 허용할 수 있습니다.

에서 파생 되는 클래스를 작성 하 여 편집기를 정의 <xref:System.Drawing.Design.UITypeEditor> 합니다. 클래스는를 재정의 해야 합니다.

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>-사용자와 상호 작용 하 고 속성 값을 업데이트 합니다.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>-편집기에서 대화 상자를 열지 또는 드롭다운 메뉴를 제공할지 여부를 지정 합니다.

속성 표에 표시 되는 속성 값에 대 한 그래픽 표현을 제공할 수도 있습니다. 이렇게 하려면 `GetPaintValueSupported` , 및를 재정의 `PaintValue` 합니다.  자세한 내용은 <xref:System.Drawing.Design.UITypeEditor>를 참조하세요.

> [!NOTE]
> **Dsl** 프로젝트에서 별도의 코드 파일에 코드를 추가 합니다.

예를 들면 다음과 같습니다.

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

이 편집기를 사용 하려면 도메인 속성의 **사용자 지정 특성** 을 다음과 같이 설정 합니다.

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

자세한 내용은 <xref:System.Drawing.Design.UITypeEditor>를 참조하세요.

## <a name="provide-a-drop-down-list-of-values"></a>값의 드롭다운 목록 제공

사용자가 선택할 수 있는 값 목록을 제공할 수 있습니다.

> [!NOTE]
> 이 기법은 런타임에 변경 될 수 있는 값의 목록을 제공 합니다. 변경 되지 않는 목록을 제공 하려는 경우 열거 형식을 도메인 속성의 형식으로 대신 사용 하는 것이 좋습니다.

표준 값 목록을 정의 하려면 다음 형식의 CLR 특성을 도메인 속성에 추가 합니다.

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

<xref:System.ComponentModel.TypeConverter>에서 파생된 클래스를 정의합니다. **Dsl** 프로젝트에서 별도의 파일에 코드를 추가 합니다. 예를 들면 다음과 같습니다.

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>참조

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
