---
title: 속성 창에 속성 노출 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c28a0520680951920ee19e91f3df098066f432dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841459"
---
# <a name="exposing-properties-to-the-properties-window"></a>속성 창에 속성 노출
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 개체의 공용 속성을 **속성** 창에 노출 합니다. 이러한 속성에 대 한 변경 내용은 **속성** 창에 반영 됩니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="exposing-properties-to-the-properties-window"></a>속성 창에 속성 노출  
 이 섹션에서는 사용자 지정 도구 창을 만들고 **속성** 창에 연결 된 창 개체의 공용 속성을 표시 합니다.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>속성 창에 속성을 노출 하려면  
  
1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트로 시작 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]이라는 VSIX 프로젝트를 만듭니다 `MyObjectPropertiesExtension` . **새 프로젝트** 대화 상자의 **Visual c #/확장성**에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.  
  
2. 이라는 사용자 지정 도구 창 항목 템플릿을 추가 하 여 도구 창을 추가 `MyToolWindow` 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택 합니다. **새 항목 추가 대화 상자**에서 **Visual c # 항목/확장성** 으로 이동 하 고 **사용자 지정 도구 창**을 선택 합니다. 대화 상자의 맨 아래에 있는 **이름** 필드에서 파일 이름을으로 변경 합니다 `MyToolWindow.cs` . 사용자 지정 도구 창을 만드는 방법에 대 한 자세한 내용은 [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조 하세요.  
  
3. MyToolWindow.cs를 열고 다음 using 문을 추가 합니다.  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. 이제 클래스에 다음 필드를 추가 합니다 `MyToolWindow` .  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. 가리키고 mytoolwindow 클래스에 다음 코드를 추가 합니다.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`속성은 `GetService` 를 사용 하 여 `STrackSelection` 인터페이스를 제공 하는 서비스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . `OnToolWindowCreated`이벤트 처리기 및 `SelectList` 메서드는 도구 창 창 개체만 포함 하는 선택 된 개체 목록을 만듭니다. `UpdateSelection`메서드는 **속성** 창에 도구 창 창의 공용 속성을 표시 하도록 지시 합니다.  
  
6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 되어야 합니다.  
  
7. **속성** 창이 표시 되지 않으면 F4 키를 눌러 엽니다.  
  
8. **가리키고 mytoolwindow** 창을 엽니다. **뷰/다른 창**에서 찾을 수 있습니다.  
  
     창이 열리고 창 창의 공용 속성이 **속성** 창에 나타납니다.  
  
9. **속성** 창의 **Caption** 속성을 **내 개체 속성**으로 변경 합니다.  
  
     가리키고 mytoolwindow 창 캡션은 그에 따라 변경 됩니다.  
  
## <a name="exposing-tool-window-properties"></a>도구 창 속성 노출  
 이 섹션에서는 도구 창을 추가 하 고 해당 속성을 노출 합니다. 속성에서 변경한 내용은 **속성** 창에 반영 됩니다.  
  
#### <a name="to-expose-tool-window-properties"></a>도구 창 속성을 노출 하려면  
  
1. MyToolWindow.cs을 열고 public boolean 속성 IsChecked를 가리키고 mytoolwindow 클래스에 추가 합니다.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     이 속성은 나중에 만들 WPF 확인란에서 해당 상태를 가져옵니다.  
  
2. MyToolWindowControl.xaml.cs를 열고 MyToolWindowControl 생성자를 다음 코드로 바꿉니다.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     이렇게 하면 `MyToolWindowControl` 창에 액세스할 수 `MyToolWindow` 있습니다.  
  
3. MyToolWindow.cs에서 `MyToolWindow` 생성자를 다음과 같이 변경 합니다.  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. MyToolWindowControl의 디자인 뷰로 변경 합니다.  
  
5. 단추를 삭제 하 고 **도구 상자** 의 왼쪽 위 모퉁이에 확인란을 추가 합니다.  
  
6. Checked 및 Unchecked 이벤트를 추가 합니다. 디자인 뷰에서 확인란을 선택 합니다. **속성** 창에서 **속성** 창의 오른쪽 위에 있는 이벤트 처리기 단추를 클릭 합니다. 확인을 찾아 텍스트 상자에 **checkbox_Checked** 를 입력 하 고, **선택 하지 않은** **상태** 를 찾아 텍스트 상자에 **checkbox_Unchecked** 를 입력 합니다.  
  
7. 확인란 이벤트 처리기를 추가 합니다.  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
9. 실험적 인스턴스에서 **가리키고 mytoolwindow** 창을 엽니다.  
  
     **속성** 창에서 창의 속성을 찾습니다. **Ischecked** 속성이 창의 아래쪽에 있는 **내 속성** 범주 아래에 나타납니다.  
  
10. **가리키고 mytoolwindow** 창에서 확인란을 선택 합니다. **속성** 창의 **Ischecked** 가 **True**로 변경 됩니다. **가리키고 mytoolwindow** 창에서 확인란의 선택을 취소 합니다. **속성** 창의 **Ischecked** 가 **False**로 변경 됩니다. **속성** 창에서 **ischecked** 값을 변경 합니다. **가리키고 mytoolwindow** 창의 확인란이 새 값과 일치 하도록 변경 됩니다.  
  
    > [!NOTE]
    > **속성** 창에 표시 되는 개체를 삭제 해야 하는 경우 `OnSelectChange` 먼저 선택 컨테이너를 사용 하 여를 호출 `null` 합니다. 속성이 나 개체를 삭제 한 후에는 업데이트 된 및 목록을 포함 하는 선택 컨테이너로 변경할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> .  
  
## <a name="changing-selection-lists"></a>선택 목록 변경  
 이 섹션에서는 기본 속성 클래스에 대 한 선택 목록을 추가 하 고 도구 창 인터페이스를 사용 하 여 표시할 선택 목록을 선택 합니다.  
  
#### <a name="to-change-selection-lists"></a>선택 목록을 변경 하려면  
  
1. MyToolWindow.cs를 열고 이라는 public 클래스를 추가 `Simple` 합니다.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2. 가리키고 mytoolwindow 클래스에 SimpleObject 속성을 추가 하 고, 창 창과 개체 사이에 **속성** 창 선택을 전환 하는 두 가지 메서드를 추가 `Simple` 합니다.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3. MyToolWindowControl.cs에서 확인란 처리기를 다음 코드 줄로 바꿉니다.  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
5. 실험적 인스턴스에서 **가리키고 mytoolwindow** 창을 엽니다.  
  
6. **가리키고 mytoolwindow** 창에서 확인란을 선택 합니다. **속성** 창에는 `Simple` 개체 속성 **SomeText** 및 **ReadOnly**가 표시 됩니다. 확인란을 선택 취소합니다. 창의 공용 속성은 **속성** 창에 표시 됩니다.  
  
    > [!NOTE]
    > **SomeText** 의 표시 이름은 **내 텍스트**입니다.  
  
## <a name="best-practice"></a>모범 사례  
 이 연습에서 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 는 선택 가능한 개체 컬렉션과 선택한 개체 컬렉션이 동일한 컬렉션을 위해 구현 됩니다. 선택한 개체만 속성 브라우저 목록에 표시 됩니다. 보다 완전 한 ISelectionContainer 구현에 대 한 자세한 내용은 참조 ToolWindow 샘플을 참조 하세요.  
  
 Visual studio 도구 창은 Visual Studio 세션 사이에서 지속 됩니다. 도구 창 상태를 유지 하는 방법에 대 한 자세한 내용은을 참조 하십시오 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="see-also"></a>참고 항목  
 [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)
