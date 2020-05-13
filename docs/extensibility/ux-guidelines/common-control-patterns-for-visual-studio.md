---
title: 비주얼 스튜디오의 일반적인 제어 패턴 | 마이크로 소프트 문서
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698708"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio의 일반 컨트롤 패턴
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>일반적인 컨트롤

### <a name="overview"></a>개요
공통 컨트롤은 Visual Studio의 대부분의 사용자 인터페이스를 구성합니다. Visual Studio 인터페이스에서 사용되는 가장 일반적인 컨트롤은 [Windows 데스크톱 상호 작용 지침을](/windows/desktop/uxguide/controls)따라야 합니다. 이 항목은 Visual Studio에만 적용되며 이러한 Windows 지침을 보강하는 특수 한 상황이나 세부 정보를 다룹니다.

#### <a name="common-controls-in-this-topic"></a>이 항목의 일반적인 컨트롤

- [스크롤 막대](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [입력 필드](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [콤보 상자 및 드롭다운 목록](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [확인란](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [라디오 단추](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [프레임 그룹화](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [버튼 및 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [트리 보기](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>비주얼 스타일
컨트롤을 스타일 지정할 때 가장 먼저 고려해야 할 것은 컨트롤이 테마 UI에서 사용되는지 여부입니다. 표준 UI의 컨트롤은 테마가 없는 UI이며 [일반 Windows Desktop 스타일을](/windows/desktop/uxguide/controls)따라야 하며, 이는 다시 템플릿화되지 않으며 기본 컨트롤 모양에 나타나야 함을 의미합니다.

- **표준(유틸리티) 대화 상자: 테마가** 없습니다. 템플릿을 다시 쓰지 마십시오. 기본 제어 스타일 기본값을 사용합니다.

- **도구 창, 문서 편집기, 디자인 표면 및 테마 대화 상자:** 컬러 서비스를 사용하여 특수 테마 모양을 사용합니다.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>스크롤 막대
 스크롤 막대는 코드 편집기와 같은 콘텐츠 정보로 보강되지 않는 한 [Windows 스크롤 막대의 일반적인 상호 작용 패턴을](/windows/desktop/Controls/about-scroll-bars) 따라야 합니다.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>입력 필드
 일반적인 상호 작용 동작의 경우 [텍스트 상자에 대한 Windows 데스크톱 지침을 따릅니다.](/windows/desktop/uxguide/ctrl-text-boxes)

#### <a name="visual-style"></a>비주얼 스타일

- 입력 필드는 유틸리티 대화 상자에서 스타일을 정할 수 없습니다. 컨트롤에 내장된 기본 스타일을 사용합니다.

- 테마 입력 필드는 테마 대화 상자 및 도구 창에서만 사용해야 합니다.

#### <a name="specialized-interactions"></a>전문적인 상호 작용

- 읽기 전용 필드에는 회색(사용 안 함) 배경이 있지만 기본(활성) 전경이 있습니다.

- 필수 필드에는 ** \<필요한>** 워터마크로 있어야 합니다. 드문 경우를 제외하고는 배경색을 변경해서는 안 됩니다.

- 오류 유효성 검사: [Visual Studio에 대한 알림 및 진행률](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) 참조

- 입력 필드는 표시되는 창의 너비에 맞지 않고 경로와 같은 긴 필드의 길이와 임의로 일치하도록 콘텐츠에 맞게 크기를 조정해야 합니다. 길이는 필드에 허용되는 문자 수에 대한 제한 을 사용자에게 표시할 수 있습니다.

     ![잘못된 입력 필드 길이: 이름이 이렇게 길어질 가능성은 거의 없습니다.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "01_IncorrectInputFieldControl 0707-01_IncorrectInputFieldControl")<br />잘못된 입력 필드 길이: 이름이 이렇게 길어질 가능성은 거의 없습니다.

     ![올바른 입력 필드 길이: 입력 필드는 예상된 콘텐츠에 대한 적당한 너비입니다.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />올바른 입력 필드 길이: 입력 필드는 예상된 콘텐츠에 대한 적당한 너비입니다.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>콤보 상자 및 드롭다운 목록
일반적인 상호 작용 동작의 경우 [드롭다운 목록 및 콤보 상자에 대한 Windows 데스크톱 지침을 따릅니다.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서는 컨트롤을 다시 템플릿으로 두지 마십시오. 컨트롤에 내장된 기본 스타일을 사용합니다.

- 테마 UI에서는 콤보 상자와 드롭다운이 컨트롤에 대한 표준 테마를 따릅니다.

#### <a name="layout"></a>레이아웃
콤보 상자와 드롭다운은 표시되는 창의 너비에 맞지 않고 경로와 같은 긴 필드의 길이와 임의로 일치하도록 내용에 맞게 크기를 조정해야 합니다.

![잘못된 내용: 드롭다운 너비가 너무 길어 표시될 콘텐츠입니다.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />잘못된 내용: 드롭다운 너비가 너무 길어 표시될 콘텐츠입니다.

![올바른: 드롭다운은 변환 증가를 허용하도록 크기가 조정되지만 불필요하게 길지는 않습니다.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "04_CorrectDropDownLayout")<br />올바른: 드롭다운은 변환 증가를 허용하도록 크기가 조정되지만 불필요하게 길지는 않습니다.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>확인란
일반적인 상호 작용 동작의 경우 [확인란에 대한 Windows 데스크톱 지침을 따릅니다.](/windows/desktop/uxguide/ctrl-check-boxes)

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서는 컨트롤을 다시 템플릿으로 두지 마십시오. 컨트롤에 내장된 기본 스타일을 사용합니다.

- 테마 UI에서 확인란은 컨트롤에 대한 표준 테마를 따릅니다.

#### <a name="specialized-interactions"></a>전문적인 상호 작용

- 확인란과의 상호 작용은 대화 상자를 팝업하거나 다른 영역으로 이동해서는 안 됩니다.

- 확인란을 첫 번째 텍스트 줄의 기준선에 정렬합니다.

     ![잘못된 것: 확인란이 텍스트의 가운데에 있습니다.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />잘못된 것: 확인란이 텍스트의 가운데에 있습니다.

     ![올바른: 확인란이 텍스트의 첫 번째 줄에 정렬됩니다.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />올바른: 확인란이 텍스트의 첫 번째 줄에 정렬됩니다.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>라디오 버튼
일반적인 상호 작용 동작의 경우 [라디오 단추에 대한 Windows 데스크톱 지침을 따릅니다.](/windows/desktop/uxguide/ctrl-radio-buttons)

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서는 라디오 단추의 스타일을 사용하지 마십시오. 컨트롤에 내장된 기본 스타일을 사용합니다.

#### <a name="specialized-interactions"></a>전문적인 상호 작용
좁은 레이아웃에서 그룹 구분을 유지해야 하는 경우가 아니면 그룹 프레임을 사용하여 라디오 선택 사항을 동봉할 필요가 없습니다.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>프레임 그룹화
일반적인 상호 작용 동작의 경우 [그룹 프레임에 대한 Windows 데스크톱 지침을](/windows/desktop/uxguide/ctrl-group-boxes)따릅니다.

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서는 그룹 프레임의 스타일을 정하지 마십시오. 컨트롤에 내장된 기본 스타일을 사용합니다.

#### <a name="layout"></a>레이아웃

- 좁은 레이아웃에서 그룹 구분을 유지해야 하는 경우가 아니면 그룹 프레임을 사용하여 라디오 선택 사항을 동봉할 필요가 없습니다.

- 단일 컨트롤에 그룹 프레임을 사용하지 마십시오.

- 그룹 프레임 컨테이너 대신 가로 규칙을 사용하는 것이 허용되는 경우도 있습니다.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>텍스트 컨트롤

### <a name="static-text-fields"></a>정적 텍스트 필드

정적 텍스트 필드는 읽기 전용 정보를 제공하며 사용자가 선택할 수 없습니다. 사용자가 클립보드에 복사할 수 있는 텍스트에는 사용하지 마십시오. 그러나 읽기 전용 정적 텍스트는 상태 변경을 반영하도록 변경할 수 있습니다. 아래 예제에서는 정보 그룹 아래의 출력 이름 정적 텍스트가 변경되어 루트 네임스페이스 텍스트 상자에 대한 변경 내용을 반영합니다.

정적 텍스트 정보를 표시하는 방법에는 두 가지가 있습니다.

정적 텍스트는 그룹화 충돌이 없을 때 아무런 포함 없이 대화 상자에서 자체적으로 사용할 수 있습니다. 상자의 추가 줄이 실제로 필요한지 결정합니다. 예를 들어 다음과 같이 그룹 선으로 만든 섹션 아래에 디렉터리 경로가 표시됩니다.

![텍스트 컨트롤의 정적 텍스트 정보](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "표시정적텍스트.png")<br />텍스트 컨트롤의 정적 텍스트 정보

다른 그룹화 된 영역이 존재 하 고 정보의 포함 하는 대화 상자에서 가독성을 도움이 될 것입니다 및 섹션을 숨길 수 있습니다 또는 표시 될 수 있는 경우 **(속성 창** 설명 창에서 와 같이) 비슷한 UI와 일치 하 고 싶을 때, 상자 안에 정적 텍스트를 배치 합니다. 이 그룹 상자는 단일 규칙이어야 `ButtonShadow`하며 다음과 같은 색상으로 지정되어야 합니다.

![속성 창의 정적 텍스트](../../extensibility/ux-guidelines/media/PropertiesWindow.png "프로퍼티윈도우.png")<br />속성 창의 정적 텍스트

### <a name="read-only-text-box"></a>읽기 전용 텍스트 상자

이렇게 하면 사용자가 필드 내부의 텍스트를 선택할 수 있지만 편집할 수는 없습니다. 이러한 텍스트 상자는 채우기와 함께 일반적인 3-D `ButtonShadow` 끌로 둘러싸여 있습니다.

사용자가 확인란을 선택/선택 취소하거나 라디오 단추를 선택/선택 취소하는 등 연결된 컨트롤을 변경할 때 텍스트 상자가 활성화(편집 가능)될 수 있습니다. 예를 들어 아래 ** &gt; 표시된 도구 옵션** 페이지에서 **기본 설정** 확인란을 선택하지 않으면 **홈 페이지** 텍스트 상자가 활성화됩니다.

![비활성 및 활성 상태를 표시하는 읽기 전용 텍스트 상자](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "읽기 전용텍스트박스.png")<br />비활성 및 활성 상태를 표시하는 읽기 전용 텍스트 상자

### <a name="using-text-in-dialogs"></a>대화 상자에서 텍스트 사용

대화 상자의 텍스트에 대한 주요 지침:

- 테마가 없는 대화상자의 텍스트 상자, 목록 상자 및 프레임에 대한 레이블은 동사로 시작하고 첫 번째 단어에만 초기 대문자가 있고 콜론으로 끝납니다.

    > 테마 대화 상자의 텍스트 컨트롤은 [Windows 데스크톱 UX 지침을](/windows/desktop/uxguide/top-violations) 따르며 도움말 링크의 물음표를 제외하고 끝문장 을 사용하지 않습니다.

- 확인란과 옵션 단추의 레이블은 첫 번째 단어의 초기 대문자인 동사로 시작하며 끝 문장 부호가 없습니다.

- 단추, 메뉴, 메뉴 항목 및 탭의 레이블에는 각 단어(제목 대/소문자)에 초기 대문자가 있습니다.

- 레이블 용어는 다른 대화 상자의 유사한 레이블과 일치해야 합니다.

- 가능하면 작성기/편집자가 구현을 위해 개발자에게 텍스트를 작성하거나 승인하도록 합니다.

- 모든 컨트롤에는 탭으로 충분한 특별한 경우를 제외하고 레이블이 있어야 합니다.
적절한 경우 도우미 텍스트를 사용하십시오.

### <a name="helper-text"></a>도우미 텍스트

대화 상자에는 사용자가 대화의 목적을 이해하거나 취할 작업을 나타낼 수 있도록 도와줍니다. 도우미 텍스트는 간단한 대화 상자가 복잡해지는 것을 피하기 위해 필요한 경우에만 사용해야 합니다. 도우미 텍스트의 두 가지 변형은 대화 상자와 워터마크입니다.

도우미 텍스트에 대 한 일반적인 위치를 따라 하 고 새로운 영역을 소개에 선택적. 도우미 텍스트에 대 한 일반적인 시나리오는 다음과 같습니다.

- 대화 상자의 도우미 텍스트로 복잡한 대화 상자와 상호 작용하는 방법에 대한 추가 방향을 제공합니다.

- 빈 도구 창 이나 대화 상자에 워터 마크 텍스트, 콘텐츠가 표시 되지 않는 이유를 설명 합니다.

- **속성 창**의 아래쪽에 있는 것과 같은 설명 창입니다.

- 빈 편집기의 워터마크 텍스트를 사용하여 사용자가 시작하기 위해 취해야 할 작업을 설명합니다.

### <a name="dialog-helper-text"></a>대화 상자 도우미 텍스트

사용자 환경 디자이너는 도우미 텍스트가 적절한 시기를 결정하는 데 도움이 될 수 있습니다. 디자이너는 도우미 텍스트가 표시되는 위치와 일반 콘텐츠를 정의할 수 있습니다. 사용자 지원은 실제 텍스트를 쓰다/ 편집할 수 있습니다.

### <a name="watermarks"></a>워터마크

대화상자는 약간 다른 워터마크 지침의 이점을 누릴 수 있습니다. 대화 상자는 많은 UI 요소(레이블, 힌트 텍스트, 단추 및 텍스트가 있는 기타 컨테이너 컨트롤)로 바쁘게 나타날 수 있기 때문에 `ButtonShadow`특히 검정색으로 표시되는 경우 워터마크가 어두운 회색(VSColor: )에서 더 잘 나타납니다. 일반적으로 워터마크는 흰색 배경이 있는 목록 상자와 같은 `Window`컨트롤 내에 나타납니다(VSColor: ).

- 텍스트가 진한 회색으로 나타납니다(VSColor: `ButtonShadow`). 그러나 워터마크가 중간 회색 또는 기타 색상(VSColor: `ButtonFace`) 배경에 나타나고 가독성에 대한 우려가 있는 `WindowText`경우 검정 텍스트(VSColor: )로 이동합니다.

- 워터마크는 가운데에 있거나 왼쪽으로 플러시할 수 있습니다. 선형 결정을 내릴 때 표준 설계 규칙을 적용합니다. 백그라운드에서 워터마크를 선택할 수 없습니다.

![워터마크 텍스트 예제](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />워터마크 텍스트 예제

### <a name="context-specific-dynamic-text"></a>컨텍스트별(동적) 텍스트

동적 텍스트는 대화 상자 또는 모데리스 UI에서 동적 레이블 또는 동적 콘텐츠로 두 가지 방법 중 하나를 사용할 수 있습니다.

- 동적 레이블: 동적 텍스트의 일반적인 사용은 오른쪽 그리드에 표시되는 요소에 대한 요소 및 속성 목록이 포함된 대화 상자와 같이 선택한 항목에 대한 자세한 정보를 제공하는 설명 패널에 있습니다. 속성 그리드의 레이블은 동적일 수 있으므로 항목이 왼쪽에서 선택되면 오른쪽 그리드에 해당 특정 항목에 대한 정보가 표시됩니다.

- 동적 텍스트: 일반적인 정보가 아닌 특정 정보를 이러한 방식으로 표시해야 하는 경우에 유용할 수 있지만 과도하게 사용하지 않도록 주의해야 합니다.

사용자가 정보를 복사할 수 있도록 하려면 동적 텍스트가 읽기 전용 텍스트 필드에 있어야 합니다.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>버튼 및 하이퍼링크

### <a name="overview"></a>개요
단추 및 링크 컨트롤(하이퍼링크)은 사용, 표현, 크기 조정 및 [간격에 대한 하이퍼링크에 대한 기본 Windows Desktop 지침을](/windows/desktop/uxguide/ctrl-links) 따라야 합니다.

### <a name="choosing-between-buttons-and-links"></a>단추와 링크 중 선택
일반적으로 단추는 작업에 사용되었으며 하이퍼링크는 탐색을 위해 예약되었습니다. 단추는 모든 경우에 사용할 수 있지만 일부 조건에서 단추와 링크를 더 상호 교환할 수 있도록 Visual Studio에서 링크 역할이 확장되었습니다.

명령 단추를 사용할 때:

- 기본 명령

- 보조 명령인 경우에도 입력을 수집하거나 선택 을 선택하는 데 사용되는 창을 표시

- 파괴적이거나 되돌릴 수 없는 행동

- 마법사 및 페이지 흐름 내의 약정 버튼

도구 창에서 명령 단추를 사용하지 않거나 레이블에 두 개 이상의 단어가 필요한 경우 사용하지 마십시오. 링크에는 레이블이 더 길수 있습니다.

 링크를 사용하는 경우:

- 다른 창, 문서 또는 웹 페이지로 탐색

- 작업의 의도를 설명하기 위해 더 긴 레이블 또는 짧은 문장이 필요한 상황

- 작업이 파괴적이거나 되돌릴 수 없는 경우 버튼이 UI를 압도하는 좁은 공간

- 명령이 많은 상황에서 보조 명령 강조 해제

#### <a name="examples"></a>예
![상태 메시지 다음에 InfoBar에 사용되는 명령 링크](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />상태 메시지 다음에 InfoBar에 사용되는 명령 링크

![CodeLens 팝업에 사용된 링크](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens 팝업에 사용된 링크

![버튼이 너무 많은 관심을 끌 수 있는 보조 명령에 사용되는 링크](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />버튼이 너무 많은 관심을 끌 수 있는 보조 명령에 사용되는 링크

### <a name="common-buttons"></a>공통 버튼

#### <a name="text"></a>텍스트
[UI 텍스트 및 용어의](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)쓰기 지침을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일

##### <a name="standard-unthemed"></a>표준(테마가 없는)
Visual Studio의 대부분의 단추는 유틸리티 대화 상자에 표시되며 스타일을 정해서는 안 됩니다. 운영 체제에서 지정한 단추의 표준 모양을 반영해야 합니다.

##### <a name="themed"></a>테마
경우에 따라 스타일이 있는 UI 내에서 단추를 사용할 수 있으며 이러한 단추는 적절하게 스타일을 조정해야 합니다. 테마 컨트롤에 대한 자세한 [내용은 대화 상자를](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 참조하십시오.

### <a name="special-buttons"></a>특수 버튼

#### <a name="browse-buttons"></a>찾아보기... 단추
**[찾아보기...]** 단추는 그리드, 대화 상자 및 도구 창 및 기타 모덜리스 UI 요소에 사용됩니다. 사용자가 값을 컨트롤에 채우는 데 도움을 주는 피커를 표시합니다. 이 버튼에는 길고 짧은 두 가지 변형이 있습니다.

![긴 [찾아보기...] 버튼](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />긴 [찾아보기...] 버튼

![타원 전용 짧은 [...] 버튼](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />타원 전용 짧은 [...] 버튼

타원 전용 짧은 단추를 사용하는 경우:

- 대화 상자에 여러 필드가 탐색을 허용하는 경우와 같이 긴 **[찾아보기...]** 버튼이 두 개 이상 있는 경우. 이 상황에서 생성된 혼란스러운 액세스 키를 피하기 위해 각각의 짧은 **[...]** 버튼을&** 찾아보기** 및 **B&행이** 동일한 대화 상자에서 행을 참조하십시오).

- 긴밀한 대화 상자에서, 또는 긴 버튼을 넣을 수있는 합리적인 장소가없는 경우.

- 단추가 그리드 컨트롤에 나타나는 경우.

단추 사용에 대 한 지침:

- 액세스 키를 사용하지 마십시오. 키보드를 사용하여 액세스하려면 사용자가 인접한 컨트롤에서 탭해야 합니다. 탭 순서가 입력할 필드 바로 그 다음으로 찾아보기 버튼이 있는지 확인합니다. 첫 번째 기간 아래에 밑줄은 사용하지 마십시오.

- 화면 판독기가 "점 점" 또는 "기간 기간"이 아닌 "찾아보기"로 읽을 수 있도록 MSAA(사용자 지정 속성) **이름을** **찾아볼** 수 있도록 설정합니다. 관리되는 컨트롤의 경우 이는 **AccessibleName** 속성을 설정하는 것을 의미합니다.

- 찾아보기 작업을 제외한 모든 작업에 는 타원 **[...]** 단추를 사용하지 마십시오. 예를 들어 **[New...]** 버튼이 필요하지만 텍스트에 대한 공간이 충분하지 않은 경우 대화 상자를 다시 디자인해야 합니다.

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
![크기 조정 [찾아보기...] 버튼: 표준 버전은 75x23 픽셀, 짧은 버전은 26x23 픽셀](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />[찾아보기...] 크기 조정 단추

![간격 [찾아보기...] 버튼: 관련 컨트롤과 표준 찾아보기 버튼 7 픽셀 사이의 간격, 관련 컨트롤과 짧은 찾아보기 버튼 5 픽셀 사이의 간격](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />[찾아보기...] 간격 조정 단추

#### <a name="graphical-buttons"></a>그래픽 버튼
일부 단추는 항상 그래픽 이미지를 사용해야 하며 공간을 절약하고 지역화 문제를 피하기 위해 텍스트를 포함하지 않아야 합니다. 이들은 종종 필드 선택기 및 기타 정렬 가능한 목록에서 사용됩니다.

> [!NOTE]
> 사용자는 이러한 단추를 탭해야 하므로(액세스 키가 없음) 합리적인 순서로 배치합니다. 화면 `name` 판독이 단추 작업을 올바르게 해석할 수 있도록 단추의 속성을 작업에 매핑합니다.

| 함수 | 단추 |
| --- | --- |
| 추가 | ![그래픽 "추가" 단추](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| 제거 | ![그래픽 "제거" 단추](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| 모두 추가 | ![그래픽 "모두 추가" 단추](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| 모두 제거 | ![그래픽 "모두 제거" 단추](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| 위로 이동 | ![그래픽 "위로 이동" 단추](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| 아래로 이동 | ![그래픽 "아래로 이동" 단추](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| DELETE | ![그래픽 "삭제" 단추](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
그래픽 버튼의 크기 조정은 **[찾아보기...]** 버튼(26x23 픽셀)의 짧은 버전과 동일합니다.

![버튼에 그래픽 이미지의 모양, 유무에 관계없이 투명 한 색상 표시](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />버튼에 그래픽 이미지의 모양, 유무에 관계없이 투명 한 색상 표시

### <a name="hyperlinks"></a>하이퍼링크
하이퍼링크는 도움말 항목, 모달 대화 상자 또는 마법사 열기와 같은 탐색 기반 작업에 적합합니다. 하이퍼링크가 명령에 사용되는 경우 항상 UI에 눈에 띄는 변경 이 표시됩니다. 일반적으로 저장, 취소 및 삭제와 같은 작업을 커밋하는 작업은 단추를 사용하여 더 잘 전달됩니다.

#### <a name="writing-style"></a>쓰기 스타일
사용자 [인터페이스 텍스트에 대한 Windows 데스크톱 지침을](/windows/desktop/uxguide/text-ui)따릅니다. "자세히 알아보기", "자세히 알아보기", "이에 대한 도움말 보기" 관용구를 사용하지 마세요. 대신 도움말 콘텐츠에서 대답하는 기본 질문의 관점에서 도움말 링크 텍스트를 구합니다. 예를 들어 "**서버 탐색기에 서버를 추가하려면 어떻게 해야 합니까?**"

#### <a name="visual-style"></a>비주얼 스타일

- 하이퍼링크는 항상 [VSColor 서비스를](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)사용해야합니다. 하이퍼링크의 스타일이 올바르게 지정되지 않으면 활성화되어 있을 때 빨간색으로 깜박이거나 방문한 후 다른 색상을 표시합니다.

- 링크가 워터마크와 같이 전체 문장 내의 문장 조각이 아니면 컨트롤 휴지 상태에 밑줄을 포함하지 마십시오.

- 밑줄은 가리키기위에 나타나지 않아야 합니다. 대신 링크가 활성 상태라는 사용자에 대한 피드백은 약간의 색상 변경과 적절한 링크 커서입니다.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>트리 뷰

트리 뷰는 복잡한 목록을 부모-자식 그룹으로 구성하는 방법을 제공합니다. 사용자는 부모 그룹을 확장하거나 축소하여 기본 하위 항목을 표시하거나 숨길 수 있습니다. 트리 뷰 내의 각 항목을 선택하여 추가 작업을 제공할 수 있습니다.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>트리 뷰 비주얼 스타일

#### <a name="expanders"></a>확장기
트리 뷰 컨트롤은 Windows 및 Visual Studio에서 사용하는 확장기 디자인을 준수해야 합니다. 각 노드는 확장기 컨트롤을 사용하여 기본 항목을 표시하거나 숨깁니다. 확장기 컨트롤을 사용하면 Windows 및 Visual Studio 내에서 다른 트리 뷰를 발생할 수 있는 사용자에게 일관성이 제공됩니다.

![올바른: 확장기 컨트롤을 사용하여 트리 뷰 노드의 적절한 스타일](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />올바른: 확장기 컨트롤을 사용하여 트리 뷰 노드의 적절한 스타일

![올바르지 않습니다: 트리 뷰 노드의 부적절한 스타일](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />올바르지 않습니다: 트리 뷰 노드의 부적절한 스타일

#### <a name="selection"></a>선택
트리 뷰 내에서 노드를 선택하면 강조 표시가 트리 뷰 컨트롤의 전체 너비로 확장됩니다. 이렇게 하면 사용자가 선택한 항목을 명확하게 식별할 수 있습니다. 선택 색상은 현재 Visual Studio 테마를 반영해야 합니다.

![올바른: 선택한 노드의 강조 표시는 트리 뷰 컨트롤의 전체 너비에 맞습니다.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />올바른: 선택한 노드의 강조 표시는 트리 뷰 컨트롤의 전체 너비에 맞습니다.

![올바르지 않은: 선택한 노드의 강조 표시가 트리 뷰 컨트롤의 전체 너비에 맞지 않습니다.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />올바르지 않은: 선택한 노드의 강조 표시가 트리 뷰 컨트롤의 전체 너비에 맞지 않습니다.

#### <a name="icons"></a>아이콘
아이콘은 항목 간의 차이점을 시각적으로 식별하는 데 도움이 되는 경우에만 트리 뷰 컨트롤에서 사용해야 합니다. 일반적으로 아이콘은 아이콘이 요소 유형을 구별하기 위해 정보를 전달하는 이기종 목록에서만 사용해야 합니다. 아이콘을 사용하는 동종 목록에서 자주 노이즈로 볼 수 있으며 피해야한다. 이 경우 그룹 아이콘(부모)은 그룹 내의 항목 유형을 전달할 수 있습니다. 이 규칙에 대한 예외는 아이콘이 동적이고 상태를 나타내는 데 사용되는 경우입니다.

#### <a name="scroll-bars"></a>스크롤 막대
트리 뷰 컨트롤에 콘텐츠가 맞는 경우 스크롤 막대는 항상 숨김을 숨김을 가져야 합니다. 스크롤 막대는 스크롤 가능한 창에서 숨기거나 반투명하게 표시되고 트리 뷰를 포함하는 창에 포커스가 있거나 트리 뷰 자체의 가리키면 나타납니다.

![내용이 트리 뷰 컨트롤의 제한을 초과했기 때문에 세로 및 가로 스크롤 막대가 모두 표시됩니다.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />내용이 트리 뷰 컨트롤의 제한을 초과했기 때문에 세로 및 가로 스크롤 막대가 모두 표시됩니다.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>트리 뷰 상호 작용

#### <a name="context-menus"></a>상황에 맞는 메뉴
트리 뷰 노드는 컨텍스트 메뉴에서 하위 메뉴 옵션을 표시할 수 있습니다. 일반적으로 사용자가 항목을 마우스 오른쪽 단추로 클릭했거나 항목을 선택한 Windows 키보드의 메뉴 키를 누를 때 발생합니다. 노드가 포커스를 얻고 선택되는 것이 중요합니다. 이렇게 하면 사용자가 하위 메뉴에 속한 항목을 식별할 수 있습니다.

![컨텍스트 메뉴를 생성한 항목은 포커스를 얻고 선택한 항목을 사용자에게 알립니다.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />컨텍스트 메뉴를 생성한 항목은 포커스를 얻고 선택한 항목을 사용자에게 알립니다.

#### <a name="keyboard"></a>키보드
트리 뷰는 키보드를 사용하여 항목을 선택하고 노드를 확장/축소하는 기능을 제공해야 합니다. 이렇게 하면 내비게이션이 내게 필요한 옵션 요구 사항을 충족할 수 있습니다.

##### <a name="tree-view-control"></a>트리 뷰 컨트롤
Visual Studio 트리 컨트롤은 일반적인 키보드 탐색을 따라야 합니다.

- **최대 화살표:** 트리위로 이동하여 항목 선택

- **아래쪽 화살표:** 트리 아래로 이동하여 항목 선택

- **오른쪽 화살표:** 트리에서 노드 확장

- **왼쪽 화살표:** 트리에서 노드 축소

- **키 입력:** 선택한 항목 시작, 로드, 실행

##### <a name="trid-tree-view-and-grid-view"></a>트라이드(트리 뷰 및 그리드 뷰)
트라이드 컨트롤은 그리드 내의 트리 뷰를 포함하는 복잡한 컨트롤입니다. 트리를 확장, 축소 및 탐색하는 것은 트리 뷰와 동일한 키보드 명령을 준수해야 하며 다음이 추가되어야 합니다.

- **오른쪽 화살표:** 노드를 확장합니다. 노드가 확장된 후에는 오른쪽에 있는 가장 가까운 열로 계속 탐색해야 합니다. 행의 끝에서 탐색을 중지해야 합니다.

- **탭:** 오른쪽에 있는 가장 가까운 셀로 이동합니다.  행의 끝에서 탐색은 다음 행으로 계속됩니다.

- **시프트 + 탭:** 왼쪽에 있는 가장 가까운 셀로 이동합니다.  행의 시작 부분에서 탐색은 이전 행의 오른쪽 셀로 계속됩니다.

![비주얼 스튜디오의 트라이드 컨트롤](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />비주얼 스튜디오의 트라이드 컨트롤
