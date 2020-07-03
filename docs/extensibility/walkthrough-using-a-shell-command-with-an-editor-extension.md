---
title: '연습: 편집기 확장에서 셸 명령 사용 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e9f7de69cfd969db8ae905ea65bbf868cf2c88a
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904446"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>연습: 편집기 확장에서 셸 명령 사용
VSPackage에서 메뉴 명령과 같은 기능을 편집기에 추가할 수 있습니다. 이 연습에서는 메뉴 명령을 호출 하 여 편집기에서 텍스트 뷰에 장식을 추가 하는 방법을 보여 줍니다.

 이 연습에서는 MEF (Managed Extensibility Framework) 구성 요소 부분과 함께 VSPackage를 사용 하는 방법을 보여 줍니다. 메뉴 명령을 Visual Studio 셸에 등록 하려면 VSPackage를 사용 해야 합니다. 명령을 사용 하 여 MEF 구성 요소 부분에 액세스할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령을 사용 하 여 확장 만들기
 **도구** 메뉴에 **장식 추가** 라는 메뉴 명령을 배치 하는 VSPackage를 만듭니다.

1. 이라는 c # VSIX 프로젝트를 만들고 `MenuCommandTest` 사용자 지정 명령 항목 템플릿 이름 **addadornment**을 추가 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. MenuCommandTest 라는 솔루션이 열립니다. MenuCommandTestPackage 파일은 메뉴 명령을 만들고 **도구** 메뉴에 배치 하는 코드를 포함 합니다. 이 시점에서 명령은 메시지 상자를 표시 하기만 하면 됩니다. 이후 단계에서는이를 변경 하 여 주석 장식을 표시 하는 방법을 보여 줍니다.

3. VSIX 매니페스트 편집기에서 *source.extension.vsixmanifest* 파일을 엽니다. 이 `Assets` 탭에는 MenuCommandTest 라는 VsPackage VisualStudio 행이 있어야 합니다.

4. *Source.extension.vsixmanifest* 파일을 저장 하 고 닫습니다.

## <a name="add-a-mef-extension-to-the-command-extension"></a>명령 확장에 MEF 확장 추가

1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 클릭 한 다음 **새 프로젝트**를 클릭 합니다. **새 프로젝트 추가** 대화 상자에서 **Visual c #** 의 **확장성** 을 클릭 한 다음 **VSIX 프로젝트**를 클릭 합니다. 프로젝트 이름을 `CommentAdornmentTest`로 지정합니다.

2. 이 프로젝트는 강력한 이름의 VSPackage 어셈블리와 상호 작용 하므로 어셈블리에 서명 해야 합니다. VSPackage 어셈블리에 대해 이미 생성 된 키 파일을 다시 사용할 수 있습니다.

    1. 프로젝트 속성을 열고 **서명** 탭을 선택 합니다.

    2. **어셈블리 서명**을 선택 합니다.

    3. **강력한 이름 키 파일 선택**에서 MenuCommandTest 어셈블리에 대해 생성 된 *key.snk* 파일을 선택 합니다.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage 프로젝트에서 MEF 확장을 참조 하세요.
 VSPackage에 MEF 구성 요소를 추가 하기 때문에 매니페스트에서 두 종류의 자산을 모두 지정 해야 합니다.

> [!NOTE]
> MEF에 대 한 자세한 내용은 [Managed Extensibility Framework (mef)](/dotnet/framework/mef/index)를 참조 하세요.

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage 프로젝트에서 MEF 구성 요소를 참조 하려면

1. MenuCommandTest 프로젝트의 VSIX 매니페스트 편집기에서 *source.extension.vsixmanifest* 파일을 엽니다.

2. **자산** 탭에서 **새로 만들기**를 클릭 합니다.

3. **유형** 목록에서 **VisualStudio**을 선택 합니다.

4. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

5. **프로젝트** 목록에서 **CommentAdornmentTest**를 선택 합니다.

6. *Source.extension.vsixmanifest* 파일을 저장 하 고 닫습니다.

7. MenuCommandTest 프로젝트에 CommentAdornmentTest 프로젝트에 대 한 참조가 있는지 확인 합니다.

8. CommentAdornmentTest 프로젝트에서 프로젝트를 설정 하 여 어셈블리를 생성 합니다. **솔루션 탐색기**에서 프로젝트를 선택 하 고 **속성** 창에서 **OutputDirectory로 빌드 출력 복사** 속성을 찾은 다음 **true**로 설정 합니다.

## <a name="define-a-comment-adornment"></a>주석 장식 정의
 주석 장식 자체는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 선택한 텍스트를 추적 하는와 텍스트의 작성자와 설명을 나타내는 일부 문자열로 구성 됩니다.

#### <a name="to-define-a-comment-adornment"></a>주석 장식을 정의 하려면

1. CommentAdornmentTest 프로젝트에서 새 클래스 파일을 추가 하 고 이름을로 추가 `CommentAdornment` 합니다.

2. 다음 참조를 추가합니다.

    1. VisualStudio. CoreUtility

    2. VisualStudio. 데이터

    3. VisualStudio.

    4. VisualStudio.

    5. VisualStudio. Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. 파일은 라는 클래스를 포함 해야 합니다 `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. `CommentAdornment`클래스에 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , 작성자 및 설명의 3 개 필드를 추가 합니다.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. 필드를 초기화 하는 생성자를 추가 합니다.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>장식의 시각적 요소 만들기
 장식의 시각적 요소를 정의 합니다. 이 연습에서는 Windows Presentation Foundation (WPF) 클래스에서 상속 되는 컨트롤을 정의 <xref:System.Windows.Controls.Canvas> 합니다.

1. CommentAdornmentTest 프로젝트에서 클래스를 만들고 이름을로 만듭니다 `CommentBlock` .

2. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 클래스를 `CommentBlock` 에서 상속 하도록 설정 <xref:System.Windows.Controls.Canvas> 합니다.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. 일부 전용 필드를 추가 하 여 장식의 시각적 측면을 정의 합니다.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. 주석 장식을 정의 하는 생성자를 추가 하 고 관련 텍스트를 추가 합니다.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. 또한 <xref:System.Windows.Controls.Panel.OnRender%2A> 장식을 그리는 이벤트 처리기를 구현 합니다.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>IWpfTextViewCreationListener 추가
 는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 보기 생성 이벤트를 수신 하는 데 사용할 수 있는 MEF 구성 요소 부분입니다.

1. CommentAdornmentTest 프로젝트에 클래스 파일을 추가 하 고 이름을로 추가 `Connector` 합니다.

2. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 을 구현 하는 클래스를 선언 하 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 고 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 및의를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . Content type 특성은 구성 요소가 적용 되는 콘텐츠의 종류를 지정 합니다. 텍스트 형식은 이진이 아닌 모든 파일 형식에 대 한 기본 형식입니다. 따라서 생성 된 거의 모든 텍스트 보기는이 형식이 됩니다. Text view role 특성은 구성 요소가 적용 되는 텍스트 뷰의 종류를 지정 합니다. 문서 텍스트 뷰 역할은 일반적으로 줄로 구성 되 고 파일에 저장 되는 텍스트를 표시 합니다.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>의 정적 이벤트를 호출 하도록 메서드를 구현 합니다 `Create()` `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. 명령을 실행 하는 데 사용할 수 있는 메서드를 추가 합니다.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>장식 계층 정의
 새 장식을 추가 하려면 장식 계층을 정의 해야 합니다.

### <a name="to-define-an-adornment-layer"></a>장식 계층을 정의 하려면

1. 클래스에서 `Connector` 형식의 public 필드를 선언 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> 하 고, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 장식 계층의 고유 이름을 지정 하는와 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 이 장식 계층의 Z-순서 관계를 정의 하는를 사용 하 여 내보냅니다 (텍스트, 캐럿 및 선택).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>주석 장식 제공
 장식을 정의할 때 주석 장식 공급자와 주석 장식 관리자도 구현 합니다. 주석 장식 공급자는 주석 장식 목록을 유지 하 고 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 기본 텍스트 버퍼에서 이벤트를 수신 하 고 내부 텍스트가 삭제 될 때 주석 장식을 삭제 합니다.

1. CommentAdornmentTest 프로젝트에 새 클래스 파일을 추가 하 고 이름을로 만듭니다 `CommentAdornmentProvider` .

2. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. `CommentAdornmentProvider`(이)라는 클래스를 추가합니다.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. 텍스트 버퍼에 대 한 전용 필드와 버퍼와 관련 된 주석 장식의 목록을 추가 합니다.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. 에 대 한 생성자를 추가 `CommentAdornmentProvider` 합니다. 공급자가 메서드에 의해 인스턴스화되기 때문에이 생성자는 전용 액세스 권한이 있어야 합니다 `Create()` . 생성자는 이벤트 `OnBufferChanged` 에 이벤트 처리기를 추가 합니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. `Create()` 메서드를 추가합니다.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. `Detach()` 메서드를 추가합니다.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. `OnBufferChanged`이벤트 처리기를 추가 합니다.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. 이벤트에 대 한 선언을 추가 `CommentsChanged` 합니다.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. 메서드를 만들어 `Add()` 장식을 추가 합니다.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. 메서드를 추가 `RemoveComments()` 합니다.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. 지정 된 `GetComments()` 스냅숏 범위의 모든 주석을 반환 하는 메서드를 추가 합니다.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. 다음과 같이 라는 클래스를 추가 `CommentsChangedEventArgs` 합니다.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>주석 장식 관리
 설명 장식 관리자는 장식을 만들어 장식 계층에 추가 합니다. 이 메서드는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 장식을 이동 하거나 삭제할 수 있도록 및 이벤트를 수신 대기 합니다. 또한 `CommentsChanged` 주석이 추가 되거나 제거 될 때 주석 장식 공급자에서 발생 하는 이벤트를 수신 대기 합니다.

1. CommentAdornmentTest 프로젝트에 클래스 파일을 추가 하 고 이름을로 추가 `CommentAdornmentManager` 합니다.

2. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. `CommentAdornmentManager`(이)라는 클래스를 추가합니다.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. 일부 전용 필드를 추가 합니다.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. 관리자를 구독 하는 생성자를 및 이벤트에 추가 하 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 고 이벤트에도 추가 `CommentsChanged` 합니다. 관리자가 정적 메서드에 의해 인스턴스화되기 때문에 생성자는 private입니다 `Create()` .

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. `Create()`공급자를 가져오는 메서드를 추가 하거나 필요한 경우 하나를 만듭니다.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. 처리기를 추가 `CommentsChanged` 합니다.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. 처리기를 추가 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 합니다.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. 처리기를 추가 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 합니다.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. 주석을 그리는 전용 메서드를 추가 합니다.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>메뉴 명령을 사용 하 여 주석 장식을 추가 합니다.
 메뉴 명령을 사용 하 여 VSPackage의 메서드를 구현 하 여 주석 장식을 만들 수 있습니다 `MenuItemCallback` .

1. MenuCommandTest 프로젝트에 다음 참조를 추가 합니다.

    - VisualStudio입니다.

    - VisualStudio

    - VisualStudio. Wpf

2. *AddAdornment.cs* 파일을 열고 다음 지시문을 추가 합니다 `using` .

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. 메서드를 삭제 `Execute()` 하 고 다음 명령 처리기를 추가 합니다.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. 활성 뷰를 가져오는 코드를 추가 합니다. `SVsTextManager`활성 상태를 가져오려면 Visual Studio 셸의를 가져와야 합니다 `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. 이 텍스트 뷰가 편집기 텍스트 뷰의 인스턴스이면 인터페이스로 캐스팅 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 다음 및 연결 된를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . 를 사용 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 하 여 메서드를 호출 합니다 `Connector.Execute()` .이 메서드는 주석 장식 공급자를 가져오고 장식을 추가 합니다. 명령 처리기는 이제 다음 코드와 같습니다.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. AddAdornmentHandler 메서드를 AddAdornment 생성자의 AddAdornment 명령에 대 한 처리기로 설정 합니다.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트

1. 솔루션을 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 되어야 합니다.

2. 텍스트 파일을 만듭니다. 텍스트를 입력 한 다음 선택 합니다.

3. **도구** 메뉴에서 **장식 추가 호출**을 클릭 합니다. 풍선을 텍스트 창의 오른쪽에 표시 하 고 다음 텍스트와 유사한 텍스트를 포함 해야 합니다.

     YourUserName

     Fourscore...

## <a name="see-also"></a>참조
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
