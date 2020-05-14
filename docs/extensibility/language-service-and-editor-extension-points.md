---
title: 언어 서비스 및 편집자 확장 포인트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703052"
---
# <a name="language-service-and-editor-extension-points"></a>언어 서비스 및 편집기 확장 지점
편집기는 대부분의 언어 서비스 기능을 포함하여 관리되는 확장성 프레임워크(MEF) 구성 요소 부분으로 확장할 수 있는 확장 지점을 제공합니다. 다음은 주요 확장 지점 범주입니다.

- 내용 유형

- 분류 유형 및 분류 형식

- 여백 및 스크롤 막대

- 태그들

- 장식

- 마우스 프로세서

- 드롭 핸들러

- 옵션

- IntelliSense

## <a name="extend-content-types"></a>콘텐츠 유형 확장
 콘텐츠 형식은 "텍스트", "코드" 또는 "CSharp"와 같은 편집기에서 처리하는 텍스트 종류에 대한 정의입니다. 형식의 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 변수를 선언하고 새 콘텐츠 형식에 고유한 이름을 지정하여 새 콘텐츠 형식을 정의합니다. 콘텐츠 형식을 편집기로 등록하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>은 콘텐츠 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>은 이 콘텐츠 형식이 파생되는 콘텐츠 형식의 이름입니다. 콘텐츠 형식은 다른 여러 콘텐츠 형식에서 상속될 수 있습니다.

  클래스가 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 봉인되어 있으므로 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예제에서는 콘텐츠 유형 정의에 대한 내보내기 특성을 보여 주며,

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 콘텐츠 형식은 기존 콘텐츠 유형이 0개 이상인 것을 기반으로 할 수 있습니다. 다음은 기본 제공 유형입니다.

- Any: 기본 콘텐츠 유형입니다. 다른 모든 콘텐츠 형식의 부모입니다.

- 텍스트: 투영되지 않은 콘텐츠의 기본 유형입니다. "any"에서 상속됩니다.

- 일반 텍스트: 코드가 아닌 텍스트의 경우. "텍스트"에서 상속합니다.

- 코드 : 모든 종류의 코드. "텍스트"에서 상속합니다.

- 불활성: 모든 종류의 처리에서 텍스트를 제외합니다. 이 콘텐츠 형식의 텍스트에는 확장이 적용되지 않습니다.

- 프로젝션: 프로젝션 버퍼의 내용입니다. "any"에서 상속됩니다.

- 인텔리센스: 인텔리센스의 내용. "텍스트"에서 상속합니다.

- 시그도움말: 서명 도움말. "인텔리센스"에서 상속됩니다.

- 시그헬프-문서: 서명 도움말 문서. "인텔리센스"에서 상속됩니다.

  다음은 Visual Studio에서 정의한 일부 콘텐츠 유형과 Visual Studio에서 호스팅되는 일부 언어입니다.

- Basic

- C/C++

- 콘솔 출력

- CSharp

- CSS

- Enc

- 결과 찾기

- F#

- HTML

- JScript

- XAML

- XML

  사용 가능한 콘텐츠 형식 목록을 검색하려면 편집기의 콘텐츠 형식 컬렉션을 유지 관리하는 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>을 가져옵니다. 다음 코드는 이 서비스를 속성으로 가져오게 합니다.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 콘텐츠 형식을 파일 이름 확장명과 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>연결하려면 을 사용합니다.

> [!NOTE]
> Visual Studio에서 파일 이름 확장자는 언어 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 서비스 패키지에서 를 사용하여 등록됩니다. MEF 콘텐츠 형식을 이러한 방식으로 등록된 파일 이름 확장명과 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 연결합니다.

 파일 이름 확장을 콘텐츠 유형 정의로 내보내려면 다음 특성을 포함해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: 파일 이름 확장명을 지정합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 콘텐츠 유형을 지정합니다.

  클래스가 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 봉인되어 있으므로 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예제에서는 파일 이름 확장자의 내보내기 특성을 콘텐츠 유형 정의에 대해 보여 주며,

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 는 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 파일 이름 확장자와 콘텐츠 형식 간의 연결을 관리합니다.

## <a name="extend-classification-types-and-classification-formats"></a>분류 유형 및 분류 형식 확장
 분류 유형을 사용하여 다른 처리를 제공할 텍스트 의 종류를 정의할 수 있습니다(예: "키워드" 텍스트 파란색과 "주석" 텍스트 녹색색). 형식의 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 변수를 선언하고 고유한 이름을 지정하여 새 분류 유형을 정의합니다.

 분류 유형을 편집기로 등록하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 분류 유형의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: 이 분류 유형이 상속되는 분류 유형의 이름입니다. 모든 분류 유형은 "text"에서 상속되며 분류 유형은 여러 다른 분류 유형에서 상속될 수 있습니다.

  클래스가 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 봉인되어 있으므로 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예제에서는 분류 유형 정의에 대한 내보내기 특성을 보여 주며 있습니다.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 표준 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 분류에 대한 액세스를 제공합니다. 기본 제공 분류 유형에는 다음이 포함됩니다.

- "text"

- "자연어"("텍스트"에서 파생)

- "형식언어"("텍스트"에서 파생)

- "문자열"("리터럴"에서 파생)

- "문자"("리터럴"에서 파생)

- "숫자"("리터럴"에서 파생)

  다른 오류 형식 집합은 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>에서 상속됩니다. 여기에는 다음과 같은 오류 유형이 포함됩니다.

- "구문 오류"

- "컴파일러 오류"

- "다른 오류"

- "경고"

  사용 가능한 분류 유형 목록을 검색하려면 편집기의 분류 유형 컬렉션을 유지 관리하는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>을 가져옵니다. 다음 코드는 이 서비스를 속성으로 가져오게 합니다.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 새 분류 유형에 대한 분류 형식 정의를 정의할 수 있습니다. 클래스를 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> 파생하고 다음 특성과 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>함께 형식과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 형식의 표시 이름입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: **옵션** 대화 상자의 **글꼴 및 색상** 페이지에 형식이 표시되는지 여부를 지정합니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 형식의 우선 순위입니다. 유효한 값은 <xref:Microsoft.VisualStudio.Text.Classification.Priority>에서 온 값입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: 이 형식이 매핑되는 분류 유형의 이름입니다.

  다음 예제에서는 분류 형식 정의에 대한 내보내기 특성을 보여 주며 있습니다.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 사용 가능한 형식 목록을 검색하려면 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>편집기의 형식 컬렉션을 유지 관리하는 을 가져옵니다. 다음 코드는 이 서비스를 속성으로 가져오게 합니다.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>여백 및 스크롤 막대 확장
 여백과 스크롤 막대는 텍스트 보기 자체 외에도 편집기의 기본 뷰 요소입니다. 텍스트 보기 주위에 나타나는 표준 여백 외에 원하는 수의 여백을 제공할 수 있습니다.

 여백을 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 정의하는 인터페이스를 구현합니다. 여백을 만들려면 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 인터페이스도 구현해야 합니다.

 여백 공급자를 편집기로 등록하려면 다음 특성과 함께 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 여백의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 여백을 기준으로 여백이 표시되는 순서입니다.

   다음은 기본 제공 여백입니다.

  - "Wpf 수평 스크롤 막대"

  - "Wpf 세로 스크롤 막대"

  - "Wpf 선 번호 여백"

    주문 특성이 있는 수평 `After="Wpf Horizontal Scrollbar"` 여백은 기본 제공 여백 아래에 표시되고, `Before ="Wpf Horizontal Scrollbar"` 주문 특성이 있는 수평 여백은 기본 제공 여백 위에 표시됩니다. 순서 특성이 있는 오른쪽 `After="Wpf Vertical Scrollbar"` 세로 여백이 스크롤 막대의 오른쪽에 표시됩니다. 순서 특성이 있는 왼쪽 `After="Wpf Line Number Margin"` 수직 여백이 줄 번호 여백의 왼쪽에 표시됩니다(표시되는 경우).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 여백의 종류(왼쪽, 오른쪽, 위쪽 또는 아래쪽)입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 여백이 유효한 콘텐츠(예: "텍스트" 또는 "코드")의 종류입니다.

  다음 예제에서는 선 번호 여백의 오른쪽에 나타나는 여백에 대한 여백 공급자의 내보내기 특성을 보여 주습니다.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>태그 확장
 태그는 데이터를 다른 종류의 텍스트와 연결하는 방법입니다. 대부분의 경우 연관된 데이터가 시각적 효과로 표시되지만 모든 태그에 시각적 표시가 있는 것은 아닙니다. 을 구현하여 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>고유한 태그 종류를 정의할 수 있습니다. 또한 지정된 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 텍스트 범위 집합에 대한 태그를 제공하고 태거를 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 제공하기 위해 구현해야 합니다. 다음 특성과 함께 태거 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 태그가 유효한 콘텐츠(예: "텍스트" 또는 "코드")의 종류입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 태그의 종류.

  다음 예제에서는 태거 공급자에 대한 내보내기 특성을 보여 주습니다.

\<코드콘텐츠플레이스 홀더</CodeContentPlaceHolder>>8 태그의 종류는 기본 제공:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>에 연결됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: 오류 유형과 연관된 것입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: 장식과 관련이 있습니다.

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>의 예는 [연습: 텍스트 강조 표시에서](../extensibility/walkthrough-highlighting-text.md)강조 표시 WordTag 정의를 참조하세요.

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: 개요에서 확장되거나 축소될 수 있는 영역과 연결됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: 텍스트 뷰에서 장식이 차지하는 공간을 정의합니다. 공간 협상 장식품에 대한 자세한 내용은 다음 섹션을 참조하십시오.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 장식에 대한 자동 간격 및 크기 조정을 제공합니다.

  버퍼 및 뷰에 대한 태그를 찾아 사용하려면 <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>요청된 형식을 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 제공하는 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> 또는 을 가져옵니다. 다음 코드는 이 서비스를 속성으로 가져오게 합니다.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>태그 및 마커 형식정의
 클래스를 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 확장하여 태그의 모양을 정의할 수 있습니다. 클래스를 다음과 같은 특성으로 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 이 형식을 참조하는 데 사용되는 이름

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: 이렇게 하면 UI에 형식이 나타납니다.

  생성자에서 태그의 표시 이름과 모양을 정의합니다. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>은 채우기 색상을 정의하고 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 테두리 색상을 정의합니다. 은 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 형식 정의의 지역화 가능한 이름입니다.

  다음은 형식 정의의 예입니다.

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 태그에 이 형식 정의를 적용하려면 클래스의 이름 특성에 설정한 이름을 참조합니다(표시 이름이 아님).

> [!NOTE]
> 의 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>예를 들어 연습에서 강조 표시 WordFormatDefinition [클래스를 참조: 텍스트 강조 표시.](../extensibility/walkthrough-highlighting-text.md)

## <a name="extend-adornments"></a>장식 확장
 장식은 텍스트 뷰또는 텍스트 뷰 자체에 표시되는 텍스트에 추가할 수 있는 시각적 효과를 정의합니다. 사용자 고유의 장식을 모든 유형의 <xref:System.Windows.UIElement>로 정의할 수 있습니다.

 장식 클래스에서 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>를 선언해야 합니다. 장식 레이어를 등록하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 장식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 장식 레이어에 대한 장식의 순서. 클래스는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 선택, 개요, 카를트 및 텍스트의 네 가지 기본 레이어를 정의합니다.

  다음 예제에서는 장식 레이어 정의에 대한 내보내기 특성을 보여 주십니다.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 장식을 인스턴스화하여 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 해당 이벤트를 구현하고 처리하는 두 번째 클래스를 만들어야 합니다. 다음 특성과 함께 이 클래스를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 장식이 유효한 콘텐츠 의 종류(예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 이 장식이 유효한 텍스트 보기의 종류입니다. 클래스에는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 미리 정의된 텍스트 보기 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 주로 파일의 텍스트 보기에 사용됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>은 사용자가 마우스와 키보드를 사용하여 편집하거나 탐색할 수 있는 텍스트 보기에 사용됩니다. 뷰의 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 예로는 편집기 텍스트 뷰와 **출력** 창이 있습니다.

  다음 예제에서는 장식 공급자에 내보내기 특성을 보여 주십니다.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 공간 협상 장식은 텍스트와 동일한 수준에서 공간을 차지하는 장식입니다. 이러한 종류의 장식을 만들려면 장식이 차지하는 공간의 양을 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>정의하는 에서 상속하는 태그 클래스를 정의해야 합니다.

 모든 장식과 마찬가지로 장식 도면층 정의를 내보내야 합니다.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 공간 협상 장식을 인스턴스화하려면 다른 종류의 장식과 마찬가지로 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>구현하는 클래스 외에 구현하는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 클래스를 만들어야 합니다.

 태거 공급자를 등록하려면 다음 특성과 함께 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 장식이 유효한 콘텐츠(예: "텍스트" 또는 "코드")의 종류입니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 이 태그 또는 장식이 유효한 텍스트 보기의 종류입니다. 클래스에는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 미리 정의된 텍스트 보기 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 주로 파일의 텍스트 보기에 사용됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>은 사용자가 마우스와 키보드를 사용하여 편집하거나 탐색할 수 있는 텍스트 보기에 사용됩니다. 뷰의 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 예로는 편집기 텍스트 뷰와 **출력** 창이 있습니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 정의한 태그 또는 장식의 종류입니다. 에 대해 두 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>번째 를 추가해야 합니다.

  다음 예제에서는 공간 협상 장식 태그에 대 한 태거 공급자에 내보내기 특성을 보여 주면됩니다.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>마우스 프로세서 확장
 마우스 입력에 대한 특수 처리를 추가할 수 있습니다. 처리하려는 입력에 대해 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 마우스 이벤트를 상속하고 재정의하는 클래스를 만듭니다. 또한 두 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 번째 클래스에서 구현하고 마우스 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 처리기가 유효한 콘텐츠 종류(예: "텍스트" 또는 "코드")를 지정하는 것과 함께 내보내야 합니다.

 다음 예제에서는 마우스 프로세서 공급자의 내보내기 특성을 보여 주며 있습니다.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>드롭 핸들러 확장
 드롭 처리기를 만드는 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> 클래스와 드롭 처리기를 만드는 두 번째 클래스를 만들어 특정 텍스트 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 종류에 맞게 드롭 처리기의 동작을 사용자 지정할 수 있습니다. 다음 특성과 함께 드롭 처리기를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: 이 드롭 처리기가 유효한 텍스트 형식입니다. 다음 형식은 가장 높은 형식에서 가장 낮은 순서로 처리됩니다.

  1. 모든 사용자 지정 형식

  2. Filedrop

  3. 향상된 메타파일

  4. 웨이브 오디오

  5. 리프

  6. Dif

  7. Locale

  8. 색상표

  9. 펜 데이터

  10. 직렬화 가능

  11. 기호링크

  12. Xaml

  13. 자믈 패키지

  14. Tiff

  15. Bitmap

  16. Dib

  17. 메타파일사진

  18. CSV

  19. System.String

  20. HTML 형식

  21. 유니코드 텍스트

  22. OEM텍스트

  23. 텍스트

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 드롭 처리기의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 기본 드롭 처리기 앞또는 이후에 놓기 처리기의 순서입니다. Visual Studio의 기본 드롭 처리기는 "DefaultFileDropHandler"라는 이름으로 지정됩니다.

  다음 예제에서는 드롭 처리기 공급자에 내보내기 특성을 보여 주다.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>편집기 옵션 확장
 예를 들어 텍스트 보기에서 특정 범위에서만 유효한 옵션을 정의할 수 있습니다. 편집기는 편집기 옵션, 보기 옵션 및 WPF(Windows 프레젠테이션 Foundation) 보기 옵션과 같은 미리 정의된 옵션 집합을 제공합니다. 이러한 옵션은 에서 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>찾을 <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>수 <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>있습니다.

 새 옵션을 추가하려면 다음 옵션 정의 클래스 중 하나에서 클래스를 파생합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  다음 예제에서는 부울 값이 있는 옵션 정의를 내보내는 방법을 보여 주며 있습니다.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>인텔리센스 확장
 IntelliSense는 구조화 된 텍스트및 명령문 완성에 대한 정보를 제공하는 기능 그룹에 대한 일반적인 용어입니다. 이러한 기능에는 명령문 완성, 서명 도움말, 빠른 정보 및 전구가 포함됩니다. 명령문 완성을 사용하면 사용자가 언어 키워드 또는 구성원 이름을 올바르게 입력할 수 있습니다. 서명 도움말은 사용자가 방금 입력한 메서드의 서명 또는 서명을 표시합니다. 빠른 정보는 마우스가 마우스위에 놓일 때 유형 또는 멤버 이름에 대한 완전한 서명을 표시합니다. 전구는 특정 컨텍스트에서 특정 식별자에 대한 추가 작업을 제공합니다(예: 한 번의 발생 의 이름을 바꾼 후 변수의 모든 발생 이름을 바꾸는 경우).

 IntelliSense 기능의 디자인은 모든 경우에 거의 동일합니다.

- IntelliSense *브로커는* 전체 프로세스를 담당합니다.

- IntelliSense *세션은* 발표자 트리거링과 선택 영역의 커밋 또는 취소 사이의 이벤트 시퀀스를 나타냅니다. 세션은 일반적으로 일부 사용자 제스처에 의해 트리거됩니다.

- IntelliSense *컨트롤러는* 세션을 시작하고 종료해야 하는 시기를 결정할 책임이 있습니다. 또한 정보를 커밋할 시기와 세션을 취소해야 하는 시기도 결정합니다.

- IntelliSense *소스는* 콘텐츠를 제공하고 가장 일치하는 것을 결정합니다.

- IntelliSense *발표자는* 콘텐츠를 표시할 책임이 있습니다.

  대부분의 경우 최소한 소스와 컨트롤러를 제공하는 것이 좋습니다. 디스플레이를 사용자 지정하려는 경우 발표자를 제공할 수도 있습니다.

### <a name="implement-an-intellisense-source"></a>인텔리센스 소스 구현
 원본을 사용자 지정하려면 다음 소스 인터페이스 중 하나 이상을 구현해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>을 위해 더 이상 사용되지 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>않습니다.

 또한 동일한 종류의 공급자를 구현해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>을 위해 더 이상 사용되지 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>않습니다.

 공급자를 다음 특성과 함께 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 소스의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 소스가 적용되는 콘텐츠 의 종류(예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 소스와 관련하여 소스가 표시되어야 하는 순서입니다.

- 다음 예제에서는 완료 원본 공급자에 대한 내보내기 특성을 보여 주습니다.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense 소스 구현에 대한 자세한 내용은 다음 연습을 참조하십시오.

- [연습: 빠른 정보 표시 도구 설명](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)

- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>인텔리센스 컨트롤러 구현
 컨트롤러를 사용자 지정하려면 인터페이스를 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 구현해야 합니다. 또한 다음 특성과 함께 컨트롤러 공급자를 구현해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 컨트롤러의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 컨트롤러가 적용되는 콘텐츠 의 종류(예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 컨트롤러와 관련하여 컨트롤러가 표시되어야 하는 순서입니다.

  다음 예제에서는 완료 컨트롤러 공급자에 대한 내보내기 특성을 보여 주습니다.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense 컨트롤러 사용에 대한 자세한 내용은 다음 연습을 참조하십시오.

- [연습: 빠른 정보 표시 도구 설명](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
