---
title: '연습: Outlook 양식 영역 디자인'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01cfe55964a1d61c2ad200c9538ced9ff0aa5599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985466"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>연습: Outlook 양식 영역 디자인
  사용자 지정 양식 영역은 표준 또는 사용자 지정 Microsoft Office Outlook 양식을 확장합니다. 이 연습에서는 연락처 항목의 검사기 창에 새 페이지로 표시되는 사용자 지정 양식 영역을 디자인합니다. 이 양식 영역은 Windows Live 로컬 검색 웹 사이트에 주소 정보를 전송하여 연락처에 대해 나열된 각 주소의 지도를 표시합니다. 양식 영역에 대 한 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 이 연습에서는 다음 작업을 수행합니다.

- 새 Outlook VSTO 추가 기능 프로젝트 만들기

- VSTO 추가 기능 프로젝트에 양식 영역 추가

- 양식 영역의 레이아웃 디자인

- 양식 영역의 동작 사용자 지정

- Outlook 양식 영역 테스트

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] 이상.

  ![비디오에 연결](../vsto/media/playvideo.gif "비디오에 링크") 이 항목의 비디오 버전은 [비디오 방법: Outlook 양식 영역 디자인](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90))을 참조 하세요.

## <a name="create-a-new-outlook-vsto-add-in-project"></a>새 Outlook VSTO 추가 기능 프로젝트 만들기
 먼저 기본 VSTO 추가 기능 프로젝트를 만듭니다.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>새 Outlook VSTO 추가 기능 프로젝트를 만들려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 이름이 **Mapitaddin**인 Outlook VSTO 추가 기능 프로젝트를 만듭니다.

2. **새 프로젝트** 대화 상자에서 **솔루션용 디렉터리 만들기**를 선택합니다.

3. 임의 디렉터리에 프로젝트를 저장합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO 추가 기능 프로젝트에 양식 영역 추가
 Outlook VSTO 추가 기능 솔루션에는 하나 이상의 Outlook 양식 영역 항목이 포함될 수 있습니다. **새 Outlook 양식 영역** 마법사를 사용 하 여 프로젝트에 양식 영역 항목을 추가 합니다.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO 추가 기능 프로젝트에 양식 영역을 추가하려면

1. **솔루션 탐색기**에서 **mapitaddin** 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

3. **새 항목 추가** 대화 상자에서 **Outlook 양식 영역**을 선택 하 고 파일 이름을 **mapit.vb**으로 지정한 다음 **추가**를 클릭 합니다.

     **Newoutlook 양식 영역** 마법사가 시작 됩니다.

4. **양식 영역을 만드는 방법 선택** 페이지에서 **새 양식 영역 디자인**을 클릭 하 고 **다음**을 클릭 합니다.

5. **만들 양식 영역 유형 선택** 페이지에서 **개별**을 클릭 한 후 **다음**을 클릭 합니다.

     *별도의* 양식 영역은 Outlook 양식에 새 페이지를 추가 합니다. 양식 영역 형식에 대 한 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

6. **설명 텍스트를 입력 하 고 디스플레이 기본 설정을 선택** 하세요. 페이지에서 **이름** 상자에 **Map It** 를 입력 합니다.

     이 이름은 연락처 항목이 열려 있을 때 검사기 창의 리본 메뉴에 나타납니다.

7. **작성 모드의 검사기** 및 **읽기 모드의 검사기**를 선택한 후 **다음**을 클릭 합니다.

8. **이 양식 영역을 표시할 메시지 클래스** 를 지정 하십시오. 페이지에서 **메일 메시지**를 지우고 **연락처**를 선택한 다음 **마침**을 클릭 합니다.

     *MapIt.cs* 또는 *mapit.vb* 파일이 프로젝트에 추가 됩니다.

## <a name="design-the-layout-of-the-form-region"></a>양식 영역의 레이아웃 디자인
 *양식 영역 디자이너*를 사용 하 여 시각적으로 양식 영역을 개발 합니다. 관리되는 컨트롤을 양식 영역 디자이너 화면으로 끌 수 있습니다. 디자이너와 **속성** 창을 사용 하 여 컨트롤 레이아웃과 모양을 조정 합니다.

### <a name="to-design-the-layout-of-the-form-region"></a>양식 영역의 레이아웃을 디자인하려면

1. **솔루션 탐색기**에서 **mapitaddin** 프로젝트를 확장 한 다음 *MapIt.cs* 또는 *Mapit.vb* 를 두 번 클릭 하 여 양식 영역 디자이너를 엽니다.

2. 디자이너를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

3. **속성** 창에서 **크기** 를 **664, 469**로 설정 합니다.

     이렇게 하면 양식 영역이 지도를 표시할 수 있을 만큼 커집니다.

4. **보기** 메뉴에서 **도구 상자**를 클릭합니다.

5. **도구 상자**의 **공용 컨트롤** 탭에서 양식 영역에 **WebBrowser** 를 추가 합니다.

     **WebBrowser** 에는 연락처에 대해 나열 된 각 주소의 지도가 표시 됩니다.

## <a name="customize-the-behavior-of-the-form-region"></a>양식 영역의 동작 사용자 지정
 양식 영역 이벤트 처리기에 코드를 추가하여 런타임에 양식 영역이 동작하는 방식을 사용자 지정합니다. 이 양식 영역에 대해 코드에서 Outlook 항목의 속성을 검사하고 Map It 양식 영역을 표시할지 여부를 확인합니다. 양식 영역을 표시하는 경우 코드에서 Windows Live 로컬 검색으로 이동하고 Outlook 연락처 항목에 나열된 각 주소의 지도를 로드합니다.

### <a name="to-customize-the-behavior-of-the-form-region"></a>양식 영역의 동작을 사용자 지정하려면

1. **솔루션 탐색기**에서 *MapIt.cs* 또는 *mapit.vb*를 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

    *MapIt.cs* 또는 *Mapit.vb* 가 코드 편집기에서 열립니다.

2. **양식 영역 팩터리** 코드 영역을 확장 합니다.

    `MapItFactory`라는 양식 영역 팩터리 클래스가 노출됩니다.

3. 다음 코드를 `MapItFactory_FormRegionInitializing` 이벤트 처리기에 추가합니다. 이 이벤트 처리기는 사용자가 연락처 항목을 열 때 호출됩니다. 다음 코드는 연락처 항목에 주소가 포함되어 있는지 여부를 확인합니다. 연락처 항목에 주소가 포함 되어 있지 않으면이 코드는 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 클래스의 속성을 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true** 로 설정 하 고 양식 영역이 표시 되지 않습니다. 그렇지 않은 경우 VSTO 추가 기능에서 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 이벤트가 발생하고 양식 영역이 표시됩니다.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. 다음 코드를 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 이벤트 처리기에 추가합니다. 이 코드는 다음 작업을 수행합니다.

   - 연락처 항목의 각 주소를 연결하고 URL 문자열을 만듭니다.

   - <xref:System.Windows.Forms.WebBrowser> 개체의 <xref:System.Windows.Forms.WebBrowser.Navigate%2A> 메서드를 호출하고 URL 문자열을 매개 변수로 전달합니다.

     로컬 검색 웹 사이트가 Map It 양식 영역에 나타나고 각 주소를 스크래치 패드에 표시합니다.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Outlook 양식 영역 테스트
 프로젝트를 실행하면 Visual Studio에서 Outlook을 엽니다. 연락처 항목을 열어 Map It 양식 영역을 표시합니다. Map It 양식 영역은 주소가 포함된 연락처 항목의 양식에 페이지로 표시됩니다.

### <a name="to-test-the-map-it-form-region"></a>Map It 양식 영역을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

     Outlook이 열립니다.

2. Outlook의 **홈** 탭에서 **새 항목**을 클릭 한 다음 **연락처**를 클릭 합니다.

3. 연락처 양식에서 연락처 이름으로 **Ann Beebe** 를 입력 하 고 다음 세 개의 주소를 지정 합니다.

    |주소 형식|주소|
    |------------------|-------------|
    |**비즈니스**|**4567 주 세인트 Buffalo,**|
    |**홈**|**1234 북부 Buffalo**|
    |**기타**|**3456 주 세인트 시애틀, WA**|

4. 연락처 항목을 저장하고 닫습니다.

5. **Ann Beebe** contact 항목을 다시 엽니다.

    Outlook에서는 연락처에 대 한 주소록을 열거나 **사용자 검색**에 Ann Beebe를 입력 하 여 **찾기** 그룹에서이 작업을 수행할 수 있습니다.

6. 항목 리본의 **표시** 그룹에서 **지도** 를 클릭 하 여 map it 양식 영역을 엽니다.

     Map It 양식 영역이 나타나고 로컬 검색 웹 사이트를 표시합니다. **비즈니스**, **홈**및 **기타** 주소가 스크래치 패드에 나타납니다. 스크래치 패드에서 매핑할 주소를 선택합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서 Outlook 애플리케이션의 UI를 사용자 지정하는 방법에 대해 자세히 알아볼 수 있습니다.

- Outlook 항목의 리본을 사용자 지정 하는 방법에 대 한 자세한 내용은 [outlook의 리본 메뉴 사용자 지정](../vsto/customizing-a-ribbon-for-outlook.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [런타임에 양식 영역 액세스](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [Outlook 양식 영역 만들기 지침](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [연습: Outlook에서 디자인 한 양식 영역 가져오기](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Outlook 양식 영역의 사용자 지정 작업](../vsto/custom-actions-in-outlook-form-regions.md)
- [방법: Outlook에서 양식 영역 표시 하지 않기](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
