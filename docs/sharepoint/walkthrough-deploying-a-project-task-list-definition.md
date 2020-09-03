---
title: '연습: 프로젝트 작업 목록 정의 배포 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b5639fe7a1b35dea41b14be3730986ad7c7309b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015764"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>연습: 프로젝트 작업 목록 정의 배포

이 연습에서는 프로젝트 작업을 추적하기 위해 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]를 사용하여 SharePoint 목록을 만들고, 사용자 지정하고, 디버깅하고, 배포하는 방법을 보여 줍니다.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio 2017 또는 Azure DevOps Services입니다.

## <a name="create-a-sharepoint-list"></a>SharePoint 목록 만들기

SharePoint 목록 프로젝트를 만들고 목록 정의를 작업과 연결합니다.

1. **새 프로젝트** 대화 상자를 열고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

2. **템플릿** 창에서 **SharePoint 2010 프로젝트** 템플릿을 선택 하 고 프로젝트 이름을 **Projecttasklist**로 지정한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

3. 디버깅에 사용할 로컬 SharePoint 사이트를 지정 하 고 **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 합니다.

4. 프로젝트에 대 한 바로 가기 메뉴를 열고 **Add**  >  **새 항목**추가를 선택 합니다.

5. **템플릿** 창에서 **목록** 템플릿을 선택한 다음 **추가** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

6. **목록에 대해 표시할 이름을 선택** 하십시오. 상자에 **Project 작업 목록**를 입력 합니다.

7. 옵션 단추의 **기존 목록 유형에 따라 사용자 지정할 수 없는 목록 만들기** 를 선택한 다음 목록에서 **작업**을 선택 하 고 **마침** 단추를 선택 합니다.

     목록, 기능 및 패키지가 **솔루션 탐색기**에 나타납니다.

## <a name="add-an-event-receiver"></a>이벤트 수신기 추가

작업 목록에서 작업의 기한과 설명을 자동으로 설정하는 이벤트 수신기를 추가할 수 있습니다. 다음 절차에서는 목록 인스턴스에 이벤트 수신자로 간단한 이벤트 처리기를 추가 합니다.

1. 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

2. SharePoint 템플릿 목록에서 **이벤트 수신기** 템플릿을 선택 하 고 이름을 **Projecttasklisteventreceiver**로 지정한 다음

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

3. **이벤트 수신기 설정 선택** 페이지에서 **원하는 이벤트 수신기 유형을** 선택 하십시오. 목록에서 이벤트 수신기 유형으로 **목록 항목 이벤트** 를 선택 합니다.

4. **이벤트 소스로 사용할 항목** 을 선택 하십시오. 목록에서 **작업**을 선택 합니다.

5. 처리할 이벤트 목록에서 **항목 추가**됨 옆의 확인란을 선택 하 고 **마침** 단추를 선택 합니다.

     새 이벤트 수신기 노드가 **Projecttasklisteventreceiver**라는 코드 파일을 사용 하 여 프로젝트에 추가 됩니다.

6. `ItemAdded` **Projecttasklisteventreceiver** 코드 파일의 메서드에 코드를 추가 합니다. 새 작업이 추가 될 때마다 기본 기한 날짜 및 설명이 작업에 추가 됩니다. 기본 기한은 2009 년 7 월 1 일입니다.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>프로젝트 작업 목록 기능 사용자 지정

SharePoint 솔루션을 만들 때 Visual Studio는 기본 프로젝트 항목에 대 한 기능을 자동으로 만듭니다. 기능 디자이너를 사용 하 여 SharePoint 사이트에 대 한 프로젝트 작업 목록 설정을 사용자 지정할 수 있습니다.

1. **솔루션 탐색기**에서 **기능**을 확장 합니다.

2. **Feature1**에 대 한 바로 가기 메뉴를 열고 **뷰 디자이너**를 선택 합니다.

3. **제목** 상자에 **Project 작업 목록 기능**을 입력 합니다.

4. **범위** 목록에서 **웹**을 선택 합니다.

5. **속성** 창에서 **버전** 속성에 대 한 값으로 **1.0.0.0** 을 입력 합니다.

## <a name="customize-the-project-task-list-package"></a>프로젝트 작업 목록 패키지 사용자 지정

SharePoint 프로젝트를 만들 때 Visual Studio는 기본 프로젝트 항목을 포함 하는 기능을 패키지에 자동으로 추가 합니다. 패키지 디자이너를 사용 하 여 SharePoint 사이트에 대 한 프로젝트 작업 목록 설정을 사용자 지정할 수 있습니다.

1. **SolutionExplorer**에서 **패키지**에 대 한 바로 가기 메뉴를 열고 **뷰 디자이너**를 선택 합니다.

2. **이름** 상자에 **Projecttasklistpackage**를 입력 합니다.

3. **웹 서버 다시 설정** 확인란을 선택 합니다.

## <a name="build-and-test-the-project-task-list"></a>프로젝트 작업 목록 빌드 및 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 그러나 작업 목록의 위치로 수동으로 이동 해야 합니다.

1. **F5** 키를 선택 하 여 프로젝트 작업 목록을 빌드하고 배포 합니다.

     SharePoint 사이트가 열립니다.

2. **홈** 탭을 선택 합니다.

3. 왼쪽 세로 막대에서 **프로젝트 작업 목록** 링크를 선택 합니다.

     프로젝트 작업 목록 페이지가 표시 됩니다.

4. **목록 도구** 탭에서 **항목** 탭을 선택 합니다.

5. **항목** 그룹에서 **새 항목** 단추를 선택 합니다.

6. **제목** 텍스트 상자에 **Task1**을 입력 합니다.

7. **저장** 단추를 선택 합니다.

     사이트를 새로 고치면 **Task1** 작업에 7/1/2009의 기한 날짜가 표시 됩니다.

8. **Task1**를 선택 합니다.

     작업의 상세 뷰가 표시 되 고 설명은 "이것이 중요 한 작업입니다."를 표시 합니다.

## <a name="deploy-the-project-task-list"></a>프로젝트 작업 목록 배포

프로젝트 작업 목록을 빌드하고 테스트 한 후 *로컬 시스템* 또는 *원격 시스템*에 배포할 수 있습니다. 로컬 시스템은 솔루션을 개발한 컴퓨터와 동일 하지만 원격 시스템은 다른 컴퓨터입니다.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>로컬 시스템에 프로젝트 작업 목록을 배포 하려면

Visual Studio 메뉴 모음에서 **빌드**  >  **솔루션 배포**를 선택 합니다.

Visual Studio는 IIS 응용 프로그램 풀을 재활용 하 고, 기존 버전의 솔루션을 취소 하 고, 솔루션 패키지 (*.wsp*) 파일을 SharePoint에 복사한 다음 기능을 활성화 합니다. 이제 SharePoint에서 솔루션을 사용할 수 있습니다. 배포 구성 단계에 대 한 자세한 내용은 [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)을 참조 하세요.

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>원격 시스템에 프로젝트 작업 목록을 배포 하려면

1. Visual Studio 메뉴 모음에서 **빌드**  >  **게시**를 선택 합니다.

2. **게시** 대화 상자에서 **파일 시스템에 게시** 옵션 단추를 선택 합니다.

     줄임표 단추 ![줄임표 아이콘](../sharepoint/media/ellipsisicon.gif "가변 매개 변수 아이콘") 을 선택 하 고 다른 위치로 이동 하 여 **게시** 대화 상자에서 대상 위치를 변경할 수 있습니다.

3. **게시** 단추를 선택합니다.

     솔루션에 대 한 *.wsp* 파일이 만들어집니다.

4. *.Wsp* 파일을 원격 SharePoint 시스템에 복사 합니다.

5. PowerShell 명령을 사용 `Add-SPUserSolution` 하 여 원격 SharePoint 설치에 패키지를 설치 합니다. (팜 솔루션의 경우 명령을 사용 `Add-SPSolution` 합니다.)

     예: `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`

6. PowerShell 명령을 사용 `Install-SPUserSolution` 하 여 솔루션을 배포 합니다. (팜 솔루션의 경우 명령을 사용 `Install-SPSolution` 합니다.)

     예: `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`

     원격 배포에 대 한 자세한 내용은 [솔루션 사용](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) 및 [SharePoint 2010의 PowerShell을 사용 하 여 솔루션 추가 및 배포](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx)를 참조 하세요.

## <a name="next-steps"></a>다음 단계

다음 항목에서 SharePoint 솔루션을 사용자 지정 하 고 배포 하는 방법에 대해 자세히 알아볼 수 있습니다.

- [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint Server 2010 용 Windows PowerShell](/powershell/module/sharepoint-server)

## <a name="see-also"></a>추가 정보
[SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
