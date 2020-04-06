---
title: '연습: 전구 제안 표시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697481"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>연습: 전구 제안 표시
전구는 Visual Studio 편집기의 아이콘으로, 기본 제공 코드 분석기 또는 코드 리팩터링으로 식별된 문제에 대한 수정 사항과 같은 작업 집합을 표시하도록 확장됩니다.

 Visual C# 및 Visual Basic 편집기에서는 .NET 컴파일러 플랫폼("Roslyn")을 사용하여 전구를 자동으로 표시하는 작업으로 사용자 고유의 코드 분석기를 작성하고 패키징할 수도 있습니다. 자세한 내용은 다음을 참조하세요.

- [방법: C# 진단 및 코드 수정 을 작성합니다.](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [방법: 시각적 기본 진단 및 코드 수정 사항 작성](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  C++와 같은 다른 언어도 해당 함수의 스텁 구현을 만드는 제안과 같은 몇 가지 빠른 작업에 대한 전구를 제공합니다.

  전구의 모양은 다음과 같습니다. 시각적 기본 또는 Visual C# 프로젝트에서 빨간색 물결선이 유효하지 않은 경우 변수 이름 아래에 나타납니다. 잘못된 식별자 위에 마우스를 두면 전구가 커서 근처에 나타납니다.

  ![전구](../extensibility/media/lightbulb.png "전구")

  전구에서 아래쪽 화살표를 클릭하면 선택한 작업의 미리 보기와 함께 제안된 작업 집합이 나타납니다. 이 경우 작업을 실행하는 경우 코드에 대한 변경 내용이 표시됩니다.

  ![전구 미리 보기](../extensibility/media/lightbulbpreview.png "전구 미리보기")

  전구를 사용하여 자신만의 제안된 작업을 제공할 수 있습니다. 예를 들어 열린 곱슬 대괄호를 새 줄로 이동하거나 이전 줄의 끝으로 이동하는 작업을 제공할 수 있습니다. 다음 연습에서는 현재 단어에 나타나고 **대문자로 변환하고** **소문자로 변환하는**두 가지 제안 된 작업이 있는 전구를 만드는 방법을 보여 주십니까?

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>관리되는 확장성 프레임워크(MEF) 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `LightBulbTest`이름을 지정합니다.

2. 프로젝트에 **편집기 분류자** 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가하고 **로컬 복사를** 다음으로 `False`설정합니다.

     *Microsoft.VisualStudio.Language.Intellisense*

5. 새 클래스 파일을 추가하고 **LightBulbTest**의 이름을 지정합니다.

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

## <a name="implement-the-light-bulb-source-provider"></a>전구 소스 공급자 구현

1. *LightBulbTest.cs* 클래스 파일에서 LightBulbTest 클래스를 삭제합니다. 을 구현하는 **테스트제안작업소스공급자라는** 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>추가합니다. **테스트 권장 작업의** 이름과 "텍스트"로 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 내보냅니다.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. 소스 공급자 클래스 내에서 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 를 가져오고 속성으로 추가합니다.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. 개체를 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> 반환하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 메서드를 구현합니다. 소스는 다음 섹션에서 설명합니다.

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

## <a name="implement-the-isuggestedactionsource"></a>I제안된 작업 환경 구현
 제안된 작업 소스는 제안된 작업 집합을 수집하고 올바른 컨텍스트에 추가하는 작업을 담당합니다. 이 경우 컨텍스트는 현재 단어이며 제안된 작업은 다음 섹션에서 설명하는 **대문자 제안 작업** 및 **소문자 제안 작업입니다.**

1. 클래스 **테스트제안작업추가를** 구현하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>소스.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. 제안된 작업 원본 공급자, 텍스트 버퍼 및 텍스트 보기에 대해 읽기 전용 전용 필드를 추가합니다.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. 개인 필드를 설정하는 생성자추가합니다.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. 현재 커서 아래에 있는 단어를 반환하는 전용 메서드를 추가합니다. 다음 메서드는 커서의 현재 위치를 살펴보고 텍스트 구조 탐색기에게 단어의 범위에 대해 묻습니다. 커서가 단어에 있으면 out <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 매개 변수에서 반환됩니다. 그렇지 않으면 `out` 매개 `null` 변수가 `false`되고 메서드가 반환됩니다.

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

5. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 메서드를 구현합니다. 편집기는 이 메서드를 호출하여 전구를 표시할지 여부를 확인합니다. 예를 들어 커서가 한 줄에서 다른 줄로 이동하거나 마우스가 오류 물결선 위로 마우스를 가져갈 때마다 이 호출이 자주 이루어집니다. 이 메서드가 작동하는 동안 다른 UI 작업을 계속할 수 있도록 하기 위해 비동기입니다. 대부분의 경우 이 메서드는 현재 줄의 일부 구문 분석 및 분석을 수행해야 하므로 처리에 다소 시간이 걸릴 수 있습니다.

     이 구현에서는 비동기적으로 범위를 얻고 <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 범위가 공백 이외의 텍스트가 있는지 여부를 결정합니다.

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

6. 다른 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> 개체를 포함 하는 <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> 개체의 배열을 반환 하는 메서드를 구현 합니다. 이 메서드는 전구를 확장할 때 호출됩니다.

    > [!WARNING]
    > 구현및 일관성이 있는지 확인해야 `HasSuggestedActionsAsync()` `GetSuggestedActions()` 합니다. 즉, `HasSuggestedActionsAsync()` 반환하는 `true`경우 `GetSuggestedActions()` 표시할 몇 가지 작업이 있어야 합니다. 대부분의 경우 `HasSuggestedActionsAsync()` 바로 전에 `GetSuggestedActions()`호출되지만 항상 그렇지는 않습니다. 예를 들어 사용자가 **(CTRL+** .)를 눌러 전구 동작을 `GetSuggestedActions()` 호출하는 경우에만 호출됩니다.

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

7. 이벤트를 `SuggestedActionsChanged` 정의합니다.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. 구현을 완료하려면 `Dispose()` 및 `TryGetTelemetryId()` 메서드에 대한 구현을 추가합니다. 원격 분석을 수행하지 않으려면 GUID를 로 `false` 설정하기만 `Empty`하면 됩니다.

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

## <a name="implement-light-bulb-actions"></a>전구 작업 구현

1. 프로젝트에서 *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll에* 대한 참조를 추가하고 로컬 `False` **복사를** 로 설정합니다.

2. 두 개의 클래스를 만듭니다. 첫 번째 클래스의 이름은 `UpperCaseSuggestedAction` 이고 두 번째 클래스의 이름은 `LowerCaseSuggestedAction`입니다. 두 클래스 모두 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>를 구현합니다.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     한 클래스는 <xref:System.String.ToUpper%2A>를 호출하고 다른 클래스는 <xref:System.String.ToLower%2A>를 호출한다는 점을 제외하고 두 클래스는 유사합니다. 다음 단계에서는 대문자 동작 클래스만 설명하지만 두 클래스를 모두 구현해야 합니다. 대문자 동작 구현 단계를 소문자 동작 구현 패턴으로 사용합니다.

3. 이러한 클래스에 대 한 지시문을 사용 하 여 다음을 추가 합니다.

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

6. 작업 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> 미리 보기를 표시되도록 메서드를 구현합니다.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. 빈 <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> 열거형이 반환되도록 메서드를 구현합니다.

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
    > 전구 동작 **호출** 메서드는 UI를 표시 하지 않습니다. 작업에 새 UI(예: 미리 보기 또는 선택 대화 상자)가 표시되는 경우 **Invoke** 메서드 내에서 직접 UI를 표시하지 않고 **Invoke에서**반환한 후 UI를 표시하도록 예약합니다.

10. 구현을 완료하려면 및 `Dispose()` `TryGetTelemetryId()` 메서드를 추가합니다.

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

11. 표시 `LowerCaseSuggestedAction` 텍스트를 "소문자로 변환"으로{0}변경하고 에 대한 호출을 <xref:System.String.ToUpper%2A> 변경하는 데 동일한 <xref:System.String.ToLower%2A>작업을 수행하는 것을 잊지 마십시오.

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 LightBulbTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 일부 텍스트를 입력합니다. 텍스트 왼쪽에 전구가 표시됩니다.

     ![전구 테스트](../extensibility/media/testlightbulb.png "테스트L리그트전구")

4. 전구를 가리킵니다. 아래쪽 화살표가 표시됩니다.

5. 전구를 클릭하면 선택한 작업의 미리 보기와 함께 두 개의 제안된 작업이 표시됩니다.

     ![전구 테스트, 확장됨](../extensibility/media/testlightbulbexpanded.gif "테스트L리그트전구 확장")

6. 첫 번째 작업을 클릭하면 현재 단어의 모든 텍스트를 대문자로 변환해야 합니다. 두 번째 작업을 클릭하면 모든 텍스트를 소문자로 변환해야 합니다.
