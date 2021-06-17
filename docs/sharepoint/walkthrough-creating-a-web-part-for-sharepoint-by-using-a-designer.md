---
title: 디자이너를 사용하여 SharePoint용 웹 파트 만들기
description: 이 연습에서는 Visual Studio SharePoint Visual Web Part 프로젝트 템플릿을 사용하여 웹 파트를 시각적으로 만듭니다.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 55f69875b06428c9bbe179e73dd6ea9b4ef40b8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112449"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>연습: 디자이너를 사용하여 SharePoint용 웹 파트 만들기

SharePoint 사이트에 대한 웹 파트를 만드는 경우 사용자는 브라우저를 사용하여 해당 사이트의 페이지 콘텐츠, 모양 및 동작을 직접 수정할 수 있습니다. 이 연습에서는 Visual Studio SharePoint Visual Web Part 프로젝트 템플릿을 사용하여 **웹 파트를** 시각적으로 만드는 방법을 보여줍니다.

만들 웹 파트에는 사이트의 각 일정 목록에 대한 월별 달력 보기와 확인란이 표시됩니다. 사용자는 확인란을 선택하여 월별 달력 보기에 포함할 달력 목록을 지정할 수 있습니다.

이 연습에서는 다음 작업을 수행합니다.

- **Visual Web Part** 프로젝트 템플릿을 사용하여 웹 파트 만들기
- Visual Studio Visual Web Developer 디자이너를 사용하여 웹 파트 디자인
- 웹 파트에서 컨트롤의 이벤트를 처리하는 코드를 추가합니다.
- SharePoint에서 웹 파트 테스트

    > [!NOTE]
    > 컴퓨터는 다음 지침에서 Visual Studio 사용자 인터페이스의 일부 요소에 대해 다른 이름 또는 위치를 표시할 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Windows 및 SharePoint 버전.

## <a name="create-a-web-part-project"></a>웹 파트 프로젝트 만들기

먼저 **Visual Web Part** 프로젝트 템플릿을 사용하여 웹 파트 프로젝트를 만듭니다.

1. 관리자 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **권한으로 실행** 옵션을 사용하여 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.
::: moniker range="=vs-2017"

3. 새 **프로젝트** 대화 상자의 **Visual C#** 또는 **Visual Basic** 아래에서 **Office/SharePoint** 를 확장한 다음 **SharePoint 솔루션 범주를** 선택합니다.

4. 템플릿 목록에서 **SharePoint 2013 - Visual Web Part** 템플릿을 선택한 다음 **확인** 단추를 선택합니다.

     **SharePoint 사용자 지정 마법사가** 나타납니다. 이 마법사를 사용하여 프로젝트를 디버그하는 데 사용할 사이트와 솔루션의 신뢰 수준을 지정할 수 있습니다.
::: moniker-end
::: moniker range=">=vs-2019"
3. 새 **프로젝트 만들기** 대화 상자에서 설치한 특정 버전의 *SharePoint에* 대해 SharePoint 빈 프로젝트 *를 선택합니다. 예를 들어 SharePoint 2019 설치가 있는 경우 **SharePoint 2019 - 빈 프로젝트** 템플릿을 선택합니다.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. **이름** 상자에 **TestProject1 을** 입력한 **다음, 만들기** 단추를 선택합니다.

::: moniker-end
5. 이 **SharePoint 솔루션의 신뢰 수준은 무엇인가요?** 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택합니다.

6. **마침** 단추를 선택하여 기본 로컬 SharePoint 사이트를 적용합니다.

## <a name="designing-the-web-part"></a>웹 파트 디자인

**도구 상자의** 컨트롤을 Visual Web Developer 디자이너의 표면에 추가하여 웹 파트를 디자인합니다.

1. Visual Web Developer 디자이너에서 **디자인** 탭을 선택하여 디자인 뷰 전환합니다.

2. 메뉴 모음에서 도구 상자 **보기를**  >  선택합니다.

3. **도구 상자의** **표준** 노드에서 **CheckBoxList** 컨트롤을 선택한 후 다음 단계 중 하나를 수행합니다.

    - **CheckBoxList** 컨트롤에 대한 바로 가기 메뉴를 **열고, 복사를** 선택하고, 디자이너의 첫 번째 줄에 대한 바로 가기 메뉴를 연 다음, **붙여넣기를** 선택합니다.

    - **도구 상자** 에서 **CheckBoxList** 컨트롤을 끌어 디자이너의 첫 번째 줄에 연결합니다.

4. 이전 단계를 반복하지만 단추를 디자이너의 다음 줄로 이동합니다.

5. 디자이너에서 **Button1** 단추를 선택합니다.

6. 메뉴 모음에서 속성 **보기**  >  **창** 을 선택합니다.

     **속성** 창이 열립니다.

7. 단추의 **Text** 속성에 업데이트 를 **입력합니다.**

## <a name="handling-the-events-of-controls-on-the-web-part"></a>웹 파트에서 컨트롤의 이벤트 처리

사용자가 마스터 달력 보기에 달력을 추가할 수 있도록 하는 코드를 추가합니다.

1. 다음 단계 중 하나를 수행합니다.

   - 디자이너에서 **업데이트** 단추를 두 번 클릭합니다.

   - **업데이트** 단추의 **속성** 창에서 **이벤트** 단추를 선택합니다. **Click** 속성에서 **Button1_Click** 입력한 다음 Enter 키를 선택합니다.

     사용자 제어 코드 파일이 코드 편집기에서 열리고 `Button1_Click` 이벤트 처리기가 나타납니다. 나중에 이 이벤트 처리기에 코드를 추가합니다.

2. 다음 문을 사용자 제어 코드 파일의 맨 위에 추가합니다.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. 클래스에 다음 코드 줄을 `VisualWebPart1` 추가합니다. 이 코드는 월간 달력 보기 컨트롤을 선언합니다.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. `Page_Load`클래스의 메서드를 `VisualWebPart1` 다음 코드로 대체합니다. 이 코드는 다음 작업을 수행합니다.

   - 사용자 컨트롤에 월별 달력 보기를 추가합니다.

   - 사이트의 각 일정 목록에 대한 확인란을 추가합니다.

   - 달력 보기에 나타나는 각 항목 유형에 대한 템플릿을 지정합니다.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. `Button1_Click`클래스의 메서드를 `VisualWebPart1` 다음 코드로 대체합니다. 이 코드는 선택한 각 달력의 항목을 마스터 달력 보기에 추가합니다.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>웹 파트 테스트

프로젝트를 실행하면 SharePoint 사이트가 열립니다. 웹 파트는 SharePoint의 웹 파트 갤러리에 자동으로 추가됩니다. 이 프로젝트를 테스트하려면 다음 작업을 수행합니다.

- 별도의 두 일정 목록에 각각 이벤트를 추가합니다.
- 웹 파트 페이지에 웹 파트를 추가합니다.
- 월별 달력 보기에 포함할 목록을 지정합니다.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>사이트의 일정 목록에 이벤트를 추가하려면

1. Visual Studio **F5** 키를 선택합니다.

     SharePoint 사이트가 열리고 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 빠른 실행 표시줄이 페이지에 표시됩니다.

2. 빠른 실행 표시줄의 **목록** 에서 **일정** 링크를 선택합니다.

     **일정** 페이지가 나타납니다.

     빠른 실행 표시줄에 일정 링크가 표시되지 않으면 사이트 **콘텐츠** 링크를 선택합니다. 사이트 콘텐츠 페이지에 **일정** 항목이 표시되지 않으면 만듭니다.

3. 달력 페이지에서 일을 선택한 다음, 선택한 날에 **추가** 링크를 선택하여 이벤트를 추가합니다.

4. **제목** 상자에 기본 **달력 에 이벤트를** 입력한 다음 **저장** 단추를 선택합니다.

5. 사이트 **콘텐츠** 링크를 선택한 다음, **앱 추가 타일을** 선택합니다.

6. **만들기** 페이지에서 **달력** 유형을 선택하고 달력 이름을 지정한 다음 **만들기** 단추를 선택합니다.

7. 새 달력에 이벤트를 **추가하고, 사용자 지정 달력에서** 이벤트 이름을 이벤트로 지정한 **다음, 저장** 단추를 선택합니다.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>웹 파트 페이지에 웹 파트를 추가하려면

1. 사이트 **콘텐츠** 페이지에서 **사이트 페이지** 폴더를 엽니다.

2. 리본에서 **파일** 탭을 선택하고 **새 문서** 메뉴를 연 다음 웹 **파트 페이지** 명령을 선택합니다.

3. 새 **웹 파트 페이지에서** 페이지 이름을 **SampleWebPartPage.aspx로** 지정한 **다음, 만들기** 단추를 선택합니다.

     웹 파트 페이지가 나타납니다.

4. 웹 파트 페이지의 위쪽 영역에서 **삽입** 탭을 선택한 다음 **웹 파트** 단추를 선택합니다.

5. 사용자 **지정** 폴더를 선택하고 **VisualWebPart1** 웹 파트를 선택한 다음, **추가** 단추를 선택합니다.

     웹 파트가 페이지에 나타납니다. 다음 컨트롤이 웹 파트에 표시됩니다.

    - 월간 달력 보기입니다.

    - **업데이트** 단추입니다.

    - **일정** 확인란입니다.

    - **사용자 지정 달력** 확인란입니다.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>월별 달력 보기에 포함할 목록을 지정하려면

웹 파트에서 월별 달력 보기에 포함할 달력을 지정한 다음 **업데이트** 단추를 선택합니다.

지정한 모든 달력의 이벤트가 월별 달력 보기에 표시됩니다.

## <a name="see-also"></a>참조

SharePoint용 웹 [파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [방법: SharePoint 웹 파트](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 만들기 [연습: SharePoint용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
