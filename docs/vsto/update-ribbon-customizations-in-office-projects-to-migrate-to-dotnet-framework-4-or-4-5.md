---
title: .NET Framework 4, 4.5로 마이그레이션된 Office 프로젝트에서 리본 사용자 지정 업데이트
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7d7ab5755f592e57e76dcd68f3dcb9dc2a7eab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254356"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Office 프로젝트에서 리본 메뉴 사용자 지정 업데이트
  프로젝트에 **리본 (비주얼 디자이너)** 프로젝트 항목을 사용 하 여 만든 리본 사용자 지정이 포함 되어 있는 경우 대상 프레임 워크가 이상 버전으로 변경 된 경우 프로젝트 코드를 다음과 같이 변경 해야 합니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

- 생성된 리본 코드를 수정합니다.

- 런타임에 리본 컨트롤을 인스턴스화하는 코드를 수정 하거나 리본 이벤트를 처리 하거나 리본 구성 요소의 위치를 프로그래밍 방식으로 설정 합니다.

## <a name="update-the-generated-ribbon-code"></a>생성 된 리본 코드를 업데이트 합니다.
 프로젝트의 대상 프레임워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상으로 변경된 경우 다음 단계를 수행하여 리본 항목에 대해 생성된 코드를 변경해야 합니다. 업데이트해야 하는 코드 파일은 프로그래밍 언어 및 프로젝트를 만든 방법에 따라 달라집니다.

- Visual Basic 프로젝트 또는에서 만든 Visual c # 프로젝트의 또는 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 리본 코드를 실행 하는 모든 파일 (리본*항목* Designer.cs 또는 해당 하는 *리본 항목*입니다. 디자이너 .vb). Visual Basic 프로젝트에서 코드 숨김 파일을 보려면 **솔루션 탐색기**의 **모든 파일 표시** 단추를 클릭 합니다.

- Visual Studio 2008에서 만든 다음로 업그레이드 한 Visual c # 프로젝트에서 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 리본 코드 파일 (해당 하는 리본*항목*.cs 또는 해당 하는 리본 *항목*.vb)의 처음 두 단계를 수행 하 고 리본 코드 숨겨진 파일에서 나머지 단계를 수행 합니다.

### <a name="to-change-the-generated-ribbon-code"></a>생성된 리본 코드를 변경하려면

1. `Microsoft.Office.Tools.Ribbon.OfficeRibbon` 대신 <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>에서 파생되도록 Ribbon 클래스의 선언을 수정합니다.

2. 아래와 같이 Ribbon 클래스의 생성자를 수정합니다. 사용자 고유의 코드를 생성자에 추가한 경우 코드를 변경하지 마세요. Visual Basic 프로젝트에서 매개 변수가 없는 생성자만 수정합니다. 다른 생성자는 무시하세요.

     다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트에서 Ribbon 클래스의 기본 생성자를 보여 줍니다.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 Ribbon 클래스의 기본 생성자를 보여 줍니다.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. `InitializeComponent` 메서드에서 리본 컨트롤을 생성하는 코드를 코드가 대신 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 개체의 도우미 메서드 중 하나를 사용하도록 수정합니다.

    > [!NOTE]
    > Visual C# 프로젝트에서 `InitializeComponent` 메서드를 확인하려면 `Component Designer generated code`라는 영역을 확장해야 합니다.

     예를 들어 파일에 .NET Framework 3.5를 대상으로 하는 프로젝트에서 `button1`이라는 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton>을 인스턴스화하는 다음 코드 줄이 포함되어 있다고 가정합니다.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서는 다음 코드를 대신 사용해야 합니다.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     리본 컨트롤에 대 한 도우미 메서드의 전체 목록은 [리본 컨트롤 인스턴스화](#ribboncontrols)를 참조 하세요.

4. Visual C# 프로젝트에서 <xref:System.EventHandler%601> 대리자를 사용하는 `InitializeComponent` 메서드의 코드 줄을 특정 리본 대리자를 대신 사용하도록 수정합니다.

     예를 들어 파일에 .NET Framework 3.5를 대상으로 하는 프로젝트에서 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 이벤트를 처리하는 다음 코드 줄이 있다고 가정합니다.

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> 이상을 대상으로 하는 프로젝트에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 다음 코드를 대신 사용 해야 합니다.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> 리본 대리자의 전체 목록은 [리본 이벤트 처리](#ribbonevents)를 참조 하세요.

5. Visual Basic 프로젝트에서 파일의 끝에 있는 `ThisRibbonCollection` 클래스를 찾습니다. 더 이상 `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`에서 상속하지 않도록 이 클래스의 선언을 수정합니다.

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> 리본 컨트롤 인스턴스화
 리본 컨트롤을 동적으로 인스턴스화하는 코드를 수정해야 합니다. .NET Framework 3.5를 대상으로 프로젝트에서 리본 컨트롤은 특정 시나리오에서 직접 인스턴스화할 수 있는 클래스입니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 이러한 컨트롤은 직접 인스턴스화할 수 없는 인터페이스입니다. <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 개체가 제공하는 메서드를 사용하여 컨트롤을 만들어야 합니다.

 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 개체에 액세스하는 방법에는 다음 두 가지가 있습니다.

- 리본 클래스의 Factory 속성 사용. Ribbon 클래스의 코드에서 이 방법을 사용합니다.

- `Globals.Factory.GetRibbonFactory` 메서드 사용. Ribbon 클래스 외부 코드에서 이 방법을 사용합니다. Globals 클래스에 대 한 자세한 내용은 [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

  다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 Ribbon 클래스에 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton>을 만드는 방법을 보여 줍니다.

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 </CodeContentPlaceHolder> 다음 표에서는 프로그래밍 방식으로 만들 수 있는 컨트롤과 이상을 대상으로 하는 프로젝트에서 컨트롤을 만드는 데 사용할 수 있는 메서드를 보여 줍니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

|컨트롤|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 프로젝트에서 사용할 RibbonFactory 메서드|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> 리본 이벤트 처리
 Ribbon 컨트롤의 이벤트를 처리하는 코드를 수정해야 합니다. .NET Framework 3.5를 대상으로 하는 프로젝트에서 이러한 이벤트는 제네릭 <xref:System.EventHandler%601> 대리자에 의해 처리됩니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서는 이제 이러한 이벤트가 다른 대리자에 의해 처리됩니다.

 다음 표에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 리본 이벤트 및 연결된 대리자를 보여 줍니다.

|이벤트|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 프로젝트에서 사용할 대리자|
|-----------| - |
|생성된 Ribbon 클래스의 <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> 이벤트|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>리본 구성 요소의 위치를 프로그래밍 방식으로 설정
 리본 그룹, 탭 또는 컨트롤의 위치를 설정하는 코드를 수정해야 합니다. .NET Framework 3.5를 대상으로 하는 프로젝트에서는 정적 `Microsoft.Office.Tools.Ribbon.RibbonPosition` 클래스의 `AfterOfficeId` 및 `BeforeOfficeId` 메서드를 사용하여 그룹, 탭 또는 컨트롤의 `Position` 속성을 할당할 수 있습니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서는 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 개체가 제공하는 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> 속성을 사용하여 이러한 메서드에 액세스해야 합니다.

 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> 개체에 액세스하는 방법에는 다음 두 가지가 있습니다.

- Ribbon 클래스의 `Factory` 속성 사용. Ribbon 클래스의 코드에서 이 방법을 사용합니다.

- `Globals.Factory.GetRibbonFactory` 메서드 사용. Ribbon 클래스 외부 코드에서 이 방법을 사용합니다. Globals 클래스에 대 한 자세한 내용은 [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

  다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트의 Ribbon 클래스에서 탭의 `Position` 속성을 설정하는 방법을 보여 줍니다.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]을 대상으로 하는 프로젝트에서의 동일한 작업을 보여 줍니다.

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>참고 항목
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
