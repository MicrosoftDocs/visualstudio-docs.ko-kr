---
title: Visual Studio에 대 한 공유 색 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699938"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio에 대 한 공유 색
일반적인 Visual Studio 셸 요소를 사용 하는 UI를 디자인 하거나 인터페이스 요소를 유사한 기능과 일치 시키는 경우 패키지 정의 파일에서 기존 토큰 이름을 사용 하 여 색을 선택 하 고 할당 합니다. 이렇게 하면 UI가 전체 Visual Studio 환경과 일관성 있게 유지되며 테마를 추가하거나 업데이트할 경우 자동으로 업데이트됩니다.

이 문서에서는 유사한 UI를 빌드할 때 참조할 수 있는 일반적인 UI 요소 및 사용되는 토큰 이름을 설명합니다. 이러한 색 토큰에 액세스하는 방법에 대한 자세한 내용은 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)를 참조하세요.

토큰 이름을 올바르게 사용해야 합니다.

- **색 자체가 아니라 함수에 따라 토큰 이름을 사용합니다.** 일반적인 공유 색은 특정 인터페이스 요소와 연결되며 동일하거나 유사한 기능에만 사용해야 합니다. 예를 들어 단순히 색을 좋아한다고 해서 누른 콤보 상자의 색을 회전 진행률 애니메이션에 다시 사용하지 마세요. 콤보 상자와 애니메이션의 기능은 서로 다르며, 콤보 상자와 연결 된 색이 변경 되 면 애니메이션 요소에 적절 한 색이 아닐 수 있습니다. 색을 일관성 있게 사용하면 사용자를 올바른 방향으로 인도하고 혼동을 방지하는 데 도움이 됩니다.

- **배경색과 텍스트 색을 올바른 조합으로 사용합니다.** 텍스트와 함께 사용되는 배경색에는 연결된 텍스트 색이 있습니다. 해당 배경에 지정된 색이 아닌 텍스트 색을 사용하지 마세요. 연결 된 텍스트 색이 없는 경우 텍스트를 표시 하려는 화면에 해당 배경색을 사용 하지 마세요. 텍스트 색과 배경색의 다른 조합은 읽을 수 없는 인터페이스를 발생 시킬 수 있습니다.

- **해당 위치에 적합한 컨트롤 색을 사용합니다.** 특정 상태에서는 일부 Visual Studio 컨트롤에 별도의 테두리와 배경색이 없습니다. 대신, 배경 화면에서 해당 색을 선택합니다. 항상 컨트롤을 배치할 위치에 적합한 토큰 이름을 사용해야 합니다.

> [!IMPORTANT]
> "시작 페이지" 또는 "Cider" 범주에 있는 토큰을 사용 하지 마세요.

## <a name="common-shared-controls"></a>공통 공유 컨트롤

기능에서 표준 Visual Studio 명령 모음을 사용 하는 경우 스타일 지정 된 셸 컨트롤에 액세스할 수 있습니다. 이러한 공용 컨트롤의 템플릿을 다시 만들면 안 됩니다. 그러나 사용자 지정 명령 모음을 빌드해야 하는 경우 사용자 지정 컨트롤도 빌드해야 할 수 있습니다. 이 경우 다음 컨트롤에 대해 각각 올바른 토큰 이름을 사용하여 UI를 Visual Studio의 나머지 부분과 일치시켜야 합니다.

### <a name="button-controls"></a>단추 컨트롤

![단추 컨트롤 검토](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... Visual Studio 테마 (밝게, 어둡게, 파랑 또는 시스템 고대비 테마)와 통합 하려는 문서 웰의 단추입니다. | ... Visual Studio 테마에 속하지 않는 사용자 지정 배경에 표시 되는 단추 |

**단추: 표준 상태**

![표준 단추](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03")<br />표준 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.Button` |
| 단추 테두리 | `CommonControls.ButtonBorder` |

**단추: 기본 상태**

![기본 단추](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03")<br />기본 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.ButtonDefault` |
| 단추 테두리 | `CommonControls.ButtonBorderDefault` |

**단추: 사용 안 함 상태**

![사용 안 함 단추](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03 사용 안 함")<br />사용 안 함 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.ButtonDisabled` |
| 단추 테두리 | `CommonControls.ButtonBorderDisabled` |

**Button: 가리키기 상태**

![단추 가리키기](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03")<br />단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.ButtonHover` |
| 단추 테두리 | `CommonControls.ButtonBorderHover` |

**단추: 누름 상태**

![누른 단추](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03")<br />누른 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.ButtonPressed` |
| 단추 테두리 | `CommonControls.ButtonBorderPressed` |

**Button: 포커스가 있는 상태**

![포커스가 있는 단추](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03")<br />포커스가 있는 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 단추 | `CommonControls.ButtonFocused` |
| 단추 테두리 | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>확인란 컨트롤
![확인란 (검토)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />확인란 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 문서 웰 내에 포함 된 확인란 컨트롤 | ... 확인란 컨트롤이 아닌 모든 UI |

**확인란: 기본 상태**

![확인란](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />기본 확인란

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackground` |
| 테두리 | `CommonControls.CheckBoxBorder` |
| 텍스트 | `CommonControls.CheckBoxText` |
| 문자 모양 | `CommonControls.CheckBoxGlyph` |

**확인란: 사용 안 함 상태**

![사용 안 함 확인란](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />사용 안 함 확인란

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackgroundDisabled` |
| 테두리 | `CommonControls.CheckBoxBorderDisabled` |
| 텍스트 | `CommonControls.CheckBoxTextDisabled` |
| 문자 모양 | `CommonControls.CheckBoxGlyphDisabled` |

**확인란: 가리키기 상태**

 ![확인란 가리키기](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />확인란 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackgroundHover` |
| 테두리 | `CommonControls.CheckBoxBorderHover` |
| 텍스트 | `CommonControls.CheckBoxTextHover` |
| 문자 모양 | `CommonControls.CheckBoxGlyphHover` |

**확인란: 누름 상태**

![누름 확인란](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />누름 확인란

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackgroundPressed` |
| 테두리 | `CommonControls.CheckBoxBorderPressed` |
| 텍스트 | `CommonControls.CheckBoxTextPressed` |
| 문자 모양 | `CommonControls.CheckBoxGlyphPressed` |

**확인란: 포커스가 있는 상태**

![포커스가 있는 확인란](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />포커스가 있는 확인란

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackgroundFocused` |
| 테두리 | `CommonControls.CheckBoxBorderFocused` |
| 텍스트 | `CommonControls.CheckBoxTextFocused` |
| 문자 모양 | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>드롭다운 및 콤보 상자
![드롭다운/콤보 상자 (검토)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />드롭다운/콤보 상자 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 문서 웰의 드롭다운 및 콤보 상자 | ... 드롭다운 또는 콤보 상자가 아닌 모든 UI |
| | ... 명령 모음 [드롭다운](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) 또는 [콤보 상자의](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)경우입니다. |

**드롭다운 및 콤보 상자: 기본 상태**

![기본 드롭다운/콤보 상자](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />기본 드롭다운/콤보 상자

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxBackground` |
| 테두리 | `CommonControls.ComboBoxBorder` |
| 텍스트 | `CommonControls.ComboBoxText` |
| 구분 기호 | `CommonControls.ComboBoxSeparator` |
| 문자 모양 | `CommonControls.ComboBoxGlyph` |
| 문자 모양 배경 | `CommonControls.ComboBoxGlyphBackground` |

**드롭다운 및 콤보 상자: 비활성화 상태**

![사용 안 함 드롭다운/콤보 상자](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />사용 안 함 드롭다운/콤보 상자

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxBackgroundDisabled` |
| 테두리 | `CommonControls.ComboBoxBorderDisabled` |
| 텍스트 | `CommonControls.ComboBoxTextDisabled` |
| 구분 기호 | `CommonControls.ComboBoxSeparatorDisabled` |
| 문자 모양 | `CommonControls.ComboBoxGlyphDisabled` |
| 문자 모양 배경 | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**드롭다운 및 콤보 상자: 가리키기 상태**

![드롭다운/콤보 상자 가리키기](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />드롭다운/콤보 상자 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxBackgroundHover` |
| 테두리 | `CommonControls.ComboBoxBorderHover` |
| 텍스트 | `CommonControls.ComboBoxTextHover` |
| 구분 기호 | `CommonControls.ComboBoxSeparatorHover` |
| 문자 모양 | `CommonControls.ComboBoxGlyphHover` |
| 문자 모양 배경 | `CommonControls.ComboBoxGlyphBackgroundHover` |

**드롭다운 및 콤보 상자: 누름 상태**

![누름 드롭다운/콤보 상자](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />누름 드롭다운/콤보 상자

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxBackgroundPressed` |
| 테두리 | `CommonControls.ComboBoxBorderPressed` |
| 텍스트 | `CommonControls.ComboBoxTextPressed` |
| 구분 기호 | `CommonControls.ComboBoxSeparatorPressed` |
| 문자 모양 | `CommonControls.ComboBoxGlyphPressed` |
| 문자 모양 배경 | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**드롭다운 및 콤보 상자 목록 항목 보기: 누름 상태**

 ![드롭다운/콤보 상자 누름 목록 항목 보기](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />드롭다운/콤보 상자 누름 목록 항목 보기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| 테두리 | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| 항목 텍스트 | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| 배경 그림자 | `CommonControls.ComboBoxListBackgroundShadow` |

**드롭다운 및 콤보 상자: 포커스가 있는 상태**

![포커스가 있는 드롭다운/콤보 상자](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />포커스가 있는 드롭다운/콤보 상자

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.ComboBoxBackgroundFocused` |
| 테두리 | `CommonControls.ComboBoxBorderFocused` |
| 텍스트 | `CommonControls.ComboBoxTextFocused` |
| 구분 기호 | `CommonControls.ComboBoxSeparatorFocused` |
| 문자 모양 | `CommonControls.ComboBoxGlyphFocused` |
| 문자 모양 배경 | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**드롭다운 및 콤보 상자: 텍스트 입력 선택**

![드롭다운/콤보 상자 텍스트 입력 선택](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />드롭다운/콤보 상자 텍스트 입력 선택

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 강조 표시 | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>표 형식 데이터(그리드) 컨트롤
표 형식 데이터 컨트롤은 그리드 컨트롤이라고도 하며, 여러 열에 많은 양의 데이터를 표시하는 데 사용할 수 있는 Visual Studio의 공용 컨트롤입니다. 표준 표 형식 데이터 컨트롤은 오류 목록 도구 창, IntelliTrace 보고서, 메모리 힙 보기 등 Visual Studio 내의 여러 위치에서 찾을 수 있습니다. 항상 제공된 표준 표 형식 데이터 컨트롤을 사용합니다. 드물긴 하지만 표준 표 형식 데이터 컨트롤에 액세스할 수 없는 경우도 있습니다. 이러한 경우 다음 토큰 이름을 사용하여 Visual Studio의 다른 표 형식 데이터 컨트롤과 UI의 일관성을 유지합니다.

![테이블 형식 데이터/표 형태 컨트롤 (검토)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />테이블 형식 데이터/표 형태 컨트롤 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 표 형식 또는 그리드 컨트롤 | ... 테이블 형식 또는 그리드 컨트롤이 아닌 모든 UI |

#### <a name="column-headers"></a>열 머리글
열 머리글은 배경, 테두리, 제목 텍스트 및 그리드가 해당 열을 기준으로 정렬된 경우 일반적으로 사용되는 선택적 문자 모양으로 구성됩니다.

**열 머리글: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Header.Default` |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 전경(문자 모양) | `Header.Glyph` |
| 테두리 | `Header.SeparatorLine` |

**열 머리글: 가리키기 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Header.MouseOver` |
| 전경(텍스트) | `Environment.CommandBarTextHover` |
| 전경(문자 모양) | `Header.MouseOverGlyph` |
| 테두리 | `Header.SeparatorLine` |

**열 머리글: 눌린 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `CommonControls.CheckBoxBackgroundPressed` |
| 전경(텍스트) | `CommonControls.CheckBoxBorderPressed` |
| 전경(문자 모양) | `CommonControls.CheckBoxTextPressed` |
| 테두리 | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>목록 뷰 항목
 목록 뷰 항목은 배경과 콘텐츠로 구성됩니다. 콘텐츠는 텍스트, 아이콘 또는 둘 다일 수 있습니다.

**목록 보기 항목: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 투명 |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 테두리 | 없음 |

**목록 보기 항목: 활성 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemActive` |
| 전경(텍스트) | `TreeView.SelectedItemActiveText` |
| 테두리 | 없음 |

**목록 보기 항목: 비활성 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemInactive` |
| 전경(텍스트) | `TreeView.SelectedItemInactiveText` |
| 테두리 | 없음 |

### <a name="ui-text"></a>UI 텍스트

#### <a name="instructional-text"></a>지침 텍스트
지침 텍스트는 대화 상자 또는 문서 페이지에서 수행할 작업에 대 한 중요 한 설명을 제공 합니다.

![기본 지침 텍스트](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />기본 지침 텍스트

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>보조 지침 텍스트
텍스트와 컨트롤이 많은 문서 페이지에서 일부 지침 텍스트는 다른 색 값을 사용 합니다. 이를 통해 가장 중요 한 정보를 전달 하 고 UI 요소의 전체 밀도를 줄일 수 있습니다. 힌트 텍스트에 대해서는 아래 섹션을 참조 하세요.

![보조 지침 텍스트](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />보조 지침 텍스트

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>힌트 텍스트
힌트 텍스트는 빈 컨트롤, 컨트롤 아래 또는 빈 문서 화면에 표시 되어 사용자가 다음에 수행할 작업을 표시 합니다. 창 또는 컨트롤 배경과 함께 힌트 텍스트를 사용할 수 있습니다.

**기본 힌트 텍스트**

![기본 힌트 텍스트](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />기본 힌트 텍스트

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Environment.ControlEditHintText` |

**필수 힌트 텍스트**

![필수 힌트 텍스트](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />필수 힌트 텍스트

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Environment.ControlRequiredHintText` |
| 배경 | `Environment.ControlRequiredBackground` |

**검색 상자 컨트롤 텍스트**

> 검색 컨트롤과 관련 된 다른 색 토큰은 [검색 상자](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) 를 참조 하세요.

![검색 상자 컨트롤 텍스트](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />검색 상자 컨트롤 텍스트

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
하이퍼링크는 전경/배경 쌍이 없는 컨트롤입니다. 모든 경우에는 진한 회색 및 흰색 배경에 올바르게 표시 되는 전경 하이퍼링크 색을 사용 합니다. Hyperlink 컨트롤에 대 한 색 토큰을 사용 하지 않는 경우 "누름"의 기본 시스템 색이 표시 되며,이는 빨간색으로 깜박입니다. 이는 컨트롤이 올바른 환경 색 토큰을 사용 하지 않는다는 신호입니다.

![Hyperlink (검토)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hyperlink (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 하이퍼링크를 만들어야 하는 경우 | ... 하이퍼링크가 아닌 모든 항목 |

**하이퍼링크: 기본 상태**

![기본 하이퍼링크](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />기본 하이퍼링크

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경(텍스트) | `Environment.PanelHyperlink` |

**Hyperlink: 가리키기 상태**

![하이퍼링크 가리키기](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />하이퍼링크 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경(텍스트) | `Environment.PanelHyperlinkHover` |

**하이퍼링크: 누름 상태**

![누른 하이퍼링크](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />누른 하이퍼링크

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경(텍스트) | `Environment.PanelHyperlinkPressed` |

**Hyperlink: disabled 상태**

![비활성화 된 하이퍼링크](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />비활성화 된 하이퍼링크

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경(텍스트) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>정보 표시줄
정보 표시줄은 지정된 컨텍스트에 대한 자세한 정보를 제공하는 데 사용되며, 항상 문서 창이나 도구 창의 맨 위에 나타납니다.

![정보 표시줄 (검토)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />정보 표시줄 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 정보 표시줄를 만들 때. | ... 정보 표시줄과 유사 하지 않은 UI 요소 |

**정보 표시줄: 기본 상태**

![기본 정보 표시줄](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />기본 정보 표시줄

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.InfoBarBackground` |
| 전경(텍스트) | `InfoBar.InfoBar` |
| 테두리 | `InfoBar.InfoBarBorder` |

**상태 표시줄 닫기 ( &times; ) 단추: 기본 상태**

![기본 정보 표시줄 닫기 ( &times; ) 단추](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />기본 정보 표시줄 닫기 ( &times; ) 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.CloseButton` |
| 테두리 | `InfoBar.CloseButtonBorder` |
| 문자 모양 | `InfoBar.CloseButtonGlyph` |

**상태 표시줄 닫기 ( &times; ) 단추: 가리키기 상태**

![정보 표시줄 닫기 ( &times; ) 단추 가리키기](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />정보 표시줄 닫기 ( &times; ) 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.CloseButtonHover` |
| 테두리 | `InfoBar.CloseButtonHoverBorder` |
| 문자 모양 | `InfoBar.CloseButtonHoverGlyph` |

**상태 표시줄 닫기 ( &times; ) 단추: 누름 상태**

![누름 정보 표시줄 닫기 ( &times; ) 단추](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />누름 정보 표시줄 닫기 ( &times; ) 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.CloseButtonDown` |
| 테두리 | `InfoBar.CloseButtonDownBorder` |
| 문자 모양 | `InfoBar.CloseButtonDownGlyph` |

**정보 표시줄 하이퍼링크 단추: 기본 상태**

![기본 정보 표시줄 하이퍼링크 단추](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />기본 정보 표시줄 하이퍼링크 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `InfoBar.Hyperlink` |

**정보 표시줄 하이퍼링크 단추: 가리키기 상태**

![정보 표시줄 하이퍼링크 단추 가리키기](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />정보 표시줄 하이퍼링크 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Infobar.HyperlinkMouseOver`<br />(밑줄 포함) |

**정보 표시줄 하이퍼링크 단추: 누름 상태**

![누름 정보 표시줄 하이퍼링크 단추](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />누름 정보 표시줄 하이퍼링크 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Infobar.HyperlinkMouseDown`<br />(밑줄 포함) |

**정보 표시줄 인라인 하이퍼링크 (문장 내): 기본 상태**

![기본 인라인 정보 표시줄 하이퍼링크 단추](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />기본 인라인 정보 표시줄 하이퍼링크 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `InfoBar.Hyperlink` |

**정보 표시줄 인라인 하이퍼링크 (문장 내): 가리키기 상태**

![정보 표시줄 인라인 하이퍼링크 단추 가리키기](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />정보 표시줄 인라인 하이퍼링크 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Infobar.HyperlinkMouseOver`<br />(밑줄 포함) |

**정보 표시줄 인라인 하이퍼링크 (문장 내): 누름 상태**

![누름 정보 표시줄 인라인 하이퍼링크 단추](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />누름 정보 표시줄 인라인 하이퍼링크 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경 (텍스트) | `Infobar.HyperlinkMouseDown`<br />(밑줄 포함) |

**정보 표시줄 단추: 기본 상태**

![기본 정보 표시줄 단추](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />기본 정보 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.Button` |
| 전경 (텍스트) | `InfoBar.Button` |
| 테두리 | `InfoBar.ButtonBorder` |

**정보 표시줄 단추: 가리키기 상태**

![정보 표시줄 단추 가리키기](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />정보 표시줄 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.ButtonMouseOver` |
| 전경 (텍스트) | `InfoBar.ButtonMouseOver` |
| 테두리 | `InfoBar.ButtonMouseOverBorder` |

**정보 표시줄 단추: 누름 상태**

![누름 정보 표시줄 단추](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />누름 정보 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.ButtonMouseDown` |
| 전경 (텍스트) | `InfoBar.ButtonMouseDown` |
| 테두리 | `InfoBar.ButtonMouseDownBorder` |

**정보 표시줄 단추: 사용 안 함 상태**

![사용 안 함 정보 표시줄 단추](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />사용 안 함 정보 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.ButtonDisabled` |
| 전경 (텍스트) | `InfoBar.ButtonDisabled` |
| 테두리 | `InfoBar.ButtonDisabledBorder` |

**정보 표시줄 단추: 포커스가 있는 상태**

![포커스가 있는 정보 표시줄 단추](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />포커스가 있는 정보 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `InfoBar.ButtonFocus` |
| 전경 (텍스트) | `InfoBar.ButtonFocus` |
| 테두리 | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>스크롤 막대
스크롤 막대는 Visual Studio 환경에서 스타일이 지정 되며 테마를 적용할 필요가 없습니다. 그러나 UI가 항상 Visual Studio 환경의이 부분과 일관 되 게 나타나도록 스크롤 막대에 사용 된 색을 활용할 수 있습니다.

![스크롤 막대 (검토)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />스크롤 막대 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... Visual Studio 스크롤 막대와 일치 시키려는 UI를 만드는 경우 | ... 항상 스크롤 막대 UI와 일치 시 키 지 않으려는 모든 항목 |

**스크롤 막대: 기본 상태**

![기본 스크롤 막대](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />기본 스크롤 막대

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 스크롤 막대 | `Environment.ScrollBarBackground` |
| 전경(Thumb) | `Environment.ScrollBarThumbBackground` |

**스크롤 막대: 가리키기 상태**

![스크롤 막대 가리키기](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />스크롤 막대 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 스크롤 막대 | `Environment.ScrollBarBackground` |
| 전경(Thumb) | `Environment.ScrollBarThumbMouseOverBackground` |

*스크롤 막대: 누름 상태**

![누른 스크롤 막대](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />누른 스크롤 막대

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 스크롤 막대 | `Environment.ScrollBarBackground` |
| 전경(Thumb) | `Environment.ScrollBarThumbPressedBackground` |

**스크롤 막대 화살표: 기본 상태**

![기본 스크롤 막대 화살표](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />기본 스크롤 막대 화살표

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ScrollBarArrowBackground`<br />(스크롤 막대와 동일한 색으로 설정 됨) |
| 전경(문자 모양) | `Environment.ScrollBarArrowGlyph` |

**스크롤 막대 화살표: 가리키기 상태**

![스크롤 막대 화살표 가리키기](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />스크롤 막대 화살표 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ScrollBarArrowMouseOverBackground`<br />(스크롤 막대와 동일한 색으로 설정 됨) |
| 전경(문자 모양) | `Environment.ScrollBarArrowGlyphMouseOver` |

**스크롤 막대 화살표: 누름 상태**

![누른 스크롤 막대 화살표](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />누른 스크롤 막대 화살표

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ScrollBarArrowPressedBackground`<br />(스크롤 막대와 동일한 색으로 설정 됨) |
| 전경(문자 모양) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>검색 상자
가능한 경우 항상 Visual Studio 환경에서 제공하는 공용 검색 컨트롤을 사용합니다. 검색 상자 색은 입력 필드, 실행 단추, 드롭다운 단추 및 드롭다운 메뉴에 대한 토큰 이름이 포함된 **ShellColors.pkgdef** 파일의 "SearchControl" 범주에 있습니다.

검색 상자는 여러 상태 중 하나일 수 있으며, 일부 상태는 함께 사용할 수 없습니다.

- "포커스 있음" 또는 "포커스 없음"은 텍스트 상자에 커서가 있는지 여부를 나타냅니다.

- "활성" 또는 "비활성"은 사용자가 텍스트 상자에 검색 쿼리를 입력했는지 여부를 나타냅니다.

- "가리키기"는 사용자가 마우스로 검색 상자를 가리켰음을 나타냅니다(이 상태는 다른 모든 상태를 재정의함).

- "사용 안 함"은 검색 기능이 현재 컨텍스트에 대해 꺼져 있음을 나타냅니다.

![검색 상자 (검토)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />검색 상자 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 검색 상자를 디자인 하는 경우 | ... 검색 상자가 아닌 모든 항목 |
| | ... 검색 상자 UI와 항상 일치 시 키 지 않으려는 모든 항목 |

**포커스가 있는 검색 입력 필드**

![포커스가 있는 검색 입력 필드](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />포커스가 있는 검색 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.FocusedBackground` |
| 전경(텍스트) | `SearchControl.FocusedBackground` |
| 테두리 | `SearchControl.FocusedBorder` |
| 구분 기호 | `SearchControl.FocusedDropDownSeparator` |

**포커스가 없는, 활성 검색 입력 필드**

![포커스가 없는 검색어 입력 필드](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />포커스가 없는, 활성 검색 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.SearchActiveBackground` |
| 전경(텍스트) | `SearchControl.SearchActiveBackground` |
| 테두리 | `SearchControl.UnfocusedBorder` |
| 구분 기호 | `SearchControl.DropDownSeparator` |

**포커스가 없는, 비활성 검색 입력 필드**

![포커스가 없는, 비활성 검색 입력 필드](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-1_SearchInputFieldUnfocusedInactive")<br />포커스가 없는, 비활성 검색 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.Unfocused` |
| 전경(텍스트) | `SearchControl.Unfocused` |
| 테두리 | `SearchControl.UnfocusedBorder` |
| 구분 기호 | `SearchControl.DropDownSeparator` |

**강조 표시 된 검색 입력 필드 (텍스트만)**

![강조 표시 된 검색 입력 필드](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />강조 표시 된 검색 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.Selection` |
| 전경(텍스트) | `SearchControl.FocusedBackground` |
| 테두리 | 없음 |
| 구분 기호 | `SearchControl.FocusedDropDownSeparator` |

**사용 하지 않도록 설정 된 검색 입력 필드**

![사용 하지 않도록 설정 된 검색 입력 필드](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />사용 하지 않도록 설정 된 검색 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.Disabled` |
| 전경(텍스트) | `SearchControl.Disabled` |
| 테두리 | `SearchControl.DisabledBorder` |
| 구분 기호 | `SearchControl.DropDownSeparator` |

**포커스가 있는 검색 작업 단추**

![포커스가 있는 검색 작업 단추](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />포커스가 있는 검색 작업 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(검색 문자 모양) | `SearchControl.SearchGlyph` |
| 전경(중지 문자 모양) | `SearchControl.StopGlyph` |
| 전경(지우기 문자 모양) | `SearchControl.ClearGlyph` |
| 테두리 | 해당 없음 |

**포커스가 없는 검색 동작 단추**

![포커스가 없는 검색 동작 단추](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />포커스가 없는 검색 동작 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(검색 문자 모양) | `SearchControl.SearchGlyph` |
| 전경(중지 문자 모양) | `SearchControl.StopGlyph` |
| 전경(지우기 문자 모양) | `SearchControl.ClearGlyph` |
| 테두리 | 해당 없음 |

**누름 검색 동작 단추**

![누름 검색 동작 단추](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-1_SearchActionButtonPressed")<br />누름 검색 동작 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.ActionButtonMouseDown` |
| 전경(문자 모양) | `SearchControl.ActionButtonMouseDownGlyph` |
| 테두리 | `SearchControl.ActionButtonMouseDownBorder` |

**비활성화 된 검색 작업 단추**

![검색 작업 단추 사용 안 함](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />비활성화 된 검색 작업 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(문자 모양) | `SearchControl.ActionButtonDisabledGlyph` |
| 테두리 | 없음 |

**포커스가 있는 검색 드롭다운 단추**

![포커스가 있는 검색 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />포커스가 있는 검색 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.FocusedDropDownButton` |
| 전경(문자 모양) | `SearchControl.FocusedDropDownButtonGlyph` |
| 테두리 | `SearchControl.FocusedDropDownButtonBorder` |

**포커스가 없는 검색 드롭다운 단추**

![포커스가 없는 검색 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />포커스가 없는 검색 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.UnfocusedDropDownButton` |
| 전경(문자 모양) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| 테두리 | `SearchControl.UnfocusedDropDownButtonBorder` |

**누른 검색 드롭다운 단추**

![누른 검색 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-2_SearchDropdownButtonPressed")<br />누른 검색 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.MouseDownDropDownButton` |
| 전경(문자 모양) | `SearchControl.MouseDownDropDownButtonGlyph` |
| 테두리 | `SearchControl.MouseDownDropDownButtonBorder` |

**비활성화 된 검색 드롭다운 단추**

![비활성화 된 검색 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />비활성화 된 검색 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(문자 모양) | `SearchControl.DisabledDownButtonGlyph` |
| 테두리 | 없음 |

#### <a name="search-drop-down-lists"></a>검색 드롭다운 목록
검색 상자 드롭다운 메뉴는 Visual Studio의 다른 드롭다운 메뉴 보다 약간 더 복잡할 수 있습니다. "제안 된 검색" 및 "검색 옵션" 섹션이 메뉴에 단독으로 또는 함께 표시 될 수 있으며 각각은 개별적으로 색이 지정 됩니다. 또한 함께 표시되는 경우 이러한 두 섹션이 줄로 구분되며, 테두리가 전체 드롭다운 메뉴를 둘러쌉니다.

![검색 드롭다운 목록 (검토)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />검색 드롭다운 목록 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 검색 드롭다운 목록을 만드는 경우 | ... 다른 컨텍스트에서 표시 되는 드롭다운 목록 |
| ... 올바른 목록 구성 요소에 대 한 올바른 토큰 이름입니다. | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**검색 드롭다운 목록 요소**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 테두리 | `SearchControl.PopupBorder` |
| 구분 기호 | `SearchControl.PopupSectionHeaderSeparator` |
| 그림자 | `Environment.DropShadowBackground` |

**제안 된 검색: 기본 상태**

![제안 된 기본 검색](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />제안 된 기본 검색

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `SearchControl.PopupItemText` |

**제안 된 검색: 가리키기 상태**

![가리키기에서 추천 검색](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />가리키기에서 추천 검색

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `SearchControl.PopupMouseOverItemText` |
| 테두리 | `SearchControl.PopupControlMouseOverBorder` |

**검색 옵션: 기본 상태**

![검색 확인란](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />기본 검색 옵션 (확인란)

![search 옵션](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />기본 검색 옵션 (링크)

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(확인란 텍스트) | `SearchControl.PopupCheckboxText` |
| 전경(링크 텍스트) | `SearchControl.PopupButtonText` |
| 머리글 배경 | `SearchControl.PopupSectionHeaderGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(머리글 텍스트) | `SearchControl.PopupSectionHeaderText` |

**검색 옵션: 가리키기 상태**

![검색 옵션 (확인란) 가리키기](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />검색 옵션 (확인란) 가리키기

![검색 옵션 (링크) 가리키기](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />검색 옵션 (링크) 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(확인란 텍스트) | `SearchControl.PopupCheckboxMouseDownText` |
| 전경(링크 텍스트) | `SearchControl.PopupButtonMouseDownText` |
| 테두리 | `SearchControl.PopupControlMouseOverBorder` |

**검색 옵션: 누름 상태**

![누른 검색 옵션 (확인란)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />누른 검색 옵션 (확인란)

![누른 검색 옵션 (링크)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />누른 검색 옵션 (링크)

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 확인란 배경 | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(확인란 텍스트) | `SearchControl.PopupCheckboxMouseDownText` |
| 링크 배경 | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(링크 텍스트) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> 트리 뷰
솔루션 탐색기, 서버 탐색기 및 클래스 뷰를 비롯 한 여러 도구 창은 범주의 색 이름으로 색이 제어 되는 계층적 조직 체계를 구현 합니다 `TreeView` . 트리 뷰의 모든 항목에는 배경색과 텍스트 색이 있습니다. 중첩된 자식 요소가 있는 항목에는 항목이 확장 또는 축소되었는지 여부를 나타내는 문자 모양도 있습니다.

![트리 뷰 (검토)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />트리 뷰 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 계층적 조직 뷰를 구현 해야 하는 모든 위치 | ... 트리 뷰와 유사 하지 않은 모든 항목 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**트리 뷰 항목: 기본 상태**

![기본 트리 보기 항목](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />기본 트리 보기 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.Background` |
| 전경(텍스트) | `TreeView.Background` |
| 전경(문자 모양) | `TreeView.Glyph` |
| 테두리 | 없음 |

**트리 뷰 항목: 가리키기 상태**

![트리 뷰 항목 가리키기](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />트리 뷰 항목 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.Background` |
| 전경(텍스트) | `TreeView.Background` |
| 전경(문자 모양) | `TreeView.GlyphMouseOver` |
| 테두리 | 없음 |

**트리 뷰 항목: 위로 상태 끌기**

![끌 때 트리 뷰 항목](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />끌 때 트리 뷰 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.DragOverItem` |
| 전경(텍스트) | `TreeView.DragOverItem` |
| 전경(문자 모양) | `TreeView.DragOverItemGlyph` |
| 테두리 | 없음 |

**트리 뷰 항목: 선택 됨, 포커스가 있는 상태**

![선택 및 포커스가 있는 트리 보기 항목](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />선택 및 포커스가 있는 트리 보기 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemActive` |
| 전경(텍스트) | `TreeView.SelectedItemActive` |
| 전경(문자 모양) | `TreeView.SelectedItemActiveGlyph` |
| 테두리 | `TreeView.FocusVisualBorder` |

**트리 뷰 항목: 선택 됨, 포커스가 없는 상태**

![선택한 및 포커스가 없는 트리 보기 항목](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />선택한 및 포커스가 없는 트리 보기 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemInactive` |
| 전경(텍스트) | `TreeView.SelectedItemInactive` |
| 전경(문자 모양) | `TreeView.SelectedItemInactiveGlyph` |
| 테두리 | 없음 |

**트리 뷰 항목: 가리킨 상태, 선택 됨 및 포커스가 있는 상태**

![선택 하 고 포커스가 있는 트리 보기 항목 가리키기](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />선택 하 고 포커스가 있는 트리 보기 항목 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemActive` |
| 전경(텍스트) | `TreeView.SelectedItemActive` |
| 전경(문자 모양) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 테두리 | `TreeView.FocusVisualBorder` |

**트리 뷰 항목: 가리킨 상태, 선택 됨 및 포커스가 없는 상태**

![선택한 및 포커스가 없는 트리 보기 항목 가리키기](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />선택한 및 포커스가 없는 트리 보기 항목 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemInactive` |
| 전경(텍스트) | `TreeView.SelectedItemInactive` |
| 전경(문자 모양) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 테두리 | 없음 |

## <a name="shell-appearance"></a>셸 모양

### <a name="background"></a>배경
환경 배경은 두 계층으로 이루어져 있습니다. 아래쪽 계층은 전체 IDE에 적용되는 단색입니다. 위쪽 계층은 명령 선반 아래와 IDE의 왼쪽 및 오른쪽 가장자리에서 도구 창 자동 숨기기 채널 사이에 적용됩니다. 위쪽 및 아래쪽 배경 계층이 밝은 테마와 어두운 테마에서 동일한 색으로 설정 됩니다.

![Visual Studio shell 배경 (검토)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio shell 배경 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... Visual Studio 환경의 배경과 일치 시키려는 위치. | ... 배경 화면이 아닌 위치에 대 한 채우기입니다. |
| | ... 전경 요소를에 삽입할 배경입니다. |

**최하위 계층 셸 모양**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.EnvironmentBackground` |

**최상위 계층 셸 모양**

> 그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>명령 선반
명령 선반 배경에는 두 가지 토큰 이름 집합이 사용되며, 각각 메뉴 모음이 있는 위치와 명령 모음이 있는 위치에 사용됩니다. 개별 명령 모음 그룹에는 자체 배경색 값이 있으며, "명령 모음" 섹션에서 자세히 설명합니다. 메뉴 모음 및 명령 모음 텍스트는 각각 메뉴 및 명령 모음 섹션에서 설명합니다.

![Visual Studio 명령 선반 (검토)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio 명령 선반 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 메뉴 또는 도구 모음을 저장 하는 영역 | ... 명령 선반과 유사 하지 않은 영역 |
|... 올바른 배경/전경 토큰 이름 조합을 사용 합니다. | |

**명령 선반 메뉴 모음**

> 그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**명령 선반 명령 모음**

> 그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>매니페스트 디자이너
매니페스트 디자이너는 Windows 8 및 Windows Phone 8 프로젝트에서 매니페스트 파일을 보다 쉽게 편집할 수 있도록 하는 하나의 방법으로 설계되었습니다. 사용할 수 있는 공유 프레임워크가 없는 동안에는 방향/탐색 탭의 디자인 레이아웃 및 색과 전체적인 구조를 일치시키는 것이 좋습니다. 레이아웃 정보에 대한 자세한 내용은 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)을 참조하세요.

![매니페스트 디자이너 (검토)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />매니페스트 디자이너 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 매니페스트 디자이너와 유사한 디자이너 | ... 6 개가 넘는 탭이 있는 경우 |
| ... 문서 웰 내에서 편집기 맨 위에 있는 공용 탭 컨트롤을 사용 하는 대신 | ... 매니페스트 디자이너 처럼 구조화 되지 않은 모든 UI |

**매니페스트 디자이너 선택 됨 탭: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `ManifestDesigner.TabActive` |
| 테두리 | 없음 |

**매니페스트 디자이너에서 선택한 설명 창: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `ManifestDesigner.DescriptionPane` |

**매니페스트 디자이너에서 콘텐츠 페이지를 선택 했습니다. 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `ManifestDesigner.Background` |
| 대화 상자 도우미 텍스트 | `ManifestDesigner.WatermarkText`<br />이 토큰 이름은 함수와 일치 하지 않습니다. |

**매니페스트 디자이너 탭: 선택 하지 않은 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `ManifestDesigner.Tab.Inactive` |

**매니페스트 디자이너 탭: 가리키기 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>명령 구조

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> 메뉴로
메뉴는 Visual Studio 내의 여러 위치에서 발생할 수 있습니다. 주 메뉴 모음은 문서 또는 도구 창에 포함 되어 있거나 IDE 전체의 다양 한 위치에서 마우스 오른쪽 단추로 클릭 합니다. 다른 UI 요소와 연결된 메뉴의 구현은 해당 요소에 대한 섹션에서 설명합니다. 항상 Visual Studio 환경에서 제공하는 표준 메뉴 구현을 사용해야 합니다. 그러나 드물긴 하지만 표준 Visual Studio 메뉴에 액세스할 수 없는 경우도 있습니다. 이러한 경우 다음 토큰 이름을 사용하여 Visual Studio의 다른 메뉴와 UI의 일관성을 유지합니다.

![Visual Studio 메뉴 (검토)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio 메뉴 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 메뉴를 만들어야 하는 경우| ... 배경색입니다. 항상 지정된 배경/전경 조합을 사용합니다. |
| ... Visual Studio 메뉴와 일치 시키려는 새 UI 구성 요소가 있는 경우| |

#### <a name="menu-titles"></a>메뉴 제목
일반적으로 메뉴가 명령 모음에 있을 경우 메뉴 제목은 배경, 테두리, 제목 텍스트 및 선택적인 문자 모양으로 구성됩니다.

![메뉴 제목 (검토)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />메뉴 제목 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 메뉴 제목을 만들 때마다. | ... 항상 메뉴 제목과 일치 시 키 지 않으려는 모든 항목 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**메뉴 제목: 기본 상태**

![기본 메뉴 제목](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />기본 메뉴 제목

![문자 모양이 포함 된 기본 메뉴 제목](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />문자 모양이 포함 된 기본 메뉴 제목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경 (텍스트) | `Environment.CommandBarTextActive` |
| 전경 (문자 모양) | `Environment.CommandBarMenuGlyph` |
| 테두리 | 없음 |

**메뉴 제목: 가리키기 상태**

![가리키면 표시되는 메뉴 제목](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />가리키면 표시되는 메뉴 제목

![가리키면 표시되는 문자 모양의 메뉴 제목](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />가리키면 표시되는 문자 모양의 메뉴 제목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경 (텍스트) | `Environment.CommandBarTextHover` |
| 전경 (문자 모양) | `Environment.CommandBarMenuMouseOverGlyph` |
| 테두리 | `Environment.CommandBarBorder` |

**메뉴 제목: 누름 상태**

![누른 메뉴 제목](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />누른 메뉴 제목

![문자 모양이 포함 된 누름 메뉴 제목](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />문자 모양이 포함 된 누름 메뉴 제목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 전경(문자 모양) | `Environment.CommandBarMenuMouseDownGlyph` |
| 테두리 | `Environment.CommandBarMenuBorder`<br />(왼쪽, 위쪽 및 오른쪽에만 해당) |

**메뉴 제목: 사용 안 함 상태**

![문자 모양이 포함 된 메뉴 제목 사용 안 함](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />문자 모양이 포함 된 메뉴 제목 사용 안 함

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(텍스트) | `Environment.CommandBarTextInactive` |
| 전경(문자 모양) | `Environment.CommandBarTextInactive` |
| 테두리 | 없음 |

#### <a name="menu-items"></a>메뉴 항목
개별 메뉴 항목은 메뉴 텍스트와 선택적 아이콘, 확인란 또는 하위 메뉴 문자 모양으로 구성됩니다. 마우스로 가리키면 해당 배경색과 텍스트 색이 바뀝니다. 이 색 토큰은 배경/전경 쌍입니다.

![메뉴 항목 검토](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| 사용 ... | 사용 하지 않음 ... |
|---|---|
| ... 메뉴 모음이 나 명령 모음에서 시작 되는 드롭다운 목록 | ... 다른 컨텍스트의 드롭다운 목록 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**메뉴 항목: 기본 상태**

![기본 메뉴 항목](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />기본 메뉴 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 전경(하위 메뉴 문자 모양) | `Environment.CommandBarMenuSubmenuGlyph` |
| 테두리 | `Environment.CommandBarMenuBorder` |
| 아이콘 채널 배경 | `Environment.CommandBarMenuIconBackground` |
| 구분 기호 | `Environment.CommandBarMenuSeparator` |
| 그림자 | `Environment.DropShadowBackground` |

**메뉴 항목: 선택 된 상태 및 선택한 상태**

![메뉴 확인됨](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />선택 된 메뉴 항목

![메뉴 선택됨](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />선택한 메뉴 항목

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 확인 표시 | `Environment.CommandBarCheckBox` |
| 확인 표시 배경 | `Environment.CommandBarSelectedIcon` |
| 아이콘 배경 | `Environment.CommandBarSelected` |
| 아이콘 테두리 | `Environment.CommandBarSelectedBorder` |

**메뉴 항목: 가리키기 상태**

![메뉴 가리키기](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />메뉴 항목 가리키기

![메뉴 가리키기 확인됨](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />선택 된 메뉴 항목 가리키기

![메뉴 가리키기 선택됨](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />선택한 메뉴 항목 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMenuItemMouseOver` |
| 전경(텍스트) | `Environment.CommandBarMenuItemMouseOverText` |
| 전경(하위 메뉴 문자 모양) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| 확인 표시 | `Environment.CommandBarCheckBoxMouseOver` |
| 확인 표시 배경 | `Environment.CommandBarHoverOverSelectedIcon` |
| 아이콘 배경 | `Environment.CommandBarHoverOverSelected` |
| 아이콘 테두리 | `Environment.CommandBarHoverOverSelectedIconBorder` |

**메뉴 항목: disabled 상태**

![메뉴 사용 안 함](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />메뉴 항목 사용 안 함

![메뉴 사용 안 함 확인됨](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />확인 표시가 있는 메뉴 항목을 사용할 수 없음

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 전경(텍스트) | `Environment.CommandBarTextInactive` |
| 전경(하위 메뉴 문자 모양) | `Environment.CommandBarMenuSubmenuGlyph` |
| 확인 표시 | `Environment.CommandBarCheckBoxDisabled` |
| 확인 표시 배경 | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>명령 모음
명령 모음은 Visual Studio IDE 내의 여러 위치에 나타날 수 있습니다. 특히 명령 선반에서 도구 또는 문서 창에 포함 됩니다.

일반적으로, 항상 Visual Studio 환경에서 제공하는 표준 명령 모음 구현을 사용합니다. 표준 메커니즘을 사용하면 모든 시각적 정보가 올바르게 표시되며 대화형 요소가 다른 Visual Studio 명령 모음 컨트롤과 일관성 있게 동작합니다. 그러나 고유한 명령 모음을 빌드해야 하는 경우 다음 토큰 이름을 사용하여 올바르게 스타일을 지정해야 합니다.

![명령 모음 검토](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />명령 모음 (검토)

![오버플로 단추 검토](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />오버플로 단추 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 포함 된 명령 모음이 필요 하지만 표준 Visual Studio 명령 모음 구현을 사용할 수 없는 위치 | ... 명령 모음과 유사 하지 않은 UI 요소 |
| | ... 토큰 이름이 지정 된 구성 요소 이외의 다른 명령 모음 구성 요소 |

#### <a name="command-bar-groups"></a>명령 모음 그룹
명령 모음 그룹은 관련된 명령 모음 컨트롤 집합으로 구성되며 임의 개수의 단추, 분할 단추, 드롭다운 메뉴, 콤보 상자 또는 메뉴를 포함할 수 있습니다. 해당 컨트롤의 색은 별도 토큰 이름으로 제어되며 이 가이드의 다른 위치에서 개별적으로 설명합니다. 구분 기호 선을 사용하여 명령 모음 그룹을 관련된 하위 그룹으로 나눕니다.

![명령 모음 그룹 검토](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />명령 모음 그룹 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 포함 된 명령 모음이 필요 하지만 표준 Visual Studio 명령 모음 구현을 사용할 수 없는 위치 | ... 명령 모음과 유사 하지 않은 UI 요소 |
| | ... 토큰 이름이 지정 된 구성 요소 이외의 다른 명령 모음 구성 요소 |

**명령 모음 그룹: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 테두리 | `Environment.CommandBarToolBarBorder` |
| 끌기 핸들 | `Environment.CommandBarDragHandle` |
| 구분 기호 | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>명령 아이콘
![명령 아이콘 검토](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />명령 아이콘 (검토)

![텍스트 검토를 사용 하는 명령 아이콘](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />텍스트를 포함 하는 명령 아이콘 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 명령 모음에 배치 되는 모든 단추 | ... 고유한 토큰 이름을 가진 컨트롤 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**명령 아이콘: 기본 상태**

![명령 아이콘 기본값](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />기본 명령 아이콘

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음(명령 모음 배경에서 상속됨) |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 테두리 | 해당 없음 |

**명령 아이콘: 기본 상태, 선택 됨**

![기본, 선택한 명령 아이콘](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />기본, 선택한 명령 아이콘

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarSelected` |
| 전경(텍스트) | `Environment.CommandBarTextSelected` |
| 테두리 | `Environment.CommandBarSelectedBorder` |

**명령 아이콘: 가리키기 또는 포커스 상태**

![가리키기 또는 포커스가 있는 명령 아이콘](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />가리키기 또는 포커스가 있는 명령 아이콘

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextHover` |
| 테두리 | `Environment.CommandBarBorder` |

**명령 아이콘: 가리키기 또는 포커스 상태, 선택 됨**

![가리키기 또는 포커스가 있을 때 선택한 명령 아이콘](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />가리키기 또는 포커스가 있을 때 선택한 명령 아이콘

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarHoverOverSelected` |
| 전경(텍스트) | `Environment.CommandBarTextHoverOverSelected` |
| 테두리 | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **명령 아이콘: 누름 상태**

![명령 아이콘 누름](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />명령 아이콘 누름

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextMouseDown` |
| 테두리 | `Environment.CommandBarBorder` |

**명령 아이콘: disabled 상태**

![명령 아이콘 사용 안 함](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />명령 아이콘 사용 안 함

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음(명령 모음 배경에서 상속됨) |
| 전경(텍스트) | `Environment.CommandBarTextInactive` |
| 테두리 | 해당 없음 |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> 명령 모음 콤보 상자

> [!IMPORTANT]
> 콤보 상자는 드롭다운과 유사하지만 편집 가능한 텍스트 영역을 포함합니다. 드롭다운에 편집 가능한 텍스트 영역이 포함 되어 있지 않은 경우 [명령 모음 드롭다운](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)에 대 한 색 토큰을 사용 합니다.

![명령 모음 콤보 상자 검토](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />명령 모음 콤보 상자 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 콤보 상자를 빌드하는 경우 | ... 명령 모음 UI와 항상 일치 시 키 지 않으려는 모든 항목 |
| ... 콤보 상자와 유사한 명령 모음 컨트롤을 만드는 경우 | ... 스타일이 적용 된 콤보 상자에 액세스할 수 있는 경우 |

**명령 모음 콤보 상자 입력 필드: 기본 상태**

![명령 모음 콤보 상자 입력 필드](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />명령 모음 콤보 상자 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxBackground` |
| 전경(텍스트) | `Environment.ComboBoxText` |
| 테두리 | `Environment.ComboBoxBorder` |
| 구분 기호 | 구분 기호 없음 |

**명령 모음 드롭다운 단추: 기본 상태**

![콤보 상자 놓기&#45;아래로 단추](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음(명령 모음 배경에서 상속됨) |
| 전경(문자 모양) | `Environment.ComboBoxGlyph` |

**명령 모음 드롭다운 목록: 기본 상태**

![명령 모음 드롭다운 목록](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />명령 모음 드롭다운 목록

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxPopupBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.ComboBoxItemText` |
| 테두리 | `Environment.ComboBoxPopupBorder` |

**명령 모음 콤보 상자 입력 필드: 가리키기 상태**

![명령 모음 콤보 상자 입력 필드 가리키기](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />명령 모음 콤보 상자 입력 필드 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.ComboBoxMouseOverText` |
| 테두리 | `Environment.ComboBoxMouseOverBorder` |
| 구분 기호 | `Environment.ComboBoxMouseOverSeparator` |

 **명령 모음 드롭다운 단추: 가리키기 상태**

![명령 모음 드롭다운 단추 가리키기](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />명령 모음 드롭다운 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxButtonMouseOverBackground` |
| 전경(문자 모양) | `Environment.ComboBoxMouseOverGlyph` |

**명령 모음 드롭다운 목록: 가리키기 상태**

 ![명령 모음 드롭다운 목록 가리키기](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />명령 모음 드롭다운 목록 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경(메뉴 항목) | `Environment.ComboBoxItemMouseOverBackground` |
| 전경(텍스트) | `Environment.ComboBoxItemMouseOverText` |
| 테두리(메뉴 항목) | `Environment.ComboBoxItemMouseOverBorder` |

 **명령 모음 콤보 상자 입력 필드: 포커스가 있는 상태**

![포커스가 있는 명령 모음 콤보 상자 입력 필드](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />포커스가 있는 명령 모음 콤보 상자 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxFocusedBackground` |
| 전경(텍스트) | `Environment.ComboBoxFocusedText` |
| 테두리 | `Environment.ComboBoxFocusedBorder` |
| 구분 기호 | `Environment.ComboBoxFocusedButtonSeparator` |

**명령 모음 드롭다운 단추: 포커스가 있는 상태**

![포커스가 있는 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />포커스가 있는 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxFocusedButtonBackground` |
| 전경(문자 모양) | `Environment.ComboBoxFocusedGlyph` |

 **명령 모음 콤보 상자 입력 필드: 누름 상태**

![누른 명령 모음 콤보 상자 입력 필드](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />누른 명령 모음 콤보 상자 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxMouseDownBackground` |
| 전경(텍스트) | `Environment.ComboBoxMouseDownText` |
| 테두리 | `Environment.ComboBoxMouseDownBorder` |
| 구분 기호 | `Environment.ComboBoxMouseDownSeparator` |

**명령 모음 드롭다운 단추: 누름 상태**

![누른 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />누른 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxButtonMouseDownBackground` |
| 전경(문자 모양) | `Environment.ComboBoxMouseDownGlyph` |

**명령 모음 콤보 상자 입력 필드: 사용 안 함 상태**

![사용할 수 없는 명령 모음 콤보 상자 입력 필드](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />사용할 수 없는 명령 모음 콤보 상자 입력 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ComboBoxDisabledBackground` |
| 전경(텍스트) | `Environment.ComboBoxDisabledText` |
| 테두리 | `Environment.ComboBoxDisabledBorder` |
| 구분 기호 | 구분 기호 없음 |

**명령 모음 드롭다운 단추: 사용 안 함 상태**

![사용할 수 없는 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />사용할 수 없는 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(문자 모양) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> 명령 모음 드롭다운

> [!IMPORTANT]
> 드롭다운은 콤보 상자와 유사하지만 편집 가능한 텍스트 영역이 없습니다. 드롭다운에 편집 가능한 텍스트 영역이 포함 되어 있으면 [명령 모음 콤보 상자](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)에 대 한 색 토큰을 사용 합니다.

![명령 모음 드롭다운 (검토)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />명령 모음 드롭다운 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 드롭다운 목록 컨트롤을 만드는 경우 | ... 드롭다운 목록과 유사 하지 않은 모든 항목 |
| | ... 콤보 상자 또는 분할 단추 |

**명령 모음 드롭다운 선택 필드: 기본 상태**

![기본 명령 모음 드롭다운 선택 필드](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />기본 명령 모음 드롭다운 선택 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownBackground` |
| 전경(텍스트) | `DropDownText` |
| 테두리 | `DropDownBorder` |
| 구분 기호 | 구분 기호 없음 |

**명령 모음 드롭다운 단추: 기본 상태**

![기본 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />기본 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(문자 모양) | `Environment.DropDownGlyph` |

**명령 모음 드롭다운 목록: 기본 상태**

![기본 명령 모음 드롭다운 목록](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />기본 명령 모음 드롭다운 목록

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownPopupBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.ComboBoxItemText` |
| 테두리 | `Environment.DropDownPopupBorder` |
| 그림자 | `Environment.DropShadowBackground` |

**명령 모음 드롭다운 선택 필드: 가리키기 상태**

![명령 모음 드롭다운 선택 필드 가리키기](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />명령 모음 드롭다운 선택 필드 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.DropDownMouseOverText` |
| 테두리 | `Environment.DropDownMouseOverBorder` |
| 구분 기호 | `Environment.DropDownButtonMouseOverSeparator` |

**명령 모음 드롭다운 단추: 가리키기 상태**

![명령 모음 드롭다운 단추 가리키기](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />명령 모음 드롭다운 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownButtonMouseOverBackground` |
| 전경(문자 모양) | `Environment.DropDownMouseOverGlyph` |

**명령 모음 드롭다운 목록: 가리키기 상태**

![명령 모음 드롭다운 목록 가리키기](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />명령 모음 드롭다운 목록 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경(메뉴 항목) | `Environment.ComboBoxItemMouseOverBackground` |
| 전경(텍스트) | `Environment.ComboBoxItemMouseOverText` |
| 테두리(메뉴 항목) | `Environment.ComboBoxItemMouseOverBorder` |

 **명령 모음 드롭다운 선택 필드: 누름 상태**

![드롭다운&#45;선택 필드 누름](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />누른 명령 모음 드롭다운 선택 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownMouseDownBackground` |
| 전경(텍스트) | `Environment.DropDownMouseDownText` |
| 테두리 | `Environment.DropDownMouseDownBorder` |
| 구분 기호 | `Environment.DropDownButtonMouseDownSeparator` |

**명령 모음 드롭다운 단추: 누름 상태**

![누른 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />누른 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownButtonMouseDownBackground` |
| 전경(문자 모양) | `Environment.DropDownMouseDownGlyph` |

**명령 모음 드롭다운 선택 필드: 사용 안 함 상태**

![비활성화 된 명령 모음 드롭다운 선택 필드](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />비활성화 된 명령 모음 드롭다운 선택 필드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DropDownDisabledBackground` |
| 전경(텍스트) | `Environment.DropDownDisabledText` |
| 테두리 | `Environment.DropDownDisabledBorder` |
| 구분 기호 | 구분 기호 없음 |

**명령 모음 드롭다운 단추: 사용 안 함 상태**

![사용할 수 없는 명령 모음 드롭다운 단추](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />사용할 수 없는 명령 모음 드롭다운 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(문자 모양) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>명령 모음 분할 단추
분할 단추는 단추, 메뉴, 명령 모음 텍스트 등 다른 명령 모음 컨트롤과 많은 토큰 이름을 공유합니다. 편의를 위해 모든 필요한 작업 및 드롭다운 단추 토큰 이름이 여기에 반복됩니다. 분할 단추 드롭다운 목록은 [명령 모음 메뉴](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)의 구현입니다.

![분할 단추 검토](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />명령 모음 분할 단추 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 분할 단추를 만드는 경우 | ... 다른 종류의 단추 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**명령 모음 분할 단추: 기본 상태**

![기본 명령 모음 분할 단추](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />기본 명령 모음 분할 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 없음 |
| 전경(텍스트) | `Environment.CommandBarTextActive` |
| 전경(문자 모양) | `Environment.CommandBarSplitButtonGlyph` |
| 테두리 | 해당 없음 |
| 구분 기호 | 해당 없음 |

**명령 모음 분할 단추: 가리키기 상태**

![명령 모음 분할 단추 가리키기](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />명령 모음 분할 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextHover` |
| 전경(문자 모양) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| 테두리 | `Environment.CommandBarBorder` |
| 구분 기호 | `Environment.CommandBarSplitButtonSeparator` |

**명령 모음 분할 단추: 누름 상태**

![누른 명령 모음 분할 단추](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />누른 명령 모음 분할 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.CommandBarTextMouseDown` |
| 전경(문자 모양) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| 테두리 | `Environment.CommandBarBorder` |
| 구분 기호 | 해당 없음 |

**명령 모음 분할 단추: 사용 안 함 상태**

![비활성화 된 명령 모음 분할 단추](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />비활성화 된 명령 모음 분할 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(텍스트) | `Environment.ComboBoxItemTextInactive` |
| 전경(문자 모양) | `Environment.CommandBarTextInactive` |
| 테두리 | 해당 없음 |
| 구분 기호 | 해당 없음 |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>명령 모음 ' 기타 옵션 ' 및 ' 오버플로 ' 단추
"기타 옵션" 단추는 관련된 명령 모음 단추를 추가하거나 제거하여 명령 모음 그룹을 사용자 지정할 수 있는 경우에 사용됩니다. "오버플로" 단추는 가로 공간이 부족하여 명령 모음이 잘리고, 클릭하면 표시되지 않는 명령 모음 단추를 포함하는 메뉴가 표시될 때 나타납니다. 이러한 두 단추의 색은 동일한 토큰 이름 집합에 의해 제어됩니다.

![명령 모음 ' 기타 옵션 ' 단추 (검토)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />명령 모음 ' 기타 옵션 ' 단추 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 ' 기타 옵션 ' 또는 ' 오버플로 ' 단추 | ... ' 기타 옵션 ' 또는 ' 오버플로 ' 단추와 유사한 기능이 없는 단추 |

**명령 모음 ' 기타 옵션 ' 및 ' 오버플로 ' 단추: 기본 상태**

![기본 명령 모음 ' 기타 옵션 ' 단추](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />기본 명령 모음 ' 기타 옵션 ' 단추

![기본 명령 모음 ' 오버플로 ' 단추](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />기본 명령 모음 ' 오버플로 ' 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarOptionsBackground` |
| 전경(문자 모양) | `Environment.CommandBarOptionsGlyph` |

**명령 모음 ' 기타 옵션 ' 및 ' 오버플로 ' 단추: 가리키기 상태**

![명령 모음의 ' 기타 옵션 ' 단추 가리키기](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />명령 모음의 ' 기타 옵션 ' 단추 가리키기

![명령 모음 ' 오버플로 ' 단추 가리키기](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />명령 모음 ' 오버플로 ' 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(문자 모양) | `Environment.CommandBarOptionsMouseDownGlyph` |

**명령 모음 ' 기타 옵션 ' 및 ' 오버플로 ' 단추: 누름 상태**

![' 기타 옵션 ' 단추 누름 명령 모음](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />' 기타 옵션 ' 단추 누름 명령 모음

![오버플로 누름](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />누름 명령 모음 ' 오버플로 ' 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(문자 모양) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>문서 창
Visual Studio 환경에서 제공 되므로 문서 창을 복제할 필요는 없습니다. 그러나 UI가 항상 Visual Studio 환경의 이 부분과 일관되게 나타나도록 문서 창에서 사용된 색을 활용할 수 있습니다.

문서 창 색 토큰을 사용 하는 경우 유사한 요소에만 사용 하 고 항상 쌍으로 사용 해야 합니다. 이렇게 하지 않으면 UI에서 예기치 않은 결과가 발생할 수 있습니다.

### <a name="document-window-frames"></a>문서 창 프레임
문서 창은 IDE에 도킹되거나 별도 창으로 부동할 수 있습니다. 문서 창이 IDE 외부에서 부동 상태인 경우에도 문서 웰에 있고, IDE의 일부인 경우와 동일한 배경, 테두리, 텍스트 및 탭 색이 있습니다. 그러나 문서는 자체 배경, 테두리 및 텍스트 색을 가진 프레임 내에 있습니다. 도구 창이 문서 저장소에 도킹되면 문서 창 토큰 이름에서 해당 탭의 동작과 색을 상속합니다.

![도킹 된 문서 창 (검토)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />도킹 된 문서 창 (검토)

![부동 문서 창 (검토)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />부동 문서 창 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 문서 창과 일치 시키려는 UI를 만드는 모든 위치 | ...  셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**도킹 또는 부동 문서 창: 기본 상태**

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 문서 종류에 따라 달라집니다. |
| 전경(텍스트) | 문서 종류에 따라 달라집니다. |
| 테두리 | `Environment.ToolWindowBorder` |

**포커스가 있는 부동 문서 창 프레임: 기본 상태**

![기본 포커스, 부동 문서 창 프레임](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />기본 포커스, 부동 문서 창 프레임

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowFloatingFrame` |
| 전경(텍스트) | `Environment.ToolWindowFloatingFrame` |
| 전경(문자 모양) | `Environment.RaftedWindowButtonActiveGlyph` |
| 테두리 | `Environment.MainWindowActiveDefaultBorder` |
| 테두리(문자 모양) | `Environment.RaftedWindowButtonActiveBorder`<br />(투명으로 설정) |

**포커스가 없는, 부동 문서 창 프레임: 기본 상태**

![기본 포커스가 없는, 부동 문서 창 프레임](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />기본 포커스가 없는, 부동 문서 창 프레임

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowFloatingFrameInactive` |
| 전경(텍스트) | `Environment.ToolWindowFloatingFrameInactive` |
| 전경(문자 모양) | `Environment.RaftedWindowButtonInactiveGlyph` |
| 테두리 | `Environment.MainWindowInactiveBorder` |
| 테두리(문자 모양) | `Environment.RaftedWindowButtonInactiveBorder`<br />(투명으로 설정) |

**포커스가 있는 부동 문서 창 프레임: 가리키기 상태**

![포커스가 있는 부동 문서 창 프레임](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />포커스가 있는 부동 문서 창 프레임

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경(문자 모양) | `Environment.RaftedWindowButtonHoverActive` |
| 전경(문자 모양) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| 테두리(문자 모양) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**포커스가 없는, 부동 문서 창 프레임: 가리키기 상태**

![포커스가 없는, 부동 문서 창 프레임 가리키기](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />포커스가 없는, 부동 문서 창 프레임 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경(문자 모양) | `EnvironmentRaftedWindowButtonHoverInactive` |
| 전경(문자 모양) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| 테두리(문자 모양) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**포커스가 있는 부동 문서 창 프레임: 누름 상태**

![누를 때 포커스가 있는 부동 문서 창 프레임](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />누를 때 포커스가 있는 부동 문서 창 프레임

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경(문자 모양) | `Environment.RaftedWindowButtonDown` |
| 전경(문자 모양) | `Environment.RaftedWindowButtonDownGlyph` |
| 테두리(문자 모양) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>문서 탭
문서 탭은 탭 채널에 있으며, 현재 선택된 문서 또는 활성 문서와 함께 현재 열려 있는 문서를 표시합니다. 사용자가 배치할 경우 도구 창이 문서 탭 채널에 도킹될 수도 있습니다. 이 경우 문서 창과 동일한 탭 색을 사용합니다. 항상 문서 창 색과 일치시키려는 UI를 만드는 경우(테마 업데이트 또는 새 테마가 설치된 경우 포함), 다음과 같은 색 토큰을 참조합니다.

![문서 탭 (검토)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />문서 탭 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 문서 탭과 일치 시키고 테마 업데이트 또는 새 테마 색을 자동으로 선택 하는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

#### <a name="open-document-tabs"></a>열린 문서 탭
문서 탭 채널에는 열려 있는 각 문서의 이름을 표시하는 탭이 있습니다. 백그라운드에서 문서를 선택하거나 열 수 있으며, 해당 탭에 다음 상태가 반영됩니다.

- 선택한 탭은 문서 저장소에 현재 표시되는 문서를 나타냅니다. 선택한 탭에는 문서 저장소의 위쪽 가장자리에서 확장되는 문서 테두리가 있습니다.

- 배경 탭은 현재 선택한 탭이 아닌 모든 문서 탭입니다. 클릭 하면 선택한 탭이 되며 해당 토큰 이름에서 모든 배경, 테두리 및 텍스트 색을 가져옵니다.

![문서 탭 열기 (검토)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />문서 탭 열기 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 문서 탭을 만드는 경우 | ... provisional (미리 보기) 탭 |
| | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**선택한, 포커스가 있는 문서 탭**

![선택한, 포커스가 있는 문서 탭](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />선택한, 포커스가 있는 문서 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabSelectedGradientTop`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.FileTabSelectedText` |
| 테두리 | `Environment.FileTabSelectedBorder`<br />(배경과 동일한 색으로 설정 됨) |
| 문서 테두리 | `Environment.FileTabDocumentBorderBackground` |

**선택 됨, 포커스가 없는 문서 탭**

![선택 됨, 포커스가 없는 문서 탭](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />선택 됨, 포커스가 없는 문서 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabInactiveGradientTop`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.FileTabInactiveText` |
| 테두리 | `Environment.FileTabInactiveBorder`<br />(배경과 동일한 색으로 설정 됨) |
| 문서 테두리 | `Environment.FileTabInactiveDocumentBorderBackground` |

**배경 문서 탭: 기본 상태**

![기본 배경 문서 탭](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />기본 배경 문서 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabBackground` |
| 전경(텍스트) | `Environment.FileTabText` |
| 테두리 | `Environment.FileTabBorder`<br />(배경과 동일한 색으로 설정 됨) |

**배경 문서 탭: 가리키기 상태**

![백그라운드 문서 탭 가리키기](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />백그라운드 문서 탭 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabHotGradientTop`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.FileTabHotText` |
| 테두리 | `Environment.FileTabHotBorder`<br />(배경과 동일한 색으로 설정 됨) |

#### <a name="preview-tab"></a>미리 보기 탭
"Provisional" 탭이 라고도 합니다. 사용자가 솔루션 탐색기 도구 창에서 항목을 클릭 하면 문서 탭 채널의 오른쪽에 미리 보기 탭이 나타납니다. 문서의 미리 보기 역할을 하며, 문서 탭 채널의 왼쪽에 문서를 열어 두는 옵션도 사용자에게 제공합니다. 한 번에 하나의 미리 보기 탭만 열 수 있습니다. 미리 보기 탭에는 열린 탭처럼 배경과 선택한 상태가 둘 다 있으며, 활성 상태에서 포커스가 있거나 포커스가 없을 수 있습니다.

![미리 보기 탭 (검토)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />미리 보기 탭 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... provisional 미리 보기를 만들고 일부 요소가 현재 미리 보기 탭 색과 일치 하 게 하려는 경우 | ... provisional (미리 보기)가 아닌 모든 종류의 문서 또는 탭 |
| | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**포커스가 있는 선택한 미리 보기 탭**

![포커스가 있는 선택한 미리 보기 탭](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />포커스가 있는 선택한 미리 보기 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabProvisionalSelectedActive` |
| 전경(텍스트) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| 테두리 | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(배경과 동일한 색으로 설정 됨) |
| 문서 테두리 | `Environment.FileTabProvisionalSelectedActiveBorder` |

**포커스가 없는, 선택한 미리 보기 탭**

![포커스가 없는, 선택한 미리 보기 탭](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />포커스가 없는, 선택한 미리 보기 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabProvisionalSelectedInactive` |
| 전경(텍스트) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| 테두리 | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| 문서 테두리 | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**백그라운드 미리 보기 탭: 기본 상태**

![기본 배경 미리 보기 탭](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />기본 배경 미리 보기 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabProvisionalInactive` |
| 전경(텍스트) | `Environment.FileTabProvisionalInactiveForeground` |
| 테두리 | `Environment.FileTabProvisionalInactiveBorder`<br />(배경과 동일한 색으로 설정 됨) |

**백그라운드 미리 보기 탭: 가리키기 상태**

![백그라운드 미리 보기 탭 가리키기](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />백그라운드 미리 보기 탭 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.FileTabProvisionalHover` |
| 전경(텍스트) | `Environment.FileTabProvisionalHoverForeground` |
| 테두리 | `Environment.FileTabProvisionalHoverBorder`<br />(배경과 동일한 색으로 설정 됨) |

#### <a name="document-overflow-button"></a>문서 오버플로 단추
현재 구성에서 모든 문서 탭에 맞는 세로 공간이 있는지 여부에 관계없이 하나 이상의 문서가 열려 있으면 문서 오버플로 단추가 있습니다. [명령 모음 메뉴](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) 색에 의해 제어 되는 문서 오버플로 드롭다운 메뉴에는 열려 있는 모든 문서 목록이 표시 되 고 숨겨져 있으며, 열려 있는 모든 문서가 탭 채널에 표시 되는지 여부에 따라 오버플로 문자 모양이 변경 됩니다.

![문서 오버플로 단추 (검토)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />문서 오버플로 단추 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 사용자 지정 문서 오버플로 단추를 만드는 경우 | ... 오버플로 단추와 유사 하지 않은 UI의 경우입니다. |
| | ... 명령 모음 오버플로 단추 |

**문서 오버플로 단추: 기본 상태**

![기본 문서 오버플로 단추](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />기본 문서 오버플로 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DocWellOverflowButtonBackground` |
| 전경(문자 모양) | `Environment.DocWellOverflowButtonGlyph` |
| 테두리 | 해당 없음 |

**문서 오버플로 단추: 가리키기 상태**

![문서 오버플로 단추 가리키기](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />문서 오버플로 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DocWellOverflowButtonMouseOverBackground` |
| 전경(문자 모양) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| 테두리 | `Environment.DocWellOverflowButtonMouseOverBorder` |

**문서 오버플로 단추: 누름 상태**

![누름의 문서 오버플로 단추](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />누름의 문서 오버플로 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.DocWellOverflowButtonMouseDownBackground` |
| 전경(문자 모양) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| 테두리 | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>태그 지정
Visual Studio는 사용자가 추적을 위해 검색 가능한 키워드를 선언할 수 있는 태깅을 지원합니다. 예를 들어 프로젝트 관리자와 개발자는 TFS(Team Foundation Server)를 사용하여 작업 항목에 태깅할 수 있습니다. 아래 표에서는 태그 자체와 가리키기 및 선택한 상태에서 표시되는 "닫기 아이콘" 문자 모양에 대한 색 이름을 제공합니다.

![Visual Studio에서 태그 지정 (검토)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Visual Studio에서 태그 지정 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 태그 지정을 지 원하는 UI. | ... 다른 형식의 UI 인 경우 |

#### <a name="tags"></a>태그들

**태그: 기본 상태**

![기본 태그](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />기본 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.Background` |
| 전경(텍스트) | `Tag.Background` |

**태그: 가리키기 상태**

![태그 가리키기](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />태그 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.HoverBackground` |
| 전경(텍스트) | `Tag.HoverBackgroundText` |

**태그: 누름 상태**

![누른 태그](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />누른 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.PressedBackground` |
| 전경(텍스트) | `Tag.PressedBackgroundText` |

**태그: 선택한 상태**

![선택한 태그](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />선택한 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.SelectedBackground` |
| 전경(텍스트) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Close ( &times; ) 태그 문자 모양

**Close ( &times; ) 태그 문자 모양: 기본 상태**

![기본 닫기 ( &times; ) 태그 문자 모양](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />기본 닫기 ( &times; ) 태그 문자 모양

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(문자 모양) | `Tag.TagHoverGlyph` |

**Close ( &times; ) 태그 문자 모양: 가리키기 상태**

![Close ( &times; ) 태그 문자 모양 가리키기](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Close ( &times; ) 태그 문자 모양 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.TagHoverGlyphHoverBackground` |
| 전경(문자 모양) | `Tag.TagHoverGlyphHover` |
| 테두리 | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; ) 태그 문자 모양: 누름 상태**

![눌러진 닫기 ( &times; ) 태그 문자 모양](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />눌러진 닫기 ( &times; ) 태그 문자 모양

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.TagHoverGlyphPressedBackground` |
| 전경(문자 모양) | `Tag.TagHoverGlyphPressed` |
| 테두리 | `Tag.TagHoverGlyphPressedBorder` |

**닫는 ( &times; ) 문자 모양으로 선택한 태그: 기본 상태**

![Close ( &times; ) 문자 모양을 사용 하는 기본 선택 태그](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Close ( &times; ) 문자 모양을 사용 하는 기본 선택 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(문자 모양) | `Tag.TagSelectedGlyph` |

**닫는 ( &times; ) 문자 모양: 가리키기 상태를 사용 하 여 태그를 선택 했습니다.**

![닫는 ( &times; ) 문자 모양을 가리킬 때 선택한 태그](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />닫는 ( &times; ) 문자 모양을 가리킬 때 선택한 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.TagSelectedGlyphHoverBackground` |
| 전경(문자 모양) | `Tag.TagSelectedGlyphHover` |
| 테두리 | `Tag.TagSelectedGlyphHoverBorder` |

**Close ( &times; ) 문자 모양: 누름 상태를 사용 하 여 선택한 태그**

![선택 됨, Close ( &times; ) 문자 모양으로 누른 태그](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />선택 됨, Close ( &times; ) 문자 모양으로 누른 태그

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Tag.TagSelectedGlyphPressedBackground` |
| 전경(문자 모양) | `Tag.TagSelectedGlyphPressed` |
| 테두리 | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>도구 창
Visual Studio 환경에서 제공 되므로 도구 창을 복제할 필요는 없습니다. 그러나 UI가 항상 Visual Studio 환경의 이 부분과 일관되게 나타나도록 도구 창에서 사용된 색을 활용할 수 있습니다.

![도구 창 (검토)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />도구 창 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 도구 창과 일치 시키려는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

### <a name="tool-window-frame"></a>도구 창 프레임
Visual Studio의 도구 창은 다양한 작업에 사용되며 여러 상태 중 하나일 수 있습니다. 도구 창이 열려 있으면 문서 영역의 네 면 중 하나에 할당할 수 있습니다. 도구 창이 IDE 외부에 부동할 수도 있으며, 이 경우 사용자 화면 내의 아무 곳에나 다시 배치할 수 있습니다. 부동 창은 항상 IDE 위에 표시됩니다. 마지막으로, 도구 창은 문서 창으로 도킹될 수 있으며, 문서 저장소에 탭으로 나타납니다. 문서 창으로 도킹된 도구 창은 부분적으로 문서 창 토큰 이름을 사용하여 색이 지정됩니다.

![도구 창 프레임 (검토)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />도구 창 프레임 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ...  도구 창과 일치 시키려는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**도킹 된 도구 창**

![도킹 된 도구 창](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />도킹 된 도구 창

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowBackground` |
| 테두리 | `Environment.ToolWindowBorder` |

**부동, 포커스가 있는 도구 창**

![부동, 포커스가 있는 도구 창](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />부동, 포커스가 있는 도구 창

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowBackground` |
| 테두리 | `Environment.MainWindowActiveDefaultBorder` |

**부동, 포커스가 없는 도구 창**

![부동, 포커스가 없는 도구 창](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />부동, 포커스가 없는 도구 창

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowBackground` |
| 테두리 | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>도구 상자와 같은 창
도구 상자는 Visual Studio에서 가장 자주 사용 되는 일반 도구 창 중 하나입니다. 기본적으로 특수 테마와 스타일이 적용 된 트리 컨트롤입니다.

![도구 상자와 같은 창 (검토)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />도구 상자와 같은 창 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 항상 셸 도구 상자와 일치 시키려는 도구 창을 디자인 하는 경우 | ... 도구 상자 UI와 유사 하지 않은 모든 항목 또는 셸 도구 상자 색이 변경 되는 경우 UI에 문제가 있는지 여부가 확실 하지 않을 수 있습니다. |

**도구 상자 노드: 기본 상태**

![기본 도구 상자 부모 노드](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />기본 도구 상자 부모 노드

![기본 도구 상자 자식 노드](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />기본 도구 상자 자식 노드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolboxContent`<br />제목의 |
| 배경 | `Environment.ToolWindowBackground`<br />(개별 항목 또는 사용할 수 있는 컨트롤이 없는 경우 전체 창) |
| 테두리 | 없음 |
| 전경(문자 모양) | `Environment.ToolboxContent` |
| 전경(텍스트) | `Environment.ToolboxContent` |

**도구 상자 자식 노드: 가리키기 상태**

![도구 상자 자식 노드 가리키기](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />도구 상자 자식 노드 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolboxContentMouseOver`<br />(개별 항목만) |
| 테두리 | 없음 |
| 전경(텍스트) | `Environment.ToolboxContentMouseOver`<br />(개별 항목만) |

**선택한 도구 상자 노드: 포커스가 있는 상태**

![포커스가 있는 선택 되는 도구 상자 부모 노드](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />포커스가 있는 선택 되는 도구 상자 부모 노드

![포커스가 있는 선택 되는 도구 상자 자식 노드](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />포커스가 있는 선택 되는 도구 상자 자식 노드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |
| 테두리 | `TreeView.FocusVisualBorder`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |
| 전경(문자 모양) | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |
| 전경(텍스트) | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |

**선택한 도구 상자 노드: 포커스가 없는 상태**

![선택, 포커스가 없는 도구 상자 부모 노드](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />선택, 포커스가 없는 도구 상자 부모 노드

![선택, 포커스가 없는 도구 상자 자식 노드](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />선택, 포커스가 없는 도구 상자 자식 노드

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |
| 테두리 | 없음 |
| 전경(문자 모양) | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |
| 전경(텍스트) | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) 범주 |

### <a name="tool-window-title-bar"></a>도구 창 제목 표시줄
제목 표시줄 테두리는 실제 테두리가 아니라 제목 표시줄 위쪽에 있는 두꺼운 선입니다. 포커스가 없는 상태에 대 한 토큰 이름이 없습니다.

![도구 창 제목 표시줄 (검토)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />도구 창 제목 표시줄 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 도구 창과 일치 시키려는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**포커스가 있는 제목 표시줄**

![포커스가 있는 제목 표시줄](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />포커스가 있는 제목 표시줄

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.TitleBarActiveGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.TitleBarActiveText` |
| 테두리 | `Environment.TitleBarActiveBorder`<br />(배경과 동일한 색으로 설정 됨) |
| 끌기 핸들 | `Environment.TitleBarDragHandleActive` |

**포커스가 없는 제목 표시줄**

![포커스가 없는 제목 표시줄](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />포커스가 없는 제목 표시줄

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.TitleBarInactiveGradientBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.TitleBarInactiveText` |
| 테두리 | 해당 없음 |
| 끌기 핸들 | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>도구 창 제목 표시줄 단추
![제목 표시줄 단추 (검토)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />제목 표시줄 단추 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 도구 창 제목 표시줄의 색 토큰을 사용 하는 UI에 표시 되는 단추입니다. | ... 다른 위치에 표시 되는 단추 |
| | ... 지정 된이 아닌 모든 배경/전경 조합입니다. |

**포커스가 있는 제목 표시줄 단추: 기본 상태**

![기본, 포커스가 있는 제목 표시줄 단추](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />기본, 포커스가 있는 제목 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(문자 모양) | `Environment.ToolWindowButtonActiveGlyph` |
| 테두리 | 해당 없음 |

**포커스가 없는 제목 표시줄 단추: 기본 상태**

![기본, 포커스가 없는 제목 표시줄 단추](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />기본, 포커스가 없는 제목 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | 해당 없음 |
| 전경(문자 모양) | `Environment.ToolWindowButtonInactiveGlyph` |
| 테두리 | 해당 없음 |

**포커스가 있는 제목 표시줄 단추: 가리키기 상태**

![포커스가 있는 제목 표시줄 단추 가리키기](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />포커스가 있는 제목 표시줄 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowButtonHoverActive` |
| 전경(문자 모양) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| 테두리 | `Environment.ToolWindowButtonHoverActiveBorder` |

**포커스가 없는 제목 표시줄 단추: 가리키기 상태**

![포커스가 없는 제목 표시줄 단추 가리키기](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />포커스가 없는 제목 표시줄 단추 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowButtonHoverInactive` |
| 전경(문자 모양) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| 테두리 | `Environment.ToolWindowButtonHoverInactiveBorder` |

**포커스가 있는 제목 표시줄 단추: 누름 상태**

![누를 때 포커스가 있는 제목 표시줄 단추](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />누를 때 포커스가 있는 제목 표시줄 단추

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowButtonDown` |
| 전경(문자 모양) | `Environment.ToolWindowButtonDownActiveGlyph` |
| 테두리 | `Environment.ToolWindowButtonDownBorder` |

**포커스가 없는 제목 표시줄 단추: 누름 상태**

![포커스가 없는 제목 표시줄 단추 누르기](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />포커스가 없는 제목 표시줄 단추 누르기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowButtonDown` |
| 전경(문자 모양) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| 테두리 | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>도구 창 탭
![도구 창 탭 (검토)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />도구 창 탭 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 도구 창과 일치 시키려는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**선택한 포커스가 있는 도구 창 탭**

![선택한 포커스가 있는 도구 창 탭](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />선택한 포커스가 있는 도구 창 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowTabSelectedTab` |
| 전경(텍스트) | `Environment.ToolWindowTabSelectedActiveText` |
| 테두리 | `Environment.ToolWindowTabSelectedBorder`<br />(배경과 동일한 색으로 설정 됨) |

**선택한 포커스가 없는 도구 창 탭**

![선택한 포커스가 없는 도구 창 탭](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />선택한 포커스가 없는 도구 창 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowTabSelectedTab` |
| 전경(텍스트) | `Environment.ToolWindowTabSelectedText` |
| 테두리 | `Environment.ToolWindowTabSelectedBorder`<br />(배경과 동일한 색으로 설정 됨) |

**백그라운드 도구 창 탭: 기본 상태**

![기본 배경 도구 창 탭](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />기본 배경 도구 창 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정 됩니다. |
| 전경(텍스트) | `Environment.ToolWindowTabText` |
| 테두리 | `Environment.ToolWindowTabBorder` |

**백그라운드 도구 창 탭: 가리키기 상태**

![백그라운드 도구 창 탭 가리키기](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />백그라운드 도구 창 탭 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정 됩니다. |
| 전경(텍스트) | `Environment.ToolWindowTabMouseOverText` |
| 테두리 | `Environment.ToolWindowTabMouseOverBorder`<br />(배경과 동일한 색으로 설정 됨) |

### <a name="auto-hide-tabs"></a>자동 숨기기 탭

![자동 숨기기 탭 (검토)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") 자동 숨기기 탭 (검토)

| 사용 ... | 사용 하지 않음 ... |
| --- | --- |
| ... 자동 숨겨진 도구 창 탭과 일치 시키려는 UI를 만드는 모든 위치 | ... 셸에 테마 업데이트가 있는 경우 자동으로 변경 하지 않으려는 모든 UI |

**자동 숨기기 탭: 기본 상태**

![기본 자동 숨기기 탭](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />기본 자동 숨기기 탭

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.AutoHideTabBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.AutoHideTabText` |
| 테두리 | `Environment.AutoHideTabBorder` |

**자동 숨기기 탭: 가리키기 상태**

![자동 숨기기 탭 가리키기](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />자동 숨기기 탭 가리키기

| 요소 | 토큰 이름: Category.color |
| --- | --- |
| 배경 | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(이 토큰에 대 한 그라데이션 중지점은 테마가 적용 되는 UI에서 사용 되지 않습니다.) |
| 전경(텍스트) | `Environment.AutoHideTabMouseOverText` |
| 테두리 | `Environment.AutoHideTabMouseOverBorder` |
