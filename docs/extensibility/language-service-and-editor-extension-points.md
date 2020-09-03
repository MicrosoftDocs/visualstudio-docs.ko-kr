---
title: 언어 서비스 및 편집기 확장 위치 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703052"
---
# <a name="language-service-and-editor-extension-points"></a>언어 서비스 및 편집기 확장 위치
편집기는 대부분의 언어 서비스 기능을 포함 하 여 Managed Extensibility Framework (MEF) 구성 요소 부분으로 확장할 수 있는 확장 위치를 제공 합니다. 기본 확장 지점 범주는 다음과 같습니다.

- 내용 유형

- 분류 유형 및 분류 형식

- 여백 및 스크롤 막대

- 태그들

- 도구 영역

- 마우스 프로세서

- Drop 처리기

- 옵션

- IntelliSense

## <a name="extend-content-types"></a>콘텐츠 형식 확장
 내용 유형은 편집기에서 처리 하는 텍스트 종류 (예: "text", "code" 또는 "CSharp")의 정의입니다. 형식의 변수를 선언 하 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 고 새 콘텐츠 형식에 고유한 이름을 지정 하 여 새 콘텐츠 형식을 정의 합니다. 내용 유형을 편집기에 등록 하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 콘텐츠 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 이 콘텐츠 형식이 파생 되는 콘텐츠 형식의 이름입니다. 콘텐츠 형식은 다른 여러 콘텐츠 형식에서 상속할 수 있습니다.

  <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>클래스가 봉인 되어 있기 때문에 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예제에서는 내용 유형 정의의 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 콘텐츠 형식은 0 개 이상의 기존 콘텐츠 형식을 기반으로 할 수 있습니다. 기본 제공 되는 형식은 다음과 같습니다.

- Any: 기본 콘텐츠 형식입니다. 다른 모든 콘텐츠 형식의 부모입니다.

- Text: 비 프로젝션 콘텐츠의 기본 형식입니다. "Any"에서 상속 됩니다.

- 일반 텍스트: 비 코드 텍스트 "Text"에서 상속 됩니다.

- Code: 모든 종류의 코드를 위한 것입니다. "Text"에서 상속 됩니다.

- 버려지는 단순한: 모든 종류의 처리에서 텍스트를 제외 합니다. 이 콘텐츠 형식의 텍스트에는 적용 된 확장이 없습니다.

- 프로젝션: 프로젝션 버퍼의 내용입니다. "Any"에서 상속 됩니다.

- Intellisense: IntelliSense의 내용입니다. "Text"에서 상속 됩니다.

- Sighelp: 시그니처 도움말입니다. "Intellisense"에서 상속 됩니다.

- Sighelp: 서명 도움말 설명서입니다. "Intellisense"에서 상속 됩니다.

  다음은 visual Studio에 정의 된 콘텐츠 형식과 Visual Studio에서 호스팅되는 일부 언어입니다.

- Basic

- C/C++

- Consoletomsbuild

- CSharp

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  사용 가능한 내용 유형 목록을 검색 하려면 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> 편집기에 대 한 내용 유형 컬렉션을 유지 관리 하는를 가져옵니다. 다음 코드에서는이 서비스를 속성으로 가져옵니다.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 콘텐츠 형식을 파일 이름 확장명과 연결 하려면를 사용 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 합니다.

> [!NOTE]
> Visual Studio에서 파일 이름 확장명은 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 언어 서비스 패키지에서를 사용 하 여 등록 됩니다. 는 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 이 방식으로 등록 된 파일 이름 확장명에 MEF 콘텐츠 형식을 연결 합니다.

 파일 이름 확장명을 콘텐츠 형식 정의로 내보내려면 다음 특성을 포함 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: 파일 이름 확장명을 지정 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 내용 유형을 지정 합니다.

  <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>클래스가 봉인 되어 있기 때문에 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예제에서는 파일 이름 확장명의 특성을 내용 유형 정의로 내보내기 하는 방법을 보여 줍니다.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 는 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 파일 이름 확장명과 콘텐츠 형식 간의 연결을 관리 합니다.

## <a name="extend-classification-types-and-classification-formats"></a>분류 유형 및 분류 형식 확장
 분류 유형을 사용 하 여 다른 처리를 제공 하려는 텍스트의 종류를 정의할 수 있습니다. 예를 들어 "키워드" 텍스트 blue와 "comment" 텍스트는 녹색으로 표시 됩니다. 유형의 변수를 선언 하 고 고유한 이름을 지정 하 여 새 분류 유형을 정의 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 합니다.

 분류 유형을 편집기에 등록 하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 분류 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>:이 분류 형식이 상속 되는 분류 형식의 이름입니다. 모든 분류 형식은 "텍스트"에서 상속 되며 분류 형식은 여러 다른 분류 형식에서 상속할 수 있습니다.

  <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>클래스가 봉인 되어 있기 때문에 형식 매개 변수 없이 내보낼 수 있습니다.

  다음 예에서는 분류 유형 정의의 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 는 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 표준 분류에 대 한 액세스를 제공 합니다. 기본 제공 분류 유형에는 다음이 포함 됩니다.

- "text"

- "자연어" ("텍스트"에서 파생 됨)

- "형식 언어" ("text"에서 파생 됨)

- "string" ("literal"에서 파생 됨)

- "character" ("literal"에서 파생 됨)

- "숫자" ("literal"에서 파생 됨)

  다른 오류 유형 집합은에서 상속 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> 됩니다. 여기에는 다음과 같은 오류 유형이 포함 됩니다.

- "구문 오류"

- "컴파일러 오류"

- "기타 오류"

- 내용의

  사용 가능한 분류 유형 목록을 검색 하려면 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 편집기에 대 한 분류 유형 컬렉션을 유지 관리 하는를 가져옵니다. 다음 코드에서는이 서비스를 속성으로 가져옵니다.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 새 분류 형식에 대 한 분류 형식 정의를 정의할 수 있습니다. 에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> 형식과 함께 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 형식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: 형식의 표시 이름입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: **옵션** 대화 상자의 **글꼴 및 색** 페이지에 서식이 표시 되는지 여부를 지정 합니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 형식의 우선 순위입니다. 유효한 값은 <xref:Microsoft.VisualStudio.Text.Classification.Priority> 입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>:이 형식이 매핑되는 분류 형식의 이름입니다.

  다음 예에서는 분류 형식 정의의 내보내기 특성을 보여 줍니다.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 사용 가능한 형식의 목록을 검색 하려면 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> 편집기의 형식 컬렉션을 유지 관리 하는를 가져옵니다. 다음 코드에서는이 서비스를 속성으로 가져옵니다.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>여백 및 스크롤 막대 확장
 여백 및 스크롤 막대는 텍스트 뷰 자체 뿐만 아니라 편집기의 주요 뷰 요소입니다. 텍스트 보기 주위에 표시 되는 표준 여백 뿐만 아니라 원하는 수의 여백을 제공할 수 있습니다.

 인터페이스를 구현 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 하 여 여백을 정의 합니다. 또한 여백을 만들려면 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> .

 편집기에 여백 공급자를 등록 하려면 다음 특성과 함께 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 여백의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 여백을 기준으로 여백이 표시 되는 순서입니다.

   기본 제공 여백:

  - "Wpf 가로 스크롤 막대"

  - "Wpf 세로 스크롤 막대"

  - "Wpf 줄 번호 여백"

    Order 특성이 있는 가로 여백은 `After="Wpf Horizontal Scrollbar"` 기본 제공 여백 아래에 표시 되 고,의 order 특성이 있는 가로 여백은 `Before ="Wpf Horizontal Scrollbar"` 기본 제공 여백 위에 표시 됩니다. Order 특성이 있는 오른쪽 세로 여백이 `After="Wpf Vertical Scrollbar"` 스크롤 막대의 오른쪽에 표시 됩니다. Order 특성이 있는 왼쪽 세로 여백은 `After="Wpf Line Number Margin"` 줄 번호 여백 (표시 되는 경우)의 왼쪽에 표시 됩니다.

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: 여백의 종류 (왼쪽, 오른쪽, 위쪽 또는 아래쪽)입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 여백이 유효한 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

  다음 예제에서는 줄 번호 여백 오른쪽에 표시 되는 여백에 대 한 여백 공급자의 특성을 내보내는 방법을 보여 줍니다.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>태그 확장
 태그는 데이터를 여러 종류의 텍스트와 연결 하는 방법입니다. 대부분의 경우 연결 된 데이터가 시각적 효과로 표시 되지만 일부 태그에는 시각적 표시가 없습니다. 을 구현 하 여 고유한 종류의 태그를 정의할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . 또한 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 지정 된 텍스트 범위 집합의 태그를 제공 하 고 태거를 제공 하기 위해를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> . 다음 특성과 함께 태거 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 태그가 유효한 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 태그의 종류입니다.

  다음 예제에서는 태거 공급자의 특성을 내보냅니다.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> 다음 종류의 태그가 기본 제공 됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>:과 연결 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: 오류 유형과 연결 됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: 장식에 연결 됩니다.

  > [!NOTE]
  > 의 예제는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> [연습: 텍스트 강조](../extensibility/walkthrough-highlighting-text.md)표시의 HighlightWordTag 정의를 참조 하세요.

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: 개요에서 확장 하거나 축소할 수 있는 영역과 연결 됩니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: 텍스트 뷰에서 장식이 차지 하는 공간을 정의 합니다. 공간 협상 장식에 대 한 자세한 내용은 다음 섹션을 참조 하세요.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: 장식의 자동 간격 및 크기 조정을 제공 합니다.

  버퍼 및 뷰에 대 한 태그를 찾아서 사용 하려면 요청 된 형식의를 제공 하는 또는를 가져옵니다 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> . 다음 코드에서는이 서비스를 속성으로 가져옵니다.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>태그 및 MarkerFormatDefinitions
 클래스를 확장 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 하 여 태그의 모양을 정의할 수 있습니다. 다음 특성을 사용 하 여 클래스 ()를 내보내야 합니다 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> .

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:이 형식을 참조 하는 데 사용 되는 이름입니다.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:이로 인해 UI에 형식이 표시 됩니다.

  생성자에서 태그의 표시 이름 및 모양을 정의 합니다. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 채우기 색을 정의 하 고 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 테두리 색을 정의 합니다. 는 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 형식 정의의 지역화할 수 있는 이름입니다.

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

 태그에이 형식 정의를 적용 하려면 표시 이름이 아니라 클래스의 name 특성에 설정 된 이름을 참조 합니다.

> [!NOTE]
> 의 예제는 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> [연습: 텍스트 강조](../extensibility/walkthrough-highlighting-text.md)표시의 HighlightWordFormatDefinition 클래스를 참조 하세요.

## <a name="extend-adornments"></a>장식 확장
 장식은 텍스트 뷰나 텍스트 뷰 자체에 표시 되는 텍스트에 추가할 수 있는 시각 효과를 정의 합니다. 사용자 고유의 장식을 모든 형식으로 정의할 수 있습니다 <xref:System.Windows.UIElement> .

 장식 클래스에서를 선언 해야 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> 합니다. 장식 레이어를 등록 하려면 다음 특성과 함께 내보냅니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 장식의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 다른 장식 레이어와 관련 된 장식의 순서입니다. 클래스는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 선택, 개요, 캐럿 및 텍스트의 네 가지 기본 계층을 정의 합니다.

  다음 예제에서는 장식 계층 정의의 내보내기 특성을 보여 줍니다.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 을 구현 하 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 고 장식을 인스턴스화하여 해당 이벤트를 처리 하는 두 번째 클래스를 만들어야 합니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> . 이 클래스는 다음 특성과 함께 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 장식이 유효한 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>:이 장식이 유효한 텍스트 뷰의 종류입니다. 클래스에는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 미리 정의 된 텍스트 뷰 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 는 주로 파일의 텍스트 보기에 사용 됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 사용자가 마우스 및 키보드를 사용 하 여 편집 하거나 탐색할 수 있는 텍스트 뷰에 사용 됩니다. 보기의 예로는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 편집기 텍스트 보기와 **출력** 창이 있습니다.

  다음 예제에서는 장식 공급자의 특성을 내보냅니다.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 텍스트와 동일한 수준에서 공간을 차지 하는 장식입니다. 이러한 종류의 장식을 만들려면에서 상속 되는 태그 클래스를 정의 해야 합니다 .이 클래스는 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> 장식이 차지 하는 공간의 크기를 정의 합니다.

 모든 장식을 사용 하는 것 처럼 장식 계층 정의를 내보내야 합니다.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 공간 협상 영역을 인스턴스화하려면를 구현 하는 클래스 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 외에 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 다른 종류의 장식을 사용 하 여을 구현 하는 클래스를 만들어야 합니다.

 태거 공급자를 등록 하려면 다음 특성과 함께 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 사용자의 장식이 유효한 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>:이 태그나 장식이 유효한 텍스트 뷰의 종류입니다. 클래스에는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 미리 정의 된 텍스트 뷰 역할 집합이 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 는 주로 파일의 텍스트 보기에 사용 됩니다. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 사용자가 마우스 및 키보드를 사용 하 여 편집 하거나 탐색할 수 있는 텍스트 뷰에 사용 됩니다. 보기의 예로는 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 편집기 텍스트 보기와 **출력** 창이 있습니다.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: 정의한 태그 또는 장식의 종류입니다. 에 대해 두 번째를 추가 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  다음 예제에서는 공간 협상 장식 태그에 대 한 태거 공급자의 특성을 내보냅니다.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>마우스 프로세서 확장
 마우스 입력에 대 한 특수 처리를 추가할 수 있습니다. 에서 상속 되는 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 처리 하려는 입력의 마우스 이벤트를 재정의 합니다. 또한 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 두 번째 클래스에서을 구현 하 고 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 마우스 처리기가 유효한 콘텐츠 종류 (예: "텍스트" 또는 "코드")를 지정 하는와 함께 내보내야 합니다.

 다음 예에서는 마우스 프로세서 공급자의 내보내기 특성을 보여 줍니다.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Drop 처리기 확장
 을 구현 하는 클래스 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> 와 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 드롭 처리기를 만들기 위해를 구현 하는 두 번째 클래스를 만들어 특정 종류의 텍스트에 대 한 drop 처리기의 동작을 사용자 지정할 수 있습니다. 다음 특성과 함께 drop handler를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>:이 drop handler가 유효한 텍스트 형식입니다. 다음 형식은 우선 순위 순서 대로 최고에서 최저로 처리 됩니다.

  1. 사용자 지정 형식

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Dif

  7. Locale

  8. 색상표

  9. PenData

  10. 직렬화 가능

  11. 값인 symboliclink

  12. Page.xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML 형식

  21. UnicodeText

  22. OEMText

  23. 텍스트

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: drop 처리기의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 기본 drop handler 전후에 drop 처리기의 순서를 지정 합니다. Visual Studio의 기본 drop handler 이름은 "DefaultFileDropHandler"입니다.

  다음 예에서는 drop handler 공급자의 특성을 내보내는 방법을 보여 줍니다.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>편집기 옵션 확장
 특정 범위 (예: 텍스트 보기) 에서만 사용할 수 있는 옵션을 정의할 수 있습니다. 편집기는 편집기 옵션, 보기 옵션 및 Windows Presentation Foundation (WPF) 보기 옵션의 미리 정의 된 옵션 집합을 제공 합니다. 이러한 옵션은, 및에서 찾을 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 새 옵션을 추가 하려면 다음 옵션 정의 클래스 중 하나에서 클래스를 파생 시킵니다.

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  다음 예제에서는 부울 값을 포함 하는 옵션 정의를 내보내는 방법을 보여 줍니다.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>IntelliSense 확장
 IntelliSense는 구조화 된 텍스트에 대 한 정보를 제공 하는 기능 그룹과이에 대 한 문 완성 기능을 제공 하는 일반적인 용어입니다. 이러한 기능에는 문 완성, 서명 도움말, 요약 정보 및 light 전구 있습니다. 문 완성 기능을 사용 하면 사용자가 언어 키워드나 멤버 이름을 올바르게 입력할 수 있습니다. 서명 도움말에는 사용자가 방금 입력 한 메서드에 대 한 시그니처 또는 서명이 표시 됩니다. 요약 정보는 마우스를 가져갈 때 형식 또는 멤버 이름에 대 한 전체 서명을 표시 합니다. 전구는 특정 컨텍스트의 특정 식별자에 대 한 추가 작업을 제공 합니다. 예를 들어 한 번 발생 한 후에 모든 변수의 이름을 바꾸면 해당 변수의 이름이 변경 됩니다.

 IntelliSense 기능의 디자인은 모든 경우에 거의 동일 합니다.

- IntelliSense *broker* 는 전체 프로세스를 담당 합니다.

- IntelliSense *세션* 은 발표자 트리거 간의 이벤트 시퀀스와 선택 항목의 커밋 또는 취소를 나타냅니다. 세션은 일반적으로 일부 사용자 제스처에 의해 트리거됩니다.

- IntelliSense *컨트롤러* 는 세션이 시작 되 고 종료 되어야 하는 시기를 결정 해야 합니다. 또한 정보를 커밋하는 시기와 세션을 취소 해야 하는 시기를 결정 합니다.

- IntelliSense *소스* 는 콘텐츠를 제공 하 고 가장 일치 하는 항목을 결정 합니다.

- IntelliSense *발표자* 는 콘텐츠를 표시 하는 일을 담당 합니다.

  대부분의 경우 적어도 원본 및 컨트롤러를 제공 하는 것이 좋습니다. 표시를 사용자 지정 하려는 경우에도 발표자를 제공할 수 있습니다.

### <a name="implement-an-intellisense-source"></a>IntelliSense 소스 구현
 소스를 사용자 지정 하려면 다음 원본 인터페이스를 하나 이상 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 는 더 이상 사용 되지 않습니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 또한 동일한 종류의 공급자를 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 는 더 이상 사용 되지 않습니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 다음 특성과 함께 공급자를 내보내야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 원본 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 소스가 적용 되는 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 소스가 표시 되는 순서입니다 (다른 소스를 기준으로 함).

- 다음 예제에서는 완료 원본 공급자에 대 한 내보내기 특성을 보여 줍니다.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense 원본을 구현 하는 방법에 대 한 자세한 내용은 다음 연습을 참조 하세요.

- [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)

- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>IntelliSense 컨트롤러 구현
 컨트롤러를 사용자 지정 하려면 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> . 또한 다음 특성과 함께 컨트롤러 공급자를 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 컨트롤러의 이름입니다.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 컨트롤러가 적용 되는 콘텐츠 종류 (예: "텍스트" 또는 "코드")입니다.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 컨트롤러가 표시 되는 순서입니다 (다른 컨트롤러에 대 한).

  다음 예제에서는 완료 컨트롤러 공급자의 특성을 내보냅니다.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense 컨트롤러를 사용 하는 방법에 대 한 자세한 내용은 다음 연습을 참조 하세요.

- [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
