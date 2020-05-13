---
title: 에디터 수입 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712007"
---
# <a name="editor-imports"></a>편집기 가져오기
코어 편집기에 대한 다양한 종류의 액세스 권한을 확장프로그램을 제공하는 여러 편집기 서비스, 팩터리 및 브로커를 가져올 수 있습니다. 예를 들어 을 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 가져와 지정된 콘텐츠 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 형식에 대한 a를 제공할 수 있습니다. (이 탐색기에서는 텍스트 버퍼에서 다양한 종류의 검색을 수행할 수 있습니다.

 편집기 가져오기를 사용 하려면 관리되는 확장성 프레임 워크 구성 요소 부분을 내 보내는 클래스의 필드 또는 속성으로 가져옵니다.

> [!NOTE]
> 관리되는 확장성 프레임워크에 대한 자세한 내용은 [MEF(관리되는 확장성 프레임워크)를](/dotnet/framework/mef/index)참조하십시오.

## <a name="import-syntax"></a>구문 가져오기
 다음 예제에서는 편집기 옵션 팩터리 서비스를 가져오는 방법을 보여 주며 있습니다.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 서비스를 속성이 아닌 필드로 가져오려면 `null` 변수에 할당하지 않는 것에 대한 컴파일러 경고를 피하기 위해 선언에서 서비스를 설정해야 합니다.

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 가져오기 사용의 자세한 예는 다음 연습을 참조하십시오.

- [연습: 여백 문말 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [연습: 텍스트 보기 사용자 지정](../extensibility/walkthrough-customizing-the-text-view.md)

- [연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)

- [연습: 빠른 정보 표시 도구 설명](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)

- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)

- [연습: 전구 제안 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>서비스 공급자 가져오기
 동일한 방법으로 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (Microsoft.VisualStudio.Shell.Immutable.10.0 어셈블리에 있는) Visual Studio 서비스에 액세스할 수 있습니다.

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 자세한 내용은 [연습: 편집기 확장에서 DTE 개체에 액세스합니다.](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)

## <a name="services"></a>Services
 편집기 서비스는 일반적으로 서비스를 제공하고 여러 구성 요소간에 공유되는 단일 엔터티입니다.

|가져오기|제공|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|파일 확장자와 <xref:Microsoft.VisualStudio.Utilities.IContentType> 개체 간의 관계입니다.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 개체의 컬렉션입니다.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>개체.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|많은 편집기 어댑터 개체:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|지정된 <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> 텍스트 뷰의 개체입니다.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>입니다.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>입니다.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> 차이점.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> 차이점.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|또는 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|개체 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 집합에 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 대한 값입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|에 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 대한 <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|에 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|에 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|에 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|개체 컬렉션을 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 유지 관리합니다.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|텍스트 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 버퍼에 대한 것입니다.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|텍스트 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 보기에 대한 것입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|지정한 범위에 대한 입니다. <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|텍스트 <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> 보기에 대한 것입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|에 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|개체를 통해 자동 들여쓰기를 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> 가져옵니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|에 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 대해 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>관리합니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>입니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|스냅샷 범위 집합에서 RTF 형식의 텍스트를 생성합니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|에 <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|뷰에서 텍스트 줄의 서식을 지정하기 위한 A입니다. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|에 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>개체입니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|텍스트 스냅샷을 검색합니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|에 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 의해 <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|텍스트 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> 보기에 대한 것입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|글리프의 표준 집합입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|에 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|키보드 핸들링을 추적합니다.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|표준 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 개체입니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|텍스트 버퍼와 <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> 개체 간의 관계를 유지 합니다.|

## <a name="other-imports"></a>기타 수입품
 공급자 팩터리 및 브로커는 일반적으로 여러 구성 요소에 여러 인스턴스를 가질 수 있는 엔터티입니다.

|가져오기|제공|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> 지정된 버퍼에 대한 형식)입니다. <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|텍스트 마커 <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> 태거(a.a 유형). <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|주어진에 <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>대한 .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>입니다.|

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
