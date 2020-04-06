---
title: 비주얼 스튜디오를 위한 UX 에센셜 | 마이크로 소프트 문서
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698338"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio용 UX Essentials

## <a name="best-practices"></a>모범 사례

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio 환경 내에서 일관성을 유지해야 합니다.

- 셸 내의 기존 [상호 작용 패턴을](interaction-patterns-for-visual-studio.md) 따릅니다.

- 쉘의 시각적 언어 및 장인 정신 [요구 사항과](evaluation-tools-for-visual-studio.md)일치하는 디자인 기능.

- 공유 명령 및 컨트롤이 있는 경우 사용합니다.

- Visual Studio 계층 구조와 컨텍스트를 설정하고 UI를 구동하는 방법을 이해합니다.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. 글꼴 및 색상에 대한 환경 서비스를 사용합니다.

- UI는 옵션 대화 상자의 글꼴 및 색상 페이지에서 사용자 지정을 위해 노출되지 않는 한 현재 [환경 글꼴](fonts-and-formatting-for-visual-studio.md) 설정을 준수해야 합니다.

- UI 요소는 공유 환경 토큰 또는 기능별 토큰을 사용하여 [VSColor 서비스를](colors-and-styling-for-visual-studio.md)사용해야 합니다.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. 모든 이미지를 새 VS 스타일과 일치시도록 합니다.

- 아이콘, 글리프 및 기타 그래픽에 대한 Visual Studio 디자인 원칙을 따릅니다.

- 그래픽 요소에 텍스트를 배치하지 마십시오.

### <a name="4-design-from-a-user-centric-perspective"></a>4. 사용자 중심의 관점에서 디자인.

- 작업 흐름을 그 안에 있는 개별 피쳐 앞에 만듭니다.

- 사용자에게 친숙하고 해당 지식을 사양에 명시합니다.

- UI를 검토할 때 전체 환경과 세부 정보를 평가합니다.

- 로캘이나 언어에 관계없이 기능적이고 매력적인 상태로 유지되도록 UI를 디자인합니다.

## <a name="screen-resolution"></a>화면 해상도

### <a name="minimum-resolution"></a>최소 해상도

- Visual Studio 2015의 최소 해상도는 **1280x720입니다.** 즉, 최적의 사용자 *환경은* 아니지만 이 해상도에서 Visual Studio를 사용할 수 있습니다. 모든 측면이 1280x720보다 낮은 해상도에서 사용할 수 있다는 보장은 없습니다.

- Visual Studio의 대상 해상도는 **1366x768입니다.** 이것은 우리가 *좋은* 사용자 경험을 약속하는 가장 낮은 해상도입니다.

- 초기 대화 상자 높이는 **700픽셀보다 작아야**하므로 96dpi에서 IDE 프레임의 최소 해상도 내에 적합합니다.

### <a name="high-density-displays"></a>고밀도 디스플레이
 Visual Studio의 UI는 Windows에서 지원하는 모든 DPI 크기 조정 요소(150%, 200%, 및 250%)에서 잘 작동해야 합니다.

## <a name="anti-patterns"></a>안티 패턴
 Visual Studio에는 지침 및 모범 사례를 따르는 많은 UI 예제가 포함되어 있습니다. 일관성을 위해 개발자는 빌드하는 것과 유사한 제품 UI 디자인 패턴을 차용하는 경우가 많습니다. 이는 사용자 상호 작용 및 시각적 디자인의 일관성을 높이는 데 도움이 되는 좋은 접근 방식이지만, 일정 제약이나 결함 우선 순위 지정으로 인해 가이드라인을 충족하지 못하는 몇 가지 세부 사항이 있는 기능을 제공하는 경우도 있습니다. 이러한 경우 팀은 Visual Studio 환경 내에서 잘못하거나 일치하지 않는 UI를 확산하기 때문에 이러한 "안티 패턴" 중 하나를 복사하지 않습니다.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>필수 필드/설정기본적으로 오류 상태로 표시됨

#### <a name="feature-team-goals"></a>기능 팀 목표

- 구성해야 하는 요소를 추가했다는 것을 사용자에게 경고합니다.

- 입력이 필요한 영역에 사용자의 주의를 기울입니다.

#### <a name="anti-pattern-solution"></a>안티 패턴 솔루션
 사용자가 작업을 시작하고 작업을 완료하기 전에 즉시 구성이 필요한 영역 옆에 중요 중지 아이콘을 배치합니다.

#### <a name="example-manifest-designer-declarations"></a>예: 매니페스트 디자이너 선언
 목록에 선언을 추가하면 사용자가 필요한 속성을 설정할 때까지 지속되는 오류 상태가 즉시 유지됩니다.

 이 경우 경고에 사용되는 아이콘에 ""&times;아이콘이 포함되어 있으므로 공통 제거 아이콘을 옆에 사용할 수 없으므로 추가 문제가 있습니다. 결과적으로 UI는 더 어설픈 컨트롤인 제거 단추를 사용합니다.

 ![기본적으로 UI를 오류 상태로 배치하는 것은 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "매니페스트디자이너오류선언산티패턴")<br />기본적으로 UI를 오류 상태로 배치하는 것은 Visual Studio 안티 패턴입니다.

#### <a name="alternatives"></a>대안

이 문제에 대한 더 나은 해결책은 다음과 같습니다.

- 사용자가 경고 없이 선언을 추가한 다음 즉시 이동하여 항목에 속성을 설정할 수 있습니다.

- 목록에 다른 선언을 추가하거나 디자이너 내에서 탭을 변경하려고 시도하는 등 항목에서 포커스가 이동할 때 경고 아이콘(금색 삼각형)을 추가합니다.

- 사용자가 선언에서 속성을 설정하기 전에 탭을 변경하려고 하면 경고가 해결될 때까지 응용 프로그램이 빌드되지 않는다는 설명의 대화 상자가 나타납니다. 사용자가 대화 상자를 해제하고 탭을 변경하면 선언 탭에 아이콘(중요 또는 경고)이 추가됩니다.

### <a name="multiple-clicks-to-dismiss-ui"></a>UI를 해제하기 위한 여러 번의 클릭

#### <a name="feature-team-goals"></a>기능 팀 목표
 사용자가 설명 텍스트를 먼저 표시하지 않고 UI를 해제하도록 허용하지 마십시오.

#### <a name="anti-pattern"></a>안티 패턴
 VS UI 내의 다양한 위치에 비디오 링크를 삽입하는 팀은 UX에서&times;지정한 "닫기 버튼 및 도구 설명"의 일반적인 패턴에 대해 결정하고 대신 드롭다운 및 "다시 표시되지 않음" 링크를 구현했습니다.

#### <a name="example-video-links-in-team-explorer"></a>예: 팀 탐색기의 비디오 링크
UI를 해제하기 전에 사용자가 설명 텍스트를 읽도록 강요하는 것은 Visual Studio 내에서 안티 패턴입니다. 올바르게 디자인된 비디오 링크는 호버에 대한 추가 정보가&times;있는 도구 설명이 표시되어야 하며 " "를 클릭하면 추가 상호 작용없이 메시지를 해제해야 합니다.

 ![설명 텍스트 안티&#45;패턴 &#45; 올바르지 않습니다.](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "잘못된 사용다번클릭")<br />잘못된 비디오 링크 패턴

간단한 닫기 버튼(한 번의 클릭)대신 사용자는 두 번의 클릭으로 비디오 링크가 나타나는 모든 장소에서 UI를 해제해야 합니다.

이 상황에 대 한 올바른 디자인은 인터넷 익스플로러, 사무실 및 Visual Studio에 일반적인 패턴을 따라 하는 것입니다.: 마우스를 가져가면 사용자가 도구 설명 설명을 볼 수 있으며 한 번의 클릭으로 UI를 숨깁니다.

 ![설명 텍스트 안티&#45;패턴 &#45; 올바른](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "설명텍스트안티 패턴-올바른")<br />올바른 비디오 링크 패턴

### <a name="using-command-bars-for-settings"></a>설정에 명령 모음 사용

**그림 A는** 명령 그 이상에 적용되는 명령 단추 아래에 설정을 배치하는 이 안티 패턴을 나타냅니다. 이 스케치에는 선택한 설정을 준수하는 검색기, 디버깅 없이 시작, 단계 입력과 같은 디버깅 시작 외에 명령이 있습니다.

![그림 A: 명령 표시줄 안티 패턴](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "커맨드바란티 패턴-그림A")<br />그림 A: 명령 표시줄 안티 패턴

약간 더 나은, 하지만 여전히 바람직하지 않은, 도구 모음에이 유형의 설정을 넣어, **그림 B와**같이 . 분할 버튼은 공간을 적게 차지하므로 드롭다운에 비해 개선되었지만 두 디자인 모두 여전히 도구 모음을 사용하여 실제로 명령이 아닌 것을 홍보하고 있습니다.

![그림 B: 더 나은,하지만 여전히 명령 표시 줄 안티 패턴](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "커맨드바란티 패턴-그림B")<br />그림 B: 더 나은,하지만 여전히 명령 표시 줄 안티 패턴

**그림 C에**표시된 올바른 접근 방식에서 설정은 일련의 명령에 연결됩니다. 전역 설정이 설정되어 있지 않으며 네 가지 명령 간에 전환하고 있습니다. 도구 모음의 명령을 사용할 수 있는 유일한 상황입니다.

![그림 C: Visual Studio 명령 모음 패턴 의 올바른 사용](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "커맨드바란티 패턴-그림C")<br />그림 C: Visual Studio 명령 모음 패턴 의 올바른 사용

### <a name="control-anti-patterns"></a>안티 패턴 제어
 일부 안티 패턴은 단순히 잘못된 사용 또는 컨트롤 또는 컨트롤 그룹의 표시입니다.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>하이퍼링크가 아닌 그룹 레이블로 사용되는 밑줄
 밑줄 텍스트는 하이퍼링크에만 사용해야 합니다.

 **나쁜:**\
 ![하이퍼링크가 아닌 밑줄이 그어진 텍스트는 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />하이퍼링크가 아닌 밑줄이 그어진 텍스트는 Visual Studio 안티 패턴입니다.

 **좋은:**\
 ![스타일이 올바르게 조정된 비하이퍼링크 텍스트는 환경 글꼴에 장식되지 않은 것으로 나타납니다.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />스타일이 올바르게 조정된 비하이퍼링크 텍스트는 환경 글꼴에 장식되지 않은 것으로 나타납니다.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>확인란을 클릭하면 팝업 대화 상자가 나타납니다.
 "Windows Azure 응용 프로그램 게시" 마법사에서 "모든 역할에 대해 원격 데스크톱 사용" 확인란을 클릭하면 즉시 Visual Studio 안티 패턴인 팝업 대화 상자가 나타납니다. 또한, 확인란 필드는 선택된 후, 또 다른 상호작용 안티패턴으로 채워지지 않는다.

 ![확인란을 클릭한 후 대화 상자를 가져오는 것은 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />확인란을 클릭한 후 대화 상자를 가져오는 것은 Visual Studio 안티 패턴입니다.

### <a name="hyperlink-anti-patterns"></a>하이퍼링크 안티패턴
 다음 예제에는 두 가지 안티 패턴이 포함되어 있습니다.

1. 호버에서 빨간색으로 바뀌는 전경은 글꼴 서비스의 올바른 공유 색상이 사용되지 않음을 의미합니다.

2. "자세히 알아보기"는 개념 적 주제에 대한 링크에 적합한 텍스트가 아닙니다. 사용자의 목표는 더 많은 것을 배우는 것이 아니라 선택한 결과를 이해하는 것입니다.

   ![색상 서비스를 무시하고 하이퍼링크에 "자세히 알아보기"를 사용하는 것은 Visual Studio 안티 패턴입니다.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />색상 서비스를 무시하고 하이퍼링크에 "자세히 알아보기"를 사용하는 것은 Visual Studio 안티 패턴입니다.

**더 나은 솔루션:** 링크를 클릭하여 사용자가 묻는 질문을 제기합니다. 다음은 그 예입니다.

- Windows Azure 서비스는 어떻게 작동합니까?

- Windows Azure 모바일 서비스 프로젝트는 언제 필요합니까?

#### <a name="using-click-here-for-links"></a>링크에 대해 "여기를 클릭하십시오"를 사용
 하이퍼링크는 자체 설명이어야 합니다. "여기를 클릭하십시오" 또는 이와 유사한 변형을 사용하는 것은 안티 패턴입니다.

 **나쁜:** "새 프로젝트를 만드는 방법에 대한 지침을 보려면 여기를 클릭하십시오."

 **좋아요:** "새 프로젝트를 만들려면 어떻게 해야 합니까?"
