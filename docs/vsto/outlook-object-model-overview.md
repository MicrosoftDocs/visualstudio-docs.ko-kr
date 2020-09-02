---
title: Outlook 개체 모델 개요
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6545815a0a24a3ba8579298151194fdd81edee77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985687"
---
# <a name="outlook-object-model-overview"></a>Outlook 개체 모델 개요
  Microsoft Office Outlook용 VSTO 추가 기능을 개발하기 위해 Outlook 개체 모델에서 제공하는 개체를 조작할 수 있습니다. Outlook 개체 모델은 사용자 인터페이스의 항목을 나타내는 클래스 및 인터페이스를 제공합니다. 예를 들어 <xref:Microsoft.Office.Interop.Outlook.Application> 개체는 전체 애플리케이션을 나타내고, <xref:Microsoft.Office.Interop.Outlook.Folder> 개체는 메일 메시지 또는 기타 항목이 포함된 폴더를 나타내고, <xref:Microsoft.Office.Interop.Outlook.MailItem> 개체는 메일 메시지를 나타냅니다.

 이 항목에서는 Outlook 개체 모델의 주요 개체 중 일부에 대해 간략하게 설명합니다. 전체 Outlook 개체 모델에 대해 자세히 알아볼 수 있는 리소스는 [outlook 개체 모델 설명서 사용](#refdoc)을 참조 하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Outlook 프로젝트의 개체 액세스
 Outlook은 조작할 수 많은 개체를 제공합니다. 개체 모델을 효과적으로 사용하려면 다음과 같은 최상위 개체를 잘 알고 있어야 합니다.

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>애플리케이션 개체
 <xref:Microsoft.Office.Interop.Outlook.Application> 개체는 Outlook 애플리케이션을 나타내며 Outlook 개체 모델의 최상위 개체입니다. 이 개체의 가장 중요한 멤버 중 일부는 다음과 같습니다.

- 메일 메시지, 작업 또는 약속과 같은 새 항목을 만드는 데 사용할 수 있는 [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) 메서드

- Outlook UI(사용자 인터페이스)에 폴더 내용을 표시하는 창에 액세스하는 데 사용할 수 있는 <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> 속성

- 메일 메시지 또는 모임 요청과 같은 단일 항목의 내용을 표시하는 창에 액세스하는 데 사용할 수 있는 <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> 속성

  개체의 인스턴스를 가져오려면 <xref:Microsoft.Office.Interop.Outlook.Application> 프로젝트에서 클래스의 응용 프로그램 필드를 사용 합니다 `ThisAddIn` . 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

> [!NOTE]
> Outlook 개체 모델 보호에 의해 차단 되는 속성 및 메서드를 사용 하는 경우 보안 경고를 방지 하려면 클래스의 응용 프로그램 필드에서 Outlook 개체를 가져옵니다 `ThisAddIn` . 자세한 내용은 [Office 솔루션에 대 한 특정 보안 고려 사항](../vsto/specific-security-considerations-for-office-solutions.md)을 참조 하세요.

### <a name="explorer-object"></a>탐색기 개체
 <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체는 메일 메시지, 작업 또는 약속과 같은 항목이 포함된 폴더의 내용을 표시하는 창을 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체에는 창을 수정하는 데 사용할 수 있는 메서드 및 속성과 창이 변경될 때 발생하는 이벤트가 포함됩니다.

 <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체를 가져오려면 다음 중 하나를 수행합니다.

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> 개체의 <xref:Microsoft.Office.Interop.Outlook.Application> 속성을 사용하여 Outlook의 모든 <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체에 액세스합니다.

- <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> 개체의 <xref:Microsoft.Office.Interop.Outlook.Application> 메서드를 사용하여 현재 포커스가 있는 <xref:Microsoft.Office.Interop.Outlook.Explorer> 를 가져옵니다.

- <xref:Microsoft.Office.Interop.Outlook.Folder> 개체의 `GetExplorer` 메서드를 사용하여 현재 폴더에 대한 <xref:Microsoft.Office.Interop.Outlook.Explorer>를 가져옵니다.

### <a name="inspector-object"></a>Inspector 개체
 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체는 메일 메시지, 작업 또는 약속과 같은 단일 항목을 표시하는 창을 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체에는 창을 수정하는 데 사용할 수 있는 메서드 및 속성과 창이 변경될 때 발생하는 이벤트가 포함됩니다.

 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체를 가져오려면 다음 중 하나를 수행합니다.

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> 개체의 <xref:Microsoft.Office.Interop.Outlook.Application> 속성을 사용하여 Outlook의 모든 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체에 액세스합니다.

- <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> 개체의 <xref:Microsoft.Office.Interop.Outlook.Application> 메서드를 사용하여 현재 포커스가 있는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 를 가져옵니다.

- <xref:Microsoft.Office.Interop.Outlook.MailItem> 또는 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>과 같은 특정 항목의 `GetInspector` 메서드를 사용하여 연결된 검사기를 검색합니다.

### <a name="folder-object"></a>Folder 개체
 <xref:Microsoft.Office.Interop.Outlook.Folder> 개체는 메일 메시지, 연락처, 작업 및 기타 항목을 포함하는 폴더를 나타냅니다. Outlook에서는 16개의 기본 제공 <xref:Microsoft.Office.Interop.Outlook.Folder> 개체를 제공합니다.

 기본 <xref:Microsoft.Office.Interop.Outlook.Folder> 개체는 <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> 열거형 값으로 정의됩니다. 예를 들면 다음과 같습니다.

 Outlook의 **수신함** 폴더에 해당 하는 oldefaultfolders. Oldefaultfolders.

 기본에 액세스 하 고 새를 만드는 방법을 보여 주는 예제는 <xref:Microsoft.Office.Interop.Outlook.Folder> <xref:Microsoft.Office.Interop.Outlook.Folder> [방법: 프로그래밍 방식으로 사용자 지정 폴더 항목 만들기](../vsto/how-to-programmatically-create-custom-folder-items.md)를 참조 하세요.

### <a name="mailitem-object"></a>MailItem 개체
 <xref:Microsoft.Office.Interop.Outlook.MailItem> 개체는 메일 메시지를 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.MailItem> 개체는 일반적으로 **받은 편지함**, **보낸 편지함**및 **보낼 편지함**과 같은 폴더에 있습니다. <xref:Microsoft.Office.Interop.Outlook.MailItem> 은 메일 메시지를 만들고 보내는 데 사용할 수 있는 속성과 메서드를 노출합니다.

 전자 메일 메시지를 만드는 방법을 보여 주는 예제는 [방법: 프로그래밍 방식으로 전자 메일 항목 만들기](../vsto/how-to-programmatically-create-an-e-mail-item.md)를 참조 하세요.

### <a name="appointmentitem-object"></a>AppointmentItem 개체
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> 개체는 모임, 일회성 약속, 되풀이 약속 또는 **일정** 폴더의 모임을 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> 개체에는 모임 요청에 응답 또는 전달과 같은 작업을 수행하는 메서드와 위치 및 시간과 같은 모임 세부 정보를 지정하는 속성이 포함됩니다.

 약속을 만드는 방법을 보여 주는 예제는 [방법: 프로그래밍 방식으로 모임 요청 만들기](../vsto/how-to-programmatically-create-a-meeting-request.md)를 참조 하세요.

### <a name="taskitem-object"></a>TaskItem 개체
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> 개체는 지정된 시간 프레임 내에 수행할 작업을 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.TaskItem> 개체는 **작업** 폴더에 있습니다.

 작업을 만들려면 [개체의](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) CreateItem <xref:Microsoft.Office.Interop.Outlook.Application> 메서드를 사용하고 매개 변수에 대해 값 <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> 을 전달합니다.

### <a name="contactitem-object"></a>ContactItem 개체
 메일 메시지, 작업 또는 약속과 같은 새 항목을 만드는 데 사용할 수 있는 <xref:Microsoft.Office.Interop.Outlook.ContactItem>개체는 **연락처** 폴더의 모임을 나타냅니다. <xref:Microsoft.Office.Interop.Outlook.ContactItem> 개체에는 주소, 메일 주소, 전화 번호 등 개체가 나타내는 사람에 대한 다양한 연락처 정보가 포함됩니다.

 새 연락처를 만드는 방법을 보여 주는 예제는 [방법: 프로그래밍 방식으로 Outlook 연락처에 항목 추가](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)를 참조 하세요. 기존 연락처를 검색 하는 방법을 보여 주는 예제는 [방법: 프로그래밍 방식으로 특정 연락처 검색](../vsto/how-to-programmatically-search-for-a-specific-contact.md)을 참조 하세요.

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Outlook 개체 모델 설명서 사용
 Outlook 개체 모델에 대한 자세한 내용은 Outlook PIA(주 interop 어셈블리) 참조 및 VBA 개체 모델 참조를 참조할 수 있습니다.

### <a name="primary-interop-assembly-reference"></a>주 interop 어셈블리 참조
 Outlook PIA 참조는 Outlook 2010에 대한 주 interop 어셈블리의 형식을 문서화합니다. 자세한 내용은 [Outlook 2010 주 interop 어셈블리 참조](/previous-versions/office/developer/office-2010/bb652780(v=office.14))를 참조 하세요.

 PIA의 모든 형식에 대한 정보를 제공할 뿐 아니라 이 설명서에서는 PIA의 구조에 대한 추가 정보 및 일반적인 Outlook 자동화 작업에 대한 코드 예제도 제공합니다.

### <a name="vba-object-model-reference"></a>VBA 개체 모델 참조
 VBA 개체 모델 참조에서는 VBA(Visual Basic for Applications) 코드로 표시되는 Outlook 개체 모델에 대해 설명합니다. 자세한 내용은 [Outlook 2010 개체 모델 참조](/office/vba/api/overview/Outlook/object-model)를 참조 하세요.

 VBA 개체 모델 참조의 모든 개체 및 멤버는 Outlook PIA의 형식 및 멤버에 해당합니다. 예를 들어 VBA 개체 모델 참조의 Inspector 개체는 <xref:Microsoft.Office.Interop.Outlook.Inspector> OUTLOOK PIA의 개체에 해당 합니다. VBA 개체 모델 참조에서는 대부분의 속성, 메서드 및 이벤트에 대한 코드 예제를 제공하지만 Visual Studio를 사용하여 만든 Outlook VSTO 추가 기능 프로젝트에서 사용하려면 이 참조의 VBA 코드를 Visual Basic 또는 Visual C#으로 변환해야 합니다.

### <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연락처 항목 작업](../vsto/working-with-contact-items.md)|연락처를 사용하여 작업을 수행하는 방법을 보여 주는 항목을 제공합니다.|
|[메일 항목 작업](../vsto/working-with-mail-items.md)|메일 항목을 사용하여 작업을 수행하는 방법을 보여 주는 항목을 제공합니다.|
|[폴더 작업](../vsto/working-with-folders.md)|폴더를 사용하여 작업을 수행하는 방법을 보여 주는 항목을 제공합니다.|
|[일정 항목 작업](../vsto/working-with-calendar-items.md)|일정 항목을 사용하여 작업을 수행하는 방법을 보여 주는 항목을 제공합니다.|
|[방법: 프로그래밍 방식으로 현재 Outlook 항목 확인](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|현재 폴더의 이름 및 선택한 항목에 대한 일부 정보를 표시하는 방법을 보여 줍니다.|
