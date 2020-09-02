---
title: 모델 요소 및 작업 항목 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657625"
---
# <a name="link-model-elements-and-work-items"></a>모델 요소 및 작업 항목 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 모델 요소와 Team Foundation Server 또는 Visual Studio Team Services의 작업 요소를 연결하여 작업, 테스트 사례, 버그, 요구 사항, 문제, 모델과 관련된 기타 작업을 추적합니다. 작업 항목을 모델 요소에 연결하려면 문서를 링크된 작업 항목에 첨부합니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!NOTE]
> 링크를 만들고 열려면 Team Explorer를 사용해야 합니다. 다른 사용자가 링크된 다이어그램을 열 수 있도록 모델링 프로젝트와 다이어그램이 버전 제어에 체크 인되었는지 확인해야 합니다.

 예를 들어, 다음을 링크할 수 있습니다.

- 사용자 스토리 작업 항목 및 스토리를 작업 시퀀스로 구현하는 방법을 보여 주는 동작 다이어그램

- 사용자 사례 다이어그램에 대한 사용 사례 및 사용자 사례가 올바르게 구현되었는지 확인하기 위한 테스트 사례 작업 항목

- UML 클래스 다이어그램의 클래스의 특성 및 특성 구현의 오류를 보여주기 위한 버그 작업 항목

- 구성 요소 다이어그램의 구성 요소 및 구성 요소 개발을 추적하기 위한 작업(Task) 작업 항목 이러한 작업(Task)은 일반적으로 더 작은 작업으로 구분됩니다.

  다음 항목과 같이 모델링 다이어그램 또는 UML 모델 탐색기에서 선택할 수 있는 요소에 작업 항목을 링크할 수 있습니다.

- UML 클래스, 수명선, 사용 사례, 하위 시스템, 동작, 개체 노드, 구성 요소, 인터페이스 등 UML 모델의 모든 요소

- 연결, 일반화, 종속성, 흐름, 메시지 등 UML 모델의 모든 관계

- 클래스의 특성과 작업, 수명선의 실행 발생, 동작의 입력/출력 핀, 구성 요소의 부분과 포트 등 요소의 부분

- 레이어 및 레이어 종속성

- 주석 및 주석 링크

- 다이어그램. 다이어그램을 선택하려면 다이어그램의 빈 부분을 선택합니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

- [팀 프로젝트에 연결합니다.](#ConnectTFS)

- [새 작업 항목에 모델 요소 링크](#LinkNew)

- [기존 작업 항목에 모델 요소 링크](#LinkExisting)

- [모델 요소에 링크된 작업 항목 보기](#OpenWorkItem)

- [작업 항목에 링크된 모델 요소 보기](#ViewLinkedModels)

- [모델 요소와 작업 항목 사이의 링크 삭제](#RemoveLinks)

- [문제 해결](#Troubleshooting)

## <a name="connect-to-a-team-project"></a><a name="ConnectTFS"></a> 팀 프로젝트에 연결
 링크를 만들거나 보거나 제거하려면 먼저 팀 프로젝트에 연결해야 합니다.

1. **팀** 메뉴에서 **연결 관리** 를 선택하여 Team Explorer 창을 표시합니다.

2. 올바른 프로젝트가 나타나지 않으면 Team Explorer에서 **연결 관리** , **팀 프로젝트에 연결**을 차례로 선택합니다. 그런 다음 필요에 따라 올바른 프로젝트 또는 서버를 선택합니다.

3. **팀 탐색기**에서 작업 항목을 만들거나 연결하거나 볼 프로젝트를 선택합니다.

## <a name="link-a-model-element-to-a-new-work-item"></a><a name="LinkNew"></a> 새 작업 항목에 모델 요소 연결

1. 사용하려는 TFS 인스턴스에 연결되어 있는지 확인합니다.

2. 모델링 다이어그램 또는 **UML 모델 탐색기**에서 모델 요소에 대한 바로 가기 메뉴를 엽니다.

3. **작업 항목 만들기** 와 만들려는 작업 항목의 종류를 선택합니다.

4. 작업 항목의 필드를 입력합니다. **작업 항목 저장**을 선택합니다.

     모델 요소가 새 작업 항목에 링크됩니다. 모델 요소 위 또는 주변에 아이콘이 나타납니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

## <a name="link-a-model-element-to-an-existing-work-item"></a><a name="LinkExisting"></a> 기존 작업 항목에 모델 요소 연결
 모델 요소를 작업 항목에 링크할 경우 작업 항목이 아닌 모델 요소에서 시작하세요.

1. 사용하려는 TFS 인스턴스에 연결되어 있는지 확인합니다.

2. 모델링 다이어그램 또는 **UML 모델 탐색기**에서 모델 요소에 대한 바로 가기 메뉴를 엽니다. **작업 항목에 연결**을 선택합니다. 그런 다음 **프로젝트** 필드에서 프로젝트를 선택합니다.

3. 다음 단계 중 하나를 따라 모델 요소에 링크할 작업 항목을 하나 이상 선택합니다.

    - **저장된 쿼리**에서 쿼리를 선택합니다.

    - **ID**에서 하나 이상의 작업 항목에 대한 ID를 공백으로 구분하여 입력합니다.

    - **제목에 다음 포함**에 단어나 구를 입력합니다.

4. **찾기**를 선택합니다.

5. 작업 항목 목록에서 링크할 작업 항목을 하나 이상 선택 합니다.

     선택을 마치면 모델 요소의 **작업 항목** 속성에 표시되는 값이 이전보다 커집니다. 모델 요소 위 또는 주변에도 아이콘이 나타납니다.

> [!WARNING]
> 작업 항목을 만들거나 작업 항목에 연결하려면 TFS SCC(소스 코드 제어)에 이미 연결되어 있어야 합니다. 다른 TFS SCC에 대한 연결을 열려고 하면 Visual Studio가 자동으로 현재 솔루션을 닫습니다. 작업 항목을 만들거나 작업 항목에 연결하기 전에 적절한 SCC에 이미 연결되어 있는지 확인합니다. Visual Studio의 이후 릴리스에서는 SCC에 연결되어 있지 않으면 메뉴 명령을 사용할 수 없습니다.

## <a name="view-work-items-linked-to-a-model-element"></a><a name="OpenWorkItem"></a> 모델 요소에 연결 된 작업 항목 보기

1. **Team Explorer**에서 작업 항목이 모델 요소에 연결된 팀 프로젝트에 연결되어 있는지 확인합니다.

2. 모델링 다이어그램 또는 **UML 모델 탐색기**에서 모델 요소에 대한 바로 가기 메뉴를 엽니다. 링크된 작업 항목 목록을 보려면 **작업 항목 보기** 를 선택합니다.

    > [!NOTE]
    > 현재 연결된 서버의 작업 항목만 표시됩니다. 아무 작업 항목이 표시되지 않을 경우 **팀 탐색기**에서 올바른 서버에 연결되어 있는지 확인합니다.

## <a name="view-model-elements-linked-to-a-work-item"></a><a name="ViewLinkedModels"></a> 작업 항목에 연결 된 모델 요소 보기
 Visual Studio Team Services 및 Team Foundation Server 2012 이상의 작업 항목에 연결된 모델링 다이어그램 및 요소를 볼 수 있습니다. 예를 들어, 작업 항목은 구현될 새 클래스의 디자인을 보여주는 클래스 모델에 링크할 수 있습니다.

1. **Team Explorer**에서 모델 요소가 작업 항목에 연결된 팀 프로젝트에 연결되어 있는지 확인합니다.

    > [!NOTE]
    > 링크된 모델 요소를 보려면 Team Web Access가 아닌 팀 탐색기를 사용해야 합니다. 작업 영역이 모델링 다이어그램 또는 요소가 포함된 모델링 프로젝트에 매핑되었는지 확인합니다. 작업 영역이 없으면 만들어야 합니다. [문제 해결](#Troubleshooting) 및 [작업 영역 만들기 및 사용](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a)을 참조하세요.

2. 작업 영역을 열고 **링크**를 선택합니다. **모델 링크**에서 링크된 모델 요소에 대한 바로 가기 메뉴를 엽니다. **링크된 항목 열기**를 선택합니다.

     ![작업 항목에서 연결된 모델 요소 열기](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="delete-links-between-model-elements-and-work-items"></a><a name="RemoveLinks"></a> 모델 요소와 작업 항목 간의 링크 삭제
 모델 요소에서 시작하여 링크된 작업 항목을 제거합니다. 그러면 작업 항목의 해당 모델 요소에 대한 상호 링크가 올바르게 제거됩니다. 그렇지 않을 경우, 작업 항목으로 시작하면 모델 요소에서 작업 항목에 대한 상호 링크가 삭제되지 않습니다.

1. 모델링 다이어그램 또는 **UML 모델 탐색기**에서 모델 요소에 대한 바로 가기 메뉴를 엽니다.

2. **작업 항목 제거**를 선택합니다.

     \- 또는 -

    1. **속성**을 선택한 다음 링크된 작업 항목 수가 나타난 **작업 항목** 을 선택합니다.

    2. **작업 항목** 속성에서 줄임표 단추 **[…]** 를 선택합니다.

        > [!NOTE]
        > 현재 서버의 작업 항목만 표시됩니다. 목록이 비어 있는데 작업 항목의 수가 0이 아니면 **팀 탐색기**에서 올바른 서버에 연결되어 있는지 확인하세요.

3. **작업 항목 링크 제거**에서 선택된 항목 중 링크를 해제할 항목을 선택 취소합니다. **확인**을 선택합니다.

## <a name="troubleshooting"></a><a name="Troubleshooting"></a> 문제 해결

|**문제점**|**가능한 원인**|**해결 방법**|
|---------------|------------------------|--------------------|
|링크를 해제할 모델 요소를 찾을 수 없습니다.|해당 요소가 [!INCLUDE[esprscc](../includes/esprscc-md.md)]에 있는 모델링 프로젝트의 다이어그램에 있을 수 있습니다. 다이어그램에 매핑되는 작업 영역이 없을 수 있습니다.|작업 영역을 모델링 프로젝트와 다이어그램에 매핑합니다. 작업 영역이 없으면 만들어야 합니다.<br /><br /> 이 문제에 대해 나타나는 오류 메시지에는 작업 영역을 매핑하는 데 사용할 수 있는 경로가 포함됩니다.<br /><br /> [작업 영역 만들기 및 사용](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a)을 참조하세요.|
|링크된 모델 요소를 찾을 수 없습니다.|연결된 요소가 이동되거나 이름이 바뀌거나 삭제된 다이어그램에 있을 수 있습니다.|1. 작업 항목에서 모델 요소에 대 한 링크를 삭제 합니다.<br />2. 작업 항목에서 모델 요소로 새 링크를 만듭니다.|
|작업 항목에 있어야 할 링크된 모델 요소가 없습니다.|작업 항목에는 작업 항목에서 링크를 만든 경우에만 링크된 계층 요소가 표시됩니다. 팀에서 [!INCLUDE[esprscc](../includes/esprscc-md.md)]를 사용하지 않는 경우 다이어그램의 로컬 경로가 링크를 만드는 데 사용됩니다. 모델링 프로젝트와 해당 다이어그램이 [!INCLUDE[esprscc](../includes/esprscc-md.md)]에 있으면 프로젝트에 액세스할 수 있는 모든 팀 멤버가 작업 항목에서 연결된 요소를 볼 수 있습니다.|작업 항목을 새로 고쳐 보세요.|
|작업 항목에서 모델 요소에 대한 링크를 삭제해도 작업 항목에 대한 모델 요소의 링크가 삭제되지 않습니다.||모델 요소에서 시작하는 작업 항목에 대한 링크를 삭제하세요.|

## <a name="see-also"></a>관련 항목
 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md) [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)
