---
title: 편집기 가져오기 | Microsoft Docs
description: 핵심 편집기에서 다양한 종류의 액세스 권한을 확장에 제공하는 편집기 서비스, 팩터리 및 브로커를 가져오는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898346"
---
# <a name="editor-imports"></a>편집기 가져오기
핵심 편집기에서 다양한 종류의 액세스 권한을 확장에 제공하는 여러 편집기 서비스, 팩터리 및 브로커를 가져올 수 있습니다. 예를 들어 를 가져와 지정된 콘텐츠 형식에 대한 를 제공할 수 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 있습니다. (이 탐색기를 사용하면 텍스트 버퍼에서 다양한 종류의 검색을 수행할 수 있습니다.)

 편집기 가져오기를 사용하려면 Managed Extensibility Framework 구성 요소 부분을 내보내는 클래스의 필드 또는 속성으로 가져옵니다.

> [!NOTE]
> Managed Extensibility Framework 대한 자세한 내용은 [MEF(Managed Extensibility Framework)를](/dotnet/framework/mef/index)참조하세요.

## <a name="import-syntax"></a>가져오기 구문
 다음 예제에서는 편집기 옵션 팩터리 서비스를 가져오는 방법을 보여줍니다.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 서비스를 속성이 아닌 필드로 가져오려면 `null` 변수에 할당되지 않는 것에 대한 컴파일러 경고를 방지하기 위해 선언에서 로 설정해야 합니다.

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 가져오기를 사용하는 더 많은 예제는 다음 연습을 참조하세요.

- [연습: 여백 문자 문자 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [연습: 텍스트 보기 사용자 지정](../extensibility/walkthrough-customizing-the-text-view.md)

- [연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)

- [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)

- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)

- [연습: 전구 제안 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>서비스 공급자 가져오기
 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>(Microsoft.VisualStudio.Shell.Immutable.10.0 어셈블리에 있는)을 동일한 방식으로 가져와서 Visual Studio 서비스에 액세스할 수도 있습니다.

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 자세한 내용은 [연습: 편집기 확장에서 DTE 개체에 액세스를](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) 참조하세요.

## <a name="services"></a>서비스
 편집기 서비스는 일반적으로 서비스를 제공하고 여러 구성 요소 간에 공유되는 단일 엔터티입니다.

|가져오기|제공|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|파일 확장명과 개체 간의 <xref:Microsoft.VisualStudio.Utilities.IContentType> 관계입니다.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 개체의 컬렉션입니다.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 개체.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|많은 편집기 어댑터 개체:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>지정된 텍스트 뷰에 대한 개체입니다.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>입니다.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>입니다.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>차이점의 입니다.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>차이점의 입니다.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>또는 <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>개체 집합에 대한 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>에 대한 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|개체의 컬렉션을 유지 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 관리합니다.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>텍스트 버퍼에 대한 입니다.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>텍스트 뷰에 대한 입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>지정된 범위에 대한 입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>텍스트 뷰에 대한 입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|개체를 통한 자동 들여쓰기 를 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> 가져옵니다.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|에 대한 를 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 관리합니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>입니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|스냅샷 범위 집합에서 RTF 형식 텍스트를 생성합니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>뷰에서 텍스트 줄의 서식을 지정하기 위한 입니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 개체입니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|텍스트 스냅샷을 검색합니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>에 대한 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 입니다. <xref:Microsoft.VisualStudio.Utilities.IContentType>|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>텍스트 뷰에 대한 입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|표준 문자 문자 집합입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>에 대한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|키보드 처리를 추적합니다.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|표준 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 개체입니다.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|텍스트 버퍼와 개체 간의 관계를 유지  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> 관리합니다.|

## <a name="other-imports"></a>기타 가져오기
 공급자 팩터리 및 브로커는 일반적으로 여러 구성 요소에 여러 인스턴스를 가질 수 있는 엔터티입니다.

|가져오기|제공|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>지정된 버퍼에 대한 형식의 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 입니다.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|텍스트 표식 <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> 태거(형식의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> )입니다.|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>지정된 에 대한 입니다. <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>입니다.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>입니다.|

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
