---
title: 속성 창에 속성 노출 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711824"
---
# <a name="expose-properties-to-the-properties-window"></a>속성 창에 속성 노출

이 연습은 개체의 공용 속성을 **속성** 창에 노출시다. 이러한 속성에 대한 변경 내용은 **속성** 창에 반영됩니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="expose-properties-to-the-properties-window"></a>속성 창에 속성 노출

이 섹션에서는 사용자 지정 도구 창을 만들고 **속성** 창에서 연결된 창 개체의 공용 속성을 표시합니다.

### <a name="to-expose-properties-to-the-properties-window"></a>속성 창에 속성을 노출하려면

1. 모든 Visual Studio 확장은 확장 에셋을 포함하는 VSIX 배포 프로젝트로 시작합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트를 `MyObjectPropertiesExtension`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. .라는 사용자 지정 도구 창 항목 `MyToolWindow`항목 템플릿을 추가하여 도구 창을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가 대화 상자에서** **Visual C# 항목** > **확장성으로** 이동하여 **사용자 지정 도구 창을**선택합니다. 대화 상자 아래쪽에 있는 **이름** 필드에서 파일 이름을 *MyToolWindow.cs.* 사용자 지정 도구 창을 만드는 방법에 대한 자세한 내용은 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

3. *MyToolWindow.cs* 열고 문을 사용하여 다음을 추가합니다.

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. 이제 클래스에 다음 `MyToolWindow` 필드를 추가합니다.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. `MyToolWindow` 클래스에 다음 코드를 추가합니다.

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

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    속성은 `TrackSelection` `GetService` `STrackSelection` <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 인터페이스를 제공하는 서비스를 가져오는 데 사용합니다. 이벤트 `OnToolWindowCreated` 처리기와 `SelectList` 메서드는 함께 도구 창 창 개체 자체만 포함 하는 선택 된 개체의 목록을 만듭니다. 메서드는 `UpdateSelection` **속성** 창에 도구 창창의 공용 속성을 표시 하도록 지시 합니다.

6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타나야 합니다.

7. **속성** 창이 표시되지 않으면 **F4를**눌러 엽니다.

8. **MyTool창** 창을 엽니다. **다른 Windows** **보기에서** > 찾을 수 있습니다.

    창이 열리고 창창의 공용 속성이 **속성** 창에 나타납니다.

9. **속성** 창에서 **캡션** 속성을 **내 개체**속성으로 변경합니다.

     MyToolWindow 창 캡션은 그에 따라 변경됩니다.

## <a name="expose-tool-window-properties"></a>공구 창 속성 노출

이 섹션에서는 도구 창을 추가하고 해당 속성을 노출합니다. 속성에 대한 변경 내용은 **속성** 창에 반영됩니다.

### <a name="to-expose-tool-window-properties"></a>도구 창 속성을 노출하려면

1. *MyToolWindow.cs*열고 공용 부울 속성을 클래스에 `MyToolWindow` 추가합니다.

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

2. *MyToolWindowControl.xaml.cs* 열고 MyToolWindowControl 생성자를 다음 코드로 바꿉니다.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     이렇게 `MyToolWindowControl` 하면 창에 `MyToolWindow` 액세스할 수 있습니다.

3. *MyToolWindow.cs* `MyToolWindow` 다음과 같이 생성자 변경합니다.

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. MyToolWindowControl의 설계 보기로 변경합니다.

5. 단추를 삭제하고 도구 상자에서 왼쪽 위 모서리에 확인란을 **추가합니다.**

6. 선택및 선택되지 않은 이벤트를 추가합니다. 설계 뷰에서 확인란을 선택합니다. **속성** 창에서 속성 **창의** 오른쪽 상단에 있는 이벤트 처리기 단추를 클릭합니다. 텍스트 상자에서 **선택됨을** 찾아 **checkbox_Checked** 입력한 다음 **선택 취소를** 찾고 텍스트 상자에서 **checkbox_Unchecked** 입력합니다.

7. 확인란 이벤트 처리기를 추가합니다.

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

9. 실험 인스턴스에서 **MyToolWindow** 창을 엽니다.

     **속성** 창에서 창의 속성을 찾습니다. **IsChecked** 속성은 **내 속성** 범주 아래 창 아래쪽에 나타납니다.

10. **MyToolWindow** 창에서 확인란을 선택합니다. 속성 **창에서** **선택됨이** **True로**변경됩니다. MyToolWindow 창에서 확인란을 선택 **취소합니다.** 속성 **창에서** **False로**변경됨을 **선택합니다.** **속성** 창에서 **IsChecked** 값을 변경합니다. **MyToolWindow** 창의 확인란이 새 값과 일치하도록 변경됩니다.

    > [!NOTE]
    > **속성** 창에 표시되는 개체를 삭제해야 하는 경우 `OnSelectChange` 먼저 `null` 선택 컨테이너를 호출합니다. 속성 또는 개체를 삭제한 후 업데이트된 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> 선택 컨테이너및 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 목록으로 변경할 수 있습니다.

## <a name="change-selection-lists"></a>선택 목록 변경

 이 섹션에서는 기본 속성 클래스에 대한 선택 목록을 추가하고 도구 창 인터페이스를 사용하여 표시할 선택 목록을 선택합니다.

### <a name="to-change-selection-lists"></a>선택 목록을 변경하려면

1. *MyToolWindow.cs* 열고 . `Simple`

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

2. `SimpleObject` 클래스에 `MyToolWindow` 속성을 추가하고 창과 `Simple` 개체 간에 **속성** 창 선택을 전환하는 두 가지 방법을 추가합니다.

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

3. *MyToolWindowControl.cs*확인란 처리기를 다음과 같은 코드 줄로 바꿉니다.

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

5. 실험 인스턴스에서 **MyToolWindow** 창을 엽니다.

6. **MyToolWindow** 창에서 확인란을 선택합니다. **속성** `Simple` 창에는 개체 속성, **SomeText** 및 **ReadOnly**가 표시됩니다. 확인란을 선택 취소합니다. 창의 공용 속성이 **속성** 창에 나타납니다.

    > [!NOTE]
    > **SomeText의** 표시 이름은 **내 텍스트입니다.**

## <a name="best-practice"></a>모범 사례

이 연습에서는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 선택 가능한 개체 컬렉션과 선택한 개체 컬렉션이 동일한 컬렉션이 되도록 구현됩니다. 선택한 개체만 속성 브라우저 목록에 나타납니다. 보다 완전한 ISelectionContainer 구현은 참조.ToolWindow 샘플을 참조하십시오.

Visual Studio 도구 창은 Visual Studio 세션 간에 유지됩니다. 도구 창 상태를 유지하는 방법에 대한 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>자세한 내용은 을 참조하십시오.

## <a name="see-also"></a>참조

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)
