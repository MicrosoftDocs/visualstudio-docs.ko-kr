---
title: '연습: Outlook 용 첫 VSTO 추가 기능 만들기'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baedd24b7eba14b3f2fa6496a7a681773b81cb9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69547993"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>연습: Outlook 용 첫 VSTO 추가 기능 만들기
  이 연습에서는 Microsoft Office Outlook용 VSTO 추가 기능을 만드는 방법을 보여 줍니다. 이러한 종류의 솔루션에서 만드는 기능은 열려 있는 Outlook 항목에 관계없이 애플리케이션 자체에서 사용할 수 있습니다. 자세한 내용은 [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조 하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 이 연습에서는 다음 작업을 수행합니다.

- Outlook용 Outlook VSTO 추가 기능 프로젝트 만들기

- Outlook 개체 모델을 사용하여 새 메일 메시지의 제목 및 본문에 텍스트를 추가하는 코드 작성

- 테스트를 위해 프로젝트 빌드 및 실행

- VSTO 추가 기능이 개발 컴퓨터에서 더 이상 자동으로 실행되지 않도록 하기 위해 완료된 프로젝트 정리

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>프로젝트를 만듭니다.

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Visual Studio에서 새로운 Outlook 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. 확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.

5. 프로젝트 템플릿 목록에서 Outlook VSTO 추가 기능 프로젝트를 선택합니다.

6. **이름** 상자에 **FirstOutlookAddIn**을 입력합니다.

7. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**firstoutlookaddin 입력** 프로젝트를 만들고 **ThisAddIn** 코드 파일을 편집기에서 엽니다.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>각각의 새 메일 메시지에 텍스트를 추가 하는 코드 작성
 다음 작업으로, ThisAddIn 코드 파일에 코드를 추가합니다. 새 코드는 Outlook 개체 모델을 사용하여 새 메일 메시지에 각각 텍스트를 추가합니다. 기본적으로 ThisAddIn 코드 파일에는 다음과 같은 생성된 코드가 포함되어 있습니다.

- `ThisAddIn` 클래스의 부분 정의. 이 클래스는 코드의 진입점을 제공하고 Outlook의 개체 모델에 대한 액세스를 제공합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요. 클래스의 나머지 부분은 `ThisAddIn` 수정 하지 않아야 하는 숨겨진 코드 파일에 정의 됩니다.

- `ThisAddIn_Startup` 및 `ThisAddIn_Shutdown` 이벤트 처리기. 이러한 이벤트 처리기는 Outlook에서 VSTO 추가 기능을 로드하고 언로드할 때 호출됩니다. 이러한 이벤트 처리기를 사용하여 VSTO 추가 기능이 로드될 때 VSTO 추가 기능을 초기화하고 VSTO 추가 기능이 언로드될 때 VSTO 추가 기능에서 사용하는 리소스를 정리할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>새 메일 메시지의 제목과 본문에 각각 텍스트를 추가하려면

1. ThisAddIn 코드 파일의 `inspectors` 클래스에서 `ThisAddIn` 라는 필드를 선언합니다. `inspectors` 필드는 현재 Outlook 인스턴스의 검사기 창 컬렉션에 대한 참조를 유지 관리합니다. 이 참조는 가비지 수집기가 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트에 대한 이벤트 처리기가 포함된 메모리를 해제할 수 없게 합니다.

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. `ThisAddIn_Startup` 메서드를 다음 코드로 바꿉니다. 이 코드는 이벤트 처리기를 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트에 연결합니다.

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. ThisAddIn 코드 파일에서 다음 코드를 `ThisAddIn` 클래스에 추가합니다. 이 코드는 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트에 대한 이벤트 처리기를 정의합니다.

    사용자가 새 메일 메시지를 만드는 경우 이 이벤트 처리기는 메시지의 제목 줄과 본문에 텍스트를 추가합니다.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   각각의 새 메일 메시지를 수정하기 위해 이전 코드 예제에서는 다음 개체를 사용합니다.

- `Application` 클래스의 `ThisAddIn` 필드. `Application` 필드는 Outlook의 현재 인스턴스를 나타내는 <xref:Microsoft.Office.Interop.Outlook.Application> 개체를 반환합니다.

- `Inspector` 이벤트에 대한 이벤트 처리기의 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 매개 변수입니다. `Inspector` 매개 변수는 새 메일 메시지의 검사기 창을 나타내는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체입니다. 자세한 내용은 [Outlook solutions](../vsto/outlook-solutions.md)을 참조 하세요.

## <a name="test-the-project"></a>프로젝트 테스트
 프로젝트를 빌드 및 실행하는 경우 새 메일 메시지의 제목 줄과 본문에 텍스트가 표시되는지 확인합니다.

### <a name="to-test-the-project"></a>프로젝트를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 빌드하고 실행합니다.

     프로젝트를 빌드하면 코드가 프로젝트의 빌드 출력 폴더에 포함된 어셈블리로 컴파일됩니다. 또한 Visual Studio에서는 Outlook에서 VSTO 추가 기능을 검색하고 로드할 수 있도록 하는 레지스트리 항목 집합을 만들고 VSTO 추가 기능이 실행될 수 있도록 개발 컴퓨터에서 보안 설정을 구성합니다. 자세한 내용은 [Office 솔루션 빌드 프로세스 개요](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)를 참조 하세요.

2. Outlook에서 새 메일 메시지를 만듭니다.

3. 다음 텍스트가 메시지의 제목 줄과 본문에 추가되었는지 확인합니다.

     **This text was added by using code.**

4. Outlook을 닫습니다.

## <a name="clean-up-the-project"></a>프로젝트 정리
 프로젝트의 개발을 완료하면 VSTO 추가 기능 어셈블리, 레지스트리 항목 및 보안 설정을 개발 컴퓨터에서 제거합니다. 이렇게 하지 않으면 개발 컴퓨터에서 Outlook을 열 때마다 VSTO 추가 기능이 실행됩니다.

### <a name="to-clean-up-your-project"></a>프로젝트를 정리하려면

1. Visual Studio의 **빌드** 메뉴에서 **솔루션 정리**를 클릭합니다.

## <a name="next-steps"></a>다음 단계
 기본적인 Outlook용 VSTO 추가 기능을 만들었으므로 다음 항목에서 VSTO 추가 기능을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.

- Outlook용 VSTO 추가 기능을 사용하여 수행할 수 있는 일반적인 프로그래밍 작업. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

- Outlook 개체 모델 사용. 자세한 내용은 [Outlook solutions](../vsto/outlook-solutions.md)을 참조 하세요.

- Outlook의 UI 사용자 지정(예: 리본에 사용자 지정 탭 추가 또는 사용자 고유의 사용자 지정 작업창 만들기). 자세한 내용은 [OFFICE UI 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

- Outlook용 VSTO 추가 기능 빌드 및 디버그. 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

- Outlook용 VSTO 추가 기능 배포. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [Outlook 솔루션](../vsto/outlook-solutions.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
