---
title: 편집기 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fc32d0126d912acab104ecefe3cb62d80b8513f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690311"
---
# <a name="editor-imports"></a>편집기 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장을 제공 하는 많은 편집기 서비스, 팩터리 및 broker를 핵심 편집기에 대 한 다양 한 종류의 액세스로 가져올 수 있습니다. 예를 들어를 가져와서 지정 된 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 콘텐츠 형식에 대해를 제공할 수 있습니다. 이 탐색기를 사용 하면 텍스트 버퍼에서 다양 한 검색을 수행할 수 있습니다.  
  
 편집기 가져오기를 사용 하려면 Managed Extensibility Framework 구성 요소 파트를 내보내는 클래스의 필드 또는 속성으로 가져옵니다.  
  
> [!NOTE]
> Managed Extensibility Framework에 대 한 자세한 내용은 [MEF (Managed Extensibility Framework)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)를 참조 하세요.  
  
## <a name="import-syntax"></a>가져오기 구문  
 다음 예제에서는 편집기 옵션 팩터리 서비스를 가져오는 방법을 보여 줍니다.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 속성을 사용 하지 않고 서비스를 필드로 가져오려는 경우 `null` 변수에 할당 하지 않는 것에 대 한 컴파일러 경고를 방지 하기 위해 선언에서이를로 설정 해야 합니다.  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Imports 사용에 대 한 자세한 예제는 다음 연습을 참조 하세요.  
  
 [연습: 여백 문자 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [연습: 텍스트 뷰 사용자 지정](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)  
  
 [연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [연습: 문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [연습: 스마트 태그 표시](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>서비스 공급자 가져오기  
 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>Visual Studio 서비스에 대 한 액세스 권한을 얻기 위해 (VisualStudio 어셈블리에 있음)를 동일한 방법으로 가져올 수도 있습니다.  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 자세한 내용은 [연습: 편집기 확장에서 DTE 개체에 액세스](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) 를 참조 하세요.  
  
## <a name="services"></a>Services  
 편집기 서비스는 일반적으로 서비스를 제공 하 고 여러 구성 요소에서 공유 되는 단일 엔터티입니다.  
  
|가져오기|하면|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|파일 확장명과 개체 간의 관계 <xref:Microsoft.VisualStudio.Utilities.IContentType> 입니다.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 개체의 컬렉션입니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|많은 편집기 어댑터 개체:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>지정 된 텍스트 뷰에 대 한 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>입니다.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>입니다.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>차이점의입니다.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>차이점의입니다.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>또는 <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>개체 집합에 대 한입니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>에 대 한 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|개체의 컬렉션을 유지 관리 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>텍스트 버퍼에 대 한입니다.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>텍스트 뷰에 대 한입니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>지정 된 범위에 대 한입니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>텍스트 뷰에 대 한입니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|개체를 통한 자동 들여쓰기를 가져옵니다 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> .|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|에 대 한를 관리 합니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>입니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|스냅숏 범위 집합에서 RTF 형식의 텍스트를 생성 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>뷰의 텍스트 줄에 서식을 지정 하기 위한입니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>에 대 한 개체 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|텍스트 스냅숏을 검색 합니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>에 대 한 <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> 입니다.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>텍스트 뷰에 대 한입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|문자 모양의 표준 집합입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|키보드 처리를 추적 합니다.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|표준 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 개체입니다.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|텍스트 버퍼와 개체 간의 관계를 유지 관리  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> 합니다.|  
  
## <a name="other-imports"></a>기타 가져오기  
 공급자 팩터리 및 브로커는 일반적으로 여러 구성 요소에서 여러 인스턴스를 가질 수 있는 엔터티입니다.  
  
|가져오기|하면|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 지정 된 버퍼에 대 한 형식의입니다.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|텍스트 표식 태거 (형식의 a <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> )입니다.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>지정 된에 대 한 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>입니다.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
