---
title: '연습: 편집기 확장이 있는 바로 가기 키 사용 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697146"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>연습: 편집기 확장이 있는 바로 가기 키 사용
편집기 확장에서 바로 가기 키에 응답할 수 있습니다. 다음 연습에서는 바로 가기 키를 사용하여 텍스트 보기에 뷰 장식을 추가하는 방법을 보여 주십니다. 이 연습은 뷰포트 장식 편집기 템플릿을 기반으로 하며 + 문자를 사용하여 장식을 추가할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>관리되는 확장성 프레임워크(MEF) 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `KeyBindingTest`이름을 지정합니다.

2. 편집기 텍스트 장식 항목 템플릿을 프로젝트에 `KeyBindingTest`추가하고 이름을 지정합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 다음 참조를 추가하고 **CopyLocal을** 다음으로 `false`설정합니다.

    마이크로소프트.비주얼스튜디오.에디터

    마이크로소프트.비주얼스튜디오.올레.인터롭

    마이크로소프트.비주얼 스튜디오.쉘.14.0

    마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭

   KeyBindingTest 클래스 파일에서 클래스 이름을 PurpleCornerBox로 변경합니다. 왼쪽 여백에 나타나는 전구를 사용하여 다른 적절한 변경을 합니다. 생성자 내부에서 장식 레이어의 이름을 **KeyBindingTest에서** **보라색코너박스로**변경합니다.

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

KeyBindingTestTextViewCreationListener.cs 클래스 파일에서 AdornmentLayer의 이름을 **키 바인딩 테스트에서** **자주색코너로**변경합니다.

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>TYPECHAR 명령 처리
Visual Studio 2017 버전 15.6 이전에는 편집기 확장에서 명령을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 처리하는 유일한 방법은 기반 명령 필터를 구현하는 것이었습니다. Visual Studio 2017 버전 15.6에서는 편집기 명령 처리기를 기반으로 하는 최신 단순화된 접근 방식을 도입했습니다. 다음 두 섹션에서는 레거시 및 최신 접근 방식을 모두 사용하여 명령을 처리하는 방법을 보여 줍니다.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>명령 필터 정의(Visual Studio 2017 버전 15.6 이전)

 명령 필터는 장식을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>인스턴스화하여 명령을 처리하는 의 구현입니다.

1. 클래스 파일을 추가하고 이름을 `KeyBindingCommandFilter`로 지정합니다.

2. 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. KeyBindingCommandFilter라는 클래스는 에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>상속해야 합니다.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. 텍스트 보기에 대한 개인 필드, 명령 체인의 다음 명령 및 명령 필터가 이미 추가되었는지 여부를 나타내는 플래그를 추가합니다.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. 텍스트 보기를 설정하는 생성자추가합니다.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. 메서드를 `QueryStatus()` 다음과 같이 구현합니다.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. plus `Exec()` sign ()**+** 문자를 입력하는 경우 보기에 보라색 상자를 추가하도록 메서드를 구현합니다.

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>명령 필터 추가(Visual Studio 2017 버전 15.6 이전)
 장식 공급자는 텍스트 보기에 명령 필터를 추가해야 합니다. 이 예제에서 공급자는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 텍스트 보기 만들기 이벤트를 수신절하는 것을 구현합니다. 이 장식 공급자는 장식의 Z 순서를 정의하는 장식 레이어도 내보올링합니다.

1. 키바인딩테스트텍스트뷰크리에이터 파일에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. 텍스트 보기 어댑터를 가져오려면 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>를 가져와야 합니다.

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. 메서드를 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 추가하여 메서드를 `KeyBindingCommandFilter`변경합니다.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. 처리기는 `AddCommandFilter` 텍스트 뷰 어댑터를 받고 명령 필터를 추가합니다.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>명령 처리기 구현(Visual Studio 2017 버전 15.6에서 시작)

먼저 프로젝트의 Nuget 참조를 업데이트하여 최신 편집기 API를 참조합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Nuget 패키지 관리를 선택합니다.**

2. **Nuget 패키지 관리자에서** **업데이트** 탭을 선택하고 모든 패키지 선택 **확인란을** 선택한 다음 **업데이트를**선택합니다.

명령 처리기는 장식을 인스턴스화하여 명령을 처리하는 <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>의 구현입니다.

1. 클래스 파일을 추가하고 이름을 `KeyBindingCommandHandler`로 지정합니다.

2. 지시문을 사용하여 다음을 추가합니다.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. KeyBindingCommandHandler라는 클래스는 `ICommandHandler<TypeCharCommandArgs>`에서 상속하고 다음으로 <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>내보내야 합니다.

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. 명령 처리기의 표시 이름을 추가합니다.

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. 메서드를 `GetCommandState()` 다음과 같이 구현합니다. 이 명령 처리기는 코어 편집기 TYPECHAR 명령을 처리하므로 코어 편집기에 명령을 사용하도록 위임할 수 있습니다.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. plus `ExecuteCommand()` sign ()**+** 문자를 입력하는 경우 보기에 보라색 상자를 추가하도록 메서드를 구현합니다.

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. KeyBindingTestTextViewCreationListener.cs *파일에서* *KeyBindingCommandHandler.cs* 장식 도면층 정의를 복사한 다음 *KeyBindingTestTextViewCreationListener.cs* 파일을 삭제합니다.

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>모든 줄에 장식이 표시되도록 합니다.

원래 장식은 텍스트 파일의 모든 문자 'a'에 나타났습니다. 이제 **+** 문자에 대한 응답으로 장식을 추가하도록 코드를 변경되었으므로 문자가 입력된 줄에만 장식이 **+** 추가됩니다. 장식 코드가 모든 'a'에 다시 나타나게 할 수 있습니다.

*KeyBindingTest.cs* 파일에서 뷰의 `CreateVisuals()` 모든 줄을 반복하여 'a' 문자를 장식하도록 메서드를 변경합니다.

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트

1. KeyBindingTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

2. 텍스트 파일을 만들거나 엽니다. 문자 'a'를 포함하는 일부 단어를 입력한 다음 텍스트 보기의 아무 곳이나 입력합니다. **+**

     파일의 모든 'a' 문자에 보라색 사각형이 나타나야 합니다.
