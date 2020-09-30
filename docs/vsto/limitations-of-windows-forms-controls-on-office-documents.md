---
title: Office 문서에서 Windows Forms 컨트롤의 제한 사항
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ade7da21a8d07fbd429a88303ad2be375877c1ec
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583738"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office 문서에서 Windows Forms 컨트롤의 제한 사항

Word 문서나 Microsoft Office Excel 워크시트 Microsoft Office에 추가 된 Windows Forms 컨트롤과 Windows Forms에 추가 되는 Windows Forms 컨트롤 간에는 몇 가지 차이점이 있습니다. 예를 들어 <xref:Microsoft.Office.Tools.Word.Controls.Button> 컨트롤을 문서에 추가 하면,, 등의 속성이 <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> <xref:System.Windows.Forms.Control.TabIndex> 예상과 다르게 동작 합니다.

이러한 차이점 중 상당수는 Windows Forms 컨트롤이 문서에 호스트 되는 방식으로 인해 발생 합니다. Windows Forms 컨트롤이 문서에 추가 되 면은 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 문서에서 Windows Forms 컨트롤을 호스트 하는 ActiveX 컨트롤을 포함 합니다. Windows Forms 컨트롤은 문서에 직접 포함 되지 않습니다.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Forms 컨트롤의 메서드 및 속성에 대 한 제한 사항

문서에서 Windows Form과 동일한 방식으로 작동 하지 않는 Windows Forms 컨트롤의 메서드 및 속성은 여러 가지가 있으므로 사용 하지 않는 것이 좋습니다. 예를 들어 및와 같은 속성을 설정 하는 것은 <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> 문서가 아니라 컨테이너 ActiveX 컨트롤에 대 한 컨트롤의 위치에만 영향을 줍니다. 다음은 Word 및 Excel 용 Windows Forms 컨트롤의 지원 되지 않는 메서드 및 속성 목록입니다.

- 지원 되지 않는 Excel 컨트롤 속성:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Word 컨트롤의 지원 되지 않는 메서드 및 속성:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

또한 <xref:System.Windows.Forms.Control.Left> <xref:System.Windows.Forms.Control.Top> Word 문서에서 텍스트를 사용 하 여 Windows Forms 컨트롤의 또는 속성을 설정할 수 없습니다. Windows Forms 컨트롤은 다음과 같은 경우 텍스트와 함께 줄에 추가 됩니다.

- 프로그래밍 방식으로 Word 문서에 컨트롤을 추가 하 고 위치의 범위를 지정 하는 메서드를 사용 합니다.

- 디자인 타임에 Word 문서에 Windows Forms 컨트롤을 추가 합니다. 디자이너에서 컨트롤을 수정 하 여이를 변경할 수 있습니다.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office 문서에서 Windows Forms 컨트롤의 차이점

Windows Forms 컨트롤은 일반적으로 Windows Form에서와 같은 방식으로 Office 문서에서 동일 하지만 몇 가지 차이점이 있습니다. 다음 표에서는 Office 문서에서 Windows Forms 컨트롤에 대해 존재 하는 차이점에 대해 설명 합니다.

|기능|차이|
|-------------------|----------------|
|컨트롤 탭 순서|Excel 워크시트 또는 Word 문서에 배치 된 컨트롤을 통해서는 tab 키를 사용할 수 없습니다.|
|컨트롤 그룹화|컨트롤을 사용 <xref:System.Windows.Forms.GroupBox> 하 여 Office 문서에 다른 컨트롤을 포함할 수 없습니다. 문서에 여러 개의 라디오 단추를 직접 추가 하는 경우 라디오 단추는 함께 사용할 수 없습니다. 라디오 단추를 함께 사용할 수 없도록 하는 코드를 작성할 수 있습니다. 그러나 기본 방법은 사용자 정의 컨트롤에 라디오 단추를 추가한 다음 사용자 정의 컨트롤을 문서에 추가 하는 것입니다. 자세한 내용은 [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)에서 Word 컨트롤 샘플 또는 Excel 컨트롤 샘플을 참조 하세요.|
|컨트롤 형식|문서에 사용 되는 Windows Forms 컨트롤은에서 제공 하는 클래스로 래핑되어 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Excel 워크시트 또는 Word 문서와 관련 된 추가 기능을 제공 합니다. 예를 들어, Excel 워크시트에 **단추** 컨트롤이 있는 경우 <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:System.Windows.Forms.Button> 개체를 참조 하거나 캐스팅할 때가 아닌 형식으로 지정 해야 합니다.|
|컨트롤 위치 및 크기|컨트롤의 크기와 위치는 컨테이너 ActiveX 컨트롤의 일부인 속성에 따라 결정 됩니다. ActiveX 컨트롤 속성은 Windows Forms 컨트롤의 해당 속성과 다른 값을 사용 합니다. `Top` `Left` 컨트롤의,, 또는 속성을 설정 하면 `Height` 픽셀이 아니라 `Width` 점으로 측정 됩니다.|
|Word 문서의 위치 제어|흐름 기반 레이아웃에 컨트롤을 추가 하는 경우 콘텐츠가 변경 될 때 컨트롤이 콘텐츠와 함께 전달 된다는 점에 유의 하세요. 컨트롤이 텍스트와 함께 Word 문서에 추가 되기 때문에 **도구 상자** 에서 끌어 오면 컨트롤을 단락에 고정할 수 없습니다. 컨트롤을 두 번 클릭 하는 등 다른 방법을 사용 하 여 컨트롤을 추가 하는 경우에는 그림 삽입을 위해 설정한 Word 옵션에 따라 컨트롤이 삽입 됩니다.<br /><br /> `Left`텍스트와 인라인으로 표시 되는 컨트롤의 또는 속성은 설정할 수 없습니다 `Top` .<br /><br /> 머리글이 나 바닥글 또는 하위 문서 내에 컨트롤을 추가할 수 없습니다.|
|컨트롤 이벤트|컨트롤을 선택 하면 다음과 같은 순서로 이벤트가 발생 합니다.<br /><br /> 1(sp1).  `Enter`<br />sr-2.  `GotFocus`<br /><br /> 컨트롤을 선택 취소 하면 다음과 같은 순서로 이벤트가 발생 합니다.<br /><br /> 1(sp1).  `Leave`<br />sr-2.  `Validating`<br />3.  `Validated`<br />3-4.  `LostFocus`|
|컨트롤 크기 조정|문서의 확대/축소 설정을 100% 이외의 값으로 변경 하면 컨트롤이 문서와 함께 크기 조정 되는 것 처럼 보이지만 사용 하지 않도록 설정 됩니다. 예를 들어 문서가 130% 확대 될 때 단추를 클릭 하면 zoom이 100%로 설정 될 때까지 컨트롤을 사용할 수 없다는 메시지가 표시 됩니다. 확대/축소를 100%로 변경 하면 컨트롤이 제대로 작동 합니다.|
|컨트롤 속성 값|Windows Form의 컨트롤 속성은 정수 값으로 설정 되지만 Word 문서에서 컨트롤의 단일 컨트롤로 설정 됩니다. Excel에서 컨트롤의 속성 값은 double로 설정 됩니다. `Height` `Width` 워크시트에 있는 컨트롤의 및 속성이 워크시트나 화면 크기를 초과 하는 경우 값이 잘립니다.|
|컨트롤 크기 조정|크기 조정 핸들 중 하나를 사용 하 여 문서에서 컨트롤의 크기를 조정 하는 경우 컨트롤이 ac 때까지 새 컨트롤 차원이 **속성** 창에 반영 되지 않습니다.|
|제어 동작|Excel 워크시트의 컨트롤은 워크시트 창이 분할 될 때 예상과 다르게 동작할 수 있습니다. 예를 들어 워크시트의에 대 한 액세스는 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> windows 중 하나 에서만 사용할 수 있습니다.|
|컨트롤 이름 지정|예약어를 사용 하 여 컨트롤의 이름을 지정할 수 없습니다. 예를 들어를 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 워크시트에 추가 하 고 이름을 **System**으로 변경 하면 프로젝트를 빌드할 때 오류가 발생 합니다.|
|프로그래밍 방식으로 컨트롤 추가|런타임에 컨트롤을 문서에 추가 하려면 컨트롤의 생성자를 사용 하지 마세요. 대신에서 제공 하는 도우미 메서드를 사용 합니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 예를 들어, 메서드를 사용 <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> 하 여 워크시트에 단추를 추가할 수 있습니다. 이러한 도우미 메서드에서 지원 하지 않는 컨트롤을 추가 하려는 경우 메서드를 사용할 수 있습니다 `AddControl` . 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)를 참조 하세요.|
|컨트롤 복사|Windows Forms 컨트롤을 복사 하 여 런타임에 문서에 붙여넣으면 빈 컨테이너 ActiveX 컨트롤이 문서에 붙여넣어집니다. Windows Forms 컨트롤은 새 위치에 표시 되지 않으며 원래 컨트롤의 코드 뒤에 있는 코드는 컨테이너 ActiveX 컨트롤에 복사 되지 않습니다.|

## <a name="limitations-in-document-level-projects"></a>문서 수준 프로젝트의 제한 사항

문서에서 Windows Forms 컨트롤을 사용 하는 경우의 몇 가지 제한 사항은 문서 수준 프로젝트에서 고유 합니다.

### <a name="control-support-at-design-time"></a>디자인 타임에 컨트롤 지원

특정 Windows Forms 컨트롤은 Visual Studio 디자이너에서 Excel 워크시트 또는 Word 문서를 열 때 **도구 상자** 에서 제거 됩니다. 이는 기술적 제한 또는 Word 또는 Excel 내에서 기능을 이미 사용할 수 있기 때문입니다. Excel 및 Word 프로젝트는 문서에 포커스가 있을 때 **도구 상자** 에 표시 되는 모든 Windows Forms 컨트롤 및 기타 구성 요소를 지원 하 고, 타사 컨트롤을 워크시트 또는 문서에 추가할 수도 있습니다.

> [!NOTE]
> 문서를 보호 하는 경우 모든 컨트롤이 **도구 상자** 에서 제거 됩니다. 문서 보호에 대 한 자세한 내용은 문서 [수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)를 참조 하세요.

> [!NOTE]
> 타사 컨트롤은 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Office 솔루션에서 사용 하기 위해 특성을 **true** 로 설정 해야 합니다.

다음 컨트롤 및 구성 요소는 **도구 상자**에서 사용할 수 없습니다.

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>레거시 ActiveX 컨트롤에 대 한 지원

ActiveX 컨트롤을 포함 하는 기존 Word 문서 또는 Excel 통합 문서를 사용 하는 문서 수준 Office 프로젝트를 만드는 경우에는 ActiveX 컨트롤의 기능이 손실 되지 않습니다. 그러나 Visual Studio 내에서 문서에 새 ActiveX 컨트롤을 추가 하는 것은 지원 되지 않습니다. 예를 들어 Word 문서에 Visual Basic for Applications (VBA) 매크로를 실행 하는 **컨트롤** 도구 상자의 단추가 있는 경우 Office 프로젝트에서 문서가 사용 된 후에도 매크로가 계속 실행 됩니다. 그러나 ActiveX 컨트롤과 VBA 매크로를 제거 하 고 Windows Forms 컨트롤 및 관리 코드로 바꾸는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [Office 문서에 대 한 Windows Forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
