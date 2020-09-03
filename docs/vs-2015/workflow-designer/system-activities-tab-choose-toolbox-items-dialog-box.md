---
title: 도구 상자 항목 선택 대화 상자, 시스템 작업 탭 Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655178"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities 탭, 도구 상자 항목 선택 대화 상자
**도구 상자 항목 선택** 대화 상자의이 탭에는 [!INCLUDE[wf](../includes/wf-md.md)] 사용할 수 있는 활동, 템플릿 및 항목의 목록이 표시 됩니다. 이 목록을 표시 하려면 **도구** 메뉴에서 도구 **상자 항목 선택** 을 선택 하거나 도구 **상자** 를 마우스 오른쪽 단추로 클릭 하 고 **항목 선택** 을 선택 하 여 **도구 상자 항목 선택** 대화 상자를 표시 한 다음, 해당 **시스템 작업** 탭을 선택 합니다. 기본적으로이 목록에는 System.web, System.servicemodel 및 System.servicemodel 어셈블리의 워크플로 작업이 포함 되어 있습니다. 그러나 **도구 상자** 에 표시 되는 시스템 제공 활동 및 다른 어셈블리를 통해 추가 된 활동만 기본적으로 선택 됩니다. 대화 상자에서 **확인을** 클릭 하면 최근에 추가한 활동이 자동으로 선택 되 고 **도구 상자** 에 표시 됩니다. 또한 이러한 항목은 **도구 상자** 에서 활동/항목/템플릿이 있는 네임 스페이스에 해당 하는 새 범주 아래에 나타납니다.

> [!WARNING]
> 워크플로 활동이 없는 어셈블리를 추가하려고 하면 해당 어셈블리에 활동이 없음을 알리는 오류 대화 상자가 표시됩니다.

 이 대화 상자는 프로젝트를 독립적으로 수행 하므로 **System. 작업** 탭은 독립 실행형 XAML 또는 비 워크플로 프로젝트 형식으로 계속 표시 됩니다.

 필터링은 각 탭에서 수행 됩니다. 즉, **.Net 구성 요소** 탭을 통해 워크플로 활동을 추가할 수 없습니다. 이러한 **작업은 system.web** 탭 자체를 통해 추가 해야 합니다.

 이 대화 상자 탭에서 **도구 상자** 에 표시 하지 않을 항목을 선택 취소 하거나, 도구 **상자** 에서 상황에 맞는 메뉴 **옵션을 사용** 하 고 어셈블리를 참조 취소 하 여 **도구 상자**에서 해당 항목을 제거 하지 않을 수도 있습니다.

 활동을 디자이너로 끌어 놓아 인스턴스화하면 해당 항목이 포함된 어셈블리가 참조 어셈블리 목록에 자동으로 추가됩니다. 어셈블리 C를 참조하는 활동인 경우 참조 어셈블리 목록에 C를 추가하지 않습니다. 어셈블리 C는 GAC 또는 활동 B와 동일한 디렉터리에 있어야 합니다. 독립 실행형 경우 어셈블리는 GAC 또는 VS의 프로브 경로에 있어야 합니다. 그래야만 Workflow Designer 화면에 활동을 끌어 놓을 수 있습니다.

 **도구 상자** 설정은 기본적으로 사용자 옵션으로 저장 되므로 다음에 **도구 상자**를 열면 사용자 지정 된 워크플로 작업 목록이 표시 됩니다. 이에 대 한 한 가지 부작용은 **도구 상자 항목 선택** 대화 상자를 통해 **도구 상자** 에 특정 도메인 항목을 추가한 경우 워크플로 콘솔 응용 프로그램 에서도 작업할 때 계속 해 서 해당 항목을 계속 표시 한다는 것입니다. 표시 하지 않으려면 상황에 맞는 메뉴를 사용 하 여 삭제 하거나 앞에서 설명한 대로 **도구 상자 항목 선택** 대화 상자에서 선택을 취소 합니다.

 이 대화 상자의 열에는 다음과 같은 정보가 포함되어 있습니다.

 이름 현재 로컬 컴퓨터에 등록 된 워크플로 활동의 이름을 나열 합니다.

 네임 스페이스 작업 구조를 정의 하는 .NET Framework 클래스 라이브러리 네임 스페이스의 계층 구조를 표시 합니다.

 어셈블리 이름 활동을 포함 하는 .NET Framework 어셈블리의 이름과 버전을 표시 합니다.

 디렉터리 워크플로 작업을 포함 하는 .NET Framework 어셈블리의 위치를 표시 합니다. 모든 어셈블리의 기본 위치는 전역 어셈블리 캐시(GAC)입니다.

 나열된 구성 요소를 정렬하려면 열 머리글을 선택합니다.