---
title: '연습: 사용자 지정 사이트 워크플로 작업 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc7eef8b0924be745de436e06acc36785b1cb99b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016538"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>연습: 사용자 지정 사이트 워크플로 작업 만들기
  이 연습에서는를 사용 하 여 사이트 수준 워크플로에 대 한 사용자 지정 활동을 만드는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 사이트 수준 워크플로는 사이트의 목록 뿐 아니라 전체 사이트에 적용 됩니다. 사용자 지정 활동은 백업 공지 목록을 만든 다음 공지 목록의 내용을 여기에 복사 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사이트 수준 워크플로 만들기

- 사용자 지정 워크플로 작업 만들기

- SharePoint 목록 만들기 및 삭제

- 한 목록에서 다른 목록으로 항목을 복사 합니다.

- 빠른 실행 표시줄에 목록을 표시 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>사이트 워크플로 사용자 지정 활동 프로젝트 만들기
 먼저, 사용자 지정 워크플로 활동을 보유 하 고 테스트할 프로젝트를 만듭니다.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>사이트 워크플로 사용자 지정 활동 프로젝트를 만들려면

1. 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2010 프로젝트** 템플릿을 선택 합니다.

4. **이름** 상자에 **AnnouncementBackup**를 입력 하 고 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 하 여 신뢰 수준 및 기본 사이트를 수락 합니다.

     이 단계에서는 솔루션에 대 한 신뢰 수준을 팜 솔루션으로 설정 합니다 .이 옵션은 워크플로 프로젝트에만 사용할 수 있습니다.

6. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

7. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

8. **템플릿** 창에서 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 다음 **추가** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

9. **디버깅할 워크플로 이름 지정** 페이지에서 기본 이름 (AnnouncementBackup-workflow1.vb)을 적용 합니다. 워크플로 템플릿 유형을 **사이트 워크플로**로 변경 하 고 **다음** 단추를 선택 합니다.

10. **마침** 단추를 선택 하 여 나머지 기본 설정을 적용 합니다.

## <a name="add-a-custom-workflow-activity-class"></a>사용자 지정 워크플로 작업 클래스 추가
 다음으로 프로젝트에 클래스를 추가 하 여 사용자 지정 워크플로 작업에 대 한 코드를 포함 합니다.

#### <a name="to-add-a-custom-workflow-activity-class"></a>사용자 지정 워크플로 활동 클래스를 추가 하려면

1. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가** 를 선택 하 여 **새 항목 추가** 대화 상자를 표시 합니다.

2. **설치 된 템플릿** 트리 보기에서 **코드** 노드를 선택 하 고 프로젝트 항목 템플릿 목록에서 **클래스** 템플릿을 선택 합니다. 기본 이름인 Class1을 사용 합니다. **추가** 단추를 선택합니다.

3. Class1의 모든 코드를 다음으로 바꿉니다.

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. 프로젝트를 저장 한 다음 메뉴 모음에서 빌드 솔루션 **빌드**를 선택  >  **Build Solution**합니다.

     Class1은 **AnnouncementBackup 구성 요소** 탭의 **도구 상자** 에 사용자 지정 작업으로 나타납니다.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>사이트 워크플로에 사용자 지정 작업 추가
 다음으로 사용자 지정 코드를 포함 하는 활동을 워크플로에 추가 합니다.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>사이트 워크플로에 사용자 지정 작업을 추가 하려면

1. 디자인 뷰의 workflow designer에서 Workflow1.vb을 엽니다.

2. 작업 아래에 표시 되도록 Class1을 **도구 상자** 에서 끌어 놓고 `onWorkflowActivated1` , class1에 대 한 바로 가기 메뉴를 열고, **복사**를 선택 하 고, 활동 아래 줄에 대 한 바로 가기 메뉴를 연 `onWorkflowActivated1` 다음 **붙여넣기**를 선택 합니다.

3. 프로젝트를 저장합니다.

## <a name="test-the-site-workflow-custom-activity"></a>사이트 워크플로 사용자 지정 활동 테스트
 그런 다음 프로젝트를 실행 하 고 사이트 워크플로를 시작 합니다. 사용자 지정 작업은 백업 알림 목록을 만들고 현재 공지 목록의 내용을 여기에 복사 합니다. 또한이 코드는 백업 목록이 이미 있는지 여부를 확인 하 여 새로 만듭니다. 백업 목록이 이미 있으면 삭제 됩니다. 또한이 코드는 SharePoint 사이트의 빠른 실행 표시줄에 새 목록에 대 한 링크를 추가 합니다.

#### <a name="to-test-the-site-workflow-custom-activity"></a>사이트 워크플로 사용자 지정 활동을 테스트 하려면

1. **F5** 키를 선택 하 여 프로젝트를 실행 하 고 SharePoint에 배포 합니다.

2. 빠른 실행 모음에서 **목록** 링크를 선택 하 여 SharePoint 사이트에서 사용할 수 있는 모든 목록을 표시 합니다. **알림 이라는 알림을**위한 목록이 하나 뿐입니다.

3. SharePoint 웹 페이지의 맨 위에서 **사이트 워크플로** 링크를 선택 합니다.

4. 새 워크플로 시작 섹션에서 **AnnouncementBackup-workflow1.vb** 링크를 선택 합니다. 그러면 사이트 워크플로가 시작 되 고 사용자 지정 작업에서 코드가 실행 됩니다.

5. 빠른 실행 모음에서 **공지 백업** 링크를 선택 합니다. **공지** 목록에 포함 된 모든 알림이이 새 목록에 복사 되었는지 확인 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
