---
title: '연습: 텍스트 강조 표시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697398"
---
# <a name="walkthrough-highlight-text"></a>연습: 텍스트 강조 표시
MEF(관리되는 확장성 프레임워크) 구성 요소 부분을 만들어 편집기에서 다른 시각 효과를 추가할 수 있습니다. 이 연습에서는 텍스트 파일에서 현재 단어의 모든 발생을 강조 표시하는 방법을 보여 주십습니다. 텍스트 파일에서 단어가 두 번 이상 발생하고 한 번에 카를을 배치하면 모든 발생이 강조 표시됩니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `HighlightWordTest`이름을 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-a-textmarkertag"></a>텍스트 마커태그 정의
 텍스트를 강조 표시하는 첫 번째 단계는 하위 클래스를 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 사용하여 모양을 정의하는 것입니다.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>텍스트 마커 태그 및 마커 형식 정의를 정의하려면

1. 클래스 파일을 추가하고 **강조 표시 WordTag**.

2. 다음 참조를 추가합니다.

    1. 마이크로소프트.비주얼 스튜디오.코어유틸리티

    2. 마이크로소프트.비주얼 스튜디오.텍스트.데이터

    3. 마이크로소프트.비주얼 스튜디오.텍스트.로직

    4. 마이크로소프트.비주얼 스튜디오.텍스트.UI

    5. 마이크로소프트.비주얼 스튜디오.텍스트.UI.Wpf

    6. System.ComponentModel.Composition

    7. 프레젠테이션.코어

    8. 프레젠테이션.프레임워크

3. 다음 네임스페이스를 가져옵니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. 에서 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 상속 하 고 이름을 `HighlightWordTag`지정 하는 클래스를 만듭니다.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>에서 상속 하는 두 번째 클래스를 `HighlightWordFormatDefinition`만들고 이름을 지정 합니다. 태그에 이 형식 정의를 사용하려면 다음 특성으로 내보내야 합니다.

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 태그는 이 형식을 참조하기 위해 이 형식을 사용합니다.

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: 이렇게 하면 UI에 형식이 나타납니다.

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. HighlightWordFormat정의 생성자에서 표시 이름과 모양을 정의합니다. Background 속성은 채우기 색상을 정의하고 포그라운드 속성은 테두리 색상을 정의합니다.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. HighlightWordTag의 생성자에서 만든 형식 정의의 이름을 전달합니다.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>ITagger 구현
 다음 단계는 인터페이스를 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 구현하는 것입니다. 이 인터페이스는 지정된 텍스트 버퍼에 텍스트 강조 표시 및 기타 시각적 효과를 제공하는 태그를 할당합니다.

### <a name="to-implement-a-tagger"></a>태거를 구현하려면

1. 형식을 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `HighlightWordTag`구현하는 클래스를 만들고 이름을 지정합니다. `HighlightWordTagger`

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. 클래스에 다음 개인 필드 및 속성을 추가합니다.

    - 현재 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>텍스트 보기에 해당하는 AN입니다.

    - 텍스트 <xref:Microsoft.VisualStudio.Text.ITextBuffer>뷰의 기초가 되는 텍스트 버퍼에 해당하는 AN입니다.

    - 텍스트를 <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>찾는 데 사용되는 AN입니다.

    - 텍스트 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>범위 내에서 탐색하는 메서드가 있는 AN입니다.

    - 강조 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>표시할 단어 집합이 포함된 A입니다.

    - 현재 <xref:Microsoft.VisualStudio.Text.SnapshotSpan>단어에 해당하는 A.

    - A는 <xref:Microsoft.VisualStudio.Text.SnapshotPoint>카류의 현재 위치에 해당합니다.

    - 잠금 개체입니다.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. 이전에 나열된 속성을 초기화하고 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 이벤트 처리기를 추가하는 생성기를 추가합니다.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. 이벤트 처리기는 모두 `UpdateAtCaretPosition` 메서드를 호출합니다.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. 또한 update 메서드에서 `TagsChanged` 호출되는 이벤트를 추가해야 합니다.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. 메서드는 `UpdateAtCaretPosition()` 텍스트 버퍼의 모든 단어를 찾아 커서가 배치된 단어와 동일하며 단어의 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 발생에 해당하는 개체 목록을 생성합니다. 그런 다음 `SynchronousUpdate`이벤트를 발생시키는 호출합니다. `TagsChanged`

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. 는 `SynchronousUpdate` `WordSpans` 및 `CurrentWord` 속성에 대한 동기 업데이트를 수행하고 `TagsChanged` 이벤트를 발생시다.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. 메서드를 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 구현 해야 합니다. 이 메서드는 개체 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 컬렉션을 사용 하 고 태그 범위의 열거형 반환 합니다.

     C#에서 이 메서드를 yield iterator로 구현하여 태그의 지연 평가(즉, 개별 항목에 액세스하는 경우에만 집합 평가)를 사용할 수 있습니다. 시각적 기본에서 목록에 태그를 추가하고 목록을 반환합니다.

     여기서 메서드는 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 파란색 배경을 제공하는 "파란색"이 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>있는 개체를 반환합니다.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>태거 공급자 만들기
 태거를 만들려면 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>를 구현해야 합니다. 이 클래스는 MEF 구성 요소 부품이므로 이 확장이 인식되도록 올바른 특성을 설정해야 합니다.

> [!NOTE]
> MEF에 대한 자세한 내용은 [MEF(관리되는 확장성 프레임워크)를](/dotnet/framework/mef/index)참조하십시오.

### <a name="to-create-a-tagger-provider"></a>태거 공급자를 만들려면

1. 을 `HighlightWordTaggerProvider` 구현하는 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>클래스를 만들고 "text" <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 및 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>a.를 사용하여 내보냅니다.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. 태거를 인스턴스화하려면 <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> 두 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>편집기 서비스(와 를 가져와야 합니다)를 가져와야 합니다.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. 의 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 인스턴스를 반환하는 `HighlightWordTagger`메서드를 구현합니다.

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 HighlightWordTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>HighlightWordTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 단어가 반복되는 일부 텍스트(예: "hello hello hello")를 입력합니다.

4. 커서를 "hello"의 발생 중 하나에 배치합니다. 모든 발생은 파란색으로 강조 표시되어야 합니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
