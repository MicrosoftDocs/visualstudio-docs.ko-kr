---
title: Visual Studio 용 UX Essentials | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698338"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio용 UX Essentials

## <a name="best-practices"></a>모범 사례

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio 환경에서 일관 되 게 유지 합니다.

- 셸 내의 기존 [상호 작용 패턴](interaction-patterns-for-visual-studio.md) 을 따릅니다.

- 셸의 시각적 언어 및 [craftsmanship 요구 사항과](evaluation-tools-for-visual-studio.md)일치 하도록 기능을 디자인 합니다.

- 공유 명령 및 컨트롤이 있는 경우이를 사용 합니다.

- Visual Studio 계층 구조와 컨텍스트를 설정 하 고 UI를 구동 하는 방법을 이해 합니다.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. 글꼴 및 색에 대해 환경 서비스를 사용 합니다.

- UI는 옵션 대화 상자의 글꼴 및 색 페이지에서 사용자 지정을 위해 노출 되지 않는 한 현재 [환경 글꼴](fonts-and-formatting-for-visual-studio.md) 설정을 준수 해야 합니다.

- UI 요소는 공유 환경 토큰 또는 기능 관련 토큰을 사용 하 여 [Vscolor 서비스](colors-and-styling-for-visual-studio.md)를 사용 해야 합니다.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. 모든 이미지를 새 VS 스타일과 일치 하 게 만듭니다.

- 아이콘, 문자 모양 및 기타 그래픽에 대 한 Visual Studio 디자인 원칙을 따릅니다.

- 그래픽 요소에 텍스트를 넣지 않습니다.

### <a name="4-design-from-a-user-centric-perspective"></a>4. 사용자 중심 관점에서 설계 합니다.

- 내 개별 기능 전에 작업 흐름을 만듭니다.

- 사용자에 게 친숙 하 고 사용자의 사양에 따라 해당 지식을 명시적으로 만듭니다.

- UI를 검토할 때 세부 정보 뿐만 아니라 전체 환경을 평가 합니다.

- 로캘 또는 언어에 관계 없이 기능 및 매력적인 상태로 유지 되도록 UI를 디자인 합니다.

## <a name="screen-resolution"></a>화면 해상도

### <a name="minimum-resolution"></a>최소 해상도

- Visual Studio 2015에 대 한 최소 해상도는 **1280x720**입니다. 즉, 최적의 사용자 환경이 아닐 수 있지만이 해상도에서 Visual *Studio를 사용할 수 있습니다* . 1280x720 보다 낮은 해상도에서 모든 측면을 사용할 수 있는 것은 아닙니다.

- Visual Studio에 대 한 대상 확인은 **1366x768**입니다. 이것은 *좋은* 사용자 환경을 보장 하는 가장 낮은 해상도입니다.

- 초기 대화 상자 높이는 **700 픽셀 보다 작아야**하므로 96 DPI에서 IDE 프레임의 최소 해상도에 맞게 조정 됩니다.

### <a name="high-density-displays"></a>고밀도 디스플레이
 Visual Studio의 UI는 Windows에서 지원 되는 모든 DPI 배율 요소 (150%, 200% 및 250%)에서 잘 작동 해야 합니다.

## <a name="anti-patterns"></a>패턴 방지
 Visual Studio에는 지침 및 모범 사례를 따르는 UI의 많은 예가 포함 되어 있습니다. 일관성을 유지 하기 위해 개발자는 종종 개발자가 작성 하는 것과 유사한 제품 UI 디자인 패턴을 제공 합니다. 이는 사용자 상호 작용 및 시각적 디자인의 일관성을 유지 하는 데 도움이 되는 좋은 방법 이지만 일정 제약 조건 또는 결함 우선 순위에 따른 지침을 충족 하지 않는 몇 가지 세부 정보를 제공 하는 경우도 있습니다. 이러한 경우에는 Visual Studio 환경 내에서 부적절 하거나 일관적이 지 않은 UI를 수가 증가 때문에 팀이 이러한 "앤티앨리어싱 패턴" 중 하나를 복사 하지 않도록 합니다.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>기본적으로 오류 상태에 표시 된 필수 필드/설정

#### <a name="feature-team-goals"></a>기능 팀 목표

- 구성 해야 하는 요소를 추가 했는지 사용자에 게 경고 합니다.

- 입력 해야 하는 영역에 사용자의 주의를 그립니다.

#### <a name="anti-pattern-solution"></a>패턴 방지 솔루션
 사용자가 작업을 시작 하 고 작업을 완료 하기 전에 즉시 구성 해야 하는 영역 옆에 중요 한 중지 아이콘을 놓습니다.

#### <a name="example-manifest-designer-declarations"></a>예: 매니페스트 디자이너 선언
 선언을 목록에 즉시 추가 하면 사용자가 필요한 속성을 설정 하기 전까지 계속 해 서 오류 상태가 됩니다.

 이 경우 경고에 사용 되는 아이콘에 "" 아이콘이 포함 되어 있기 때문에 추가 문제가 있습니다 &times; . 따라서 해당 아이콘 옆에는 일반적인 제거 아이콘을 사용할 수 없습니다. 결과적으로 UI는 제거 단추인 clunky 컨트롤을 사용 합니다.

 ![UI를 오류 상태에 배치 하는 것은 기본적으로 Visual Studio 앤티 pattern입니다.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-패턴")<br />UI를 오류 상태에 배치 하는 것은 기본적으로 Visual Studio 앤티 pattern입니다.

#### <a name="alternatives"></a>대안

이 문제에 대 한 더 나은 해결 방법은 다음과 같습니다.

- 사용자가 경고 없이 선언을 추가한 다음 즉시 이동 하 여 항목의 속성을 설정할 수 있습니다.

- 항목에서 포커스를 이동할 때 (예: 목록에 다른 선언을 추가 하거나 디자이너 내에서 탭을 변경 하려는 경우) 경고 아이콘 (금색 삼각형)을 추가 합니다.

- 선언에 대 한 속성을 설정 하기 전에 사용자가 탭을 변경 하려고 하면 경고가 해결 될 때까지 응용 프로그램이 빌드되지 않는다는 것을 설명 하는 대화 상자를 표시 합니다. 사용자가 대화 상자를 해제 하 고 탭을 변경 하는 경우 적절 한 아이콘 (위험 또는 경고)이 선언 탭에 추가 됩니다.

### <a name="multiple-clicks-to-dismiss-ui"></a>UI를 해제 하려면 여러 번 클릭

#### <a name="feature-team-goals"></a>기능 팀 목표
 사용자가 설명 텍스트를 먼저 보지 않고도 UI를 해제할 수 있습니다.

#### <a name="anti-pattern"></a>앤티 패턴
 VS UI 내의 다양 한 위치에 비디오 링크를 삽입 하는 팀은 &times; UX에 지정 된 "" 닫기 단추 및 도구 설명 설명의 일반적인 패턴에 대해 결정 했으며 대신 드롭다운 및 "다시 표시 안 함" 링크를 구현 했습니다.

#### <a name="example-video-links-in-team-explorer"></a>예: 팀 탐색기 비디오 링크
UI를 해제 하기 전에 사용자가 설명 텍스트를 읽을 수 있도록 하는 것은 Visual Studio 내의 앤티 패턴입니다. 올바르게 설계 되 면 비디오 링크에는 가리키기에 대 한 추가 정보가 포함 된 도구 설명이 표시 되 고 ""를 클릭 하면 추가 &times; 상호 작용 없이 메시지를 해제 해야 합니다.

 ![설명 텍스트 앤티&#45;패턴이 잘못 &#45;.](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />잘못 된 비디오 링크 패턴

간단한 닫기 단추 (한 번 클릭) 대신 사용자가 두 번의 클릭을 사용 하 여 비디오 링크가 표시 되는 모든 곳에서 UI를 해제 하기만 하면 됩니다.

이러한 상황에 적합 한 디자인은 Internet Explorer, Office 및 Visual Studio에 공통적인 패턴을 따르는 것입니다. 마우스로 가리키면 사용자가 도구 설명 설명을 볼 수 있고 한 번 클릭 하면 UI가 숨겨집니다.

 ![설명 텍스트 앤티&#45;패턴 &#45; 올바릅니다.](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-패턴을 수정 합니다.")<br />올바른 비디오 링크 패턴

### <a name="using-command-bars-for-settings"></a>설정에 명령 모음 사용

**그림은** 이 앤티 패턴을 나타냅니다. 명령 단추 아래에 설정을 추가 하는 명령에만 적용 됩니다. 이 스케치에는 선택한 설정을 적용 하는 디버깅 시작 (예: 브라우저에서 보기, 디버깅 하지 않고 시작 및 한 단계씩 코드 실행) 외에도 명령이 있습니다.

![그림 A: 명령 모음 앤티 pattern](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-FigureA")<br />그림 A: 명령 모음 앤티 pattern

**그림 B**에 표시 된 것 처럼 약간 더 나은 방법으로 도구 모음에이 유형의 설정을 저장 하 고 있습니다. 분할 단추는 공간을 절약 하는 반면 드롭다운 보다 향상 된 기능 이므로, 두 디자인 모두 도구 모음을 사용 하 여 실제 명령이 아닌 항목의 수준을 올립니다.

![그림 B: 더 우수 하지만 명령 모음 앤티 패턴이 있습니다.](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-FigureB")<br />그림 B: 더 우수 하지만 명령 모음 앤티 패턴이 있습니다.

**그림 C**에 표시 된 올바른 방법에서이 설정은 일련의 명령에 연결 됩니다. 설정 되는 전역 설정이 없으며 네 개의 명령 간에만 전환 하 고 있습니다. 이 경우 도구 모음에서 명령을 사용할 수 있습니다.

![그림 C: Visual Studio 명령 모음 패턴의 올바른 사용](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-패턴")<br />그림 C: Visual Studio 명령 모음 패턴의 올바른 사용

### <a name="control-anti-patterns"></a>컨트롤 앤티앨리어싱
 일부 앤티 패턴은 단순히 컨트롤이 나 컨트롤 그룹을 사용 하거나 표시 하지 않을 수 있습니다.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>하이퍼링크가 아닌 그룹 레이블로 사용 되는 밑줄
 밑줄 텍스트는 하이퍼링크에만 사용 해야 합니다.

 **올바르지**\
 ![하이퍼링크가 아닌 밑줄이 그어진 텍스트는 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />하이퍼링크가 아닌 밑줄이 그어진 텍스트는 Visual Studio 안티 패턴입니다.

 **좋음**\
 ![스타일이 올바르게 지정 된 경우 비 하이퍼링크 텍스트가 환경 글꼴에 되지 않은 나타납니다.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />스타일이 올바르게 지정 된 경우 비 하이퍼링크 텍스트가 환경 글꼴에 되지 않은 나타납니다.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>확인란을 클릭 하면 팝업 대화 상자가 표시 됩니다.
 "Windows Azure 애플리케이션 게시" 마법사에서 "모든 역할에 대해 원격 데스크톱 사용" 확인란을 클릭 하면 Visual Studio 앤티앨리어싱 인 팝업 대화 상자가 즉시 표시 됩니다. 또한 확인란 필드는 선택 된 후 다른 상호 작용 방지 패턴을 사용 하 여 입력 하지 않습니다.

 ![확인란을 클릭 한 후 대화 상자를 표시 하는 것은 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />확인란을 클릭 한 후 대화 상자를 표시 하는 것은 Visual Studio 안티 패턴입니다.

### <a name="hyperlink-anti-patterns"></a>하이퍼링크 안티패턴
 다음 예제에는 두 가지 앤티 패턴이 포함 되어 있습니다.

1. 전경에 빨간색을 가리키면 글꼴 서비스의 올바른 공유 색이 사용 되지 않는 것을 의미 합니다.

2. "자세한 정보"는 개념 항목에 대 한 링크에 대 한 적절 한 텍스트가 아닙니다. 사용자의 목표는 자세히 알아보는 것이 아니라 선택한 결과를 이해 하는 것입니다.

   ![색 서비스를 무시 하 고 하이퍼링크에 대해 "자세한 정보"를 사용 하는 것은 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />색 서비스를 무시 하 고 하이퍼링크에 대해 "자세한 정보"를 사용 하는 것은 Visual Studio 안티 패턴입니다.

**향상 되는 솔루션:** 사용자가 링크를 클릭 하 여 요청 하는 질문을 합니다. 예:

- Microsoft Azure 서비스는 어떻게 작동 하나요?

- Microsoft Azure Mobile Services 프로젝트는 언제 필요 한가요?

#### <a name="using-click-here-for-links"></a>링크에 대 한 "여기를 클릭" 사용
 하이퍼링크는 설명이 포함 되어야 합니다. 이 패턴은 "여기를 클릭 하십시오." 또는 비슷한 변형을 사용 하는 앤티앨리어싱입니다.

 **잘못 됨:** "새 프로젝트를 만드는 방법에 대 한 지침을 보려면 여기를 클릭 하십시오."

 **양호:** "새 프로젝트를 만드는 어떻게 할까요??"
