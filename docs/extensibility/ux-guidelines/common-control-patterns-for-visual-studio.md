---
title: Visual Studio의 공용 컨트롤 패턴 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698708"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio의 일반 컨트롤 패턴
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> 공용 컨트롤

### <a name="overview"></a>개요
공용 컨트롤은 Visual Studio에서 대부분의 사용자 인터페이스를 구성 합니다. Visual Studio 인터페이스에서 가장 일반적으로 사용 되는 컨트롤은 [Windows 데스크톱 상호 작용 지침](/windows/desktop/uxguide/controls)을 따라야 합니다. 이 항목은 Visual Studio와 관련 되어 있으며 이러한 Windows 지침을 보완 하는 특별 한 상황 또는 세부 정보를 다룹니다.

#### <a name="common-controls-in-this-topic"></a>이 항목의 공용 컨트롤

- [스크롤 막대](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [입력 필드](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [콤보 상자 및 드롭다운 목록](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [확인란](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [라디오 단추](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [프레임 그룹화](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [단추 및 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [트리 보기](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>비주얼 스타일
컨트롤의 스타일을 지정 하는 경우 가장 먼저 고려해 야 할 사항은 컨트롤이 테마가 지정 된 UI에서 사용 되는지 여부입니다. 표준 UI의 컨트롤은 테마가 적용 되지 않은 UI 이며 [일반적인 Windows 바탕 화면 스타일](/windows/desktop/uxguide/controls)을 따라야 합니다. 즉, 템플릿이 다시 지정 되지 않으며 기본 컨트롤 모양에 표시 되어야 합니다.

- **표준 (유틸리티) 대화 상자:** 테마가 적용 되지 않습니다. 템플릿을 다시 만들지 마세요. 기본 컨트롤 스타일 기본값을 사용 합니다.

- **도구 창, 문서 편집기, 디자인 화면 및 테마가 적용 되는 대화 상자:** 색 서비스를 사용 하 여 특수 테마 모양을 사용 합니다.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> 스크롤 막대
 스크롤 막대는 코드 편집기에서와 같이 콘텐츠 정보를 사용 하 여 확대 되지 않는 한 [Windows 스크롤 막대에 대 한 일반적인 상호 작용 패턴](/windows/desktop/Controls/about-scroll-bars) 을 따라야 합니다.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> 입력 필드
 일반적인 상호 작용 동작의 경우 [텍스트 상자에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-text-boxes)을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 입력 필드의 스타일을 지정 하지 않아야 합니다. 컨트롤에 내장 된 기본 스타일을 사용 합니다.

- 테마가 지정 되는 입력 필드는 테마가 적용 되는 대화 상자 및 도구 창 에서만 사용 해야 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 읽기 전용 필드는 회색 (사용 안 함) 배경 이지만 기본 (활성) 전경입니다.

- 필수 필드에는 **\<Required>** 워터 마크로 포함 되어야 합니다. 드문 경우를 제외 하 고는 배경 색을 변경해 서는 안 됩니다.

- 오류 유효성 검사: [Visual Studio에 대 한 알림 및 진행률을](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) 참조 하세요.

- 입력 필드는 내용이 표시 되는 창의 너비에 맞지 않고 경로와 같이 긴 필드의 길이와 임의로 일치 하도록 크기를 조정 해야 합니다. 길이는 필드에 허용 되는 문자 수에 대 한 제한 사항을 사용자에 게 표시 하는 것일 수 있습니다.

     ![입력 필드 길이가 잘못 되었습니다. 이름이 길면 안 됩니다.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />입력 필드 길이가 잘못 되었습니다. 이름이 길면 안 됩니다.

     ![올바른 입력 필드 길이: 입력 필드는 예상 되는 콘텐츠의 적절 한 너비입니다.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />올바른 입력 필드 길이: 입력 필드는 예상 되는 콘텐츠의 적절 한 너비입니다.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> 콤보 상자 및 드롭다운 목록
일반적인 상호 작용 동작의 경우 [드롭다운 목록 및 콤보 상자에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-drop)을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 컨트롤의 템플릿을 다시 만들지 마세요. 컨트롤에 내장 된 기본 스타일을 사용 합니다.

- 테마가 적용 된 UI에서 콤보 상자와 드롭다운은 컨트롤에 대 한 표준 테마를 따릅니다.

#### <a name="layout"></a>Layout
콤보 상자와 드롭다운은 콘텐츠에 맞게 크기를 조정 해야 하며, 표시 되는 창의 너비에 맞지 않고 경로와 같이 긴 필드의 길이와 임의로 일치 하지 않습니다.

![잘못 됨: 드롭다운 너비가 너무 길어서 표시 되는 콘텐츠에 사용할 수 없습니다.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />잘못 됨: 드롭다운 너비가 너무 길어서 표시 되는 콘텐츠에 사용할 수 없습니다.

![수정: 드롭다운은 변환 증가를 허용 하기 위해 크기가 조정 되지만 불필요 한 긴 시간이 아닙니다.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />수정: 드롭다운은 변환 증가를 허용 하기 위해 크기가 조정 되지만 불필요 한 긴 시간이 아닙니다.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> 확인란
일반적인 상호 작용 동작의 경우 [확인란에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-check-boxes)을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일

- 유틸리티 대화 상자에서 컨트롤의 템플릿을 다시 만들지 마세요. 컨트롤에 내장 된 기본 스타일을 사용 합니다.

- 테마가 적용 된 UI에서 확인란은 컨트롤에 대 한 표준 테마를 따릅니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용

- 확인란을 사용 하 여 상호 작용 하면 대화 상자를 표시 하거나 다른 영역으로 이동 해서는 안 됩니다.

- 확인란을 첫 번째 텍스트 줄의 기준선과 맞춥니다.

     ![잘못 됨: 확인란은 텍스트를 중심으로 합니다.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />잘못 됨: 확인란은 텍스트를 중심으로 합니다.

     ![올바릅니다. 확인란은 텍스트의 첫 번째 줄에 정렬 됩니다.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />올바릅니다. 확인란은 텍스트의 첫 번째 줄에 정렬 됩니다.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> 라디오 단추
일반적인 상호 작용 동작의 경우 [라디오 단추에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-radio-buttons)을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서 라디오 단추에 스타일을 만들지 않습니다. 컨트롤에 내장 된 기본 스타일을 사용 합니다.

#### <a name="specialized-interactions"></a>특수 한 상호 작용
엄격한 레이아웃에서 그룹 구분을 유지 해야 하는 경우가 아니면 그룹 프레임을 사용 하 여 라디오 선택 항목을 묶을 필요는 없습니다.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> 프레임 그룹화
일반적인 상호 작용 동작의 경우 [그룹 프레임에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-group-boxes)을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일
유틸리티 대화 상자에서 그룹 프레임의 스타일을 만들지 않습니다. 컨트롤에 내장 된 기본 스타일을 사용 합니다.

#### <a name="layout"></a>Layout

- 엄격한 레이아웃에서 그룹 구분을 유지 해야 하는 경우가 아니면 그룹 프레임을 사용 하 여 라디오 선택 항목을 묶을 필요는 없습니다.

- 단일 컨트롤에는 그룹 프레임을 사용 하지 마십시오.

- 그룹 프레임 컨테이너 대신 수평선 규칙을 사용 하는 것이 허용 되는 경우도 있습니다.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> 텍스트 컨트롤

### <a name="static-text-fields"></a>정적 텍스트 필드

정적 텍스트 필드는 읽기 전용 정보를 제공 하며 사용자가 선택할 수 없습니다. 사용자가 클립보드에 복사할 수 있는 텍스트에는이를 사용 하지 마십시오. 그러나 읽기 전용 정적 텍스트는 상태 변경을 반영 하도록 변경 될 수 있습니다. 아래 예제에서 정보 그룹 아래의 출력 이름 정적 텍스트는 위의 루트 네임 스페이스 텍스트 상자에 적용 된 변경 내용을 반영 하도록 변경 됩니다.

정적 텍스트 정보를 표시 하는 방법에는 두 가지가 있습니다.

정적 텍스트는 그룹화 충돌이 없을 때 포함 없이 대화 상자에서 고유 하 게 사용할 수 있습니다. 상자의 추가 줄이 정말 필요한 지 여부를 결정 합니다. 예를 들어 아래와 같이 그룹 줄에서 만든 섹션 아래의 디렉터리 경로를 표시 합니다.

![텍스트 컨트롤의 정적 텍스트 정보](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />텍스트 컨트롤의 정적 텍스트 정보

다른 그룹화 된 영역이 있고 정보를 포함 하는 대화 상자에서 가독성을 향상 시킬 수 있으며, 섹션을 숨기 거 나 표시할 수 있는 경우 ( **속성 창** 설명 창) 또는 비슷한 UI를 사용 하려는 경우에는 정적 텍스트를 상자 안에 넣습니다. 이 그룹 상자는 단일 규칙 이며 다음과 같이 색을 지정 해야 합니다 `ButtonShadow` .

![속성 창의 정적 텍스트](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />속성 창의 정적 텍스트

### <a name="read-only-text-box"></a>읽기 전용 텍스트 상자

이렇게 하면 사용자가 필드 내의 텍스트를 선택할 수 있지만 편집할 수는 없습니다. 이러한 텍스트 상자는 채우기가 있는 일반적인 3 차원 선으로 테두리가 `ButtonShadow` 있습니다.

확인란을 선택/선택 취소 하거나 라디오 단추를 선택/선택 취소 하는 등의 방법으로 사용자가 연결 된 컨트롤을 변경 하면 텍스트 상자가 활성화 (편집 가능) 될 수 있습니다. 예를 들어 아래에 표시 된 **도구 &gt; 옵션** 페이지에서 **기본값 사용** 확인란의 선택을 취소 하면 **홈 페이지** 텍스트 상자가 활성화 됩니다.

![비활성 및 활성 상태를 표시 하는 읽기 전용 텍스트 상자](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />비활성 및 활성 상태를 표시 하는 읽기 전용 텍스트 상자

### <a name="using-text-in-dialogs"></a>대화 상자에 텍스트 사용

대화 상자의 텍스트에 대 한 주요 지침은 다음과 같습니다.

- 테마가 적용 되지 않은 대화 상자의 입력란, 목록 상자 및 프레임에 대 한 레이블은 동사를 사용 하 여 시작 하 고 첫 번째 단어에만 초기 대문자를 사용 하며 콜론으로 끝납니다.

    > 테마 대화 상자의 텍스트 컨트롤은 [Windows 바탕 화면 UX 지침](/windows/desktop/uxguide/top-violations) 을 따르고, 도움말 링크에서 물음표를 제외 하 고 끝 문장 부호를 사용 하지 않습니다.

- 확인란 및 옵션 단추의 레이블은 첫 번째 단어에 대 한 초기 자본만으로 시작 하 고 끝 문장 부호는 포함 하지 않습니다.

- 단추, 메뉴, 메뉴 항목 및 탭의 레이블은 각 단어에 대 한 초기 대문자 (제목 사례)가 있습니다.

- 레이블 용어는 다른 대화 상자의 유사한 레이블과 일치 해야 합니다.

- 가능 하면 작성기/편집기에서 구현 하기 위해 개발자에 게 전달 하기 전에 텍스트를 쓰거나 승인 합니다.

- 모든 컨트롤에는 탭 이동이 충분 한 특수 한 경우를 제외 하 고 레이블이 있어야 합니다.
적절 한 경우 도우미 텍스트를 사용 합니다.

### <a name="helper-text"></a>도우미 텍스트

사용자가 대화의 용도를 이해 하거나 수행할 작업을 나타내는 데 도움이 되는 대화 상자에 포함 되어 있습니다. 복잡 한 대화 상자를 피하는 데 필요한 경우에만 도우미 텍스트를 사용 해야 합니다. 도우미 텍스트의 두 가지 변형은 대화 상자 및 워터 마크입니다.

도우미 텍스트에 대 한 일반적인 위치를 따르고 새로운 영역을 선택적으로 소개 합니다. 도우미 텍스트에 대 한 일반적인 시나리오는 다음과 같습니다.

- 복합 대화 상자와 상호 작용 하는 방법에 대 한 추가 지침을 제공 하는 대화 상자의 도우미 텍스트입니다.

- 콘텐츠가 표시 되지 않는 이유를 설명 하는 빈 도구 창 또는 대화 상자의 워터 마크 텍스트입니다.

- **속성 창**아래와 같은 설명 창

- 빈 편집기의 워터 마크 텍스트를 사용 하 여 시작 하기 위해 수행 해야 하는 작업을 설명 합니다.

### <a name="dialog-helper-text"></a>대화 상자 도우미 텍스트

사용자 환경 디자이너는 도우미 텍스트가 적절 한 시기를 결정 하는 데 도움이 될 수 있습니다. 디자이너는 도우미 텍스트가 표시 되는 위치 및 일반 콘텐츠를 정의할 수 있습니다. 사용자 지원에서 실제 텍스트를 쓰거나 편집할 수 있습니다.

### <a name="watermarks"></a>워터마크

대화 상자는 약간 다른 워터 마크 지침을 활용 합니다. 대부분의 UI 요소 (레이블, 힌트 텍스트, 단추 및 기타 컨테이너 컨트롤 텍스트)를 사용 하 여 대화 상자가 표시 될 수 있기 때문에 특히 검정색으로 표시 되는 워터 마크는 진한 회색 (VSColor:)에서 더 잘 표시 `ButtonShadow` 됩니다. 일반적으로 워터 마크는 흰색 배경 (VSColor:)을 포함 하는 목록 상자와 같은 컨트롤 안에 표시 됩니다 `Window` .

- 텍스트가 진한 회색 (VSColor:)으로 나타납니다 `ButtonShadow` . 그러나 워터 마크가 중간 회색 또는 기타 컬러 (VSColor: `ButtonFace` ) 배경에 표시 되 고 가독성에 문제가 있는 경우에는 검정 텍스트 (vscolor:)로 이동 `WindowText` 합니다.

- 워터 마크는 왼쪽에서 가운데 맞춤 또는 플러시가 가능 합니다. 맞춤 결정을 내리는 경우 표준 디자인 규칙을 적용 합니다. 배경에서 워터 마크를 선택할 수 없습니다.

![워터 마크 텍스트 예](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />워터 마크 텍스트 예

### <a name="context-specific-dynamic-text"></a>컨텍스트별 (동적) 텍스트

동적 텍스트는 대화 상자 또는 모덜리스 UI의 두 가지 방법 중 하나 (동적 레이블 또는 동적 콘텐츠)로 사용할 수 있습니다.

- 동적 레이블: 동적 텍스트의 일반적인 용도는 설명 패널에서 오른쪽에 표시 되는 요소에 대 한 요소 및 속성의 목록을 포함 하는 대화 상자와 같이 선택한 항목에 대 한 자세한 정보를 제공 합니다. 속성 표의 레이블은 동적 일 수 있으므로 왼쪽에서 항목을 선택 하면 오른쪽 표에 해당 특정 항목에 대 한 정보가 표시 됩니다.

- 동적 텍스트: 이러한 방식으로 일반 정보를 표시 하는 대신 특정 정보를 표시 해야 하는 경우에 유용할 수 있지만 주의를 기울여야 합니다.

사용자에 게 정보를 복사 하는 기능을 제공 하려면 동적 텍스트가 읽기 전용 텍스트 필드에 있어야 합니다.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> 단추 및 하이퍼링크

### <a name="overview"></a>개요
단추 및 링크 컨트롤 (하이퍼링크)은 사용, 단어, 크기 조정 및 간격에 대 한 [하이퍼링크의 기본 Windows 바탕 화면 지침](/windows/desktop/uxguide/ctrl-links) 을 따라야 합니다.

### <a name="choosing-between-buttons-and-links"></a>단추와 링크 중에서 선택
일반적으로 작업에는 단추가 사용 되 고 하이퍼링크는 탐색용으로 예약 되어 있습니다. 모든 경우에 단추를 사용할 수 있지만 Visual Studio에서 링크 역할이 확장 되어 일부 조건에서 단추와 링크가 더 쉽게 교환할 수 있습니다.

명령 단추를 사용 하는 경우:

- 기본 명령

- 보조 명령인 경우에도 입력을 수집 하거나 선택 하는 데 사용 되는 창 표시

- 소거식 또는 취소할 때 작업

- 마법사 및 페이지 흐름 내의 약정 단추

도구 창의 명령 단추를 사용 하지 않거나 레이블에 세 개 이상의 단어가 필요한 경우에는입니다. 링크의 레이블은 더 길어질 수 있습니다.

 링크를 사용 하는 경우:

- 다른 창, 문서 또는 웹 페이지 탐색

- 작업 의도를 설명 하는 데 더 긴 레이블이나 짧은 문장이 필요한 상황

- 작업이 안전 하지 않거나 취소할 수 없는 경우 단추가 UI를 지나치게 넣을 수 있는 근접 한 공간

- 많은 명령이 있는 경우의 보조 명령 강조

#### <a name="examples"></a>예제
![상태 메시지 다음의 정보 표시줄에 사용 되는 명령 링크](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />상태 메시지 다음의 정보 표시줄에 사용 되는 명령 링크

![CodeLens 팝업에 사용된 링크](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens 팝업에 사용된 링크

![단추에 너무 많은 주의가 필요한 보조 명령에 사용 되는 링크](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />단추에 너무 많은 주의가 필요한 보조 명령에 사용 되는 링크

### <a name="common-buttons"></a>일반 단추

#### <a name="text"></a>텍스트
[UI 텍스트 및 용어](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)에서 작성 지침을 따릅니다.

#### <a name="visual-style"></a>비주얼 스타일

##### <a name="standard-unthemed"></a>표준 (테마가 적용 되지 않음)
Visual Studio의 단추 대부분은 유틸리티 대화 상자에 표시 되며 스타일을 지정 하면 안 됩니다. 운영 체제에서 지시한 대로 단추의 표준 모양을 반영 해야 합니다.

##### <a name="themed"></a>테마
경우에 따라 스타일이 지정 된 UI 내에서 단추를 사용할 수 있으며 이러한 단추는 적절 하 게 스타일을 지정 해야 합니다. 테마가 적용 한 컨트롤에 대 한 자세한 내용은 [대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 를 참조 하세요.

### <a name="special-buttons"></a>특수 단추

#### <a name="browse-buttons"></a>찾아보기 ... 단추
**[찾아보기 ...]** 단추는 그리드, 대화 상자, 도구 창 및 기타 모덜리스 UI 요소에 사용 됩니다. 사용자가 컨트롤에 값을 채우는 데 도움이 되는 선택기를 표시 합니다. 이 단추에는 길고 short의 두 가지 변형이 있습니다.

![[찾아보기 ...] 단추를 클릭 합니다.](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />[찾아보기 ...] 단추를 클릭 합니다.

![줄임표 전용 [...] 단추](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />줄임표 전용 [...] 단추

줄임표 (short) 전용 단추를 사용 하는 경우:

- 여러 필드가 검색을 허용 하는 경우와 같이 대화 상자에 긴 **[찾아보기 ...]** 단추가 있는 경우입니다. 이러한 상황에서 생성 되는 혼란 스러운 액세스 키를 방지 하려면 각에 대해 short **[...]** 단추를 사용 합니다 (**&Browse** 및 **B&** 같은 대화 상자에서).

- 근접 대화 상자에서 또는 긴 단추를 넣을 적절 한 위치가 없는 경우

- 단추가 표 형태 컨트롤에 표시 되 면이 고,

단추 사용에 대 한 지침:

- 액세스 키를 사용 하지 마세요. 키보드를 사용 하 여 액세스 하려면 사용자가 인접 컨트롤에서 탭 해야 합니다. 탭 순서에 따라 모든 찾아보기 단추가 채워질 필드 바로 다음에 오는 것을 확인할 수 있습니다. 첫 번째 마침표 아래에는 밑줄을 사용 하지 마십시오.

- Microsoft Active Accessibility (MSAA) **Name** 속성을 **찾아가기 ...** (줄임표 포함)로 설정 하 여 화면 읽기 프로그램이 "점-점" 또는 "기간-기간"이 아닌 "찾아보기"로 읽도록 합니다. 관리 되는 컨트롤의 경우이는 **AccessibleName** 속성을 설정 하는 것입니다.

- 찾아보기 동작을 제외한 모든 항목에는 줄임표 **[...]** 단추를 사용 하지 마십시오. 예를 들어 **[새 ...]** 단추가 필요 하지만 텍스트를 위한 공간이 충분 하지 않은 경우 대화 상자를 다시 디자인 해야 합니다.

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
![크기 조정 [찾아보기 ...] 단추: 표준 버전은 75x23 픽셀, 짧은 버전은 26x23 픽셀](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />[찾아보기...] 크기 조정 단추

![간격 [찾아보기 ...] 단추: 관련 컨트롤과 표준 찾아보기 단추 7 픽셀 사이의 간격, 관련 컨트롤과 짧은 찾아보기 단추 5 픽셀 사이의 간격](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />[찾아보기...] 간격 조정 단추

#### <a name="graphical-buttons"></a>그래픽 단추
일부 단추는 항상 그래픽 이미지를 사용 하 고 공간을 절약 하 고 지역화 문제를 방지 하는 텍스트를 포함 하지 않아야 합니다. 이러한 필드는 필드 선택기 및 기타 정렬 가능한 목록에서 자주 사용 됩니다.

> [!NOTE]
> 사용자는 이러한 단추 (선택 키 없음)로 이동 하 여 적절 한 순서로 배치할 수 있습니다. `name`단추의 속성을 화면 판독기가 단추 작업을 올바르게 해석 하기 위해 수행 하는 동작에 매핑합니다.

| 함수 | 단추 |
| --- | --- |
| 추가 | ![그래픽 "추가" 단추](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| 제거 | ![그래픽 "제거" 단추](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| 모두 추가 | ![그래픽 "모두 추가" 단추](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| 모두 제거 | ![그래픽 "모두 제거" 단추](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| 위로 이동 | ![그래픽 "위로 이동" 단추](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| 아래로 이동 | ![그래픽 "아래로 이동" 단추](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| 삭제 | ![그래픽 "삭제" 단추](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>크기 조정 및 간격
그래픽 단추의 크기 조정은 **[찾아보기 ...]** 단추 (26x23 픽셀)의 약식 버전과 동일 합니다.

![투명 한 색을 표시 하거나 표시 하지 않는 단추의 그래픽 이미지 모양](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />투명 한 색을 표시 하거나 표시 하지 않는 단추의 그래픽 이미지 모양

### <a name="hyperlinks"></a>하이퍼링크
하이퍼링크는 도움말 항목, 모달 대화 상자 또는 마법사 열기와 같은 탐색 기반 작업에 적합 합니다. 명령에 하이퍼링크를 사용 하는 경우에는 항상 UI에 대 한 눈에 띄는 변경 내용이 표시 되어야 합니다. 일반적으로 작업 (예: 저장, 취소 및 삭제)에 커밋하는 작업은 단추를 사용 하 여 보다 효율적으로 전달 됩니다.

#### <a name="writing-style"></a>쓰기 스타일
[사용자 인터페이스 텍스트에 대 한 Windows 바탕 화면 지침](/windows/desktop/uxguide/text-ui)을 따릅니다. "자세한 정보"를 사용 하지 마세요. "에 대 한 자세한 정보" 또는 "이에 대 한 도움 받기" 구문 대신, 문구는 도움말 콘텐츠에서 답변 한 주요 질문을 기준으로 텍스트를 연결 합니다. 예를 들어 "**어떻게 할까요? 서버 탐색기에 서버를 추가 하 시겠습니까?**"

#### <a name="visual-style"></a>비주얼 스타일

- 하이퍼링크 [는 항상 VSColor 서비스를](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)사용 해야 합니다. 하이퍼링크의 스타일이 올바르게 지정 되지 않은 경우 활성 상태 이거나 방문한 후 다른 색을 표시 하는 경우 빨간색으로 깜박입니다.

- 워터 마크와 같이 전체 문장 내에서 링크를 문장 조각으로 지정 하지 않는 한 컨트롤의 표시 상태에 밑줄을 포함 하지 않습니다.

- 호버에는 밑줄이 표시 되지 않습니다. 대신 링크가 활성화 된 사용자에 대 한 피드백은 약간의 색 변경 및 적절 한 링크 커서입니다.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> 트리 뷰

트리 뷰는 복합 목록을 부모-자식 그룹으로 구성 하는 방법을 제공 합니다. 사용자는 부모 그룹을 확장 하거나 축소 하 여 기본 자식 항목을 표시 하거나 숨길 수 있습니다. 트리 뷰 내의 각 항목을 선택 하 여 추가 작업을 제공할 수 있습니다.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> 트리 뷰 비주얼 스타일

#### <a name="expanders"></a>확장 기가
트리 뷰 컨트롤은 Windows 및 Visual Studio에서 사용 하는 확장기 디자인을 준수 해야 합니다. 각 노드는 확장 컨트롤을 사용 하 여 기본 항목을 표시 하거나 숨깁니다. 확장기 컨트롤을 사용 하면 Windows 및 Visual Studio 내에서 다른 트리 보기를 발견할 수 있는 사용자에 게 일관성이 제공 됩니다.

![올바릅니다. 확장 컨트롤을 사용 하는 트리 뷰 노드의 적절 한 스타일](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />올바릅니다. 확장 컨트롤을 사용 하는 트리 뷰 노드의 적절 한 스타일

![잘못 됨: 트리 뷰 노드의 스타일이 잘못 되었습니다.](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />잘못 됨: 트리 뷰 노드의 스타일이 잘못 되었습니다.

#### <a name="selection"></a>선택
트리 뷰 내에서 노드를 선택 하면 강조 표시는 tree view 컨트롤의 전체 너비로 확장 됩니다. 이렇게 하면 사용자가 선택한 항목을 명확 하 게 식별할 수 있습니다. 선택 색은 현재 Visual Studio 테마를 반영 해야 합니다.

![수정: 선택한 노드를 강조 표시 하 여 tree view 컨트롤의 전체 너비에 맞춥니다.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />수정: 선택한 노드를 강조 표시 하 여 tree view 컨트롤의 전체 너비에 맞춥니다.

![잘못 됨: 선택한 노드의 강조 표시가 tree view 컨트롤의 전체 너비에 맞지 않습니다.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />잘못 됨: 선택한 노드의 강조 표시가 tree view 컨트롤의 전체 너비에 맞지 않습니다.

#### <a name="icons"></a>아이콘
항목 간의 차이를 시각적으로 식별 하는 데 도움이 되는 경우에만 트리 뷰 컨트롤에 아이콘을 사용 해야 합니다. 일반적으로 아이콘은 요소 유형을 구분 하기 위해 아이콘이 정보를 전달 하는 유형이 다른 목록 에서만 사용 해야 합니다. 아이콘을 사용 하는 경우에 따라 아이콘을 사용 하는 것이 보통 소음으로 표시 될 수 있으므로 피해 야 합니다. 이 경우 그룹 아이콘 (부모)은 그 안에 있는 항목의 형식을 전달할 수 있습니다. 아이콘이 동적이 고 상태를 나타내는 데 사용 되는 경우이 규칙의 예외입니다.

#### <a name="scroll-bars"></a>스크롤 막대
콘텐츠가 tree view 컨트롤 내에 있는 경우 스크롤 막대는 항상 숨겨야 합니다. 스크롤 막대를 숨기 거 나 스크롤 가능한 창에서 반투명 하 게 만들거나, 트리 뷰를 포함 하는 창에 포커스가 있거나 트리 뷰 자체를 가리킬 때 표시 되는 스크롤 막대를 사용할 수 있습니다.

![내용이 tree view 컨트롤의 제한을 초과 하 여 세로 및 가로 스크롤 막대가 모두 표시 됩니다.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />내용이 tree view 컨트롤의 제한을 초과 하 여 세로 및 가로 스크롤 막대가 모두 표시 됩니다.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> 트리 뷰 상호 작용

#### <a name="context-menus"></a>상황에 맞는 메뉴
트리 뷰 노드는 상황에 맞는 메뉴의 하위 메뉴 옵션을 표시할 수 있습니다. 일반적으로이는 사용자가 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 항목을 사용 하 여 Windows 키보드에서 메뉴 키를 누를 때 발생 합니다. 노드가 포커스를 획득 하 고 선택 하는 것이 중요 합니다. 이렇게 하면 하위 메뉴가 속한 항목을 사용자가 식별할 수 있습니다.

![상황에 맞는 메뉴를 생성 하는 항목은 선택 된 항목을 사용자에 게 알리기 위해 포커스를 얻습니다.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />상황에 맞는 메뉴를 생성 하는 항목은 선택 된 항목을 사용자에 게 알리기 위해 포커스를 얻습니다.

#### <a name="keyboard"></a>Keyboard
트리 뷰에서는 항목을 선택 하 고 키보드를 사용 하 여 노드를 확장/축소할 수 있는 기능을 제공 해야 합니다. 이렇게 하면 탐색이 접근성 요구 사항을 충족 합니다.

##### <a name="tree-view-control"></a>트리 뷰 컨트롤
Visual Studio 트리 컨트롤은 일반적인 키보드 탐색을 따라야 합니다.

- **위쪽 화살표:** 트리를 위로 이동 하 여 항목 선택

- **아래쪽 화살표:** 트리를 아래로 이동 하 여 항목 선택

- **오른쪽 화살표:** 트리의 노드 확장

- **왼쪽 화살표:** 트리의 노드 축소

- **키 입력:** 선택한 항목 시작, 로드, 실행

##### <a name="trid-tree-view-and-grid-view"></a>Trid (트리 뷰 및 그리드 뷰)
Trid 컨트롤은 그리드 내에서 트리 뷰를 포함 하는 복잡 한 컨트롤입니다. 트리를 확장 하 고 축소 하 고 탐색 하는 것은 트리 뷰와 동일한 키보드 명령을 준수 해야 하며 다음과 같이 추가 됩니다.

- **오른쪽 화살표:** 노드를 확장 합니다. 노드가 확장 된 후에는 오른쪽의 가장 가까운 열로 계속 이동 해야 합니다. 행의 끝에서 탐색을 중지 해야 합니다.

- **탭:** 오른쪽의 가장 가까운 셀로 이동 합니다.  행의 끝에서 탐색은 다음 행으로 계속 됩니다.

- **Shift + Tab:** 왼쪽의 가장 가까운 셀로 이동 합니다.  행의 시작 부분에서 탐색은 이전 행의 맨 오른쪽 셀로 계속 됩니다.

![Visual Studio의 trid 컨트롤](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Visual Studio의 trid 컨트롤
