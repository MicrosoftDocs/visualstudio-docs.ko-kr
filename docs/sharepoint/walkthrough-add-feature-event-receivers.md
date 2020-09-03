---
title: '연습: 기능 이벤트 수신자 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f40358c157ec24557947f36b0c6eadb6d8a2622d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015362"
---
# <a name="walkthrough-add-feature-event-receivers"></a>연습: 기능 이벤트 수신자 추가
  기능 이벤트 수신기는 SharePoint에서 다음 기능 관련 이벤트 중 하나가 발생할 때 실행 되는 메서드입니다.

- 기능이 설치 되었습니다.

- 기능이 활성화 됩니다.

- 기능이 비활성화 됩니다.

- 기능이 제거 됩니다.

  이 연습에서는 SharePoint 프로젝트의 기능에 이벤트 수신기를 추가 하는 방법을 보여 줍니다. 다음 작업을 보여 줍니다.

- 기능 이벤트 수신기를 사용 하 여 빈 프로젝트를 만듭니다.

- **Featuredeactivating** 메서드를 처리 합니다.

- SharePoint 프로젝트 개체 모델을 사용 하 여 공지 목록에 공지를 추가 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>기능 이벤트 수신기 프로젝트 만들기
 먼저 기능 이벤트 수신기를 포함 하는 프로젝트를 만듭니다.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>기능 이벤트 수신기를 사용 하 여 프로젝트를 만들려면

1. 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2010 프로젝트** 템플릿을 선택 합니다.

     이 프로젝트 형식은 프로젝트 템플릿이 없으므로 기능 이벤트 수신기에 사용 합니다.

4. **이름** 상자에 **featureevttest**를 입력 한 다음 **확인** 단추를 선택 하 여 **SharePoint 사용자 지정 마법사**를 표시 합니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 새 사용자 지정 필드 항목을 추가할 SharePoint 서버 사이트의 URL을 입력 하거나 기본 위치 (http:///)를 사용 합니다 \<*system name*> .

6. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

     샌드박스 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **마침** 단추를 선택 하 고 이름이 Feature1 인 기능이 **기능** 노드 아래에 표시 되는지 확인 합니다.

## <a name="add-an-event-receiver-to-the-feature"></a>기능에 이벤트 수신기 추가
 그런 다음 기능에 이벤트 수신기를 추가 하 고 기능이 비활성화 될 때 실행 되는 코드를 추가 합니다.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>기능에 이벤트 수신기를 추가 하려면

1. 기능 노드에 대 한 바로 가기 메뉴를 열고 **기능 추가** 를 선택 하 여 기능을 만듭니다.

2. **기능** 노드 아래에서 **Feature1**에 대 한 바로 가기 메뉴를 열고 **이벤트 수신기 추가** 를 선택 하 여 기능에 이벤트 수신기를 추가 합니다.

     그러면 Feature1에 코드 파일이 추가 됩니다. 이 경우 프로젝트의 개발 언어에 따라 *Feature1.EventReceiver.cs* 또는 *Feature1*로 이름이 지정 됩니다.

3. 에서 프로젝트를 작성 한 경우에는 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 이벤트 수신기의 맨 위에 다음 코드를 추가 합니다 (아직 없는 경우).

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. 이벤트 수신기 클래스에는 이벤트로 작동 하는 주석 처리 된 여러 메서드가 포함 되어 있습니다. **Featuredeactivating** 메서드를 다음으로 바꿉니다.

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>기능 이벤트 수신기 테스트
 다음으로 기능을 비활성화 하 여 **featuredeactivating** 메서드가 SharePoint 공지 목록에 알림을 출력 하는지 테스트 합니다.

#### <a name="to-test-the-feature-event-receiver"></a>기능 이벤트 수신기를 테스트 하려면

1. 프로젝트의 **활성 배포 구성** 속성 값을 **활성화 안 함**으로 설정 합니다.

     이 속성을 설정 하면 SharePoint에서 기능을 활성화할 수 없으며 기능 이벤트 수신기를 디버그할 수 있습니다. 자세한 내용은 [SharePoint 솔루션 디버그](../sharepoint/debugging-sharepoint-solutions.md)를 참조 하세요.

2. **F5** 키를 선택 하 여 프로젝트를 실행 하 고 SharePoint에 배포 합니다.

3. SharePoint 웹 페이지 위쪽에서 **사이트 작업** 메뉴를 연 다음 **사이트 설정**을 선택 합니다.

4. 사이트 **설정** 페이지의 **사이트 작업** 섹션에서 **사이트 기능 관리** 링크를 선택 합니다.

5. **기능** 페이지에서 **Featureevttest Feature1** 기능 옆에 있는 **활성화** 단추를 선택 합니다.

6. **기능** 페이지에서 **Featureevttest Feature1** 기능 옆의 **비활성화** 단추를 선택 하 고 **이 기능 비활성화** 확인 링크를 선택 하 여 기능을 비활성화 합니다.

7. **홈** 단추를 선택 합니다.

     기능이 비활성화 된 후 **공지 목록에 알림이 표시** 됩니다.

## <a name="see-also"></a>추가 정보

- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)