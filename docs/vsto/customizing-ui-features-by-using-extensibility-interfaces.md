---
title: 확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d28c9456afdc60b1bddadf759ec3090ba37f2040
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841414"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정
  Visual Studio의 Office 개발 도구에는 많은 구현 세부 사항을 처리하는 클래스와 디자이너가 제공되며, 이를 사용하여 VSTO 추가 기능에 사용자 지정 작업창, 리본 사용자 지정, Outlook 양식 영역을 만들 수 있습니다. 하지만 특별한 요구 사항이 있는 경우 각각의 기능에 대한 *확장성 인터페이스* 를 직접 구현할 수도 있습니다.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>확장성 인터페이스 개요
 Microsoft Office에서는 COM VSTO 추가 기능이 리본 같은 특정 기능을 사용자 지정하기 위해 구현할 수 있는 일련의 확장성 인터페이스를 정의합니다. 이러한 인터페이스는 액세스를 지원하는 기능에 대한 모든 권한을 제공합니다. 하지만 이러한 인터페이스를 구현하려면 관리 코드의 COM 상호 운용성에 대해 어느 정도 이해하고 있어야 합니다. 경우에 따라 .NET Framework에 익숙한 개발자 입장에서는 이러한 인터페이스의 프로그래밍 모델이 직관적으로 파악되지 않기도 합니다.

 Visual Studio의 Office 프로젝트 템플릿을 사용하여 VSTO 추가 기능을 만드는 경우에는 리본 같은 기능을 사용자 지정하기 위해 확장성 인터페이스를 구현할 필요가 없습니다. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 은 이러한 인터페이스를 자동으로 구현합니다. 대신 Visual Studio에서 제공하는 보다 직관적인 클래스와 디자이너를 사용할 수 있습니다. 하지만 원하는 경우에는 여전히 VSTO 추가 기능에 바로 확장성 인터페이스를 구현할 수도 있습니다.

 Visual Studio에서 이러한 기능에 대해 제공 하는 클래스 및 디자이너에 대 한 자세한 내용은 [사용자 지정 작업창](../vsto/custom-task-panes.md), [리본 디자이너](../vsto/ribbon-designer.md)및 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>VSTO 추가 기능에서 구현할 수 있는 확장성 인터페이스
 다음 표에는 구현할 수 있는 확장성 인터페이스와 이러한 인터페이스를 지원하는 애플리케이션이 나와 있습니다.

|인터페이스|Description|애플리케이션|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|리본 UI를 사용자 지정하려면 이 인터페이스를 구현합니다. **참고:**  프로젝트에 **리본 (XML)** 항목을 추가 하 여 <xref:Microsoft.Office.Core.IRibbonExtensibility> VSTO 추가 기능에 기본 구현을 생성할 수 있습니다. 자세한 내용은 [Ribbon XML](../vsto/ribbon-xml.md)을 참조하세요.|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|사용자 지정 작업창을 만들려면 이 인터페이스를 구현합니다.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Outlook 양식 영역을 만들려면 이 인터페이스를 구현합니다.|Outlook|

 <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, <xref:Microsoft.Office.Core.SignatureProvider>같은 Microsoft Office에 정의된 그 밖의 여러 확장성 인터페이스도 있습니다. Visual Studio에서는 Office 프로젝트 템플릿을 사용하여 만든 VSTO 추가 기능에 이러한 인터페이스를 구현하는 기능을 지원하지 않습니다.

## <a name="use-extensibility-interfaces"></a>확장성 인터페이스 사용
 확장성 인터페이스를 사용하여 UI 기능을 사용자 지정하려면 VSTO 추가 기능 프로젝트에 적절한 인터페이스를 구현합니다. 그런 다음 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 메서드를 재정의하여 인터페이스를 구현하는 클래스의 인스턴스를 반환합니다.

 Outlook 용 VSTO 추가 기능에서, 및 인터페이스를 구현 하는 방법을 보여 주는 샘플 응용 프로그램은 <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> [OFFICE 개발 샘플](../vsto/office-development-samples.md)에서 UI Manager 샘플을 참조 하세요.

### <a name="example-of-implementing-an-extensibility-interface"></a>확장성 인터페이스를 구현 하는 예제
 다음 코드 예제에서는 사용자 지정 작업창을 만들기 위한 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 인터페이스의 간단한 구현을 보여 줍니다. 이 예제에서는 다음 두 개의 클래스를 정의합니다.

- `TaskPaneHelper` 클래스는 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> 를 구현하여 사용자 지정 작업창을 만들고 표시합니다.

- `TaskPaneUI` 클래스에서는 작업창의 UI를 제공합니다. `TaskPaneUI` 클래스의 특성은 클래스를 COM에 노출하여 Microsoft Office 애플리케이션에서 클래스를 검색할 수 있도록 합니다. 이 예제에서 UI는 빈 <xref:System.Windows.Forms.UserControl>이지만 코드를 수정하여 컨트롤을 추가할 수 있습니다.

  > [!NOTE]
  > `TaskPaneUI` 클래스를 COM에 노출하려면 프로젝트에 대해 **COM interop 등록** 속성도 설정해야 합니다.

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  구현에 대 한 자세한 내용은 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> Microsoft Office 설명서의 [2007 Office system에서 사용자 지정 작업창 만들기](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) 를 참조 하세요.

### <a name="example-of-overriding-the-requestservice-method"></a>RequestService 메서드 재정의 예제
 다음 코드 예제에서는 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 메서드를 재정의하여 이전 코드 예제의 `TaskPaneHelper` 클래스 인스턴스를 반환하는 방법을 보여 줍니다. 또한 *serviceGuid* 매개 변수 값을 확인하여 요청되는 인터페이스를 파악한 후 이 인터페이스를 구현하는 개체를 반환합니다.

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>참고 항목
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
