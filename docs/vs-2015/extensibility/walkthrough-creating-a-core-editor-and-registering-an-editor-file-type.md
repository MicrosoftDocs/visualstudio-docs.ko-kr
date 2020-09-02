---
title: '연습: 핵심 편집기 만들기 및 편집기 파일 형식 등록 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687642"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>연습: 코어 편집기 만들기 및 편집기 파일 형식 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . myext 파일 이름 확장명을 가진 파일이 로드 될 때 핵심 편집기를 시작 하는 VSPackage를 만드는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿의 위치  
 Visual Studio 패키지 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 세 가지 서로 다른 위치에 있습니다.  
  
1. Visual Basic 확장성에 위치한 템플릿 프로젝트의 기본 언어는 Visual Basic입니다.  
  
2. C# 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C#입니다.  
  
3. 다른 프로젝트 형식 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C++입니다.  
  
### <a name="to-create-the-vspackage"></a>VSPackage를 만들려면  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] `MyPackage` [연습: 메뉴 명령 만들기 VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32)에 설명 된 대로를 시작 하 고 VSPackage를 만듭니다.  
  
### <a name="to-add-the-editor-factory"></a>편집기 팩터리를 추가 하려면  
  
1. **MyPackage** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 가리킨 다음 **클래스**를 클릭 합니다.  
  
2. **새 항목 추가** 대화 상자에서 **클래스** 템플릿이 선택 되어 있는지 확인 하 고 이름으로를 입력 한 `EditorFactory.cs` 다음 **추가** 를 클릭 하 여 클래스를 프로젝트에 추가 합니다.  
  
     EditorFactory.cs 파일이 자동으로 열립니다.  
  
3. 코드에서 다음 어셈블리를 참조 합니다.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. 클래스 `EditorFactory` 선언 바로 앞에 특성을 추가 하 여 클래스에 GUID를 추가 `Guid` 합니다.  
  
     명령 프롬프트에서 guidgen.exe 프로그램 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 을 사용 하거나 **도구** 메뉴에서 **guid 만들기** 를 클릭 하 여 새 guid를 생성할 수 있습니다. 여기에 사용 되는 GUID는 예입니다. 프로젝트에 사용 하지 마세요.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. 클래스 정의에서 부모 패키지 및 서비스 공급자를 포함 하는 두 개의 private 변수를 추가 합니다.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. 형식의 매개 변수 하나를 사용 하는 public 클래스 생성자를 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Package> .  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. `EditorFactory`인터페이스에서 파생 되도록 클래스 선언을 수정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. 마우스 오른쪽 단추 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 를 클릭 하 고 **인터페이스 구현**을 클릭 한 다음 **명시적으로 인터페이스 구현**을 클릭 합니다.  
  
     이렇게 하면 인터페이스에 구현 해야 하는 네 가지 메서드가 추가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 됩니다.  
  
9. `IVsEditorFactory.Close` 메서드의 콘텐츠를 다음 코드로 바꿉니다.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 의 내용을 `IVsEditorFactory.SetSite` 다음 코드로 바꿉니다.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. `IVsEditorFactory.MapLogicalView` 메서드의 콘텐츠를 다음 코드로 바꿉니다.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. `IVsEditorFactory.CreateEditorInstance` 메서드의 콘텐츠를 다음 코드로 바꿉니다.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. 프로젝트를 컴파일하고 오류가 없는지 확인 합니다.  
  
### <a name="to-register-the-editor-factory"></a>편집기 팩터리를 등록 하려면  
  
1. **솔루션 탐색기**에서 리소스 .resx 파일을 두 번 클릭 하 여 문자열 테이블에 엽니다. 여기서 **String1** 항목을 선택 합니다.  
  
2. 식별자의 이름을로 변경 하 `IDS_EDITORNAME` 고 텍스트를 **MyPackage 편집기** 로 변경 합니다. 이 문자열은 편집기의 이름으로 표시 됩니다.  
  
3. VSPackage 파일을 열고 이름을 **101** 로 설정 하 고 값을로 설정 `IDS_EDITORNAME` 합니다. 이렇게 하면 패키지에 리소스 ID를 제공 하 여 방금 만든 문자열에 액세스할 수 있습니다.  
  
    > [!NOTE]
    > VSPackage 파일에 특성이 101로 설정 된 다른 문자열이 포함 된 경우 `name` 다음 **101**단계에서 다른 고유한 숫자 값으로 대체 합니다.  
  
4. **솔루션 탐색기**에서 MyPackagePackage.cs 파일을 엽니다.  
  
     이 파일은 주 패키지 파일입니다.  
  
5. 특성 바로 앞에 다음 사용자 특성을 추가 `Guid` 합니다.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>특성은 확장명이 인 파일이 로드 될 때마다 편집기 팩터리가 호출 되도록 .myext 파일 확장명을 편집기 팩터리에 연결 합니다.  
  
6. 생성자 바로 앞에 private 변수를 클래스에 추가 하 `MyPackage` 고 해당 형식을 지정 `EditorFactory` 합니다.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. 메서드를 찾고 `Initialize` (숨겨진 영역을 열어야 할 수도 있음 `Package Members` )에 대 한 호출 뒤에 다음 코드를 추가 `base.Initialize()` 합니다.  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. 프로그램을 컴파일하고 오류가 없는지 확인합니다.  
  
     이 단계에서는의 실험적 레지스트리 하이브에 편집기 팩터리를 등록 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Resource.h 파일을 재정의 하 라는 메시지가 표시 되 면 **확인**을 클릭 합니다.  
  
9. Textfile1.txt 라는 샘플 파일을 만듭니다.  
  
10. **F5** 키를 눌러 실험적 인스턴스를 엽니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. 실험적의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **파일** 메뉴에서 **열기** 를 가리킨 다음 **파일**을 클릭 합니다.  
  
12. Textfile1.txt을 찾은 다음 **열기**를 클릭 합니다.  
  
     이제 파일이 로드 됩니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]핵심 편집기는 다양 한 텍스트 기반 파일 형식을 처리 하 고 언어 서비스와 긴밀 하 게 작동 하 여 구문 강조 표시, 중괄호 일치, IntelliSense 단어 완성 및 멤버 완성 목록과 같은 풍부한 기능을 제공 합니다. 텍스트 기반 파일로 작업 하는 경우 특정 파일 형식을 지 원하는 사용자 지정 언어 서비스와 함께 핵심 편집기를 사용할 수 있습니다.  
  
 VSPackage는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기 팩터리를 제공 하 여 핵심 편집기를 호출할 수 있습니다. 이 편집기 팩터리는 연결 된 파일이 로드 될 때마다 사용 됩니다. 파일이 프로젝트의 일부인 경우에는 VSPackage에 의해 재정의 되지 않는 한 핵심 편집기가 자동으로 호출 됩니다. 그러나 파일이 프로젝트 외부에서 로드 되는 경우에는 VSPackage에서 핵심 편집기를 명시적으로 호출 해야 합니다.  
  
 핵심 편집기에 대 한 자세한 내용은 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)를 참조 하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)   
 [레거시 API를 사용하여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
