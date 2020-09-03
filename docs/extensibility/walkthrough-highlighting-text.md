---
title: '연습: 텍스트 강조 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0331c0d240503dd88257269397e1afae80a17803
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86418066"
---
# <a name="walkthrough-highlight-text"></a>연습: 텍스트 강조 표시
MEF (Managed Extensibility Framework) 구성 요소 부분을 만들어 편집기에 다른 시각적 효과를 추가할 수 있습니다. 이 연습에서는 텍스트 파일에서 현재 단어의 모든 항목을 강조 표시 하는 방법을 보여 줍니다. 텍스트 파일에서 단어가 두 번 이상 발생 하는 경우 한 번에 캐럿을 배치 하면 모든 항목이 강조 표시 됩니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `HighlightWordTest` 합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-a-textmarkertag"></a>TextMarkerTag 정의
 텍스트를 강조 표시 하는 첫 번째 단계는 하위 클래스를 지정 하 고 모양을 정의 하는 것입니다 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>TextMarkerTag 및 MarkerFormatDefinition을 정의 하려면

1. 클래스 파일을 추가 하 고 이름을 **HighlightWordTag**로 추가 합니다.

2. 다음 참조를 추가합니다.

    1. VisualStudio. CoreUtility

    2. VisualStudio. 데이터

    3. VisualStudio.

    4. VisualStudio.

    5. VisualStudio. Wpf

    6. System.ComponentModel.Composition

    7. 프레젠테이션. 핵심

    8. Presentation. 프레임 워크

3. 다음 네임 스페이스를 가져옵니다.

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

4. 에서 상속 되는 클래스를 만들고 이름을로 만듭니다 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. 에서 상속 되는 두 번째 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 이름을로 만듭니다 `HighlightWordFormatDefinition` . 태그에이 형식 정의를 사용 하려면 다음 특성을 사용 하 여 해당 정의를 내보내야 합니다.

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 태그이 형식을 참조 하려면이 형식을 사용 합니다.

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:이로 인해 UI에 형식이 표시 됩니다.

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. HighlightWordFormatDefinition에 대 한 생성자에서 표시 이름 및 모양을 정의 합니다. 배경 속성은 채우기 색을 정의 하는 반면, 전경 속성은 테두리 색을 정의 합니다.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. HighlightWordTag에 대 한 생성자에서 만든 형식 정의의 이름을 전달 합니다.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>ITagger 구현
 다음 단계는 인터페이스를 구현 하는 것입니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> . 이 인터페이스는 지정 된 텍스트 버퍼에 텍스트 강조 표시와 기타 시각적 효과를 제공 하는 태그를 할당 합니다.

### <a name="to-implement-a-tagger"></a>태거를 구현 하려면

1. 형식을 구현 하는 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `HighlightWordTag` 이름을로 입력 `HighlightWordTagger` 합니다.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. 클래스에 다음 전용 필드와 속성을 추가 합니다.

    - <xref:Microsoft.VisualStudio.Text.Editor.ITextView>현재 텍스트 뷰에 해당 하는입니다.

    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>텍스트 뷰의 기반이 되는 텍스트 버퍼에 해당 하는입니다.

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>텍스트를 찾는 데 사용 되는입니다.

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>텍스트 범위 내에서 탐색 하기 위한 메서드를 포함 하는입니다.

    - <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>강조 표시할 단어 집합이 들어 있는입니다.

    - <xref:Microsoft.VisualStudio.Text.SnapshotSpan>현재 단어에 해당 하는입니다.

    - <xref:Microsoft.VisualStudio.Text.SnapshotPoint>캐럿의 현재 위치에 해당 하는입니다.

    - Lock 개체입니다.

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

3. 앞에 나열 된 속성을 초기화 하 고 및 이벤트 처리기를 추가 하는 생성자를 추가 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 합니다.

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

4. 이벤트 처리기는 모두 메서드를 호출 합니다 `UpdateAtCaretPosition` .

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

5. 또한 `TagsChanged` update 메서드에서 호출 하는 이벤트도 추가 해야 합니다.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. `UpdateAtCaretPosition()`메서드는 커서가 배치 된 단어와 동일한 텍스트 버퍼의 모든 단어를 찾아 해당 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 단어의 발생에 해당 하는 개체의 목록을 생성 합니다. 그런 다음를 호출 하 `SynchronousUpdate` 여 이벤트를 발생 시킵니다 `TagsChanged` .

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

7. 는 `SynchronousUpdate` 및 속성에 대해 동기 업데이트를 수행 `WordSpans` `CurrentWord` 하 고 이벤트를 발생 시킵니다 `TagsChanged` .

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

8. 메서드를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> . 이 메서드는 개체의 컬렉션을 사용 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 하 여 태그 범위의 열거형을 반환 합니다.

     C #에서이 메서드를 yield iterator로 구현 합니다 .이 메서드를 사용 하면 지연 계산 (즉, 개별 항목에 액세스 하는 경우에만 집합의 계산)이 태그에 적용 됩니다. Visual Basic에서 목록에 태그를 추가 하 고 목록을 반환 합니다.

     여기서 메서드는 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 파란색 배경을 제공 하는 "blue"가 있는 개체를 반환 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

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
 태거를 만들려면를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . 이 클래스는 MEF 구성 요소 파트 이므로이 확장이 인식 되도록 올바른 특성을 설정 해야 합니다.

> [!NOTE]
> MEF에 대 한 자세한 내용은 [Managed Extensibility Framework (mef)](/dotnet/framework/mef/index)를 참조 하세요.

### <a name="to-create-a-tagger-provider"></a>태거 공급자를 만들려면

1. `HighlightWordTaggerProvider`을 구현 하는 라는 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 및의를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. 및의 두 가지 편집기 서비스를 가져와 <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> 태거를 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 인스턴스화해야 합니다.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. 인스턴스를 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 반환 하는 메서드를 구현 합니다 `HighlightWordTagger` .

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
 이 코드를 테스트 하려면 HighlightWordTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>HighlightWordTest 솔루션을 빌드하고 테스트 하려면

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만들고 단어를 반복 하는 텍스트를 입력 합니다 (예: "hello hello hello").

4. "Hello"의 발생 중 하나에 커서를 놓습니다. 모든 항목은 파란색으로 강조 표시 되어야 합니다.

## <a name="see-also"></a>추가 정보
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
