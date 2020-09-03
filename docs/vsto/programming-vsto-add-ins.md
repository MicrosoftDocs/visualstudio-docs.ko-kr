---
title: VSTO 추가 기능 프로그램
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 240995eb744f8107503c108cbcdbbb8522748b79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87115328"
---
# <a name="program-vsto-add-ins"></a>VSTO 추가 기능 프로그램
  VSTO 추가 기능을 만들어 Microsoft Office 애플리케이션을 확장하는 경우 프로젝트의 `ThisAddIn` 클래스에 대해 직접 코드를 작성합니다. 이 클래스를 사용하여 Microsoft Office 호스트 애플리케이션의 개체 모델 액세스, 애플리케이션의 UI(사용자 인터페이스) 사용자 지정, 다른 Office 솔루션에 VSTO 추가 기능의 개체 표시 등의 작업을 수행할 수 있습니다.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 VSTO 추가 기능 프로젝트에서 코드 작성의 일부 측면은 Visual Studio의 다른 프로젝트 유형과 다릅니다. 이러한 차이점 대부분은 Office 개체 모델이 관리 코드에 표시되는 방식에 기인합니다. 자세한 내용은 [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)을 참조 하세요.

 Visual Studio에서 Office 개발 도구를 사용 하 여 만들 수 있는 VSTO 추가 기능 및 다른 유형의 솔루션에 대 한 일반적인 내용은 [office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조 하세요.

## <a name="use-the-thisaddin-class"></a>ThisAddIn 클래스 사용
 `ThisAddIn` 클래스에서 VSTO 추가 기능 코드 작성을 시작할 수 있습니다. Visual Studio는 *ThisAddIn.vb* [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VSTO 추가 기능 프로젝트의 ThisAddIn (in) 또는 *ThisAddIn.cs* (c #) 코드 파일에이 클래스를 자동으로 생성 합니다. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 은 Microsoft Office 애플리케이션에서 VSTO 추가 기능을 로드할 때 이 클래스를 자동으로 인스턴스화합니다.

 `ThisAddIn` 클래스에는 두 가지 기본 이벤트 처리기가 있습니다. VSTO 추가 기능이 로드될 때 코드를 실행하려면 `ThisAddIn_Startup` 이벤트 처리기에 코드를 추가합니다. VSTO 추가 기능이 언로드되기 직전에 코드를 실행하려면 `ThisAddIn_Shutdown` 이벤트 처리기에 코드를 추가합니다. 이러한 이벤트 처리기에 대 한 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

> [!NOTE]
> Outlook에서는 기본적으로 VSTO 추가 기능이 언로드될 때 `ThisAddIn_Shutdown` 이벤트 처리기가 항상 호출되지는 않습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="access-the-object-model-of-the-host-application"></a>호스트 응용 프로그램의 개체 모델에 액세스
 호스트 애플리케이션의 개체 모델에 액세스하려면 `Application` 클래스의 `ThisAddIn` 필드를 사용합니다. 이 필드는 호스트 애플리케이션의 현재 인스턴스를 나타내는 개체를 반환합니다. 다음 표에서는 각 VSTO 추가 기능 프로젝트에서 `Application` 필드에 대한 반환 값의 형식을 보여 줍니다.

|호스트 애플리케이션|반환 값 형식|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[애플리케이션](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 다음 코드 예제에서는 필드를 사용 하 여 `Application` Microsoft Office Excel 용 VSTO 추가 기능에서 새 통합 문서를 만드는 방법을 보여 줍니다. 이 예제는 `ThisAddIn` 클래스에서 실행하기 위한 것입니다.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 `ThisAddIn` 클래스 외부에서 동일한 작업을 수행하려면 `Globals` 개체를 사용하여 `ThisAddIn` 클래스에 액세스합니다. 개체에 대 한 자세한 내용은 `Globals` [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 특정 Microsoft Office 애플리케이션의 개체 모델에 대한 자세한 내용은 다음 항목을 참조하세요.

- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)

- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)

- [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)

- [InfoPath 솔루션](../vsto/infopath-solutions.md)

- [PowerPoint 솔루션](../vsto/powerpoint-solutions.md)

- [프로젝트 솔루션](../vsto/project-solutions.md)

- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> Office 응용 프로그램이 시작 될 때 문서 액세스
 일부 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 애플리케이션은 시작될 때 자동으로 문서를 열지 않고, [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 애플리케이션은 시작될 때 문서를 열지 않습니다. 따라서 `ThisAdd-In_Startup` 코드에서 문서를 열어야 하는 경우 이벤트 처리기에 코드를 추가 하지 마세요. 대신 사용자가 문서를 만들거나 열 때 Office 애플리케이션에서 발생하는 이벤트에 해당 코드를 추가합니다. 이런 식으로 코드에서 작업을 수행하기 전에 문서가 열리도록 할 수 있습니다.

 다음 코드 예제에서는 사용자가 문서를 만들거나 기존 문서를 여는 경우에만 Word에서 문서로 작업합니다.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>다른 작업에 사용할 ThisAddIn 멤버
 다음 표에서는 다른 일반적인 작업에 대해 설명하고 작업을 수행하는 데 사용할 수 있는 `ThisAddIn` 클래스의 멤버를 보여 줍니다.

|Task|사용할 멤버|
|----------|-------------------|
|VSTO 추가 기능이 로드될 때 코드를 실행하여 VSTO 추가 기능을 초기화합니다.|`ThisAddIn_Startup` 메서드에 코드를 추가합니다. <xref:Microsoft.Office.Tools.AddInBase.Startup> 이벤트에 대한 기본 이벤트 처리기입니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.|
|VSTO 추가 기능이 언로드되기 전에 코드를 실행하여 VSTO 추가 기능에서 사용된 리소스를 정리합니다.|`ThisAddIn_Shutdown` 메서드에 코드를 추가합니다. <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 이벤트에 대한 기본 이벤트 처리기입니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요. **참고:**  Outlook에서는 기본적으로 `ThisAddIn_Shutdown` VSTO 추가 기능이 언로드될 때 이벤트 처리기가 항상 호출 되지는 않습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.|
|사용자 지정 작업창을 표시합니다.|`CustomTaskPanes` 필드를 사용합니다. 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.|
|다른 Microsoft Office 솔루션에 VSTO 추가 기능의 개체를 표시합니다.|<xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 메서드를 재정의합니다. 자세한 내용은 [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)을 참조 하세요.|
|확장성 인터페이스를 구현하여 Microsoft Office 시스템의 기능을 사용자 지정합니다.|<xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 메서드를 재정의하여 인터페이스를 구현하는 클래스의 인스턴스를 반환합니다. 자세한 내용은 [확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)을 참조 하세요. **참고:**  리본 UI를 사용자 지정 하려면 메서드를 재정의할 수도 있습니다 <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> .|

### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn 클래스 디자인 이해
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트에서 <xref:Microsoft.Office.Tools.AddIn> 은 인터페이스입니다. `ThisAddIn` 클래스는 <xref:Microsoft.Office.Tools.AddInBase> 클래스에서 파생됩니다. 이 기본 클래스는 해당 멤버에 대한 모든 호출을 <xref:Microsoft.Office.Tools.AddIn> 에서 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]인터페이스의 내부 구현으로 리디렉션합니다.

 Outlook의 VSTO 추가 기능 프로젝트에서 `ThisAddIn` 클래스는 .NET Framework 3.5를 대상으로 하는 프로젝트의 `Microsoft.Office.Tools.Outlook.OutlookAddIn` 클래스 및 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트의 <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase>에서 파생됩니다. 이러한 기본 클래스는 양식 영역을 지원하기 위해 몇 가지 추가 기능을 제공합니다. 양식 영역에 대 한 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office 응용 프로그램의 사용자 인터페이스 사용자 지정
 VSTO 추가 기능을 사용하여 Microsoft Office 애플리케이션의 UI를 프로그래밍 방식으로 사용자 지정할 수 있습니다. 예를 들어 리본을 사용자 지정하거나, 사용자 지정 작업창을 표시하거나, Outlook에서 사용자 지정 양식 영역을 만들 수 있습니다. 자세한 내용은 [OFFICE UI 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

 Visual Studio는 사용자 지정 작업창, 리본 사용자 지정 및 Outlook 양식 영역을 만드는 데 사용할 수 있는 디자이너 및 클래스를 제공합니다. 이러한 디자이너 및 클래스를 사용하면 이러한 기능을 사용자 지정하는 프로세스를 간소화할 수 있습니다. 자세한 내용은 [사용자 지정 작업창](../vsto/custom-task-panes.md), [리본 디자이너](../vsto/ribbon-designer.md)및 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

 클래스 및 디자이너에서 지원하지 않는 방식으로 이러한 기능 중 하나를 사용자 지정하려는 경우 VSTO 추가 기능에서 *확장성 인터페이스* 를 구현하여 이러한 기능을 사용자 지정할 수도 있습니다. 자세한 내용은 [확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)을 참조 하세요.

 또한 문서 및 통합 문서의 동작을 확장하는 호스트 항목을 생성하여 Word 문서 및 Excel 통합 문서의 UI를 수정할 수 있습니다. 그러면 문서 및 워크시트에 관리되는 컨트롤을 추가할 수 있습니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>다른 솔루션에서 VSTO 추가 기능의 코드 호출
 VSTO 추가 기능의 개체를 다른 Office 솔루션을 비롯한 다른 솔루션에 표시할 수 있습니다. 이는 해당 VSTO 추가 기능이 다른 솔루션에서 사용하도록 하려는 서비스를 제공하는 경우에 유용합니다. 예를 들어 웹 서비스의 재무 데이터에 대해 계산을 수행 하는 Microsoft Office Excel 용 VSTO 추가 기능이 있는 경우 다른 솔루션은 런타임에 Excel VSTO 추가 기능을 호출 하 여 이러한 계산을 수행할 수 있습니다.

 자세한 내용은 [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
