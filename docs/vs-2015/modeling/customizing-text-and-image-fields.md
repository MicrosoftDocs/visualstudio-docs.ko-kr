---
title: 텍스트 및 이미지 필드 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6baaa9ceba8f40aa5ad7888384027131e0ffe94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654977"
---
# <a name="customizing-text-and-image-fields"></a>텍스트 및 이미지 필드 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도형에서 텍스트 데코레이터를 정의할 때 텍스트 데코레이터는 TextField로 표시 됩니다. TextFields 및 기타 ShapeFields를 초기화 하는 예는 DSL 솔루션에서 Dsl\GeneratedCode\Shapes.cs를 검사 합니다.

 TextField는 레이블에 할당 된 공백과 같이 셰이프 내의 영역을 관리 하는 개체입니다. 하나의 TextField 인스턴스는 동일한 클래스의 여러 셰이프 간에 공유 됩니다. TextField 인스턴스는 각 인스턴스에 대해 레이블 텍스트를 개별적으로 저장 하지 않습니다. 대신 `GetDisplayText(ShapeElement)` 메서드는 셰이프를 매개 변수로 사용 하 고 셰이프 및 해당 모델 요소의 현재 상태에 따라 텍스트를 조회할 수 있습니다.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>텍스트 필드의 모양을 결정 하는 방법
 `DoPaint()`메서드를 호출 하 여 화면에 필드를 표시 합니다. 기본를 재정의 `DoPaint(),` 하거나 호출 하는 메서드 중 일부를 재정의할 수 있습니다. 기본 메서드의 다음 단순화 된 버전은 기본 동작을 재정의 하는 방법을 이해 하는 데 도움이 될 수 있습니다.

```
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape’s styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application’s styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape’s styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application’s styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 과 같은 여러 가지 메서드와 속성 쌍이 있습니다 `Get` `Default` `DefaultMultipleLine/GetMultipleLine()` . 기본 속성에 값을 할당 하 여 셰이프 필드의 모든 인스턴스에 대 한 값을 변경할 수 있습니다. 셰이프 인스턴스 간에 값이 다르게 하거나 모양이 나 해당 모델 요소의 상태에 따라 달라 지도록 하려면 메서드를 재정의 합니다 `Get` .

## <a name="static-customizations"></a>정적 사용자 지정
 이 셰이프 필드의 모든 인스턴스를 변경 하려면 먼저 DSL 정의에서 속성을 설정할 수 있는지 여부를 확인 합니다. 예를 들어 속성 창에서 글꼴 크기와 스타일을 설정할 수 있습니다.

 그렇지 않은 경우에는 `InitializeShapeFields` shape 클래스의 메서드를 재정의 하 고 텍스트 필드의 해당 속성에 값을 할당 `Default...` 합니다.

> [!WARNING]
> 을 재정의 하려면 `InitializeShapeFields()` DSL 정의에서 shape 클래스의 **Double 파생 클래스 생성** 속성을로 설정 해야 합니다 `true` .

 이 예에서는 셰이프에 사용자 주석에 사용 되는 텍스트 필드가 있습니다. 표준 주석 글꼴을 사용 하려고 합니다. 스타일 집합의 표준 글꼴 이기 때문에 기본 글꼴 id를 설정할 수 있습니다.

```

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;

```

## <a name="dynamic-customizations"></a>동적 사용자 지정
 모양이 셰이프나 모델 요소의 상태에 따라 달라 지 게 하려면의 고유한 서브 클래스를 파생 하 `TextField` 고 하나 이상의 메서드를 재정의 `Get...` 합니다. 또한 셰이프의 InitializeShapeFields 메서드를 재정의 하 고 TextField의 인스턴스를 고유한 클래스의 인스턴스로 바꾸어야 합니다.

 다음 예에서는 텍스트 필드의 글꼴을 셰이프의 모델 요소에 대 한 부울 도메인 속성의 상태에 따라 결정 합니다.

 이 예제 코드를 실행 하려면 최소 언어 템플릿을 사용 하 여 새 DSL 솔루션을 만듭니다. ExampleElement 도메인 클래스에 부울 도메인 속성을 추가 `AlternateState` 합니다. ExampleShape 클래스에 아이콘 데코레이터를 추가 하 고 해당 이미지를 비트맵 파일로 설정 합니다. **모든 템플릿 변환**을 클릭 합니다. DSL 프로젝트에 새 코드 파일을 추가 하 고 다음 코드를 삽입 합니다.

 코드를 테스트 하려면 F5 키를 누르고 디버깅 솔루션에서 샘플 다이어그램을 엽니다. 아이콘의 기본 상태가 표시 되어야 합니다. 셰이프를 선택 하 고 속성 창 **AlternateState** 속성의 값을 변경 합니다. 요소 이름의 글꼴이 변경 되어야 합니다.

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }

```

## <a name="style-sets"></a>스타일 집합
 앞의 예제에서는 텍스트 필드를 사용할 수 있는 글꼴로 변경 하는 방법을 보여 줍니다. 그러나이 방법은 셰이프 또는 응용 프로그램과 연결 된 스타일 집합 중 하나로 변경 하는 것이 좋습니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> 또는 GetTextBrushId ()를 재정의 합니다.

 또는를 재정의 하 여 모양의 스타일 집합을 변경 하는 것이 좋습니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . 이 경우 모든 셰이프 필드의 글꼴과 브러시를 변경 하는 효과가 있습니다.

## <a name="customizing-image-fields"></a>이미지 필드 사용자 지정
 모양에서 이미지 데코레이터를 정의 하 고 이미지 셰이프를 정의 하는 경우 모양이 표시 되는 영역이 ImageField에서 관리 됩니다. ImageFields 및 기타 ShapeFields를 초기화 하는 예는 DSL 솔루션에서 Dsl\GeneratedCode\Shapes.cs를 검사 합니다.

 ImageField는 데코레이터에 할당 된 공간과 같이 셰이프 내의 영역을 관리 하는 개체입니다. 하나의 ImageField 인스턴스는 동일한 shape 클래스의 여러 셰이프 간에 공유 됩니다. ImageField 인스턴스는 각 셰이프에 대해 별도의 이미지를 저장 하지 않습니다. 대신 `GetDisplayImage(ShapeElement)` 메서드는 셰이프를 매개 변수로 사용 하 고 셰이프 및 해당 모델 요소의 현재 상태에 따라 이미지를 조회할 수 있습니다.

 변수 이미지와 같은 특수 한 동작을 원하는 경우 ImageField에서 파생 된 고유한 클래스를 만들 수 있습니다.

#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField의 하위 클래스를 만들려면

1. DSL 정의에서 부모 shape 클래스의 **생성 된 이중 파생** 속성을 설정 합니다.

2. `InitializeShapeFields`Shape 클래스의 메서드를 재정의 합니다.

    - DSL 프로젝트에서 새 코드 파일을 만들고 shape 클래스에 대 한 partial 클래스 정의를 작성 합니다. 여기에서 메서드 정의를 재정의 합니다.

3. `InitializeShapeFields`Dsl\generatedcode\orcss의 코드를 검사 합니다.

     재정의 메서드에서 기본 메서드를 호출한 다음 고유한 이미지 필드 클래스의 인스턴스를 만듭니다. 이를 사용 하 여 목록의 일반 이미지 필드를 바꿉니다 `shapeFields` .

## <a name="dynamic-icons"></a>동적 아이콘
 이 예제에서는 셰이프의 모델 요소 상태에 따라 아이콘 변경을 수행 합니다.

> [!WARNING]
> 이 예제에서는 동적 이미지 데코레이터를 만드는 방법을 보여 줍니다. 그러나 모델 변수의 상태에 따라 하나 또는 두 개의 이미지만 전환 하려는 경우에는 여러 이미지 데코레이터을 만들고 모양의 동일한 위치에서 찾은 다음 표시 유형 필터를 모델 변수의 특정 값에 따라 다르게 설정 하는 것이 더 간단 합니다. 이 필터를 설정 하려면 DSL 정의에서 도형 맵을 선택 하 고 DSL 정보 창을 열고 데코레이터 탭을 클릭 합니다.

 이 예제 코드를 실행 하려면 최소 언어 템플릿을 사용 하 여 새 DSL 솔루션을 만듭니다. ExampleElement 도메인 클래스에 부울 도메인 속성을 추가 `AlternateState` 합니다. ExampleShape 클래스에 아이콘 데코레이터를 추가 하 고 해당 이미지를 비트맵 파일로 설정 합니다. **모든 템플릿 변환**을 클릭 합니다. DSL 프로젝트에 새 코드 파일을 추가 하 고 다음 코드를 삽입 합니다.

 코드를 테스트 하려면 F5 키를 누르고 디버깅 솔루션에서 샘플 다이어그램을 엽니다. 아이콘의 기본 상태가 표시 되어야 합니다. 셰이프를 선택 하 고 속성 창 **AlternateState** 속성의 값을 변경 합니다. 그러면 아이콘이 해당 모양에서 90도 회전 하 여 표시 됩니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}

```

## <a name="see-also"></a>관련 항목
 [모양 및 연결선 정의](../modeling/defining-shapes-and-connectors.md) [다이어그램에서 배경 이미지 설정](../modeling/setting-a-background-image-on-a-diagram.md) [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md) [코드 작성 코드를 작성 하 여 도메인별 언어를 지정](../modeling/writing-code-to-customise-a-domain-specific-language.md) 합니다.
