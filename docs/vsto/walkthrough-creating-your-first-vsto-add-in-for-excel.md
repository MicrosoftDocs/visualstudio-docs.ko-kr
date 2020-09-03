---
title: '연습: Excel 용 첫 VSTO 추가 기능 만들기'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b683b1f75f2967807f171c204fbf02a2e5db69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69548009"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>연습: Excel 용 첫 VSTO 추가 기능 만들기
  이 소개용 연습에서는 Microsoft Office Excel의 애플리케이션 수준 추가 기능을 만드는 방법을 보여 줍니다. 이러한 종류의 솔루션에서 만드는 기능은 열려 있는 통합 문서에 관계없이 애플리케이션 자체에서 사용할 수 있습니다.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 이 연습에서는 다음 작업을 수행합니다.

- Excel용 Excel VSTO 추가 기능 프로젝트 만들기

- Excel의 개체 모델을 사용하여 통합 문서가 저장될 때 통합 문서에 텍스트를 추가하는 코드 작성

- 테스트를 위해 프로젝트 빌드 및 실행

- VSTO 추가 기능이 개발 컴퓨터에서 더 이상 자동으로 실행되지 않도록 하기 위해 완료된 프로젝트 정리

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트를 만듭니다.

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Visual Studio에서 새로운 Excel VSTO 추가 기능 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. 확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.

5. 프로젝트 템플릿의 목록에서 **Excel 2010 추가 기능** 또는 **Excel 2013 추가 기능**을 선택합니다.

6. **이름** 상자에 **FirstExcelAddIn**을 입력합니다.

7. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Firstexcel 추가 기능** 프로젝트를 만들고 ThisAddIn 코드 파일을 편집기에서 엽니다.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>저장 된 통합 문서에 텍스트를 추가 하는 코드 작성
 다음 작업으로, ThisAddIn 코드 파일에 코드를 추가합니다. 새 코드에서는 Excel의 개체 모델을 사용하여 현재 워크시트의 첫 행에 상용구 텍스트를 삽입합니다. 현재 워크시트는 사용자가 통합 문서를 저장할 때 열려 있는 워크시트입니다. 기본적으로 ThisAddIn 코드 파일에는 다음과 같은 생성된 코드가 포함되어 있습니다.

- `ThisAddIn` 클래스의 부분 정의. 이 클래스는 코드의 진입점을 제공하고 Excel의 개체 모델에 대한 액세스를 제공합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요. 클래스의 나머지 부분은 `ThisAddIn` 수정 하지 않아야 하는 숨겨진 코드 파일에 정의 됩니다.

- `ThisAddIn_Startup` 및 `ThisAddIn_Shutdown` 이벤트 처리기. 이러한 이벤트 처리기는 Excel에서 VSTO 추가 기능을 로드하고 언로드할 때 호출됩니다. 이러한 이벤트 처리기를 사용하여 VSTO 추가 기능이 로드될 때 VSTO 추가 기능을 초기화하고 추가 기능이 언로드될 때 추가 기능에서 사용하는 리소스를 정리할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>저장된 통합 문서에 텍스트 줄을 추가하려면

1. ThisAddIn 코드 파일에서 다음 코드를 `ThisAddIn` 클래스에 추가합니다. 새 코드에서는 통합 문서가 저장될 때 발생하는 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 이벤트의 이벤트 처리기를 정의합니다.

    사용자가 통합 문서를 저장하면 이벤트 처리기는 현재 워크시트의 시작 부분에 새 텍스트를 추가합니다.

    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]

2. C#을 사용하는 경우 필요한 다음 코드를 `ThisAddIn_Startup` 이벤트 처리기에 추가합니다. 이 코드는 `Application_WorkbookBeforeSave` 이벤트 처리기를 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 이벤트와 연결하는 데 사용됩니다.

    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]

   통합 문서가 저장될 때 통합 문서를 수정하기 위해 앞의 코드 예제에서는 다음 개체를 사용합니다.

- `Application` 클래스의 `ThisAddIn` 필드. `Application` 필드는 Excel의 현재 인스턴스를 나타내는 <xref:Microsoft.Office.Interop.Excel.Application> 개체를 반환합니다.

- `Wb` 이벤트에 대한 이벤트 처리기의 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 매개 변수입니다. `Wb` 매개 변수는 저장된 통합 문서를 나타내는 <xref:Microsoft.Office.Interop.Excel.Workbook> 개체입니다. 자세한 내용은 [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)를 참조 하세요.

## <a name="test-the-project"></a>프로젝트 테스트

### <a name="to-test-the-project"></a>프로젝트를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 빌드하고 실행합니다.

     프로젝트를 빌드하면 코드가 프로젝트의 빌드 출력 폴더에 포함된 어셈블리로 컴파일됩니다. 또한 Visual Studio에서는 Excel에서 VSTO 추가 기능을 검색하고 로드할 수 있도록 하는 레지스트리 항목 집합을 만들고 VSTO 추가 기능이 실행될 수 있도록 개발 컴퓨터에서 보안 설정을 구성합니다. 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

2. Excel에서 통합 문서를 저장합니다.

3. 다음 텍스트가 통합 문서에 추가되었는지 확인합니다.

     **This text was added by using code.**

4. Excel을 닫습니다.

## <a name="clean-up-the-project"></a>프로젝트 정리
 프로젝트의 개발을 완료하면 VSTO 추가 기능 어셈블리, 레지스트리 항목 및 보안 설정을 개발 컴퓨터에서 제거합니다. 이렇게 하지 않으면 개발 컴퓨터에서 Excel을 열 때마다 VSTO 추가 기능이 계속 실행됩니다.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>개발 컴퓨터에서 완료된 프로젝트를 정리하려면

1. Visual Studio의 **빌드** 메뉴에서 **솔루션 정리**를 클릭합니다.

## <a name="next-steps"></a>다음 단계
 기본적인 Excel용 VSTO 추가 기능을 만들었으므로 다음 항목에서 VSTO 추가 기능을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.

- VSTO 추가 기능에서 수행할 수 있는 일반적인 프로그래밍 작업: [Vsto 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md).

- Excel VSTO 추가 기능과 관련 된 프로그래밍 작업: [excel 솔루션](../vsto/excel-solutions.md).

- Excel 개체 모델 사용: [excel 개체 모델 개요](../vsto/excel-object-model-overview.md)

- 예를 들어 리본의 사용자 지정 탭을 추가 하거나 사용자 고유의 사용자 지정 작업창을 만드는 등의 방법으로 Excel의 UI (사용자 인터페이스) 사용자 지정: [OFFICE ui 사용자](../vsto/office-ui-customization.md)지정.

- Excel 용 VSTO 추가 기능 빌드 및 디버그: [Office 솔루션 빌드](../vsto/building-office-solutions.md)

- Excel 용 VSTO 추가 기능 배포: [Office 솔루션을 배포](../vsto/deploying-an-office-solution.md)합니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel 솔루션](../vsto/excel-solutions.md)
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
