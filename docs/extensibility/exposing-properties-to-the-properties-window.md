---
title: 속성 창에 속성 노출 | Microsoft Docs
description: 개체의 공용 속성에 대해 알아봅니다. 이러한 속성에 대한 변경 내용은 속성 창 반영됩니다.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f932772b031332d7df2a2487c70576f49407ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898739"
---
# <a name="expose-properties-to-the-properties-window"></a>속성 창 속성 노출

이 연습에서는 개체의 공용 속성을 **속성** 창에 노출합니다. 이러한 속성에 대한 변경 내용은 **속성** 창에 반영됩니다.

## <a name="prerequisites"></a>필수 구성 요소

Visual Studio 2015부터 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에 선택적 기능으로 포함되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를 참조하세요.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>속성 창 속성 노출

이 섹션에서는 사용자 지정 도구 창을 만들고 속성 창에 연결된 창 개체의 공용 속성을 표시합니다. 

### <a name="to-expose-properties-to-the-properties-window"></a>속성 창 속성을 노출하려면

1. 모든 Visual Studio 확장은 확장 자산을 포함하는 VSIX 배포 프로젝트로 시작합니다. 라는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 프로젝트를 `MyObjectPropertiesExtension` 만듭니다. "vsix"를 검색하여 **새 프로젝트** 대화 상자에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.

2. 라는 사용자 지정 도구 창 항목 템플릿을 추가하여 도구 창을 `MyToolWindow` 추가합니다. **솔루션 탐색기** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 새 항목 **추가를**  >  선택합니다. 새 **항목 추가 대화 상자에서** **Visual C# 항목**  >  **확장성으로** 이동하고 **사용자 지정 도구 창** 을 선택합니다. 대화 상자 아래쪽의 **이름** 필드에서 파일 이름을 *MyToolWindow.cs 로 변경합니다.* 사용자 지정 도구 창을 만드는 방법에 대한 자세한 내용은 도구 [창을 사용하여 확장 만들기를 참조하세요.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. *MyToolWindow.cs를* 열고 다음 using 문을 추가합니다.

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. 이제 클래스에 다음 필드를 `MyToolWindow` 추가합니다.

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

    `TrackSelection`속성은 를 사용하여 `GetService` `STrackSelection` 인터페이스를 제공하는 서비스를 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 얻습니다. `OnToolWindowCreated`이벤트 처리기와 `SelectList` 메서드는 함께 도구 창 개체 자체만 포함하는 선택한 개체 목록을 만듭니다. `UpdateSelection`메서드는 **도구** 창의 공용 속성을 표시하도록 속성 창에 지시합니다.

6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스가 표시됩니다.

7. **속성** 창이 표시되지 않으면 **F4** 키를 눌러 엽니다.

8. **MyToolWindow** 창을 엽니다. 다른 창 **보기** 에서 찾을 수  >  있습니다.

    창이 열리고 창의 공용 속성이 **속성** 창에 나타납니다.

9. **속성** 창의 **Caption** 속성을 내 개체 속성 으로 **변경합니다.**

     MyToolWindow 창 캡션이 그에 따라 변경됩니다.

## <a name="expose-tool-window-properties"></a>도구 창 속성 노출

이 섹션에서는 도구 창을 추가하고 해당 속성을 노출합니다. 속성에 대한 변경 내용은 **속성** 창에 반영됩니다.

### <a name="to-expose-tool-window-properties"></a>도구 창 속성을 노출하려면

1. *MyToolWindow.cs* 를 열고 공용 부울 속성 IsChecked를 `MyToolWindow` 클래스에 추가합니다.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     이 속성은 나중에 만들 WPF 확인란에서 해당 상태를 가져옵니다.

2. *MyToolWindowControl.xaml.cs를* 열고 MyToolWindowControl 생성자를 다음 코드로 대체합니다.

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

3. *MyToolWindow.cs에서* 다음과 `MyToolWindow` 같이 생성자를 변경합니다.

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. MyToolWindowControl의 디자인 뷰로 변경합니다.

5. 단추를 삭제하고 도구 상자에서 왼쪽 위 모서리에 **확인란을** 추가합니다.

6. Checked 및 Unchecked 이벤트를 추가합니다. 디자인 뷰에서 확인란을 선택합니다. **속성** 창에서 속성 **창의** 오른쪽 위에 있는 이벤트 처리기 단추를 클릭합니다. **Checked를** 찾고 텍스트 상자에 **checkbox_Checked** 입력한 다음 **Unchecked를 찾은** 다음 텍스트 상자에 **checkbox_Unchecked** 입력합니다.

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

9. 실험적 인스턴스에서 **MyToolWindow** 창을 엽니다.

     **속성** 창에서 창의 속성을 찾습니다. **IsChecked** 속성은 **내 속성** 범주 아래의 창 아래쪽에 나타납니다.

10. **MyToolWindow** 창에서 확인란을 선택합니다. **속성** 창에서 **IsChecked가** **True** 로 변경됩니다. **MyToolWindow** 창에서 확인란의 선택 취소를 선택합니다. **속성** 창에서 **IsChecked가** **False** 로 변경됩니다. **속성** 창에서 **IsChecked** 값을 변경합니다. **MyToolWindow** 창의 확인란이 새 값과 일치하도록 변경됩니다.

    > [!NOTE]
    > **속성** 창에 표시되는 개체를 삭제해야 하는 경우 `OnSelectChange` 먼저 선택 컨테이너와 함께 를 호출합니다. `null` 속성 또는 개체를 삭제한 후 및 목록이 업데이트된 선택 컨테이너로 변경할 수 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 있습니다.

## <a name="change-selection-lists"></a>선택 목록 변경

 이 섹션에서는 기본 속성 클래스에 대한 선택 목록을 추가하고 도구 창 인터페이스를 사용하여 표시할 선택 목록을 선택합니다.

### <a name="to-change-selection-lists"></a>선택 목록을 변경하려면

1. *MyToolWindow.cs를* 열고 라는 공용 클래스를 `Simple` 추가합니다.

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
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

2. 속성을 `SimpleObject` `MyToolWindow` 클래스에 추가하고 두 메서드를 추가하여 창 창과 개체 간에 **속성** 창 선택을 `Simple` 전환합니다.

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

3. *MyToolWindowControl.cs에서* 확인란 처리기를 다음 코드 줄로 대체합니다.

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

5. 실험적 인스턴스에서 **MyToolWindow** 창을 엽니다.

6. **MyToolWindow** 창에서 확인란을 선택합니다. **속성** 창에는 `Simple` 개체 속성 **SomeText** 및 **ReadOnly** 가 표시됩니다. 확인란을 선택 취소합니다. 창의 공용 속성이 **속성** 창에 나타납니다.

    > [!NOTE]
    > **SomeText의** 표시 이름은 **내 텍스트** 입니다.

## <a name="best-practice"></a>모범 사례

이 연습에서는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 선택 가능한 개체 컬렉션과 선택한 개체 컬렉션이 동일한 컬렉션이 되도록 가 구현됩니다. 선택한 개체만 속성 브라우저 목록에 나타납니다. 보다 완전한 ISelectionContainer 구현은 Reference.ToolWindow 샘플을 참조하세요.

Visual Studio 도구 창은 Visual Studio 세션 간에 유지됩니다. 도구 창 상태 유지에 대한 자세한 내용은 를 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 참조하세요.

## <a name="see-also"></a>참조

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)
