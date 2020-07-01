---
title: 속성 창 사용자 지정
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4dac40177c3df2a346039a08cf557b6083ed9fc2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548280"
---
# <a name="customize-the-properties-window"></a>속성 창 사용자 지정

Visual Studio에서 DSL (도메인별 언어)의 속성 창 모양 및 동작을 사용자 지정할 수 있습니다. DSL 정의에서 각 도메인 클래스에 대해 도메인 속성을 정의 합니다. 기본적으로 다이어그램 또는 모델 탐색기에서 클래스의 인스턴스를 선택 하면 속성 창에 모든 도메인 속성이 나열 됩니다. 이렇게 하면 다이어그램의 셰이프 필드에 매핑되지 않은 경우에도 도메인 속성의 값을 보고 편집할 수 있습니다.

## <a name="names-descriptions-and-categories"></a>이름, 설명 및 범주

**이름 및 표시 이름**입니다. 도메인 속성의 정의에서 속성의 표시 이름은 런타임에 속성 창에 표시 되는 이름입니다. 이와 대조적으로이 이름은 프로그램 코드를 작성 하 여 속성을 업데이트할 때 사용 됩니다. 이름은 올바른 CLR 영숫자 이름 이어야 하지만 표시 이름에는 공백을 포함할 수 있습니다.

DSL 정의에서 속성의 이름을 설정 하면 해당 표시 이름이 이름 복사본으로 자동 설정 됩니다. "FuelGauge"과 같은 파스칼식 대/소문자 이름을 작성 하면 표시 이름에 "연료 계기" 라는 공백이 자동으로 포함 됩니다. 그러나 표시 이름을 명시적으로 다른 값으로 설정할 수 있습니다.

**설명**. 도메인 속성에 대 한 설명은 다음 두 위치에 표시 됩니다.

- 속성 창 맨 아래에서 사용자가 속성을 선택 합니다. 이를 사용 하 여 속성이 나타내는 사용자를 설명할 수 있습니다.

- 생성 된 프로그램 코드입니다. 문서 기능을 사용 하 여 API 설명서를 추출 하는 경우 API에서이 속성에 대 한 설명으로 표시 됩니다.

**범주**. 범주는 속성 창의 제목입니다.

## <a name="expose-style-features"></a>스타일 기능 노출

그래픽 요소의 동적 기능 중 일부는 도메인 *속성으로 표시 하거나 표시할 수* 있습니다. 이러한 방식으로 노출 된 기능은 사용자가 업데이트할 수 있으며 프로그램 코드를 사용 하 여 보다 쉽게 업데이트할 수 있습니다.

DSL 정의에서 shape 클래스를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 가리킨 다음 기능을 선택 합니다.

도형에서 **FillColor**, **OutlineColor**, **textcolor**, **OutlineDashStyle**, **OutlineThickness** 및 **FillGradientMode** 속성을 노출할 수 있습니다. 커넥터에서 **색** `,` **textcolor**, **일점 style**및 **두께** 속성을 노출할 수 있습니다. 다이어그램에서 **FillColor** 및 **textcolor** 속성을 노출할 수 있습니다.

## <a name="forwarding-display-properties-of-related-elements"></a>전달: 관련 된 요소의 속성을 표시 합니다.

DSL의 사용자가 모델에서 요소를 선택 하면 해당 요소의 속성이 속성 창에 표시 됩니다. 그러나 지정 된 관련 요소의 속성을 표시할 수도 있습니다. 이는 함께 작동 하는 요소 그룹을 정의한 경우에 유용 합니다. 예를 들어 main 요소와 선택적 플러그 인 요소를 정의할 수 있습니다. Main 요소가 셰이프에 매핑되고 다른 요소가이 아닌 경우 모든 속성을 한 요소에 있는 것 처럼 표시 하는 것이 유용 합니다.

이 효과는 명명 된 *속성 전달*이며, 여러 경우에 자동으로 발생 합니다. 다른 경우에는 도메인 유형 설명자를 정의 하 여 속성 전달을 달성할 수 있습니다.

### <a name="default-property-forwarding-cases"></a>기본 속성 전달 사례

사용자가 셰이프 또는 연결선 이나 탐색기에서 요소를 선택 하면 속성 창에 다음과 같은 속성이 표시 됩니다.

- 기본 클래스에 정의 된 요소를 포함 하 여 model 요소의 도메인 클래스에 정의 된 도메인 속성입니다. 단, 설정한 도메인 속성은로 **찾아볼** 수 있습니다 `False` .

- 복합성이 0 ..1 인 관계를 통해 연결 된 요소의 이름입니다. 이렇게 하면 관계에 대 한 커넥터 매핑을 정의 하지 않은 경우에도 선택적으로 연결 된 요소를 볼 수 있는 편리한 방법이 제공 됩니다.

- 요소를 대상으로 하는 포함 관계의 도메인 속성입니다. 포함 관계는 일반적으로 명시적으로 표시 되지 않으므로 사용자가 해당 속성을 볼 수 있습니다.

- 선택한 셰이프 또는 연결선에 정의 된 도메인 속성입니다.

### <a name="add-property-forwarding"></a>속성 전달 추가

속성을 전달 하려면 도메인 유형 설명자를 정의 합니다. 두 도메인 클래스 간에 도메인 관계가 있는 경우 도메인 유형 설명자를 사용 하 여 첫 번째 클래스의 도메인 속성을 두 번째 도메인 클래스의 도메인 속성 값으로 설정할 수 있습니다. 예를 들어 **book** 도메인 클래스와 **Author** 도메인 클래스 간에 관계가 있는 경우 도메인 유형 설명자를 사용 하 여 사용자가 책을 선택할 때 책 **작성자** 의 **이름** 속성이 속성 창에 표시 되도록 할 수 있습니다.

> [!NOTE]
> 속성 전달은 사용자가 모델을 편집할 때 속성 창에만 영향을 줍니다. 수신 클래스의 도메인 속성을 정의 하지 않습니다. DSL 정의의 다른 부분이 나 프로그램 코드에서 전달 된 도메인 속성에 액세스 하려면 전달 요소에 액세스 해야 합니다.

다음 절차에서는 DSL을 만들었다고 가정 합니다. 처음 몇 단계에서는 필수 구성 요소를 요약 합니다.

#### <a name="forward-a-property-from-another-element"></a>다른 요소에서 속성 전달

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]두 개 이상의 클래스를 포함 하는 솔루션을 만듭니다 .이 예제에서는이를 **Book** 및 **Author**라고 합니다. **Book** 과 **Author**사이에는 두 종류의 관계가 있어야 합니다.

    원본 역할의 복합성 ( **북** 측의 역할)은 0 ..1 또는 1 ..1 이어야 하므로 각 **책** 에 하나의 **저자가**있습니다.

2. **DSL 탐색기**에서 **Book** 도메인 클래스를 마우스 오른쪽 단추로 클릭 한 다음 **새 DomainTypeDescriptor 추가**를 클릭 합니다.

    사용자 지정 **속성 설명자의** 명명 된 경로 노드가 **사용자 지정 형식 설명자** 노드 아래에 나타납니다.

3. **사용자 지정 형식 설명자** 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 PropertyPath 추가**를 클릭 합니다.

    새 속성 경로가 **사용자 지정 속성 설명자 노드의 경로** 아래에 나타납니다.

4. 새 속성 경로를 선택 하 고 **속성** 창에서 **경로 속성** 을 적절 한 모델 요소의 경로로 설정 합니다.

    이 속성의 오른쪽에 있는 아래쪽 화살표를 클릭 하 여 트리 뷰에서 경로를 편집할 수 있습니다. 도메인 경로에 대 한 자세한 내용은 [도메인 경로 구문](../modeling/domain-path-syntax.md)을 참조 하세요. 이 파일을 편집한 후에는 경로가 **BookReferencesAuthor/!와 비슷해야 합니다. 작성자**.

5. **속성** 을 **Author**의 **이름** 도메인 속성으로 설정 합니다.

6. **표시 이름을** **작성자 이름**으로 설정 합니다.

7. 모든 템플릿을 변환 하 고 DSL을 빌드하고 실행 합니다.

8. 모델 다이어그램에서 책, 저자를 만들고 참조 관계를 사용 하 여 연결 합니다. Book 요소를 선택 하 고 속성 창에서 책의 속성 외에도 작성자 이름이 표시 되어야 합니다. 연결 된 만든이의 이름을 변경 하거나 책을 다른 작성자에 연결 하 고, 책의 작성자 이름이 변경 되는지 확인 합니다.

## <a name="custom-property-editors"></a>사용자 지정 속성 편집기

속성 창은 각 도메인 속성의 형식에 대 한 적절 한 기본 편집 환경을 제공 합니다. 예를 들어, 열거 형식의 경우 사용자에 게 드롭다운 목록이 표시 되 고 숫자 속성의 경우 사용자가 숫자를 입력할 수 있습니다. 이는 기본 제공 형식에 대해서만 적용 됩니다. 외부 형식을 지정 하는 경우 사용자는 속성의 값을 볼 수 있지만 편집할 수는 없습니다.

그러나 다음 편집기와 형식을 지정할 수 있습니다.

1. 표준 형식과 함께 사용 되는 다른 편집기입니다. 예를 들어 문자열 속성에 대 한 파일 경로 편집기를 지정할 수 있습니다.

2. 도메인 속성의 외부 형식 및 해당 속성에 대 한 편집기입니다.

3. 파일 경로 편집기와 같은 .NET 편집기를 사용할 수도 있고 사용자 지정 속성 편집기를 직접 만들 수도 있습니다.

   외부 형식과 기본 편집기를 포함 하는 문자열과 같은 형식 간의 변환입니다.

   DSL에서 *외부 형식은* 단순 형식 (예: 부울 또는 Int32) 또는 문자열 중 하나가 아닌 형식입니다.

### <a name="define-a-domain-property-that-has-an-external-type"></a>외부 형식을 포함 하는 도메인 속성 정의

1. **솔루션 탐색기**에서 외부 형식이 포함 된 어셈블리 (DLL)에 대 한 참조를 **Dsl** 프로젝트에 추가 합니다.

    어셈블리는 .NET 어셈블리 이거나 사용자가 제공 하는 어셈블리 일 수 있습니다.

2. 아직 수행 하지 않은 경우 형식을 **도메인 유형** 목록에 추가 합니다.

   1. DslDefinition. dsl을 열고 **Dsl 탐색기**에서 루트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 외부 형식 추가**를 클릭 합니다.

        **도메인 유형** 노드 아래에 새 항목이 나타납니다.

       > [!WARNING]
       > 메뉴 항목은 **도메인 유형** 노드가 아닌 DSL 루트 노드에 있습니다.

   2. 속성 창에서 새 형식의 이름 및 네임 스페이스를 설정 합니다.

3. 일반적인 방법으로 도메인 클래스에 도메인 속성을 추가 합니다.

    속성 창의 **유형** 필드에 있는 드롭다운 목록에서 외부 유형을 선택 합니다.

   이 단계에서 사용자는 속성의 값을 볼 수 있지만 편집할 수는 없습니다. 표시 된 값은 함수에서 가져옵니다 `ToString()` . 예를 들어 명령 또는 규칙에서 속성의 값을 설정 하는 프로그램 코드를 작성할 수 있습니다.

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

3. 도메인 속성의 형식을 기본 **문자열**설정으로 그대로 둡니다.

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

<xref:System.ComponentModel.TypeConverter>에서 파생된 클래스를 정의합니다. **Dsl** 프로젝트에서 별도의 파일에 코드를 추가 합니다. 예를 들어:

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

## <a name="see-also"></a>참고 항목

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
