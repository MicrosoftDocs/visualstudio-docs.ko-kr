---
title: Excel 용 첫 문서 수준 사용자 지정 만들기
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b75bf6894bff4e5fa8d6ac17ed537f15041b3ede
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585004"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>연습: Excel 용 첫 문서 수준 사용자 지정 만들기

  이 소개용 연습에서는 Microsoft Office Excel에 대한 문서 수준 사용자 지정을 만드는 방법을 보여 줍니다. 이러한 종류의 솔루션에서 만드는 기능은 특정 통합 문서가 열려 있는 경우에만 사용할 수 있습니다. 통합 문서가 열려 있을 때 새 리본 탭 표시와 같은 애플리케이션 수준 변경은 문서 수준 사용자 지정을 사용하여 수행할 수 없습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- Excel 통합 문서 프로젝트 만들기

- Visual Studio 디자이너에 호스트된 워크시트에 텍스트 추가

- Excel의 개체 모델을 사용하여 사용자 지정 워크시트가 열릴 때 워크시트에 텍스트를 추가하는 코드 작성

- 테스트를 위해 프로젝트 빌드 및 실행

- 완료된 프로젝트를 정리하여 개발 컴퓨터에서 불필요한 빌드 파일 및 보안 설정 제거

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소

 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 또는 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]

## <a name="create-the-project"></a>프로젝트 만들기

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Visual Studio에서 새 Excel 통합 문서 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.
::: moniker range="vs-2017"
3. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. 확장 된 **Office/SharePoint** 노드 아래에서 **VSTO 추가 기능** 노드를 선택 합니다.

5. 프로젝트 템플릿 목록에서 Excel VSTO 통합 문서 프로젝트를 선택 합니다.

6. **이름** 상자에 **first통합 사용자 지정**을 입력 합니다.

7. **확인**을 클릭합니다.

8. **Visual Studio Tools for Office 프로젝트 마법사**에서 **새 문서 만들기** 를 선택 하 고 **확인**을 클릭 합니다.
::: moniker-end
::: moniker range=">=vs-2019"
3. **새 프로젝트 만들기** 대화 상자에서 **Excel VSTO 통합 문서** 프로젝트를 선택 합니다.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. **다음**을 클릭합니다.

5. **새 프로젝트 구성** 대화 상자의 **이름** 상자에 **first통합 사용자 지정** 을 입력 하 고 **만들기**를 클릭 합니다.

6. **Visual Studio Tools for Office 프로젝트 마법사**에서 **새 문서 만들기** 를 선택 하 고 **확인**을 클릭 합니다.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**First통합 문서의 사용자 지정** 프로젝트를 만들고 프로젝트에 다음 파일을 추가 합니다.

   - *Firstworkbook 사용자 지정*.xlsx-프로젝트의 Excel 통합 문서를 나타냅니다. 모든 워크시트 및 차트를 포함합니다.

   - Sheet1 (Visual Basic의 경우 *.vb* 파일 또는 Visual c #의 경우 *.cs* 파일)-통합 문서의 첫 번째 워크시트에 대 한 디자인 화면 및 코드를 제공 하는 워크시트입니다. 자세한 내용은 [워크시트 호스트 항목](../vsto/worksheet-host-item.md)을 참조 하세요.

   - Sheet2 (Visual Basic의 경우 *.vb* 파일 또는 Visual c #의 경우 *.cs* 파일)-통합 문서의 두 번째 워크시트에 대 한 디자인 화면 및 코드를 제공 하는 워크시트입니다.

   - Sheet3 (Visual Basic의 경우 *.vb* 파일 또는 Visual c #의 경우 *.cs* 파일)-통합 문서의 세 번째 워크시트에 대 한 디자인 화면 및 코드를 제공 하는 워크시트입니다.

   - ThisWorkbook (Visual Basic의 경우 *.vb* 파일 또는 Visual c #의 경우 *.cs* 파일)-통합 문서 수준 사용자 지정을 위한 디자인 화면 및 코드를 포함 합니다. 자세한 내용은 [통합 문서 호스트 항목](../vsto/workbook-host-item.md)을 참조 하세요.

     Sheet1 코드 파일이 디자이너에서 자동으로 열립니다.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>디자이너에서 워크시트를 닫았다가 다시 엽니다.

 프로젝트를 개발하는 동안 디자이너에서 의도적으로 또는 실수로 통합 문서 또는 워크시트를 닫은 경우 다시 열 수 있습니다.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>디자이너에서 워크시트를 닫았다가 다시 열려면

1. 디자이너 창의 **닫기** 단추 (X)를 클릭 하 여 통합 문서를 닫습니다.

2. **솔루션 탐색기**에서 **Sheet1** 코드 파일을 마우스 오른쪽 단추로 클릭 하 고 **디자이너 보기**를 클릭 합니다.

     \- 또는 -

     **솔루션 탐색기**에서 **Sheet1** 코드 파일을 두 번 클릭 합니다.

## <a name="add-text-to-a-worksheet-in-the-designer"></a>디자이너에서 워크시트에 텍스트 추가

 디자이너에서 열려 있는 워크시트를 수정하여 사용자 지정의 UI(사용자 인터페이스)를 디자인할 수 있습니다. 예를 들어 셀에 텍스트를 추가하거나, 수식을 적용하거나, Excel 컨트롤을 추가할 수 있습니다. 디자이너를 사용 하는 방법에 대 한 자세한 내용은 [Visual Studio 환경의 Office 프로젝트](../vsto/office-projects-in-the-visual-studio-environment.md)를 참조 하세요.

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>디자이너를 사용하여 워크시트에 텍스트를 추가하려면

1. 디자이너에 열려 있는 워크시트에서 **A1**셀을 선택 하 고 다음 텍스트를 입력 합니다.

     **This text was added by using the designer.**

> [!WARNING]
> 이 텍스트 줄을 **A2**셀에 추가 하는 경우이 예제에서 다른 코드를 통해 덮어씁니다.

## <a name="add-text-to-a-worksheet-programmatically"></a>프로그래밍 방식으로 워크시트에 텍스트 추가

 다음에는 Sheet1 코드 파일에 코드를 추가합니다. 새 코드는 Excel의 개체 모델을 사용하여 통합 문서에 두 번째 텍스트 줄을 추가합니다. 기본적으로 Sheet1 코드 파일에는 다음과 같은 생성된 코드가 포함됩니다.

- 워크시트의 프로그래밍 모델을 나타내고 Excel의 개체 모델에 대한 액세스를 제공하는 `Sheet1` 클래스의 부분 정의입니다. 자세한 내용은 [워크시트 호스트 항목](../vsto/worksheet-host-item.md) 및 [Word 개체 모델 개요](../vsto/word-object-model-overview.md)를. `Sheet1` 클래스의 나머지 부분은 수정해서는 안 되는 숨김 코드 파일에서 정의됩니다.

- `Sheet1_Startup` 및 `Sheet1_Shutdown` 이벤트 처리기. 이러한 이벤트 처리기는 Excel에서 사용자 지정을 로드하고 언로드할 때 호출됩니다. 이러한 이벤트 처리기를 사용하여 사용자 지정이 로드될 때 사용자 지정을 초기화하고 사용자 지정이 언로드될 때 사용자 지정에서 사용하는 리소스를 정리할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>코드를 사용하여 워크시트에 두 번째 텍스트 줄을 추가하려면

1. **솔루션 탐색기**에서 **Sheet1**을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

     Visual Studio에서 코드 파일이 열립니다.

2. `Sheet1_Startup` 이벤트 처리기를 다음 코드로 바꿉니다. Sheet1이 열릴 때 이 코드는 워크시트에 두 번째 텍스트 줄을 추가합니다.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>프로젝트 테스트

### <a name="to-test-your-workbook"></a>통합 문서를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 빌드하고 실행합니다.

     프로젝트를 빌드하면 코드가 통합 문서와 연결된 어셈블리로 컴파일됩니다. Visual Studio는 프로젝트에 대한 빌드 출력 폴더에 통합 문서와 어셈블리의 복사본을 넣고 사용자 지정을 실행할 수 있도록 개발 컴퓨터의 보안 설정을 구성합니다. 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

2. 통합 문서에서 다음 텍스트가 표시되는지 확인합니다.

     **This text was added by using the designer.**

     **This text was added by using code.**

3. 통합 문서를 닫습니다.

## <a name="clean-up-the-project"></a>프로젝트 정리

 프로젝트 개발을 완료하면 빌드 출력 폴더의 파일 및 빌드 프로세스에서 생성된 보안 설정을 제거해야 합니다.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>개발 컴퓨터에서 완료된 프로젝트를 정리하려면

1. Visual Studio의 **빌드** 메뉴에서 **솔루션 정리**를 클릭합니다.

## <a name="next-steps"></a>다음 단계

 기본적인 Excel용 문서 수준 사용자 지정을 만들었으므로 다음 항목에서 사용자 지정을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.

- 문서 수준 사용자 지정에서 수행할 수 있는 일반적인 프로그래밍 작업: [문서 수준 사용자 지정](../vsto/programming-document-level-customizations.md)프로그래밍.

- Excel 용 문서 수준 사용자 지정과 관련 된 프로그래밍 작업: [excel 솔루션](../vsto/excel-solutions.md).

- Excel 개체 모델 사용: [excel 개체 모델 개요](../vsto/excel-object-model-overview.md)

- 예를 들어, 리본 메뉴에 사용자 지정 탭을 추가 하거나 사용자 고유의 작업 창 ( [OFFICE ui 사용자 지정](../vsto/office-ui-customization.md))을 만들어 EXCEL의 ui를 사용자 지정할 수 있습니다.

- Visual Studio의 Office 개발 도구에서 제공 하는 확장 된 Excel 개체를 사용 하 여 Excel 개체 모델을 사용 하 여 불가능 한 작업 수행 (예: 문서에서 관리 되는 컨트롤 호스팅 및 Windows Forms 데이터 바인딩 모델을 사용 하 여 Excel 컨트롤을 데이터에 바인딩): [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)

- Excel 용 문서 수준 사용자 지정 빌드 및 디버그: [Office 솔루션 빌드](../vsto/building-office-solutions.md)

- Excel 용 문서 수준 사용자 지정 배포: [Office 솔루션을 배포](../vsto/deploying-an-office-solution.md)합니다.

## <a name="see-also"></a>참고 항목

- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel 솔루션](../vsto/excel-solutions.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)
- [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
