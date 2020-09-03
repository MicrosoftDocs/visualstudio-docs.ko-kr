---
title: '연습: 편집기 확장에서 바로 가기 키 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201951"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>연습: 편집기 확장에서 바로 가기 키 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 확장에서 바로 가기 키에 응답할 수 있습니다. 다음 연습에서는 바로 가기 키를 사용 하 여 텍스트 뷰에 뷰 장식을 추가 하는 방법을 보여 줍니다. 이 연습은 뷰포트 장식 편집기 템플릿을 기반으로 하며 + 문자를 사용 하 여 장식을 추가할 수 있습니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>MEF(Managed Extensibility Framework) 프로젝트 만들기  
  
1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `KeyBindingTest` 합니다.  
  
2. 프로젝트에 편집기 텍스트 장식 항목 템플릿을 추가 하 고 이름을로 다시 추가 `KeyBindingTest` 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.  
  
3. 다음 참조를 추가 하 고 **CopyLocal** 을로 설정 합니다 `false` .  
  
    VisualStudio  
  
    VisualStudio.  
  
    VisualStudio. 14.0  
  
    VisualStudio입니다.  
  
   KeyBindingTest 클래스 파일에서 클래스 이름을 PurpleCornerBox로 변경 합니다. 왼쪽 여백에 표시 되는 전구를 사용 하 여 다른 적절 한 변경을 수행 합니다. 생성자 내에서 장식 계층의 이름을 **Keybindingtest** 에서 **PurpleCornerBox**로 변경 합니다.  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>명령 필터 정의  
 명령 필터는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 장식을 인스턴스화하여 명령을 처리 하는의 구현입니다.  
  
1. 클래스 파일을 추가하고 이름을 `KeyBindingCommandFilter`로 지정합니다.  
  
2. 다음 using 문을 추가합니다.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. KeyBindingCommandFilter 라는 클래스는에서 상속 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. 텍스트 뷰의 전용 필드, 명령 체인의 다음 명령, 명령 필터가 이미 추가 되었는지 여부를 나타내는 플래그를 추가 합니다.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. 텍스트 뷰를 설정 하는 생성자를 추가 합니다.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. `QueryStatus()`다음과 같이 메서드를 구현 합니다.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. `Exec()`+ 문자를 입력 하는 경우 뷰에 자주색 상자를 추가 하도록 메서드를 구현 합니다.  
  
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
  
## <a name="adding-the-command-filter"></a>명령 필터 추가  
 장식 공급자는 텍스트 뷰에 명령 필터를 추가 해야 합니다. 이 예제에서 공급자는을 구현 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 하 여 텍스트 뷰 생성 이벤트를 수신 합니다. 또한이 장식 공급자는 장식의 Z 순서를 정의 하는 장식 계층을 내보냅니다.  
  
1. KeyBindingTestTextViewCreationListener 파일에서 다음 using 문을 추가 합니다.  
  
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
  
2. 장식 계층 정의에서 AdornmentLayer의 이름을 **Keybindingtest** 에서 **PurpleCornerBox**로 변경 합니다.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. 텍스트 뷰 어댑터를 가져오려면를 가져와야 합니다 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. 메서드를 변경 하 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 여를 추가 `KeyBindingCommandFilter` 합니다.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`처리기는 텍스트 뷰 어댑터를 가져오고 명령 필터를 추가 합니다.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>모든 줄에 장식 표시  
 원본 장식이 텍스트 파일의 모든 문자 ' a '에 표시 됩니다. 이제 ' + ' 문자에 대 한 응답으로 장식을 추가 하도록 코드를 변경 했으므로 ' + '가 입력 된 줄에만 장식을 추가 합니다. 장식 코드를 변경 하 여 모든 ' a '에 더 많이 표시 되도록 할 수 있습니다.  
  
 KeyBindingTest.cs 파일에서 CreateVisuals 개체 () 메서드를 변경 하 여 뷰의 모든 줄을 반복 하 고 ' a ' 문자를 장식 합니다.  
  
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
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
  
1. KeyBindingTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
2. 텍스트 파일을 만들거나 엽니다. 문자 ' a '를 포함 하는 단어를 입력 한 다음 텍스트 보기에서 +를 입력 합니다.  
  
     자주색 사각형은 파일의 모든 ' a ' 문자에 표시 되어야 합니다.
