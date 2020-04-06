---
title: '연습: 편집기 확장이 있는 셸 명령 사용 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697159"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>연습: 편집기 확장이 있는 셸 명령 사용
VSPackage에서 메뉴 명령과 같은 기능을 편집기에 추가할 수 있습니다. 이 연습에서는 메뉴 명령을 호출하여 편집기의 텍스트 보기에 장식을 추가하는 방법을 보여 줍니다.

 이 연습에서는 관리되는 확장성 프레임워크(MEF) 구성 요소 부분과 함께 VSPackage를 사용하는 것을 보여 줍니다. VSPackage를 사용하여 메뉴 명령을 Visual Studio 셸에 등록해야 합니다. 또한 명령을 사용하여 MEF 구성 요소 부품에 액세스할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령으로 확장 만들기
 **도구** 메뉴에 **장식 추가라는** 메뉴 명령을 넣는 VSPackage를 만듭니다.

1. 라는 `MenuCommandTest`C # VSIX 프로젝트를 만들고 사용자 지정 명령 항목 템플릿 이름 **AddAdornment를**추가 합니다. 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. MenuCommandTest라는 솔루션이 열립니다. MenuCommandTestPackage 파일에는 메뉴 명령을 만들고 **도구** 메뉴에 배치하는 코드가 있습니다. 이 시점에서 명령은 메시지 상자를 표시합니다. 이후 단계에서는 주석 장식을 표시하도록 변경하는 방법을 보여 줄 것입니다.

3. VSIX 매니페스트 편집기에서 *source.extension.vsixmanifest* 파일을 엽니다. 탭에는 `Assets` Microsoft.VisualStudio.VsPackage라는 이름의 MenuCommandTest에 대한 행이 있어야 합니다.

4. *source.extension.vsixmanifest* 파일을 저장하고 닫습니다.

## <a name="add-a-mef-extension-to-the-command-extension"></a>명령 확장에 MEF 확장 추가

1. **솔루션 탐색기에서**솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **에서 추가를**클릭한 다음 **새 프로젝트**를 클릭합니다. 새 **프로젝트 추가** 대화 상자에서 **Visual C#** 및 **VSIX 프로젝트**에서 **확장성을** 클릭합니다. 프로젝트 `CommentAdornmentTest`의 이름을 지정합니다.

2. 이 프로젝트는 강력한 이름의 VSPackage 어셈블리와 상호 작용하므로 어셈블리에 서명해야 합니다. VSPackage 어셈블리에 대해 이미 만든 키 파일을 다시 사용할 수 있습니다.

    1. 프로젝트 속성을 열고 **서명** 탭을 선택합니다.

    2. **어셈블리 서명을 선택합니다.**

    3. **강력한 이름 키 파일 선택에서**MenuCommandTest 어셈블리에 대해 생성된 *Key.snk* 파일을 선택합니다.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage 프로젝트의 MEF 확장 참조
 VSPackage에 MEF 구성 요소를 추가하기 때문에 매니페스트에 두 가지 종류의 자산을 모두 지정해야 합니다.

> [!NOTE]
> MEF에 대한 자세한 내용은 [MEF(관리되는 확장성 프레임워크)를](/dotnet/framework/mef/index)참조하십시오.

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage 프로젝트의 MEF 구성 요소를 참조하려면

1. MenuCommandTest 프로젝트에서 VSIX 매니페스트 편집기에서 *source.extension.vsixmanifest* 파일을 엽니다.

2. **자산** 탭에서 새 을 **클릭합니다.**

3. **유형** 목록에서 **Microsoft.VisualStudio.Mef구성 요소를**선택합니다.

4. **소스** 목록에서 현재 **솔루션의 A 프로젝트를 선택합니다.**

5. **프로젝트** 목록에서 **CommentAdornmentTest를**선택합니다.

6. *source.extension.vsixmanifest* 파일을 저장하고 닫습니다.

7. MenuCommandTest 프로젝트에 CommentAdornmentTest 프로젝트에 대한 참조가 있는지 확인합니다.

8. CommentAdornmentTest 프로젝트에서 어셈블리를 생성하도록 프로젝트를 설정합니다. 솔루션 **탐색기에서**프로젝트를 선택하고 **[출력에 대한 복사 빌드 출력]** **창에서** 보고 **이를 true로**설정합니다.

## <a name="define-a-comment-adornment"></a>주석 장식 정의
 주석 장식 자체는 선택한 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 텍스트를 추적하는 문자열과 작성자 및 텍스트 설명을 나타내는 일부 문자열로 구성됩니다.

#### <a name="to-define-a-comment-adornment"></a>주석 장식을 정의하려면

1. CommentAdornmentTest 프로젝트에서 새 클래스 파일을 추가하고 이름을 `CommentAdornment`지정합니다.

2. 다음 참조를 추가합니다.

    1. 마이크로소프트.비주얼 스튜디오.코어유틸리티

    2. 마이크로소프트.비주얼 스튜디오.텍스트.데이터

    3. 마이크로소프트.비주얼 스튜디오.텍스트.로직

    4. 마이크로소프트.비주얼 스튜디오.텍스트.UI

    5. 마이크로소프트.비주얼 스튜디오.텍스트.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. 다음 지시문을 추가합니다. `using`

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. 파일에는 .라는 `CommentAdornment`클래스가 포함되어야 합니다.

    ```csharp
    internal class CommentAdornment
    ```

5. 의 작성자 `CommentAdornment` 및 설명에 대한 세 개의 필드를 클래스에 추가합니다. <xref:Microsoft.VisualStudio.Text.ITrackingSpan>

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. 필드를 초기화하는 생성자추가합니다.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>장식에 대한 시각적 요소 만들기
 장식에 대한 시각적 요소를 정의합니다. 이 연습에서는 WPF(Windows 프레젠테이션 파운데이션) 클래스에서 <xref:System.Windows.Controls.Canvas>상속하는 컨트롤을 정의합니다.

1. CommentAdornmentTest 프로젝트에서 클래스를 만들고 이름을 `CommentBlock`지정합니다.

2. 다음 `using` 지시문을 추가합니다.

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

3. 클래스를 `CommentBlock` <xref:System.Windows.Controls.Canvas>상속합니다.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. 일부 개인 필드를 추가하여 장식의 시각적 측면을 정의합니다.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. 주석 장식을 정의하고 관련 텍스트를 추가하는 생성자추가합니다.

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

6. 또한 장식을 그리는 <xref:System.Windows.Controls.Panel.OnRender%2A> 이벤트 처리기를 구현합니다.

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

## <a name="add-an-iwpftextviewcreationlistener"></a>IWpfTextView크리에이션 추가
 는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 생성 이벤트를 보는 데 사용할 수 있는 MEF 구성 요소 부분입니다.

1. CommentAdornmentTest 프로젝트에 클래스 파일을 추가하고 이름을 `Connector`지정합니다.

2. 다음 `using` 지시문을 추가합니다.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. 을 구현하는 클래스를 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>선언하고 "text" 및 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>a.를 사용 하여 내보냅니다. 콘텐츠 형식 특성은 구성 요소가 적용되는 콘텐츠의 종류를 지정합니다. 텍스트 형식은 이진이 아닌 모든 파일 형식의 기본 형식입니다. 따라서 생성되는 거의 모든 텍스트 보기는 이 유형이 됩니다. 텍스트 보기 역할 특성은 구성 요소가 적용되는 텍스트 뷰의 종류를 지정합니다. 문서 텍스트 보기 역할은 일반적으로 선으로 구성되고 파일에 저장되는 텍스트를 표시합니다.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. 의 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 정적 `Create()` 이벤트를 호출할 수 있도록 `CommentAdornmentManager`메서드를 구현합니다.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. 명령을 실행하는 데 사용할 수 있는 메서드를 추가합니다.

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

## <a name="define-an-adornment-layer"></a>장식 레이어 정의
 새 장식을 추가하려면 장식 레이어를 정의해야 합니다.

### <a name="to-define-an-adornment-layer"></a>장식 레이어를 정의하려면

1. `Connector` 클래스에서 형식의 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>공용 필드를 선언하고 장식 레이어에 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> 대한 고유한 이름을 지정하는 것으로 내보내고 이 장식 레이어의 Z-order 관계를 다른 텍스트 뷰 레이어(텍스트, 캐릿 및 선택)로 정의합니다.

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>댓글 장식 제공
 장식을 정의할 때 주석 장식 공급자와 주석 장식 관리자도 구현합니다. 주석 장식 공급자는 주석 장식 목록을 유지하고, 기본 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 텍스트 버퍼의 이벤트를 듣고, 기본 텍스트가 삭제될 때 주석 장식을 삭제합니다.

1. CommentAdornmentTest 프로젝트에 새 클래스 파일을 추가하고 `CommentAdornmentProvider`이름을 지정합니다.

2. 다음 `using` 지시문을 추가합니다.

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

4. 텍스트 버퍼에 대한 개인 필드와 버퍼와 관련된 주석 장식 목록을 추가합니다.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. 에 대한 `CommentAdornmentProvider`생성자 추가 이 생성자는 메서드에 의해 공급자가 인스턴스화되므로 `Create()` 개인 액세스 권한이 있어야 합니다. 생성자는 `OnBufferChanged` 이벤트 처리기를 이벤트에 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 추가합니다.

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

8. `OnBufferChanged` 이벤트 처리기를 추가합니다.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. 이벤트에 대한 선언을 추가합니다. `CommentsChanged`

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. 장식을 `Add()` 추가하는 메서드를 만듭니다.

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

11. 메서드를 `RemoveComments()` 추가합니다.

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

12. 지정된 `GetComments()` 스냅숏 범위의 모든 주석을 반환하는 메서드를 추가합니다.

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

13. 이라는 클래스를 `CommentsChangedEventArgs`다음과 같이 추가합니다.

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

## <a name="manage-comment-adornments"></a>댓글 장식 관리
 주석 장식 관리자는 장식을 만들고 장식 레이어에 추가합니다. 장식을 이동하거나 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 삭제할 수 있도록 및 이벤트를 수신합니다. 또한 주석이 `CommentsChanged` 추가되거나 제거될 때 주석 표시 공급자가 발생시키는 이벤트를 수신 대기합니다.

1. CommentAdornmentTest 프로젝트에 클래스 파일을 추가하고 이름을 `CommentAdornmentManager`지정합니다.

2. 다음 `using` 지시문을 추가합니다.

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

4. 일부 개인 필드를 추가합니다.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 관리자를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 구독하는 생성자 및 이벤트 및 `CommentsChanged` 이벤트에 추가합니다. 생성자는 정적 `Create()` 메서드에 의해 관리자가 인스턴스화되므로 비공개입니다.

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

6. 공급자를 `Create()` 얻거나 필요한 경우 공급자를 만드는 메서드를 추가합니다.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. 처리기를 `CommentsChanged` 추가합니다.

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

8. 처리기를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> 추가합니다.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. 처리기를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 추가합니다.

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

10. 주석을 그리는 개인 메서드를 추가합니다.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>메뉴 명령을 사용하여 주석 장식 추가
 VSPackage의 `MenuItemCallback` 메서드를 구현 하 여 주석 장식을 만들 수 있는 메뉴 명령을 사용할 수 있습니다.

1. MenuCommandTest 프로젝트에 다음 참조를 추가합니다.

    - 마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭

    - 마이크로소프트.비주얼스튜디오.에디터

    - 마이크로소프트.비주얼 스튜디오.텍스트.UI.Wpf

2. *AddAdornment.cs* 파일을 열고 다음 `using` 지시문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. 메서드를 `Execute()` 삭제 하고 다음 명령 처리기를 추가 합니다.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. 활성 보기를 얻으려면 코드를 추가합니다. 활성 `IVsTextView`을 `SVsTextManager` 얻으려면 Visual Studio 셸을 얻어야 합니다.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. 이 텍스트 뷰가 편집기 텍스트 뷰의 인스턴스인 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 인터페이스에 캐스팅한 다음 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>해당 및 관련 을 얻을 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 수 있습니다. 을 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 사용하여 메서드를 `Connector.Execute()` 호출하여 주석 장식 공급자를 얻고 장식을 추가합니다. 이제 명령 처리기는 다음 코드와 같습니다.

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

6. AddAdornmentHandler 메서드를 AddAdornment 생성자에서 AddAdornment 명령어에 대 한 처리기로 설정 합니다.

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

1. 솔루션을 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

2. 텍스트 파일을 만듭니다. 일부 텍스트를 입력한 다음 선택합니다.

3. **도구** 메뉴에서 **장전 추가 호출을 클릭합니다.** 풍선은 텍스트 창의 오른쪽에 표시되어야 하며 다음 텍스트와 유사한 텍스트를 포함해야 합니다.

     사용자 이름

     네 스코어 ...

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
