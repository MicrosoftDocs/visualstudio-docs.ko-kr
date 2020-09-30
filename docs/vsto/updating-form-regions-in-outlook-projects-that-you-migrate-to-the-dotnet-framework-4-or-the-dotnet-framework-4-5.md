---
title: .NET Framework 4.5으로 마이그레이션될 때 Outlook 양식 영역 업데이트
titleSuffix: ''
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
ms.openlocfilehash: 9d8978703630e99ecb930e18e7d128eddff8792f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584401"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>.NET Framework 4.5으로 마이그레이션될 때 Outlook 양식 영역 업데이트

  양식 영역이 있는 Outlook VSTO 추가 기능 프로젝트의 대상 프레임워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경된 경우 생성된 양식 영역 코드 및 런타임에 특정 양식 영역 클래스를 인스턴스화하는 코드를 일부 변경해야 합니다.

## <a name="update-the-generated-form-region-code"></a>생성 된 양식 영역 코드 업데이트
 프로젝트의 대상 프레임워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경된 경우 생성된 양식 영역 코드를 변경해야 합니다. Visual Studio에서 디자인한 양식 영역과 Outlook에서 가져온 양식 영역에 대한 변경 내용이 서로 다릅니다. 이러한 양식 영역 형식 간의 차이점에 대 한 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Visual Studio에서 디자인한 양식 영역에 대해 생성된 코드를 업데이트하려면

1. 코드 편집기에서 양식 영역 코드 숨김 파일을 엽니다. 이 파일의 이름은 *YourFormRegion*.Designer.cs 또는 *YourFormRegion*.Designer.vb입니다. Visual Basic 프로젝트에서 이 파일을 보려면 **솔루션 탐색기** 에서 **모든 파일 표시**단추를 클릭합니다.

2. `Microsoft.Office.Tools.Outlook.FormRegionControl` 대신 <xref:Microsoft.Office.Tools.Outlook.FormRegionBase>에서 파생되도록 양식 영역 클래스의 선언을 수정합니다.

3. 다음 코드 예제에 표시된 것처럼 양식 영역 클래스의 생성자를 수정합니다.

     다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트에서 양식 영역 클래스의 생성자를 보여 줍니다.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트에서 양식 영역 클래스의 생성자를 보여 줍니다.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. 아래 표시된 대로 `InitializeManifest` 메서드의 서명을 수정합니다. 메서드의 코드를 수정하지 마세요. 이 코드는 디자이너에서 적용한 양식 영역 설정을 나타냅니다. Visual C# 프로젝트에서 이 메서드를 확인하려면 `Form Region Designer generated code` 라는 영역을 확장해야 합니다.

     다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트에서 `InitializeManifest` 메서드의 서명을 보여 줍니다.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     다음 코드 예제에서는 `InitializeManifest` 를 대상으로 하는 프로젝트에서 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]메서드의 서명을 보여 줍니다.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. 프로젝트에 새 Outlook 양식 영역 항목을 추가합니다. 새 양식 영역에 대 한 코드 숨겨진 파일을 열고 *YourNewFormRegion* `Factory` 파일의 YourNewFormRegion 및 클래스를 찾은 다음 `WindowFormRegionCollection` 이러한 클래스를 클립보드에 복사 합니다.

6. 프로젝트에 추가한 새 양식 영역을 삭제합니다.

7. 대상이 변경 된 프로젝트에서 작동 하도록 업데이트 하는 양식 영역의 코드 숨김이 파일의 *YourOriginalFormRegion* `Factory` 및 클래스를 찾아 `WindowFormRegionCollection` 새 양식 영역에서 복사한 코드로 바꿉니다.

8. *YourNewFormRegion* `Factory` 및 클래스에서 `WindowFormRegionCollection` *YourNewFormRegion* 클래스에 대 한 모든 참조를 검색 하 고 *YourOriginalFormRegion* 클래스에 대 한 각 참조를 대신 변경 합니다. 예를 들어 업데이트하는 양식 영역의 이름이 `SalesDataFormRegion` 이고 5단계에서 만든 새 양식 영역의 이름이 `FormRegion1`인 경우 `FormRegion1` 의 모든 참조를 `SalesDataFormRegion`으로 변경합니다.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Outlook에서 가져온 양식 영역에 대해 생성된 코드를 업데이트하려면

1. 코드 편집기에서 양식 영역 코드 숨김 파일을 엽니다. 이 파일의 이름은 *YourFormRegion*.Designer.cs 또는 *YourFormRegion*.Designer.vb입니다. Visual Basic 프로젝트에서 이 파일을 보려면 **솔루션 탐색기** 에서 **모든 파일 표시**단추를 클릭합니다.

2. `Microsoft.Office.Tools.Outlook.ImportedFormRegion` 대신 <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase>에서 파생되도록 양식 영역 클래스의 선언을 수정합니다.

3. 다음 코드 예제에 표시된 것처럼 양식 영역 클래스의 생성자를 수정합니다.

     다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트에서 양식 영역 클래스의 생성자를 보여 줍니다.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트에서 양식 영역 클래스의 생성자 서명을 보여 줍니다.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. 양식 영역 클래스의 컨트롤을 초기화하는 `InitializeControls` 메서드의 각 코드 줄에 대해 아래와 같이 코드를 수정합니다.

     다음 코드 예제에서는 .NET Framework 3.5를 대상으로 하는 프로젝트에서 컨트롤을 초기화하는 방법을 보여 줍니다. 이 코드에서 `GetFormRegionControl` 메서드에는 반환되는 컨트롤의 형식을 지정하는 형식 매개 변수가 있습니다.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     다음 코드 예제에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트에서 컨트롤을 초기화하는 방법을 보여 줍니다. 이 코드에서 <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> 메서드에는 형식 매개 변수가 없습니다. 반환 값을 초기화하는 컨트롤의 형식으로 캐스팅해야 합니다.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. 프로젝트에 새 Outlook 양식 영역 항목을 추가합니다. 새 양식 영역에 대 한 코드 숨겨진 파일을 열고 *YourNewFormRegion* `Factory` 파일의 YourNewFormRegion 및 클래스를 찾은 다음 `WindowFormRegionCollection` 이러한 클래스를 클립보드에 복사 합니다.

6. 프로젝트에 추가한 새 양식 영역을 삭제합니다.

7. 대상이 변경 된 프로젝트에서 작동 하도록 업데이트 하는 양식 영역의 코드 숨김이 파일의 *YourOriginalFormRegion* `Factory` 및 클래스를 찾아 `WindowFormRegionCollection` 새 양식 영역에서 복사한 코드로 바꿉니다.

8. *YourNewFormRegion* `Factory` 및 클래스에서 `WindowFormRegionCollection` *YourNewFormRegion* 클래스에 대 한 모든 참조를 검색 하 고 *YourOriginalFormRegion* 클래스에 대 한 각 참조를 대신 변경 합니다. 예를 들어 업데이트하는 양식 영역의 이름이 `SalesDataFormRegion` 이고 5단계에서 만든 새 양식 영역의 이름이 `FormRegion1`인 경우 `FormRegion1` 의 모든 참조를 `SalesDataFormRegion`으로 변경합니다.

## <a name="instantiate-form-region-classes"></a>양식 영역 클래스 인스턴스화
 특정 양식 영역 클래스를 동적으로 인스턴스화하는 코드를 수정해야 합니다. .NET Framework 3.5를 대상으로 하는 프로젝트에서 `Microsoft.Office.Tools.Outlook.FormRegionManifest`와 같은 양식 영역 클래스를 직접 인스턴스화할 수 있습니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 이러한 클래스는 직접 인스턴스화할 수 없는 인터페이스입니다.

 프로젝트의 대상 프레임워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경된 경우 `Globals.Factory` 속성이 제공하는 메서드를 사용하여 인터페이스를 인스턴스화해야 합니다. 속성에 대 한 자세한 내용은 `Globals.Factory` [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

 다음 표에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 형식을 인스턴스화하는 데 사용할 메서드 및 양식 영역 형식을 보여 줍니다.

|Type|사용할 팩터리 메서드|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>참고 항목
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
