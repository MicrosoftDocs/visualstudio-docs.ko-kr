---
title: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 732bd9fe3d34a768e0c6f71315f212c49bdf02af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016389"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기

SharePoint 사이트에 대 한 웹 파트를 만드는 경우 사용자는 브라우저를 사용 하 여 해당 사이트에서 페이지의 콘텐츠, 모양 및 동작을 직접 수정할 수 있습니다. 이 연습에서는 Visual Studio에서 SharePoint **비주얼 웹 파트** 프로젝트 템플릿을 사용 하 여 시각적으로 웹 파트를 만드는 방법을 보여 줍니다.

만들 웹 파트는 월별 달력 보기와 사이트의 각 달력 목록에 대 한 확인란을 표시 합니다. 사용자는 확인란을 선택 하 여 월별 달력 보기에 포함할 달력 목록을 지정할 수 있습니다.

이 연습에서는 다음 작업을 수행합니다.

- **비주얼 웹 파트** 프로젝트 템플릿을 사용 하 여 웹 파트를 만듭니다.
- Visual Studio의 Visual Web Developer designer를 사용 하 여 웹 파트를 디자인 합니다.
- 웹 파트에 있는 컨트롤의 이벤트를 처리 하는 코드를 추가 합니다.
- SharePoint에서 웹 파트 테스트

    > [!NOTE]
    > 다음 지침에서는 사용자 컴퓨터에서 Visual Studio 용 사용자 인터페이스의 일부 요소에 대해 다른 이름이 나 위치를 표시할 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원 되는 버전의 Windows 및 SharePoint

## <a name="create-a-web-part-project"></a>웹 파트 프로젝트 만들기

먼저 **비주얼 웹 파트** 프로젝트 템플릿을 사용 하 여 웹 파트 프로젝트를 만듭니다.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **관리자 권한으로 실행** 옵션을 사용 하 여 시작 합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

     **새 프로젝트** 대화 상자가 나타납니다.

3. **새 프로젝트** 대화 상자의 **Visual c #** 또는 **Visual Basic**에서 **Office/sharepoint**를 확장 한 다음 **SharePoint 솔루션** 범주를 선택 합니다.

4. 템플릿 목록에서 **SharePoint 2013-비주얼 웹 파트** 템플릿을 선택한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다. 이 마법사를 사용 하 여 프로젝트를 디버깅 하는 데 사용할 사이트와 솔루션의 신뢰 수준을 지정할 수 있습니다.

5. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

6. **마침** 단추를 선택 하 여 기본 로컬 SharePoint 사이트를 적용 합니다.

## <a name="designing-the-web-part"></a>웹 파트 디자인

**도구 상자** 에서 비주얼 웹 개발자 디자이너의 화면에 컨트롤을 추가 하 여 웹 파트를 디자인 합니다.

1. Visual Web Developer 디자이너에서 **디자인** 탭을 선택 하 여 디자인 뷰로 전환 합니다.

2. 메뉴 모음에서 **View**  >  **도구 상자**보기를 선택 합니다.

3. **도구 상자**의 **표준** 노드에서 **CheckBoxList** 컨트롤을 선택 하 고 다음 단계 중 하나를 수행 합니다.

    - **CheckBoxList** 컨트롤에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 하 고 디자이너의 첫 번째 줄에 대 한 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    - **도구 상자**에서 **CheckBoxList** 컨트롤을 끌고 디자이너의 첫 번째 줄에 컨트롤을 연결 합니다.

4. 이전 단계를 반복 하지만 단추를 디자이너의 다음 줄로 이동 합니다.

5. 디자이너에서 **Button1** 단추를 선택 합니다.

6. 메뉴 모음에서 **보기**  >  **속성 창**을 선택 합니다.

     **속성** 창이 열립니다.

7. 단추의 **텍스트** 속성에서 **Update**를 입력 합니다.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>웹 파트에 있는 컨트롤의 이벤트 처리

사용자가 마스터 달력 보기에 달력을 추가 하는 데 사용할 수 있는 코드를 추가 합니다.

1. 다음 단계 중 하나를 수행합니다.

   - 디자이너에서 **업데이트** 단추를 두 번 클릭 합니다.

   - **업데이트** 단추의 **속성** 창에서 **이벤트** 단추를 선택 합니다. **클릭** 속성에서 **Button1_Click**를 입력 한 다음 enter 키를 선택 합니다.

     코드 편집기에서 사용자 정의 컨트롤 코드 파일이 열리고 `Button1_Click` 이벤트 처리기가 나타납니다. 나중에이 이벤트 처리기에 코드를 추가 합니다.

2. 사용자 정의 컨트롤 코드 파일의 맨 위에 다음 문을 추가 합니다.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. 클래스에 다음 코드 줄을 추가 `VisualWebPart1` 합니다. 이 코드는 월별 달력 뷰 컨트롤을 선언 합니다.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. `Page_Load`클래스의 메서드를 `VisualWebPart1` 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - 사용자 정의 컨트롤에 월별 달력 보기를 추가 합니다.

   - 사이트의 각 달력 목록에 대 한 확인란을 추가 합니다.

   - 달력 보기에 표시 되는 각 항목 형식에 대 한 템플릿을 지정 합니다.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. `Button1_Click`클래스의 메서드를 `VisualWebPart1` 다음 코드로 바꿉니다. 이 코드는 선택한 각 달력의 항목을 마스터 달력 보기에 추가 합니다.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>웹 파트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 웹 파트는 SharePoint의 웹 파트 갤러리에 자동으로 추가 됩니다. 이 프로젝트를 테스트 하려면 다음 작업을 수행 합니다.

- 두 개의 개별 달력 목록에 이벤트를 추가 합니다.
- 웹 파트 페이지에 웹 파트를 추가 합니다.
- 월별 달력 보기에 포함할 목록을 지정 합니다.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>사이트의 일정 목록에 이벤트를 추가 하려면

1. Visual Studio에서 **F5** 키를 선택 합니다.

     SharePoint 사이트가 열리고 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 빠른 실행 표시줄이 페이지에 나타납니다.

2. 빠른 실행 표시줄의 **목록**에서 **달력** 링크를 선택 합니다.

     **달력** 페이지가 나타납니다.

     빠른 실행 표시줄에 일정 링크가 표시 되지 않는 경우 **사이트 콘텐츠** 링크를 선택 합니다. 사이트 콘텐츠 페이지에 **일정** 항목이 표시 되지 않으면 하나를 만듭니다.

3. 달력 페이지에서 일을 선택한 다음 선택한 날짜의 **추가** 링크를 선택 하 여 이벤트를 추가 합니다.

4. **제목** 상자에서 **기본 달력에 이벤트**를 입력 한 다음 **저장** 단추를 선택 합니다.

5. **사이트 콘텐츠** 링크를 선택 하 고 **앱 추가** 타일을 선택 합니다.

6. **만들기** 페이지에서 **달력** 유형을 선택 하 고 일정 이름을 지정한 다음 **만들기** 단추를 선택 합니다.

7. 새 일정에 이벤트를 추가 하 고 **사용자 지정 달력에서 이벤트 이벤트**의 이름을 지정한 다음 **저장** 단추를 선택 합니다.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>웹 파트 페이지에 웹 파트를 추가 하려면

1. **사이트 내용** 페이지에서 **사이트 페이지** 폴더를 엽니다.

2. 리본 메뉴에서 **파일** 탭을 선택 하 고 **새 문서** 메뉴를 연 다음 **웹 파트 페이지** 명령을 선택 합니다.

3. **새 웹 파트 페이지** 페이지에서 **SampleWebPartPage**페이지의 이름을 지정한 다음 **만들기** 단추를 선택 합니다.

     웹 파트 페이지가 표시 됩니다.

4. 웹 파트 페이지의 위쪽 영역에서 **삽입** 탭을 선택한 다음 **웹 파트** 단추를 선택 합니다.

5. **사용자 지정** 폴더를 선택 하 고 **VisualWebPart1** 웹 파트를 선택한 다음 **추가** 단추를 선택 합니다.

     웹 파트가 페이지에 표시 됩니다. 웹 파트에 표시 되는 컨트롤은 다음과 같습니다.

    - 월별 달력 뷰입니다.

    - **업데이트** 단추입니다.

    - **달력** 확인란입니다.

    - **사용자 지정 달력** 확인란입니다.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>월별 달력 보기에 포함할 목록을 지정 하려면

웹 파트에서 월별 달력 보기에 포함할 달력을 지정한 다음 **업데이트** 단추를 선택 합니다.

지정한 모든 달력의 이벤트가 월별 달력 보기에 표시 됩니다.

## <a name="see-also"></a>추가 정보

SharePoint 용 웹 [파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
