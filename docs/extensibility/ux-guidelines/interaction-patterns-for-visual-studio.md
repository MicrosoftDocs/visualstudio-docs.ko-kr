---
title: 비주얼 스튜디오를 위한 상호 작용 패턴 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698370"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio의 상호 작용 패턴
## <a name="overview"></a>개요
 일반적으로 디자인 패턴은 유사한 제약 조건 집합의 문제를 해결하기 위해 특정 상황에서 적용할 수 있는 설계의 핵심입니다. 기능 및 시스템 설계자는 이러한 디자인 패턴을 시작점으로 사용하여 특정 상황에 맞게 조정할 수 있습니다.

 Visual Studio에는 새 기능을 빌드할 때 고려해야 할 일반적인 상호 작용 패턴 라이브러리가 있습니다. 디자인 패턴에는 비주얼 스튜디오 클라이언트(devenv)와 비주얼 스튜디오 온라인의 두 가지 핵심 컨텍스트가 있습니다. 일부 디자인 문제의 경우 모든 상황에서 잘 작동하는 유비쿼터스 패턴이 있습니다. 그러나 대부분의 경우 브라우저 내에 표시되는 UI와 클라이언트 응용 프로그램에서 호스팅되는 UI에 대해 솔루션이 다를 수 있습니다.

### <a name="visual-studio-client-pattern-types"></a>비주얼 스튜디오 클라이언트 패턴 유형

|패턴 타입|설명|예제|
|------------------|-----------------|--------------|
|**응용 프로그램 수준 패턴**|응용 프로그램에 공통적인 상위 수준 패턴, 응용 프로그램 컨텍스트 결정 또는 표시, 응용 프로그램 내 복합 및 제어 패턴 포함|- 공구 창<br />- 문서 창|
|**복합 패턴**|응용 프로그램 패턴에 걸쳐 있을 수 있는 일반적인 패턴 또는 고유한 구성에서 여러 컨트롤로 구성된 인식된 패턴|- 보기 전환<br />- 목록 빌더<br />- 데이터 표시<br />- 알림<br />- 유효성 검사<br />- 선택 모델|
|**패턴 제어**|하위 수준 컨트롤이 어떻게 행동할지에 대한 세부 사항|- 나무 보기<br />- 그리드 컨트롤 내에서 편집|

## <a name="application-patterns"></a>애플리케이션 패턴
 상위 수준에서 Visual Studio 인터페이스는 단일 IDE 내의 여러 창, 대화 상자, 명령 및 도구 모음으로 구성됩니다. Visual Studio 계층 구조는 컨텍스트를 결정하고 메뉴를 구동합니다. IDE의 사용자 인터페이스의 주요 통합 지점은 문서 창, 도구 창, 프로젝트, 명령 구조, 텍스트 편집기, 도구 상자, 속성 창 및 도구 > 옵션입니다.

 IDE의 사용자 인터페이스에 있는 각 주요 통합 지점에 대한 기본 사용 패턴이 있습니다.

- [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [창 상호 작용](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [도구 창](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [문서 편집기 규칙](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [프로젝트](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>일반적인 제어 패턴
 컨트롤 패턴은 주로 개별 컨트롤이 어떻게 행동할지에 관한 것입니다. 일관성이 가장 중요한 영역 중 하나입니다.

 Visual Studio의 가장 일반적인 컨트롤은 데스크톱 Windows 지침을 따라야 합니다. 가이드라인에는 Visual Studio 관련 상호 작용을 통해 공통 규칙을 보강해야 하는 영역 또는 정교한 사용자의 요구에 맞게 Visual Studio를 맞춤화하기 위해 지침을 완전히 대체하는 영역만 포함됩니다.

- [Visual Studio의 일반 컨트롤 패턴](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [공용 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [버튼 및 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>복합 패턴
 사용자가 작업을 수행할 것으로 예상하는 방법에는 여러 가지가 있습니다. 가능하면 상호 작용 및 시각적 디자인모두에 이러한 패턴을 사용하도록 피처를 설계해야 합니다.

 Visual Studio에는 많은 복합 패턴이 있지만 일관성과 관련하여 가장 중요한 것은 다음과 같습니다.

- [Visual Studio의 복합 패턴](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [개체 내 UI 및 엿보기](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [선택 모델](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [지속성 및 저장 설정](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [터치 입력](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
