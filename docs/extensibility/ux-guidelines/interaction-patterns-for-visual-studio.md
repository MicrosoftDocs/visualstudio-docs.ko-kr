---
title: Visual Studio의 상호 작용 패턴 | Microsoft Docs
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cbfeef3352e4abd03e12cc6b228cea8a8c124a6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184408"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio의 상호 작용 패턴
## <a name="overview"></a>개요
 일반적으로 디자인 패턴은 비슷한 제약 조건 집합의 문제를 해결 하기 위해 특정 상황에서 적용할 수 있는 디자인의 핵심입니다. 기능 및 시스템 디자이너는 이러한 디자인 패턴을 시작 점으로 사용 하 여 특정 상황에 맞게 조정할 수 있습니다.

 Visual Studio에는 새로운 기능을 빌드할 때 고려해 야 하는 일반적인 상호 작용 패턴의 라이브러리가 있습니다. 디자인 패턴에는 두 가지 핵심 컨텍스트 (devenv)와 visual studio Codespaces (이전의 Visual Studio Online)가 있습니다. 일부 디자인 문제에는 모든 상황에서 잘 작동 하는 다양 한 패턴이 있습니다. 그러나 대부분의 경우 솔루션은 브라우저에 표시 되 고 클라이언트 응용 프로그램에서 호스트 되는 UI에 대해 다를 수 있습니다.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio 클라이언트 패턴 형식

|패턴 유형|설명|예제|
|------------------|-----------------|--------------|
|**응용 프로그램 수준 패턴**|응용 프로그램에 공통적으로 적용 되는 응용 프로그램 컨텍스트를 결정 또는 표시 하 고 그 안에 복합 및 컨트롤 패턴을 포함 하는 상위 수준 패턴|-도구 창<br />-문서 창|
|**복합 패턴**|응용 프로그램 패턴 전체에 걸쳐 있을 수 있는 일반적인 패턴 또는 개별 구성의 여러 컨트롤로 구성 된 인식 된 패턴|-전환 보기<br />-목록 작성기<br />-데이터 표시<br />-알림<br />-유효성 검사<br />-선택 모델|
|**컨트롤 패턴**|하위 수준 컨트롤이 동작할 것으로 예상 되는 방법에 대 한 세부 정보|-트리 보기<br />-Grid 컨트롤 내에서 편집|

## <a name="application-patterns"></a>애플리케이션 패턴
 상위 수준에서 Visual Studio 인터페이스는 단일 IDE 내에서 여러 창, 대화 상자, 명령 및 도구 모음으로 구성 됩니다. Visual Studio 계층 구조는 컨텍스트 및 드라이브 메뉴를 결정 합니다. IDE의 사용자 인터페이스에서 핵심 통합 지점은 문서 창, 도구 창, 프로젝트, 명령 구조, 텍스트 편집기, 도구 상자, 속성 창 및 도구 > 옵션입니다.

 IDE의 사용자 인터페이스에는 각 키 통합 지점의 기본 사용 패턴이 있습니다.

- [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [창 상호 작용](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [도구 창](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [문서 편집기 규칙](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [다이얼로그](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [프로젝트](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>공용 컨트롤 패턴
 컨트롤 패턴은 주로 개별 컨트롤이 동작 하는 방법에 대 한 것입니다. 이는 일관성이 가장 중요 한 한 영역입니다.

 Visual Studio의 가장 일반적인 컨트롤은 바탕 화면 Windows 지침을 따라야 합니다. Microsoft의 지침에는 Visual Studio와 관련 된 상호 작용으로 일반적인 규칙을 강화 해야 하는 영역이 포함 되어 있거나, 복잡 한 사용자의 요구에 맞게 Visual Studio를 조정 하기 위해 지침을 완전히 대체 하는 장소가 포함 되어 있습니다.

- [Visual Studio의 일반 컨트롤 패턴](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [공용 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [단추 및 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>복합 패턴
 사용자가 작업을 완료 하는 데는 여러 가지 방법이 있습니다. 가능 하면 이러한 패턴을 상호 작용 및 시각적 디자인에 모두 사용 하도록 기능을 디자인 해야 합니다.

 Visual Studio에는 다양 한 복합 패턴이 있지만 일관성과 관련 하 여 가장 중요 한 것은 다음과 같습니다.

- [Visual Studio의 복합 패턴](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [개체 내 UI 및 보기](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [선택 모델](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [유지 및 설정 저장](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [터치식 입력](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
