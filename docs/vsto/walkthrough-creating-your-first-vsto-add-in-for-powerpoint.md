---
title: '연습: PowerPoint 용 첫 VSTO 추가 기능 만들기'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a50a47a813891151427707c371f1ebf3f75c336f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584310"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>연습: PowerPoint 용 첫 VSTO 추가 기능 만들기
  이 연습에서는 Microsoft Office PowerPoint 용 VSTO 추가 기능을 만드는 방법을 보여 줍니다. 이러한 종류의 솔루션에서 만드는 기능은 열려 있는 프레젠테이션에 관계없이 애플리케이션 자체에서 사용할 수 있습니다. 자세한 내용은 [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조 하세요.

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- PowerPoint용 PowerPoint VSTO 추가 기능 프로젝트 만들기

- PowerPoint의 개체 모델을 사용하여 각각의 새 슬라이드에 텍스트 상자를 추가하는 코드 작성

- 테스트를 위해 프로젝트 빌드 및 실행

- VSTO 추가 기능이 개발 컴퓨터에서 더 이상 자동으로 실행되지 않도록 하기 위해 프로젝트 정리

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>프로젝트 만들기

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. 확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.

5. 프로젝트 템플릿 목록에서 PowerPoint VSTO 추가 기능 프로젝트를 선택합니다.

6. **이름** 상자에 **FirstPowerPointAddIn**을 입력 합니다.

7. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstPowerPointAddIn** 프로젝트를 만들고 **ThisAddIn** 코드 파일을 편집기에서 엽니다.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>각각의 새 슬라이드에 텍스트를 추가 하는 코드 작성
 다음 작업으로, ThisAddIn 코드 파일에 코드를 추가합니다. 새 코드는 PowerPoint의 개체 모델을 사용하여 각각의 새 슬라이드에 텍스트 상자를 추가합니다. 기본적으로 ThisAddIn 코드 파일에는 다음과 같은 생성된 코드가 포함되어 있습니다.

- `ThisAddIn` 클래스의 부분 정의. 이 클래스는 코드의 진입점을 제공하고 PowerPoint의 개체 모델에 대한 액세스를 제공합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요. 클래스의 나머지 부분은 `ThisAddIn` 수정 하지 않아야 하는 숨겨진 코드 파일에 정의 됩니다.

- `ThisAddIn_Startup` 및 `ThisAddIn_Shutdown` 이벤트 처리기. 이러한 이벤트 처리기는 PowerPoint에서 VSTO 추가 기능을 로드하고 언로드할 때 호출됩니다. 이러한 이벤트 처리기를 사용하여 VSTO 추가 기능이 로드될 때 VSTO 추가 기능을 초기화하고 VSTO 추가 기능이 언로드될 때 VSTO 추가 기능에서 사용하는 리소스를 정리할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="to-add-a-text-box-to-each-new-slide"></a>각각의 새 슬라이드에 텍스트 상자를 추가하려면

1. ThisAddIn 코드 파일에서 다음 코드를 `ThisAddIn` 클래스에 추가합니다. 이 코드는 [응용 프로그램](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) 개체의 [PresentationNewSlide 이벤트 EApplication_Event](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) 에 대 한 이벤트 처리기를 정의 합니다.

    사용자가 활성 프레젠테이션에 새 슬라이드를 추가하면 이 이벤트 처리기가 새 슬라이드의 맨 위에 텍스트 상자를 추가하고 텍스트 상자에 일부 텍스트를 추가합니다.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. C#을 사용하는 경우 다음 코드를 `ThisAddIn_Startup` 이벤트 처리기에 추가합니다. 이 코드는 `Application_PresentationNewSlide` 이벤트 처리기를 [PresentationNewSlide 이벤트 EApplication_Event](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) 와 연결 하는 데 필요 합니다.

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   각각의 새 슬라이드를 수정하기 위해 이전 코드 예제에서는 다음 개체를 사용합니다.

- `Application` 클래스의 `ThisAddIn` 필드. `Application`필드는 PowerPoint의 현재 인스턴스를 나타내는 [응용 프로그램](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) 개체를 반환 합니다.

- `Sld` [PresentationNewSlide 이벤트 EApplication_Event](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) 에 대 한 이벤트 처리기의 매개 변수입니다. `Sld`매개 변수는 새 슬라이드를 나타내는 [슬라이드](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) 개체입니다. 자세한 내용은 [PowerPoint solutions](../vsto/powerpoint-solutions.md)을 참조 하세요.

## <a name="test-the-project"></a>프로젝트 테스트
 프로젝트를 빌드 및 실행하는 경우 프레젠테이션에 추가하는 새 슬라이드에 텍스트 상자가 표시되는지 확인합니다.

### <a name="to-test-the-project"></a>프로젝트를 테스트하려면

1. **F5** 키를 눌러 프로젝트를 빌드하고 실행합니다.

     프로젝트를 빌드하면 코드가 프로젝트의 빌드 출력 폴더에 배치된 어셈블리로 컴파일됩니다. 또한 Visual Studio에서는 PowerPoint에서 VSTO 추가 기능을 검색하고 로드할 수 있도록 하는 레지스트리 항목 집합을 만들고 VSTO 추가 기능이 실행될 수 있도록 개발 컴퓨터에서 보안 설정을 구성합니다. 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

2. PowerPoint에서 활성 프레젠테이션에 새 슬라이드를 추가합니다.

3. 슬라이드 맨 위의 새 텍스트 상자에 다음 텍스트가 추가되었는지 확인합니다.

     **This text was added by using code.**

4. PowerPoint를 닫습니다.

## <a name="clean-up-the-project"></a>프로젝트 정리
 프로젝트의 개발을 완료하면 VSTO 추가 기능 어셈블리, 레지스트리 항목 및 보안 설정을 개발 컴퓨터에서 제거합니다. 이렇게 하지 않으면 개발 컴퓨터에서 PowerPoint를 열 때마다 VSTO 추가 기능이 실행됩니다.

### <a name="to-clean-up-your-project"></a>프로젝트를 정리하려면

1. Visual Studio의 **빌드** 메뉴에서 **솔루션 정리**를 클릭합니다.

## <a name="next-steps"></a>다음 단계
 기본적인 PowerPoint용 VSTO 추가 기능을 만들었으므로 다음 항목에서 VSTO 추가 기능을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.

- PowerPoint용 VSTO 추가 기능에서 수행할 수 있는 일반적인 프로그래밍 작업. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

- PowerPoint 개체 모델 사용. 자세한 내용은 [PowerPoint solutions](../vsto/powerpoint-solutions.md)을 참조 하세요.

- PowerPoint의 UI 사용자 지정(예: 리본에 사용자 지정 탭 추가 또는 사용자 고유의 사용자 지정 작업창 만들기). 자세한 내용은 [OFFICE UI 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

- PowerPoint용 VSTO 추가 기능 빌드 및 디버그. 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

- PowerPoint용 VSTO 추가 기능 배포. 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [PowerPoint 솔루션](../vsto/powerpoint-solutions.md)
- [Office UI 사용자 지정](../vsto/office-ui-customization.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
