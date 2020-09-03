---
title: '연습: 전구 제안 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153eda065b9a6e845a39c35aaae34bbe1745f7a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905000"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>연습: 전구 제안 표시
Light 전구은 Visual Studio 편집기에서 작업 집합을 표시 하도록 확장 되는 아이콘입니다. 예를 들어 기본 제공 코드 분석기 또는 코드 리팩터링에 의해 식별 되는 문제에 대 한 수정 등이 있습니다.

 Visual c # 및 Visual Basic 편집기에서 .NET Compiler Platform ("Roslyn")를 사용 하 여 light 전구을 자동으로 표시 하는 작업으로 사용자 고유의 코드 분석기를 작성 하 고 패키지할 수도 있습니다. 자세한 내용은 다음을 참조하십시오.

- [방법: c # 진단 및 코드 수정 작성](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [방법: Visual Basic 진단 및 코드 수정 작성](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  또한 c + +와 같은 다른 언어는 해당 함수의 스텁 구현을 만드는 제안 등의 몇 가지 빠른 작업을 위한 가벼운 전구 제공 합니다.

  전구는 다음과 같습니다. Visual Basic 또는 Visual c # 프로젝트에서 잘못 된 경우 변수 이름 아래에 빨간색 물결선이 나타납니다. 잘못 된 식별자 위로 마우스를 가져가면 커서 근처에 전구를 표시 합니다.

  ![전구](../extensibility/media/lightbulb.png "전구")

  전구 옆에 있는 아래쪽 화살표를 클릭 하면 선택한 작업의 미리 보기와 함께 일련의 제안 된 작업이 표시 됩니다. 이 경우 작업을 실행 하는 경우 코드에 적용 된 변경 내용을 보여 줍니다.

  ![전구 미리 보기](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Light 전구를 사용 하 여 고유한 제안 조치를 제공할 수 있습니다. 예를 들어 여는 중괄호를 새 줄로 이동 하거나 앞 줄의 끝으로 이동 하는 작업을 제공할 수 있습니다. 다음 연습에서는 현재 단어에 표시 되 고 두 개의 제안 동작 ( **대문자로 변환** 및 소문자로 **변환**)이 있는 전구를 만드는 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) 프로젝트 만들기

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `LightBulbTest` 합니다.

2. **편집기 분류자** 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가 하 고 **로컬 복사** 를로 설정 합니다 `False` .

     *Microsoft.VisualStudio.Language.Intellisense*

5. 새 클래스 파일을 추가 하 고 이름을 **LightBulbTest**로 추가 합니다.

6. 다음 using 지시문을 추가합니다.

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>전구 원본 공급자를 구현 합니다.

1. *LightBulbTest.cs* 클래스 파일에서 LightBulbTest 클래스를 삭제 합니다. 을 구현 하는 **TestSuggestedActionsSourceProvider** 라는 클래스를 추가 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> 합니다. **테스트 제안 작업** 의 이름 및 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"로 내보냅니다.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. 소스 공급자 클래스 내에서를 가져와서 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 속성으로 추가 합니다.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. 메서드를 구현 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> 하 여 개체를 반환 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 합니다. 원본에 대해서는 다음 섹션에서 설명 합니다.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>ISuggestedActionSource 구현
 제안 된 작업 원본은 제안 된 작업 집합을 수집 하 고 올바른 컨텍스트에 추가 하는 작업을 담당 합니다. 이 경우 컨텍스트는 현재 단어 이며 제안 된 작업은 **UpperCaseSuggestedAction** 및 **LowerCaseSuggestedAction**입니다 .이에 대해서는 다음 섹션에서 설명 합니다.

1. 을 구현 하는 **TestSuggestedActionsSource** 클래스를 추가 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 합니다.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. 제안 된 동작 원본 공급자, 텍스트 버퍼 및 텍스트 뷰에 대해 전용, 읽기 전용 필드를 추가 합니다.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Private 필드를 설정 하는 생성자를 추가 합니다.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. 현재 커서 아래에 있는 단어를 반환 하는 private 메서드를 추가 합니다. 다음 메서드는 커서의 현재 위치를 확인 하 고 텍스트 구조 탐색기에 단어 범위를 요청 합니다. 커서가 단어에 있으면 <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> out 매개 변수에서가 반환 되 고, 그렇지 않으면 `out` 매개 변수가이 `null` 고 메서드에서를 반환 합니다 `false` .

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 메서드를 구현합니다. 편집기는이 메서드를 호출 하 여 전구를 표시할지 여부를 확인 합니다. 이 호출은 예를 들어 커서가 한 줄에서 다른 줄로 이동 하거나 마우스가 오류 물결선을 가리킬 때 자주 수행 됩니다. 이 메서드가 작동 하는 동안 다른 UI 작업을 수행할 수 있도록 하기 위해 비동기입니다. 대부분의 경우이 메서드는 현재 줄의 일부 구문 분석 및 분석을 수행 해야 하므로 처리 하는 데 시간이 걸릴 수 있습니다.

     이 구현에서는를 비동기적으로 가져오고,와 <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 같이 공백이 아닌 텍스트가 있는지 여부를 확인 합니다.

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> 다른 개체를 포함 하는 개체의 배열을 반환 하는 메서드를 구현 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> . 이 메서드는 전구를 확장할 때 호출 됩니다.

    > [!WARNING]
    > 및의 구현이 일치 하는지 확인 해야 합니다 `HasSuggestedActionsAsync()` . 즉, `GetSuggestedActions()` 가를 반환 하는 경우에는 `HasSuggestedActionsAsync()` `true` `GetSuggestedActions()` 몇 가지 작업을 표시 해야 합니다. 대부분의 경우 `HasSuggestedActionsAsync()` 는 바로 전에 호출 `GetSuggestedActions()` 되지만 항상 그렇지는 않습니다. 예를 들어 사용자가 (**ctrl +** .)를 눌러 전구 동작을 호출 하면만 `GetSuggestedActions()` 호출 됩니다.

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7. 이벤트를 정의 `SuggestedActionsChanged` 합니다.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. 구현을 완료 하려면 및 메서드에 대 한 구현을 추가 `Dispose()` `TryGetTelemetryId()` 합니다. 원격 분석을 수행 하지 않으려는 경우 `false` 에는를 반환 하 고 GUID를로 설정 하기만 하면 `Empty` 됩니다.

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>전구 동작 구현

1. 프로젝트에서 *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* 에 대 한 참조를 추가 하 고 **로컬 복사** 를로 설정 `False` 합니다.

2. 두 개의 클래스를 만듭니다. 첫 번째 클래스의 이름은 `UpperCaseSuggestedAction` 이고 두 번째 클래스의 이름은 `LowerCaseSuggestedAction`입니다. 두 클래스 모두 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>를 구현합니다.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     한 클래스는 <xref:System.String.ToUpper%2A>를 호출하고 다른 클래스는 <xref:System.String.ToLower%2A>를 호출한다는 점을 제외하고 두 클래스는 유사합니다. 다음 단계에서는 대문자 동작 클래스만 설명하지만 두 클래스를 모두 구현해야 합니다. 대문자 동작 구현 단계를 소문자 동작 구현 패턴으로 사용합니다.

3. 이러한 클래스에 대해 다음 using 지시문을 추가 합니다.

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. 전용 필드 집합을 선언합니다.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. 필드를 설정하는 생성자를 추가합니다.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>작업 미리 보기를 표시 하도록 메서드를 구현 합니다.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>빈 열거형을 반환 하도록 메서드를 구현 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> .

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. 속성을 다음과 같이 구현합니다.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. 범위에 있는 텍스트를 해당 대문자로 바꾸어 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> 메서드를 구현합니다.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > 전구 작업 **호출** 메서드는 UI를 표시 하지 않을 것으로 예상 됩니다. 작업에서 새 UI (예: 미리 보기 또는 선택 대화 상자)를 표시 하는 경우 **invoke** 메서드 내에서 직접 ui를 표시 하지 말고 **호출**에서 반환한 후 ui를 표시 하도록 예약 합니다.

10. 구현을 완료 하려면 및 메서드를 추가 `Dispose()` 합니다 `TryGetTelemetryId()` .

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. `LowerCaseSuggestedAction`표시 텍스트를 "변환 ' '에서 소문자로 변환 하 {0} 고를 호출 하는 것과 동일한 작업을 수행 해야 합니다 <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 LightBulbTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만들고 일부 텍스트를 입력합니다. 텍스트의 왼쪽에 전구를 표시 해야 합니다.

     ![전구 테스트](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. 전구를 가리킵니다. 아래쪽 화살표가 표시 됩니다.

5. 전구를 클릭 하면 선택한 작업의 미리 보기와 함께 두 개의 제안 된 동작이 표시 됩니다.

     ![전구 테스트, 확장됨](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. 첫 번째 동작을 클릭 하면 현재 단어의 모든 텍스트가 대문자로 변환 됩니다. 두 번째 동작을 클릭 하면 모든 텍스트가 소문자로 변환 됩니다.
