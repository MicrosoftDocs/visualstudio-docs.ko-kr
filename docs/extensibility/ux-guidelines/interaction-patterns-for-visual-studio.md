---
title: Visual Studio | 상호 작용 패턴 Microsoft Docs
description: Visual Studio 새 기능을 빌드할 때 사용할 수 있는 일반적인 상호 작용 패턴의 라이브러리에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900553"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio의 상호 작용 패턴
## <a name="overview"></a>개요
 일반적으로 디자인 패턴은 유사한 제약 조건 집합의 문제를 해결하기 위해 특정 상황에서 적용할 수 있는 디자인의 핵심입니다. 기능 및 시스템 디자이너는 이러한 디자인 패턴을 시작점으로 사용하여 특정 상황에 맞게 조정할 수 있습니다.

 Visual Studio 새로운 기능을 빌드할 때 고려해야 하는 일반적인 상호 작용 패턴 라이브러리가 있습니다. 디자인 패턴에는 Visual Studio Client(devenv) 및 GitHub Codespaces(이전의 Visual Studio Online)의 두 가지 핵심 컨텍스트가 있습니다. 일부 디자인 문제의 경우 모든 상황에서 잘 작동하는 유비쿼터스 패턴이 있습니다. 그러나 대부분의 경우 솔루션은 브라우저 내에 표시되고 클라이언트 애플리케이션에서 호스트되는 UI에 대해 다를 수 있습니다.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio 클라이언트 패턴 형식

|패턴 유형|설명|예|
|------------------|-----------------|--------------|
|**애플리케이션 수준 패턴**|애플리케이션에 공통적인 상위 수준 패턴, 애플리케이션 컨텍스트 확인 또는 표시 및 그 안에 복합 및 컨트롤 패턴 포함|- 도구 창<br />- 문서 창|
|**복합 패턴**|애플리케이션 패턴에 걸쳐 있을 수 있는 일반적인 패턴 또는 고유 구성의 여러 컨트롤로 구성된 인식된 패턴|- 보기 전환<br />- 목록 작성기<br />- 데이터 표시<br />- 알림<br />- 유효성 검사<br />- 선택 모델|
|**컨트롤 패턴**|낮은 수준의 컨트롤이 작동하는 방식에 대한 세부 정보|- 트리 뷰<br />- 그리드 컨트롤 내에서 편집|

## <a name="application-patterns"></a>애플리케이션 패턴
 상위 수준에서 Visual Studio 인터페이스는 단일 IDE 내에서 여러 창, 대화 상자, 명령 및 도구 모음으로 구성됩니다. Visual Studio 계층 구조는 상황에 맞는 메뉴와 드라이브 메뉴를 결정합니다. IDE 사용자 인터페이스의 주요 통합 지점은 문서 창, 도구 창, 프로젝트, 명령 구조, 텍스트 편집기, 도구 상자, 속성 창 및 도구 > 옵션입니다.

 IDE의 사용자 인터페이스에는 각 주요 통합 지점에 대한 기본 사용 패턴이 있습니다.

- [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [창 상호 작용](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [도구 창](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [문서 편집기 규칙](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [다이얼로그](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [프로젝트](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>일반적인 컨트롤 패턴
 컨트롤 패턴은 주로 개별 컨트롤이 동작하는 방식에 관한 것입니다. 일관성이 가장 중요한 영역 중 하나입니다.

 Visual Studio 가장 일반적인 컨트롤은 데스크톱 Windows 지침을 따라야 합니다. 지침에는 Visual Studio 특정 상호 작용을 통해 일반적인 규칙을 보강해야 하는 영역 또는 정교한 사용자의 요구에 맞게 Visual Studio 조정하기 위해 지침을 완전히 대체해야 하는 영역만 포함됩니다.

- [Visual Studio의 일반 컨트롤 패턴](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [공용 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [단추 및 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>복합 패턴
 사용자가 작업을 수행할 것으로 예상하는 여러 가지 방법이 있습니다. 가능하면 상호 작용 및 시각적 디자인 모두에 이러한 패턴을 사용하도록 기능을 디자인해야 합니다.

 Visual Studio 내에는 여러 복합 패턴이 있지만 일관성과 관련하여 가장 중요한 몇 가지는 다음과 같습니다.

- [Visual Studio의 복합 패턴](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [개체 UI 켜기 및 피킹](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [선택 모델](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [지속성 및 설정 저장](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [터치 입력](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
