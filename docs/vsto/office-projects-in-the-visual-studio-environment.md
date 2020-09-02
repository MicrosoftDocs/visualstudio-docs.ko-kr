---
title: Visual Studio 환경의 Office 프로젝트
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65f3a3abfe7e49872c7131a247d74612200bf42a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62978060"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Visual Studio 환경의 Office 프로젝트
  Microsoft Office 프로젝트에는 Windows Forms 프로젝트를 비롯하여 Visual Studio의 다른 프로젝트 형식과 비슷한 개발 환경이 있습니다. Office 프로젝트를 만들거나 열 경우 **솔루션 탐색기**에 프로젝트 항목이 나타납니다. 문서 수준 프로젝트의 경우 문서(Word 문서 또는 Excel 통합 문서)가 Visual Studio에서 열리고 이 문서가 비주얼 디자이너와 같은 기능을 수행합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>솔루션 탐색기의 프로젝트 항목
 문서 수준 프로젝트에서는 **솔루션 탐색기** 에 다음과 같은 기본 항목이 표시됩니다.

- 프로젝트에 의해 사용자 지정된 문서, 통합 문서 및 시트의 노드. 이러한 노드는 문서, 통합 문서 및 시트와 연결된 코드 파일의 컨테이너 역할을 합니다.

- 프로젝트에 의해 사용자 지정된 문서, 통합 문서 및 시트와 연결된 코드 파일. Word 프로젝트에서는 코드 파일이 Word 문서 또는 템플릿에 연결되어 있습니다. Excel 프로젝트에서는 코드 파일이 Excel 통합 문서 또는 템플릿뿐 아니라 통합 문서 또는 템플릿 내의 각 워크시트 및 차트 시트에도 연결되어 있습니다.

- 직접 편집할 수 없는 숨겨진 프로젝트 파일. 자세한 내용은 [숨겨진 프로젝트 파일](#hiddenfiles)을 참조 하세요.

  VSTO 추가 기능 프로젝트에서는 **솔루션 탐색기** 에 다음과 같은 기본 항목이 표시됩니다.

- 애플리케이션 노드. 이 노드의 이름은 **Word**, **Excel**또는 **Outlook**등의 호스트 애플리케이션과 동일합니다. 애플리케이션 노드에는 ThisAddIn 코드 파일이 포함되어 있습니다. 또한 이 노드에서는 **호스트 항목의 네임스페이스** 속성도 제공합니다. 이 속성에 대 한 자세한 내용은 [Office 프로젝트의 속성](../vsto/properties-in-office-projects.md)을 참조 하세요.

- ThisAddIn 코드 파일. 이 파일에는 VSTO 추가 기능에 대해 생성된 `ThisAddIn` 클래스가 포함되어 있습니다. 이 클래스에 대 한 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

- 직접 편집할 수 없는 숨겨진 프로젝트 파일. 자세한 내용은 [숨겨진 프로젝트 파일](#hiddenfiles)을 참조 하세요.

### <a name="temporary-certificates"></a>임시 인증서
 Office 프로젝트에는 *Project Name*_TemporaryKey.pfx라는 임시 인증서도 포함되어 있습니다. 이 인증서는 개발 중 프로젝트의 애플리케이션 및 배포 매니페스트에 서명하는 데 사용됩니다. 자세한 내용은 [office 솔루션에 신뢰 부여](../vsto/granting-trust-to-office-solutions.md) 및 [office 솔루션 보안](../vsto/securing-office-solutions.md)을 참조 하세요.

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> 숨겨진 프로젝트 파일
 몇 개의 프로젝트 파일은 기본적으로 숨겨져 있습니다. 이러한 파일은 Visual Studio에서 생성되며 프로젝트 형식에 따라 달라집니다. 숨김 파일을 표시하려면 **솔루션 탐색기** 에서 **모든 파일 표시**를 클릭합니다.

 숨겨진 프로젝트 파일은 수정하지 마십시오. 이러한 파일은 직접 변경할 수 없으며 변경할 경우 프로젝트가 손상될 수 있습니다. 숨겨진 프로젝트 파일은 문서가 변경될 때마다 다시 생성됩니다. 숨겨진 프로젝트 파일을 수동으로 변경할 경우 해당 변경 내용은 파일이 다시 생성될 때 손실됩니다.

## <a name="document-designer-in-document-level-projects"></a>문서 수준 프로젝트의 문서 디자이너
 Excel 및 Word용 문서 수준 프로젝트에서는 Visual Studio의 프로젝트와 연결된 문서를 호스팅하는 디자이너를 제공합니다. 이 디자이너를 사용하면 Visual Studio 환경을 벗어나지 않고도 문서를 수정할 수 있습니다.

 디자이너에서 문서를 열려면 **솔루션 탐색기** 에서 문서와 연결된 코드 파일을 두 번 클릭합니다. 예를 들어 디자이너에서 Excel 프로젝트의 **Sheet1** 워크시트를 열려면 **Sheet1** 코드 파일을 두 번 클릭합니다.

 디자이너에서 문서를 수정할 경우 Office 애플리케이션 본래의 기능을 사용할 수 있습니다. 예를 들어 문서 또는 워크시트에 텍스트를 입력하거나, 리본 메뉴를 사용하여 테이블 또는 차트를 추가하는 등의 작업을 수행할 수 있습니다. 기본적으로 바로 가기 키 매핑은 Visual Studio 매핑으로 설정됩니다. Office 바로 가기 키 매핑을 대신 사용하려면 **도구** 메뉴의 **옵션** 대화 상자에서 **Microsoft Office 키보드 설정** 노드의 설정을 변경합니다.

### <a name="controls-on-documents"></a>문서의 컨트롤
 Visual Studio *도구 상자* 에서 문서 디자인 화면으로 **호스트 컨트롤** 과 Windows Forms 컨트롤을 끌어 올 수 있습니다. 호스트 컨트롤은 Word 콘텐츠 컨트롤 및 Excel 범위와 같은 특수한 버전의 Office 개체로서, Visual Studio를 사용하여 만든 Office 프로젝트에서 사용할 수 있습니다. 호스트 컨트롤에는 데이터 바인딩 및 추가 이벤트와 같이 해당 Office 개체에서 사용할 수 없는 추가 기능이 있습니다.

 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md) 및 [Office 문서의 Windows forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)를 참조 하세요.

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>디자이너의 Excel 워크시트 및 통합 문서
 디자이너에서 워크시트를 열면 Excel에서 직접 워크시트를 열었을 때와 동일한 방법으로 워크시트를 수정할 수 있습니다. 워크시트 셀을 두 번 클릭하면 셀이 편집 모드로 변경됩니다. 호스트 컨트롤이 들어 있는 셀을 두 번 클릭 하면 코드 편집기가 열리고 Visual Studio에서 컨트롤에 대 한 기본 이벤트 처리기가 생성 됩니다. 다른 워크시트로 이동하려면 디자이너 맨 아래의 워크시트 탭을 클릭합니다.

 디자이너에서 통합 문서를 열 경우 디자인 화면이 표시되지 않습니다. 통합 문서의 디자인 뷰는 디자이너를 채우는 커다란 구성 요소 트레이입니다.

 통합 문서와 통합 문서의 각 시트에는 연결된 코드 파일이 있습니다. 각 코드 파일에는 통합 문서 또는 시트를 나타내는 생성된 *호스트 항목* 클래스가 들어 있습니다. 자세한 내용은 [확장 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)를 참조 하세요.

### <a name="word-documents-in-the-designer"></a>디자이너의 Word 문서
 디자이너에서 문서를 열면 Word에서 직접 문서를 열었을 때와 동일한 방법으로 문서를 수정할 수 있습니다. 문서의 단어를 두 번 클릭하면 해당 단어가 선택됩니다. 그러나 이 단어가 호스트 컨트롤 내에 있으면 코드 편집기가 열리고 Visual Studio에서 컨트롤에 대한 기본 이벤트 처리기가 생성됩니다.

 문서에는 연결된 코드 파일이 있습니다. 이 코드 파일에는 문서를 나타내는 생성된 *호스트 항목* 클래스가 들어 있습니다. 자세한 내용은 [문서 호스트 항목](../vsto/document-host-item.md)을 참조 하세요.

### <a name="design-mode-vs-runtime-mode"></a>디자인 모드와 런타임 모드 비교
 Visual Studio 환경에서 문서를 열 때 문서는 항상 *디자인 모드*에서 열립니다. 호스트 컨트롤을 문서 화면으로 끄는 등의 일부 작업은 디자인 모드에서만 수행할 수 있습니다.

 *런타임 모드*에서 문서를 보려면 Visual Studio 외부에서 응용 프로그램과 문서를 열어야 합니다. 프로젝트를 빌드하여 실행할 수도 있습니다. 이렇게 하면 Visual Studio 외부에서 문서와 애플리케이션이 자동으로 열립니다.

## <a name="code-editor"></a>코드 편집기
 코드 편집기를 사용하면 솔루션에서 표시되는 코드 파일을 보고 수정할 수 있습니다. 이러한 파일에는 솔루션의 동작을 정의하는 코드가 들어 있습니다.

 코드 편집기에 대 한 자세한 내용은 코드 [및 텍스트 편집기에서 코드 작성](../ide/writing-code-in-the-code-and-text-editor.md)을 참조 하세요. Office 프로젝트에서 코드를 작성 하는 방법에 대 한 자세한 내용은 [office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)을 참조 하세요.

## <a name="properties-window"></a>속성 창
 **속성** 창에는 **솔루션 탐색기**에서 선택한 프로젝트 항목에 대한 속성과 디자이너에서 선택한 UI 요소(예: 문서 수준 프로젝트의 문서 또는 컨트롤)에 대한 속성이 표시됩니다. 일부 속성은 애플리케이션이나 문서에 따로 적용되지만 일부 속성은 모든 프로젝트에 동일하게 사용됩니다.

## <a name="data-sources-window"></a>데이터 소스 창
 문서 수준 Office 프로젝트에서 **데이터 원본** 창을 사용하여 데이터 원본을 문서로 끌어 올 수 있으며 데이터 원본에 바인딩된 컨트롤을 만들 수 있습니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 프로젝트의 속성](../vsto/properties-in-office-projects.md)
