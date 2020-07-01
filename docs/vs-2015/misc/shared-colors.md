---
title: 공유 색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 76c04680b63eb362e02fdf26d817660d671b3b52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548358"
---
# <a name="shared-colors"></a>공유 색
여기에 소개하는 내용을 삽입합니다.  
  
## <a name="shared-colors"></a>공유 색  
 일반적인 Visual Studio 셸 요소를 사용하는 UI를 디자인하거나 인터페이스 요소를 유사한 기능과 일치시키려는 경우 패키지 정의 파일에서 기존 토큰 이름을 사용하여 색을 선택하고 할당합니다. 이렇게 하면 UI가 전체 Visual Studio 환경과 일관성 있게 유지되며 테마를 추가하거나 업데이트할 경우 자동으로 업데이트됩니다.  
  
 이 문서에서는 유사한 UI를 빌드할 때 참조할 수 있는 일반적인 UI 요소 및 사용되는 토큰 이름을 설명합니다. 이러한 색 토큰에 액세스하는 방법에 대한 자세한 내용은 [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)를 참조하세요.  
  
 토큰 이름을 올바르게 사용해야 합니다.  
  
- **색 자체가 아니라 함수에 따라 토큰 이름을 사용합니다.** 일반적인 공유 색은 특정 인터페이스 요소와 연결되며 동일하거나 유사한 기능에만 사용해야 합니다. 예를 들어 단순히 색을 좋아한다고 해서 누른 콤보 상자의 색을 회전 진행률 애니메이션에 다시 사용하지 마세요. 콤보 상자와 애니메이션의 기능은 서로 다르며, 콤보 상자와 연결된 색이 변경될 경우 애니메이션 요소에 적절한 색이 아닐 수 있습니다. 색을 일관성 있게 사용하면 사용자를 올바른 방향으로 인도하고 혼동을 방지하는 데 도움이 됩니다.  
  
- **배경색과 텍스트 색을 올바른 조합으로 사용합니다.** 텍스트와 함께 사용되는 배경색에는 연결된 텍스트 색이 있습니다. 해당 배경에 지정된 색이 아닌 텍스트 색을 사용하지 마세요. 연결된 텍스트 색이 없는 경우 텍스트를 표시하려는 화면에 해당 배경색을 사용하지 마세요. 텍스트 색과 배경색의 다른 조합에서는 읽을 수 없는 인터페이스가 발생할 수 있습니다.  
  
- **해당 위치에 적합한 컨트롤 색을 사용합니다.** 특정 상태에서는 일부 Visual Studio 컨트롤에 별도 테두리와 배경색이 없습니다. 대신, 배경 화면에서 해당 색을 선택합니다. 항상 컨트롤을 배치할 위치에 적합한 토큰 이름을 사용해야 합니다.  
  
> [!IMPORTANT]
> "시작 페이지" 또는 "Cider" 범주에 있는 토큰을 사용하지 마세요.  
  
### <a name="command-structures"></a>명령 구조  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>메뉴로  
 메뉴는 Visual Studio 2013 내의 여러 위치에서 발생할 수 있습니다. 주 메뉴 모음에 표시되거나, 문서 또는 도구 창에 포함되거나, IDE 전체의 다양한 위치에서 마우스 오른쪽 단추를 클릭할 때 표시됩니다. 다른 UI 요소와 연결된 메뉴의 구현은 해당 요소에 대한 섹션에서 설명합니다. 항상 Visual Studio 환경에서 제공하는 표준 메뉴 구현을 사용해야 합니다. 그러나 드물긴 하지만 표준 Visual Studio 메뉴에 액세스할 수 없는 경우도 있습니다. 이러한 경우 다음 토큰 이름을 사용하여 Visual Studio의 다른 메뉴와 UI의 일관성을 유지합니다.  
  
 ![메뉴 검토](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
사용  
- 사용자 지정 메뉴를 만들어야 하는 경우 항상  
  
- Visual Studio 메뉴와 일치시키려는 새 UI 구성 요소가 있는 경우  
  
사용 안 함  
배경색만 단독으로 사용하지 마세요. 항상 지정된 배경/전경 조합을 사용합니다.  
  
##### <a name="menu-title"></a>메뉴 제목  
 일반적으로 메뉴가 명령 모음에 있을 경우 메뉴 제목은 배경, 테두리, 제목 텍스트 및 선택적인 문자 모양으로 구성됩니다.  
  
 ![메뉴 제목 검토](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
사용  
사용자 지정 메뉴 제목을 만드는 경우 항상  
  
사용 안 함  
- 항상 메뉴 제목과 일치시키지 않으려는 모든 항목  
  
- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![메뉴 제목 기본값](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **메뉴 제목**|배경|None|  
|![메뉴 제목 기본값](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **메뉴 제목**|전경(텍스트)|`Environment.CommandBarTextActive`|  
|![문자 모양 기본값으로 표시되는 메뉴 제목](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **문자 모양의 메뉴 제목**|전경(문자 모양)|`Environment.CommandBarMenuGlyph`|  
|![문자 모양 기본값으로 표시되는 메뉴 제목](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **문자 모양의 메뉴 제목**|테두리|None|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 메뉴 제목](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **메뉴 제목**|배경|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![가리키면 표시되는 메뉴 제목](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **메뉴 제목**|전경(텍스트)|`Environment.CommandBarTextHover`|  
|![가리키면 표시되는 문자 모양의 메뉴 제목](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **문자 모양의 메뉴 제목**|전경(문자 모양)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![가리키면 표시되는 문자 모양의 메뉴 제목](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **문자 모양의 메뉴 제목**|테두리|`Environment.CommandBarBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![메뉴 제목 누름](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **메뉴 제목**|배경|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![메뉴 제목 누름](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **메뉴 제목**|전경(텍스트)|`Environment.CommandBarTextActive`|  
|![문자 모양이 있는 메뉴 제목 누름](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **문자 모양의 메뉴 제목**|전경(문자 모양)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![문자 모양이 있는 메뉴 제목 누름](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **문자 모양의 메뉴 제목**|테두리|`Environment.CommandBarMenuBorder`<br /><br /> 왼쪽, 위쪽 및 오른쪽만|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![문자 모양을 사용하지 않은 메뉴 제목](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **문자 모양의 메뉴 제목**|배경|None|  
|![문자 모양을 사용하지 않은 메뉴 제목](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **문자 모양의 메뉴 제목**|전경(텍스트)|`Environment.CommandBarTextInactive`|  
|![문자 모양을 사용하지 않은 메뉴 제목](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **문자 모양의 메뉴 제목**|전경(문자 모양)|`Environment.CommandBarTextInactive`|  
|![문자 모양을 사용하지 않은 메뉴 제목](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **문자 모양의 메뉴 제목**|테두리|None|  
  
##### <a name="menu"></a>메뉴  
 개별 메뉴 항목은 메뉴 텍스트와 선택적 아이콘, 확인란 또는 하위 메뉴 문자 모양으로 구성됩니다. 마우스로 가리키면 해당 배경색과 텍스트 색이 바뀝니다. 이 색 토큰은 배경/전경 쌍입니다.  
  
 ![메뉴 항목 검토](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 사용  
 메뉴 모음이나 명령 모음에서 시작된 모든 드롭다운 목록  
  
사용 안 함  
- 다른 컨텍스트에서 발생하는 모든 드롭다운 목록  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|배경|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|전경(텍스트)|`Environment.CommandBarTextActive`|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|전경(하위 메뉴 문자 모양)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|테두리|`Environment.CommandBarMenuBorder`|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|아이콘 채널 배경|`Environment.CommandBarMenuIconBackground`|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|구분 기호|`Environment.CommandBarMenuSeparator`|  
|![메뉴 기본값](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **메뉴**|그림자|`Environment.DropShadowBackground`|  
|![메뉴 확인됨](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **검사할**|확인 표시|`Environment.CommandBarCheckBox`|  
|![메뉴 확인됨](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **검사할**|확인 표시 배경|`Environment.CommandBarSelectedIcon`|  
|![메뉴 선택됨](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selected**|아이콘 배경|`Environment.CommandBarSelected`|  
|![메뉴 선택됨](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selected**|아이콘 테두리|`Environment.CommandBarSelectedBorder`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![메뉴 가리키기](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **메뉴 항목**|배경|`Environment.CommandBarMenuItemMouseOver`|  
|![메뉴 가리키기](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **메뉴 항목**|전경(텍스트)|`Environment.CommandBarMenuItemMouseOver`|  
|![메뉴 가리키기](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **메뉴 항목**|전경(하위 메뉴 문자 모양)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![메뉴 가리키기 확인됨](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **검사할**|확인 표시|`Environment.CommandBarCheckBoxMouseOver`|  
|![메뉴 가리키기 확인됨](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **검사할**|확인 표시 배경|`Environment.CommandBarHoverOverSelectedIcon`|  
|![메뉴 가리키기 선택됨](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selected**|아이콘 배경|`Environment.CommandBarHoverOverSelected`|  
|![메뉴 가리키기 선택됨](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selected**|아이콘 테두리|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![메뉴 사용 안 함](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menu item|전경(텍스트)|`Environment.CommandBarTextInactive`|  
|![메뉴 사용 안 함](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menu item|전경(하위 메뉴 문자 모양)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![메뉴 사용 안 함 확인됨](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> 선택|확인 표시|`Environment.CommandBarCheckBoxDisabled`|  
|![메뉴 사용 안 함 확인됨](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> 선택|확인 표시 배경|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>명령 모음  
 명령 모음은 Visual Studio IDE 내의 여러 위치에 나타날 수 있습니다. 특히, 명령 선반에 표시되며 도구 또는 문서 창에 포함됩니다.  
  
 일반적으로, 항상 Visual Studio 환경에서 제공하는 표준 명령 모음 구현을 사용합니다. 표준 메커니즘을 사용하면 모든 시각적 정보가 올바르게 표시되며 대화형 요소가 다른 Visual Studio 명령 모음 컨트롤과 일관성 있게 동작합니다. 그러나 고유한 명령 모음을 빌드해야 하는 경우 다음 토큰 이름을 사용하여 올바르게 스타일을 지정해야 합니다.  
  
 ![명령 모음 검토](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![오버플로 단추 검토](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 사용  
 포함된 명령 모음이 필요하지만 표준 Visual Studio 명령 모음 구현을 사용할 수 없는 위치  
  
사용 안 함  
- 명령 모음과 유사하지 않은 UI 요소  

- 토큰 이름이 지정된 구성 요소 이외의 다른 명령 모음 구성 요소  
  
##### <a name="command-bar-group"></a>명령 모음 그룹  
 명령 모음 그룹은 관련된 명령 모음 컨트롤 집합으로 구성되며 임의 개수의 단추, 분할 단추, 드롭다운 메뉴, 콤보 상자 또는 메뉴를 포함할 수 있습니다. 해당 컨트롤의 색은 별도 토큰 이름으로 제어되며 이 가이드의 다른 위치에서 개별적으로 설명합니다. 구분 기호 선을 사용하여 명령 모음 그룹을 관련된 하위 그룹으로 나눕니다.  
  
 ![명령 모음 그룹 검토](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 사용  
 포함된 명령 모음이 필요하지만 표준 Visual Studio 명령 모음 구현을 사용할 수 없는 위치  
  
사용 안 함  
- 명령 모음과 유사하지 않은 UI 요소  

- 토큰 이름이 지정된 구성 요소 이외의 다른 명령 모음 구성 요소  
  
  **기본값** (다른 상태 없음)  
  
|요소|토큰 이름: Category.color|  
|-------------|--------------------------------|  
|배경|`Environment.CommandBarGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|테두리|`Environment.CommandBarToolBarBorder`|  
|끌기 핸들|`Environment.CommandBarDragHandle`|  
|구분 기호|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>명령 아이콘  
 ![명령 아이콘 검토](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![명령 아이콘 검토](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 사용  
 명령 모음에 배치되는 모든 단추  
  
사용 안 함  
- 고유한 토큰 이름을 가진 컨트롤  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![명령 아이콘 기본값](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **기본값**|배경|해당 없음(명령 모음 배경에서 상속됨)|  
|![명령 아이콘 기본값](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **기본값**|전경(텍스트)|`Environment.CommandBarTextActive`|  
|![명령 아이콘 기본값](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **기본값**|테두리|N/A|  
|![명령 아이콘 기본값 선택됨](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|배경|`Environment.CommandBarSelected`|  
|![명령 아이콘 기본값 선택됨](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|전경(텍스트)|`Environment.CommandBarTextSelected`|  
|![명령 아이콘 기본값 선택됨](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|테두리|`Environment.CommandBarSelectedBorder`|  
  
 **가리키기 및 키보드 포커스 있음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![명령 아이콘 가리키기](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **표준 가리키기**|배경|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![명령 아이콘 가리키기](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **표준 가리키기**|전경(텍스트)|`Environment.CommandBarTextHover`|  
|![명령 아이콘 가리키기](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **표준 가리키기**|테두리|`Environment.CommandBarBorder`|  
|![명령 아이콘 가리키기 선택됨](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **선택한 항목 가리키기**|배경|`Environment.CommandBarHoverOverSelected`|  
|![명령 아이콘 가리키기 선택됨](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **선택한 항목 가리키기**|전경(텍스트)|`Environment.CommandBarTextHoverOverSelected`|  
|![명령 아이콘 가리키기 선택됨](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **선택한 항목 가리키기**|테두리|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![명령 아이콘 누름](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **명령 아이콘 누름**|배경|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![명령 아이콘 누름](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **명령 아이콘 누름**|전경(텍스트)|`Environment.CommandBarTextMouseDown`|  
|![명령 아이콘 누름](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **명령 아이콘 누름**|테두리|`Environment.CommandBarBorder`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![명령 아이콘 사용 안 함](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **명령 아이콘 사용 안 함**|배경|해당 없음(명령 모음 배경에서 상속됨)|  
|![명령 아이콘 사용 안 함](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **명령 아이콘 사용 안 함**|전경(텍스트)|`Environment.CommandBarTextInactive`|  
|![명령 아이콘 사용 안 함](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **명령 아이콘 사용 안 함**|테두리|N/A|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>콤보 상자  
  
> [!IMPORTANT]
> 콤보 상자는 드롭다운과 유사하지만 편집 가능한 텍스트 영역을 포함합니다. 드롭다운에 편집 가능한 텍스트 영역이 포함되어 있지 않으면 [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown)아래의 색 토큰을 사용합니다.  
  
 ![콤보 상자 검토](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
사용  
- 사용자 지정 콤보 상자를 빌드하는 경우  

- 콤보 상자와 유사한 명령 모음 컨트롤을 만드는 경우  

사용 안 함  
- 명령 모음 UI와 항상 일치시키지 않으려는 모든 항목  

- 스타일이 적용된 콤보 상자에 액세스할 수 있는 경우  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **입력 필드**|배경|`Environment.ComboBoxBackground`|  
|![콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **입력 필드**|전경(텍스트)|`Environment.ComboBoxText`|  
|![콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **입력 필드**|테두리|`Environment.ComboBoxBorder`|  
|![콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **입력 필드**|구분 기호|구분 기호 없음|  
|![콤보 상자 놓기&#45;아래로 단추](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **드롭다운 단추**|배경|해당 없음(상속됨)|  
|![콤보 상자 놓기&#45;아래로 단추](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.ComboBoxGlyph`|  
|![콤보 상자&#47;드롭&#45;아래쪽 목록](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **드롭다운 목록**|배경|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![콤보 상자&#47;드롭&#45;아래쪽 목록](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **드롭다운 목록**|전경(텍스트)|`Environment.ComboBoxItemText`|  
|![콤보 상자&#47;드롭&#45;아래쪽 목록](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **드롭다운 목록**|테두리|`Environment.ComboBoxPopupBorder`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **입력 필드**|배경|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![가리키면 표시되는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **입력 필드**|전경(텍스트)|`Environment.ComboBoxMouseOverText`|  
|![가리키면 표시되는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **입력 필드**|테두리|`Environment.ComboBoxMouseOverBorder`|  
|![가리키면 표시되는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **입력 필드**|구분 기호|`Environment.ComboBoxMouseOverSeparator`|  
|![콤보 상자&#47;드롭다운 단추를 가리킨&#45;](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **드롭다운 단추**|배경|`Environment.ComboBoxButtonMouseOverBackground`|  
|![콤보 상자&#47;드롭다운 단추를 가리킨&#45;](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.ComboBoxMouseOverGlyph`|  
|![콤보 상자&#47;드롭다운 목록&#45;가리키기](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **드롭다운 목록**|배경(메뉴 항목)|`Environment.ComboBoxItemMouseOverBackground`|  
|![콤보 상자&#47;드롭다운 목록&#45;가리키기](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **드롭다운 목록**|전경(텍스트)|`Environment.ComboBoxItemMouseOverText`|  
|![콤보 상자&#47;드롭다운 목록&#45;가리키기](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **드롭다운 목록**|테두리(메뉴 항목)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **입력 필드**|배경|`Environment.ComboBoxFocusedBackground`|  
|![포커스가 있는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **입력 필드**|전경(텍스트)|`Environment.ComboBoxFocusedText`|  
|![포커스가 있는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **입력 필드**|테두리|`Environment.ComboBoxFocusedBorder`|  
|![포커스가 있는 콤보 상자 입력 필드](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **입력 필드**|구분 기호|`Environment.ComboBoxFocusedButtonSeparator`|  
|![콤보 상자&#47;드롭다운 단추가 포커스를&#45;.](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **드롭다운 단추**|배경|`Environment.ComboBoxFocusedButtonBackground`|  
|![콤보 상자&#47;드롭다운 단추가 포커스를&#45;.](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![콤보 상자 입력 필드 누름](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **입력 필드**|배경|`Environment.ComboBoxMouseDownBackground`|  
|![콤보 상자 입력 필드 누름](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **입력 필드**|전경(텍스트)|`Environment.ComboBoxMouseDownText`|  
|![콤보 상자 입력 필드 누름](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **입력 필드**|테두리|`Environment.ComboBoxMouseDownBorder`|  
|![콤보 상자 입력 필드 누름](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **입력 필드**|구분 기호|`Environment.ComboBoxMouseDownSeparator`|  
|![콤보 상자&#47;드롭&#45;down 단추 누름](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **드롭다운 단추**|배경|`Environment.ComboBoxButtonMouseDownBackground`|  
|![콤보 상자&#47;드롭&#45;down 단추 누름](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![콤보 상자 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **입력 필드**|배경|`Environment.ComboBoxDisabledBackground`|  
|![콤보 상자 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **입력 필드**|전경(텍스트)|`Environment.ComboBoxDisabledText`|  
|![콤보 상자 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **입력 필드**|테두리|`Environment.ComboBoxDisabledBorder`|  
|![콤보 상자 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **입력 필드**|구분 기호|구분 기호 없음|  
|![콤보 상자&#47;드롭&#45;down 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **드롭다운 단추**|배경|None|  
|![콤보 상자&#47;드롭&#45;down 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>드롭다운  
  
> [!IMPORTANT]
> 드롭다운은 콤보 상자와 유사하지만 편집 가능한 텍스트 영역이 없습니다. 드롭다운에 편집 가능한 텍스트 영역이 포함되어 있으면 [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox)아래의 색 토큰을 사용합니다.  
  
 ![Drop&#45;down 검토](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 사용  
 사용자 지정 드롭다운 목록 컨트롤을 만드는 경우  
  
사용 안 함  
- 드롭다운 목록과 유사하지 않은 모든 항목  

- 콤보 상자 또는 분할 단추  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;드롭다운 선택 필드 삭제](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **선택 필드**|배경|`Environment.DropDownBackground`|  
|![&#45;드롭다운 선택 필드 삭제](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **선택 필드**|전경(텍스트)|`DropDownText`|  
|![&#45;드롭다운 선택 필드 삭제](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **선택 필드**|테두리|`DropDownBorder`|  
|![&#45;드롭다운 선택 필드 삭제](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **선택 필드**|구분 기호|구분 기호 없음|  
|![드롭다운&#45;단추](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **드롭다운 단추**|배경|None|  
|![드롭다운&#45;단추](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.DropDownGlyph`|  
|![드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **드롭다운 목록**|배경|`Environment.DropDownPopupBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **드롭다운 목록**|전경(텍스트)|`Environment.ComboBoxItemText`|  
|![드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **드롭다운 목록**|테두리|`Environment.DropDownPopupBorder`|  
|![드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **드롭다운 목록**|그림자|`Environment.DropShadowBackground`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![마우스로 가리키면 선택 영역&#45;드롭다운 필드 삭제](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **선택 필드**|배경|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![마우스로 가리키면 선택 영역&#45;드롭다운 필드 삭제](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **선택 필드**|전경(텍스트)|`Environment.DropDownMouseOverText`|  
|![마우스로 가리키면 선택 영역&#45;드롭다운 필드 삭제](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **선택 필드**|테두리|`Environment.DropDownMouseOverBorder`|  
|![마우스로 가리키면 선택 영역&#45;드롭다운 필드 삭제](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **선택 필드**|구분 기호|`Environment.DropDownButtonMouseOverSeparator`|  
|![마우스로 가리키면 드롭다운 단추를&#45;.](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **드롭다운 단추**|배경|`Environment.DropDownButtonMouseOverBackground`|  
|![마우스로 가리키면 드롭다운 단추를&#45;.](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.DropDownMouseOverGlyph`|  
|![마우스로 가리키면 드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **드롭다운 목록**|배경(메뉴 항목)|`Environment.ComboBoxItemMouseOverBackground`|  
|![마우스로 가리키면 드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **드롭다운 목록**|전경(텍스트)|`Environment.ComboBoxItemMouseOverText`|  
|![마우스로 가리키면 드롭다운 목록&#45;](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **드롭다운 목록**|테두리(메뉴 항목)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![드롭다운&#45;선택 필드 누름](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **선택 필드**|배경|`Environment.DropDownMouseDownBackground`|  
|![드롭다운&#45;선택 필드 누름](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **선택 필드**|전경(텍스트)|`Environment.DropDownMouseDownText`|  
|![드롭다운&#45;선택 필드 누름](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **선택 필드**|테두리|`Environment.DropDownMouseDownBorder`|  
|![드롭다운&#45;선택 필드 누름](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **선택 필드**|구분 기호|`Environment.DropDownButtonMouseDownSeparator`|  
|![&#45;아래로 삭제 단추 누름](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **드롭다운 단추**|배경|`Environment.DropDownButtonMouseDownBackground`|  
|![&#45;아래로 삭제 단추 누름](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`Environment.DropDownMouseDownGlyph`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;드롭다운 선택 필드 삭제 사용 안 함](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|배경|`Environment.DropDownDisabledBackground`|  
|![&#45;드롭다운 선택 필드 삭제 사용 안 함](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|전경(텍스트)|`Environment.DropDownDisabledText`|  
|![&#45;드롭다운 선택 필드 삭제 사용 안 함](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|테두리|`Environment.DropDownDisabledBorder`|  
|![&#45;드롭다운 선택 필드 삭제 사용 안 함](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|구분 기호|구분 기호 없음|  
|![드롭&#45;down 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|배경|N/A|  
|![드롭&#45;down 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|전경(문자 모양)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>분할 단추  
 분할 단추는 단추, 메뉴, 명령 모음 텍스트 등 다른 명령 모음 컨트롤과 많은 토큰 이름을 공유합니다. 편의를 위해 모든 필요한 작업 및 드롭다운 단추 토큰 이름이 여기에 반복됩니다. 분할 단추 드롭다운 목록은 명령 모음의 구현입니다 [Menus](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![분할 단추 검토](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 사용  
 사용자 지정 분할 단추를 빌드하는 경우  
  
사용 안 함  
- 다른 종류의 단추  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![분할 단추](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **분할 단추(기본값)**|배경|None|  
|![분할 단추](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **분할 단추(기본값)**|전경(텍스트)|`Environment.CommandBarTextActive`|  
|![분할 단추](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **분할 단추(기본값)**|전경(문자 모양)|`Environment.CommandBarSplitButtonGlyph`|  
|![분할 단추](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **분할 단추(기본값)**|테두리|N/A|  
|![분할 단추](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **분할 단추(기본값)**|구분 기호|N/A|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![마우스로 가리키기의 분할 단추](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **분할 단추(가리키기)**|배경|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![마우스로 가리키기의 분할 단추](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **분할 단추(가리키기)**|전경(텍스트)|`Environment.CommandBarTextHover`|  
|![마우스로 가리키기의 분할 단추](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **분할 단추(가리키기)**|전경(문자 모양)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![마우스로 가리키기의 분할 단추](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **분할 단추(가리키기)**|테두리|`Environment.CommandBarBorder`|  
|![마우스로 가리키기의 분할 단추](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **분할 단추(가리키기)**|구분 기호|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![분할 단추 누름](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **분할 단추(누름)**|배경|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![분할 단추 누름](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **분할 단추(누름)**|전경(텍스트)|`Environment.CommandBarTextMouseDown`|  
|![분할 단추 누름](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **분할 단추(누름)**|전경(문자 모양)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![분할 단추 누름](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **분할 단추(누름)**|테두리|`Environment.CommandBarBorder`|  
|![분할 단추 누름](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **분할 단추(누름)**|구분 기호|N/A|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![분할 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **분할 단추(사용 안 함)**|배경|N/A|  
|![분할 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **분할 단추(사용 안 함)**|전경(텍스트)|`Environment.ComboBoxItemTextInactive`|  
|![분할 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **분할 단추(사용 안 함)**|전경(문자 모양)|`Environment.CommandBarTextInactive`|  
|![분할 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **분할 단추(사용 안 함)**|테두리|N/A|  
|![분할 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **분할 단추(사용 안 함)**|구분 기호|N/A|  
  
##### <a name="more-options-and-overflow-buttons"></a>'기타 옵션' 및 '오버플로' 단추  
 "기타 옵션" 단추는 관련된 명령 모음 단추를 추가하거나 제거하여 명령 모음 그룹을 사용자 지정할 수 있는 경우에 사용됩니다. "오버플로" 단추는 가로 공간이 부족하여 명령 모음이 잘리고, 클릭하면 표시되지 않는 명령 모음 단추를 포함하는 메뉴가 표시될 때 나타납니다. 이러한 두 단추의 색은 동일한 토큰 이름 집합에 의해 제어됩니다.  
  
 ![기타 옵션 검토](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 사용  
 사용자 지정 '기타 옵션' 또는 '오버플로' 단추  
  
 사용 안 함  
 '기타 옵션' 또는 '오버플로' 단추와 유사한 기능이 없는 단추  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![추가 옵션](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **추가 옵션**|배경|`Environment.CommandBarOptionsBackground`|  
|![추가 옵션](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **추가 옵션**|전경(문자 모양)|`Environment.CommandBarOptionsGlyph`|  
|![오버플로 단추](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **오버플로**|배경|`Environment.CommandBarOptionsBackground`|  
|![오버플로 단추](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **오버플로**|전경(문자 모양)|`Environment.CommandBarOptionsGlyph`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 기타 옵션](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **추가 옵션**|배경|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![가리키면 표시되는 기타 옵션](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **추가 옵션**|전경(문자 모양)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![가리키면 표시되는 오버플로](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **오버플로**|배경|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![가리키면 표시되는 오버플로](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **오버플로**|전경(문자 모양)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![기타 옵션 누름](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **추가 옵션**|배경|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![기타 옵션 누름](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **추가 옵션**|전경(문자 모양)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![오버플로 누름](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **오버플로**|배경|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![오버플로 누름](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **오버플로**|전경(문자 모양)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>문서 창  
 Visual Studio 환경에서 제공되므로 문서 창을 복제할 필요는 없습니다. 그러나 UI가 항상 Visual Studio 환경의 이 부분과 일관되게 나타나도록 문서 창에서 사용된 색을 활용할 수 있습니다.  
  
 문서 창 색 토큰을 사용하는 경우 유사한 요소에만 항상 쌍으로 사용해야 합니다. 이렇게 하지 않으면 UI에서 예기치 않은 결과가 발생합니다.  
  
#### <a name="document-window-frame"></a>문서 창 프레임  
 문서 창은 IDE에 도킹되거나 별도 창으로 부동할 수 있습니다. 문서 창이 IDE 외부에 부동하는 경우에도 여전히 문서 저장소에 있으며, IDE의 일부인 경우와 동일한 배경, 테두리, 텍스트 및 탭 색을 갖습니다. 그러나 문서는 자체 배경, 테두리 및 텍스트 색을 가진 프레임 내에 있습니다. 도구 창이 문서 저장소에 도킹되면 문서 창 토큰 이름에서 해당 탭의 동작과 색을 상속합니다.  
  
 ![도킹된 문서 창 검토](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **도킹된 문서 창**  
  
 ![부동 문서 창 검토](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **부동 문서 창**  
  
 사용  
 문서 창과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|문서: 도킹됨 또는 부동|배경|문서 종류에 따라 달라집니다.|  
|문서: 도킹됨 또는 부동|전경(텍스트)|문서 종류에 따라 달라집니다.|  
|문서: 도킹됨 또는 부동|테두리|`Environment.ToolWindowBorder`|  
|![포커스가 있는 프레임](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **프레임: 부동, 포커스 있음**|배경|`Environment.ToolWindowFloatingFrame`|  
|![포커스가 있는 프레임](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **프레임: 부동, 포커스 있음**|전경(텍스트)|`Environment.ToolWindowFloatingFrame`|  
|![포커스가 있는 프레임](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **프레임: 부동, 포커스 있음**|전경(문자 모양)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![포커스가 있는 프레임](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **프레임: 부동, 포커스 있음**|테두리|`Environment.MainWindowActiveDefaultBorder`|  
|![포커스가 있는 프레임](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **프레임: 부동, 포커스 있음**|테두리(문자 모양)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> 투명으로 설정됨|  
|![포커스가 없는 프레임](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **프레임: 부동, 포커스 없음**|배경|`Environment.ToolWindowFloatingFrameInactive`|  
|![포커스가 없는 프레임](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **프레임: 부동, 포커스 없음**|전경(텍스트)|`Environment.ToolWindowFloatingFrameInactive`|  
|![포커스가 없는 프레임](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **프레임: 부동, 포커스 없음**|전경(문자 모양)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![포커스가 없는 프레임](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **프레임: 부동, 포커스 없음**|테두리|`Environment.MainWindowInactiveBorder`|  
|![포커스가 없는 프레임](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **프레임: 부동, 포커스 없음**|테두리(문자 모양)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> 투명으로 설정됨|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **프레임: 부동, 포커스 있음**|배경(문자 모양)|`Environment.RaftedWindowButtonHoverActive`|  
|![포커스가 있는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **프레임: 부동, 포커스 있음**|전경(문자 모양)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![포커스가 있는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **프레임: 부동, 포커스 있음**|테두리(문자 모양)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![포커스가 없는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **프레임: 부동, 포커스 없음**|배경(문자 모양)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![포커스가 없는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **프레임: 부동, 포커스 없음**|전경(문자 모양)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![포커스가 없는 프레임 가리키기](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **프레임: 부동, 포커스 없음**|테두리(문자 모양)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 프레임 누름](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **프레임: 부동, 포커스 있음**|배경(문자 모양)|`Environment.RaftedWindowButtonDown`|  
|![포커스가 있는 프레임 누름](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **프레임: 부동, 포커스 있음**|전경(문자 모양)|`Environment.RaftedWindowButtonDownGlyph`|  
|![포커스가 있는 프레임 누름](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **프레임: 부동, 포커스 있음**|테두리(문자 모양)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>문서 탭  
 문서 탭은 탭 채널에 있으며, 현재 선택된 문서 또는 활성 문서와 함께 현재 열려 있는 문서를 표시합니다. 사용자가 배치할 경우 도구 창이 문서 탭 채널에 도킹될 수도 있습니다. 이 경우 문서 창과 동일한 탭 색을 사용합니다. 항상 문서 창 색과 일치시키려는 UI를 만드는 경우(테마 업데이트 또는 새 테마가 설치된 경우 포함), 다음과 같은 색 토큰을 참조합니다.  
  
 ![문서 탭 검토](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 사용  
 문서 탭과 일치시키고 테마 업데이트 또는 새 테마 색을 자동으로 선택하는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
##### <a name="open-document-tabs"></a>열린 문서 탭  
 문서 탭 채널에는 열려 있는 각 문서의 이름을 표시하는 탭이 있습니다. 백그라운드에서 문서를 선택하거나 열 수 있으며, 해당 탭에 다음 상태가 반영됩니다.  
  
- 선택한 탭은 문서 저장소에 현재 표시되는 문서를 나타냅니다. 선택한 탭에는 문서 저장소의 위쪽 가장자리에서 확장되는 문서 테두리가 있습니다.  
  
- 배경 탭은 현재 선택한 탭이 아닌 모든 문서 탭입니다. 클릭 하면 선택한 탭이 되며 해당 토큰 이름에서 모든 배경, 테두리 및 텍스트 색을 가져옵니다.  
  
  ![열린 문서 탭 검토](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  사용  
  사용자 지정 문서 탭을 만드는 경우  
  
  사용 안 함  
  - 임시(미리 보기) 탭  
  
- 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
##### <a name="selected-tab"></a>선택한 탭  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 선택한 탭](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **선택한 문서 탭, 포커스 있음**|배경|`Environment.FileTabSelectedGradientTop`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![포커스가 있는 선택한 탭](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **선택한 문서 탭, 포커스 있음**|전경(텍스트)|`Environment.FileTabSelectedText`|  
|![포커스가 있는 선택한 탭](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **선택한 문서 탭, 포커스 있음**|테두리|`Environment.FileTabSelectedBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
|![포커스가 있는 선택한 탭](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **선택한 문서 탭, 포커스 있음**|문서 테두리|`Environment.FileTabDocumentBorderBackground`|  
  
 **포커스 없음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 선택한 탭](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **선택한 문서 탭, 포커스 없음**|배경|`Environment.FileTabInactiveGradientTop`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![포커스가 없는 선택한 탭](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **선택한 문서 탭, 포커스 없음**|전경(텍스트)|`Environment.FileTabInactiveText`|  
|![포커스가 없는 선택한 탭](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **선택한 문서 탭, 포커스 없음**|테두리|`Environment.FileTabInactiveBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
|![포커스가 없는 선택한 탭](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **선택한 문서 탭, 포커스 없음**|문서 테두리|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>백그라운드 탭  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![백그라운드 탭](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **백그라운드 탭 기본값**|배경|`Environment.FileTabBackground`|  
|![백그라운드 탭](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **백그라운드 탭 기본값**|전경(텍스트)|`Environment.FileTabText`|  
|![백그라운드 탭](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **백그라운드 탭 기본값**|테두리|`Environment.FileTabBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 배경 탭](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **가리키면 표시되는 배경 탭**|배경|`Environment.FileTabHotGradientTop`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![가리키면 표시되는 배경 탭](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **가리키면 표시되는 배경 탭**|전경(텍스트)|`Environment.FileTabHotText`|  
|![가리키면 표시되는 배경 탭](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **가리키면 표시되는 배경 탭**|테두리|`Environment.FileTabHotBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
##### <a name="preview-tab"></a>미리 보기 탭  
 사용자가 솔루션 탐색기 도구 창에서 항목을 클릭하면 문서 탭 채널의 오른쪽에 미리 보기 탭이 나타납니다. 문서의 미리 보기 역할을 하며, 문서 탭 채널의 왼쪽에 문서를 열어 두는 옵션도 사용자에게 제공합니다. 한 번에 하나의 미리 보기 탭만 열 수 있습니다. 미리 보기 탭에는 열린 탭처럼 배경과 선택한 상태가 둘 다 있으며, 활성 상태에서 포커스가 있거나 포커스가 없을 수 있습니다.  
  
 ![미리 보기 탭 검토](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 사용  
 임시 미리 보기를 만들며 일부 요소를 현재 미리 보기 탭 색과 일치시키려는 모든 위치  
  
사용 안 함  
- 임시(미리 보기)가 아닌 모든 종류의 문서 또는 탭  

- 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
  **선택한 미리 보기 탭: 포커스 있음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **포커스가 있는 미리 보기 탭**|배경|`Environment.FileTabProvisionalSelectedActive`|  
|![포커스가 있는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **포커스가 있는 미리 보기 탭**|전경(텍스트)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![포커스가 있는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **포커스가 있는 미리 보기 탭**|테두리|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
|![포커스가 있는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **포커스가 있는 미리 보기 탭**|문서 테두리|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **선택한 미리 보기 탭: 포커스 없음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **포커스가 없는 미리 보기 탭**|배경|`Environment.FileTabProvisionalSelectedInactive`|  
|![포커스가 없는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **포커스가 없는 미리 보기 탭**|전경(텍스트)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![포커스가 없는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **포커스가 없는 미리 보기 탭**|테두리|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![포커스가 없는 미리 보기 탭](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **포커스가 없는 미리 보기 탭**|문서 테두리|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **백그라운드 미리 보기 탭: 기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![배경 미리 보기 탭](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **미리 보기 탭 백그라운드 탭**|배경|`Environment.FileTabProvisionalInactive`|  
|![배경 미리 보기 탭](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **미리 보기 탭 백그라운드 탭**|전경(텍스트)|`Environment.FileTabProvisionalInactiveForeground`|  
|![배경 미리 보기 탭](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **미리 보기 탭 백그라운드 탭**|테두리|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
 **백그라운드 미리 보기 탭: 가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 미리 보기 배경 탭](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **미리 보기 탭 백그라운드 탭 가리키기**|배경|`Environment.FileTabProvisionalHover`|  
|![가리키면 표시되는 미리 보기 배경 탭](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **미리 보기 탭 백그라운드 탭 가리키기**|전경(텍스트)|`Environment.FileTabProvisionalHoverForeground`|  
|![가리키면 표시되는 미리 보기 배경 탭](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **미리 보기 탭 백그라운드 탭 가리키기**|테두리|`Environment.FileTabProvisionalHoverBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
##### <a name="document-overflow-button"></a>문서 오버플로 단추  
 현재 구성에서 모든 문서 탭에 맞는 세로 공간이 있는지 여부에 관계없이 하나 이상의 문서가 열려 있으면 문서 오버플로 단추가 있습니다. **CommandBarMenu** 색으로 제어되는 문서 오버플로 드롭다운 메뉴( [Menus](../misc/shared-colors.md#BKMK_CommandMenus)참조)는 표시되고 숨겨진 모든 열린 문서의 목록을 표시하며, 모든 열린 문서가 탭 채널에 표시되는지 여부에 따라 오버플로 문자 모양이 바뀝니다.  
  
 ![오버플로 검토](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
사용  
사용자 지정 문서 오버플로 단추를 만드는 경우  

사용 안 함  
- 오버플로 단추와 유사하지 않은 UI  

- 명령 모음 오버플로 단추  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![오버플로](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **문서 오버플로 단추**|배경|`Environment.DocWellOverflowButtonBackground`|  
|![오버플로](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **문서 오버플로 단추**|전경(문자 모양)|`Environment.DocWellOverflowButtonGlyph`|  
|![오버플로](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **문서 오버플로 단추**|테두리|N/A|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![가리키면 표시되는 오버플로](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **문서 오버플로 단추 가리키기**|배경|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![가리키면 표시되는 오버플로](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **문서 오버플로 단추 가리키기**|전경(문자 모양)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![가리키면 표시되는 오버플로](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **문서 오버플로 단추 가리키기**|테두리|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![오버플로 누름](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **문서 오버플로 단추 누름**|배경|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![오버플로 누름](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **문서 오버플로 단추 누름**|전경(문자 모양)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![오버플로 누름](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **문서 오버플로 단추 누름**|테두리|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>도구 창  
 Visual Studio 환경에서 제공되므로 도구 창을 복제할 필요는 없습니다. 그러나 UI가 항상 Visual Studio 환경의 이 부분과 일관되게 나타나도록 도구 창에서 사용된 색을 활용할 수 있습니다.  
  
 ![도구 창 검토](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 사용  
 도구 창과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
#### <a name="tool-window-frame"></a>도구 창 프레임  
 Visual Studio의 도구 창은 다양한 작업에 사용되며 여러 상태 중 하나일 수 있습니다. 도구 창이 열려 있으면 문서 영역의 네 면 중 하나에 할당할 수 있습니다. 도구 창이 IDE 외부에 부동할 수도 있으며, 이 경우 사용자 화면 내의 아무 곳에나 다시 배치할 수 있습니다. 부동 창은 항상 IDE 위에 표시됩니다. 마지막으로, 도구 창은 문서 창으로 도킹될 수 있으며, 문서 저장소에 탭으로 나타납니다. 문서 창으로 도킹된 도구 창은 부분적으로 문서 창 토큰 이름을 사용하여 색이 지정됩니다.  
  
 ![도구 창 프레임 검토](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 사용  
 도구 창과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
 **도킹됨**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![도구 창 도킹됨](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|배경|`Environment.ToolWindowBackground`|  
|![도구 창 도킹됨](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|테두리|`Environment.ToolWindowBorder`|  
  
 **부동: 포커스 있음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 도구 창](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|배경|`Environment.ToolWindowBackground`|  
|![포커스가 있는 도구 창](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|테두리|`Environment.MainWindowActiveDefaultBorder`|  
  
 **부동: 포커스 없음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 도구 창](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|배경|`Environment.ToolWindowBackground`|  
|![포커스가 없는 도구 창](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|테두리|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>도구 창 제목 표시줄  
 제목 표시줄 테두리는 실제 테두리가 아니라 제목 표시줄 위쪽에 있는 두꺼운 선입니다. 포커스가 없는 상태에 대한 토큰 이름은 없습니다.  
  
 ![도구 창의 제목 표시줄 검토](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 사용  
 도구 창과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 제목 표시줄](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **포커스가 있는 제목 표시줄**|배경|`Environment.TitleBarActiveGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![포커스가 있는 제목 표시줄](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **포커스가 있는 제목 표시줄**|전경(텍스트)|`Environment.TitleBarActiveText`|  
|![포커스가 있는 제목 표시줄](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **포커스가 있는 제목 표시줄**|테두리|`Environment.TitleBarActiveBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
|![포커스가 있는 제목 표시줄](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **포커스가 있는 제목 표시줄**|끌기 핸들|`Environment.TitleBarDragHandleActive`|  
  
 **포커스 없음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 제목 표시줄](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **포커스가 없는 제목 표시줄**|배경|`Environment.TitleBarInactiveGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![포커스가 없는 제목 표시줄](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **포커스가 없는 제목 표시줄**|전경(텍스트)|`Environment.TitleBarInactiveText`|  
|![포커스가 없는 제목 표시줄](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **포커스가 없는 제목 표시줄**|테두리|N/A|  
|![포커스가 없는 제목 표시줄](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **포커스가 없는 제목 표시줄**|끌기 핸들|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>제목 표시줄 단추  
 ![제목 표시줄 단추 검토](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 사용  
 도구 창 제목 표시줄의 색 토큰을 사용하는 UI에 표시되는 단추  
  
사용 안 함  
- 다른 위치에 표시되는 단추  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 제목 표시줄 단추](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|배경|N/A|  
|![포커스가 있는 제목 표시줄 단추](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|전경(문자 모양)|`Environment.ToolWindowButtonActiveGlyph`|  
|![포커스가 있는 제목 표시줄 단추](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|테두리|N/A|  
|![제목 표시줄 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **포커스 없음**|배경|N/A|  
|![제목 표시줄 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **포커스 없음**|전경(문자 모양)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![제목 표시줄 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **포커스 없음**|테두리|N/A|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|배경|`Environment.ToolWindowButtonHoverActive`|  
|![포커스가 있는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|전경(문자 모양)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![포커스가 있는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|테두리|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![포커스가 없는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **포커스 없음**|배경|`Environment.ToolWindowButtonHoverInactive`|  
|![포커스가 없는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **포커스 없음**|전경(문자 모양)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![포커스가 없는 제목 표시줄 단추 가리키기](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **포커스 없음**|테두리|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|배경|`Environment.ToolWindowButtonDown`|  
|![포커스가 있는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|전경(문자 모양)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![포커스가 있는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|테두리|`Environment.ToolWindowButtonDownBorder`|  
|![포커스가 없는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **포커스 없음**|배경|`Environment.ToolWindowButtonDown`|  
|![포커스가 없는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **포커스 없음**|전경(문자 모양)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![포커스가 없는 제목 표시줄 단추 누름](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **포커스 없음**|테두리|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>도구 창 탭  
 ![도구 창 탭 검토](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 사용  
 도구 창과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
 **선택한 탭**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 도구 창 탭](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **선택한 포커스가 있는 도구 창 탭**|배경|`Environment.ToolWindowTabSelectedTab`|  
|![포커스가 있는 도구 창 탭](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **선택한 포커스가 있는 도구 창 탭**|전경(텍스트)|`Environment.ToolWindowTabSelectedActiveText`|  
|![포커스가 있는 도구 창 탭](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **선택한 포커스가 있는 도구 창 탭**|테두리|`Environment.ToolWindowTabSelectedBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 도구 창 탭](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **선택한 포커스가 없는 도구 창 탭**|배경|`Environment.ToolWindowTabSelectedTab`|  
|![포커스가 없는 도구 창 탭](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **선택한 포커스가 없는 도구 창 탭**|전경(텍스트)|`Environment.ToolWindowTabSelectedText`|  
|![포커스가 없는 도구 창 탭](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **선택한 포커스가 없는 도구 창 탭**|테두리|`Environment.ToolWindowTabSelectedBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
 **백그라운드 탭**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![도구 창 배경 탭](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **백그라운드 도구 창 탭**|배경|`Environment.ToolWindowTabGradientBegin`<br /><br /> 그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정됩니다.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> 그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정됩니다.|  
|![도구 창 배경 탭](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **백그라운드 도구 창 탭**|전경(텍스트)|`Environment.ToolWindowTabText`|  
|![도구 창 배경 탭](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **백그라운드 도구 창 탭**|테두리|`Environment.ToolWindowTabBorder`|  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![도구 창 배경 탭 가리키기](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **백그라운드 도구 창 탭 가리키기**|배경|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> 그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정됩니다.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> 그라데이션 중지점은 Visual Studio 2013에서 동일한 색 값으로 설정됩니다.|  
|![도구 창 배경 탭 가리키기](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **백그라운드 도구 창 탭 가리키기**|전경(텍스트)|`Environment.ToolWindowTabMouseOverText`|  
|![도구 창 배경 탭 가리키기](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **백그라운드 도구 창 탭 가리키기**|테두리|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> 배경색과 동일한 색으로 설정됨|  
  
#### <a name="auto-hide-tabs"></a>자동 숨기기 탭  
 ![자동&#45;숨기기 검토](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 사용  
 자동으로 숨겨진 도구 창 탭과 일치시키려는 UI를 만드는 모든 위치  
  
 사용 안 함  
 셸에 테마 업데이트가 있는 경우 자동으로 변경하지 않으려는 모든 UI  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![자동&#45;숨기기 탭](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **기본 자동 숨기기 탭**|배경|`Environment.AutoHideTabBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![자동&#45;숨기기 탭](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **기본 자동 숨기기 탭**|전경(텍스트)|`Environment.AutoHideTabText`|  
|![자동&#45;숨기기 탭](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **기본 자동 숨기기 탭**|테두리|`Environment.AutoHideTabBorder`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![자동&#45;숨기기 탭 가리키기](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **자동 숨기기 탭 가리키기**|배경|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![자동&#45;숨기기 탭 가리키기](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **자동 숨기기 탭 가리키기**|전경(텍스트)|`Environment.AutoHideTabMouseOverText`|  
|![자동&#45;숨기기 탭 가리키기](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **자동 숨기기 탭 가리키기**|테두리|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>공통 공유 컨트롤  
 기능에서 표준 Visual Studio 명령 모음을 사용하는 경우 스타일이 적용된 셸 컨트롤에 액세스할 수 있으므로 이러한 공통 컨트롤의 템플릿을 다시 만들면 안 됩니다. 그러나 사용자 지정 명령 모음을 빌드해야 하는 경우 사용자 지정 컨트롤도 빌드해야 할 수 있습니다. 이 경우 다음 컨트롤에 대해 각각 올바른 토큰 이름을 사용하여 UI를 Visual Studio의 나머지 부분과 일치시켜야 합니다.  
  
#### <a name="search-box"></a>검색 상자  
 가능한 경우 항상 Visual Studio 환경에서 제공하는 공용 검색 컨트롤을 사용합니다. 검색 상자 색은 입력 필드, 실행 단추, 드롭다운 단추 및 드롭다운 메뉴에 대한 토큰 이름이 포함된 **ShellColors.pkgdef** 파일의 "SearchControl" 범주에 있습니다.  
  
 검색 상자는 여러 상태 중 하나일 수 있으며, 일부 상태는 함께 사용할 수 없습니다.  
  
- "포커스 있음" 또는 "포커스 없음"은 텍스트 상자에 커서가 있는지 여부를 나타냅니다.  
  
- "활성" 또는 "비활성"은 사용자가 텍스트 상자에 검색 쿼리를 입력했는지 여부를 나타냅니다.  
  
- "가리키기"는 사용자가 마우스로 검색 상자를 가리켰음을 나타냅니다(이 상태는 다른 모든 상태를 재정의함).  
  
- "사용 안 함"은 검색 기능이 현재 컨텍스트에 대해 꺼져 있음을 나타냅니다.  
  
  ![검색 상자 검토](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  사용  
  사용자 지정 검색 상자를 디자인하는 경우  
  
  사용 안 함  
  - 검색 상자가 아닌 모든 항목  
  
- 검색 상자 UI와 항상 일치시키지 않으려는 모든 항목  
  
  **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **입력 필드**|배경|`SearchControl.FocusedBackground`|  
|![포커스가 있는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **입력 필드**|전경(텍스트)|`SearchControl.FocusedBackground`|  
|![포커스가 있는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **입력 필드**|테두리|`SearchControl.FocusedBorder`|  
|![포커스가 있는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **입력 필드**|구분 기호|`SearchControl.FocusedDropDownSeparator`|  
|![포커스가 있는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **작업 단추**|배경|None|  
|![포커스가 있는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **작업 단추**|전경(검색 문자 모양)|`SearchControl.SearchGlyph`|  
|![포커스가 있는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **작업 단추**|전경(중지 문자 모양)|`SearchControl.StopGlyph`|  
|![포커스가 있는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **작업 단추**|전경(지우기 문자 모양)|`SearchControl.ClearGlyph`|  
|![포커스가 있는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **작업 단추**|테두리|N/A|  
|![검색 삭제&#45;다운 단추 포커스가 있음](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **드롭다운 단추**|배경|`SearchControl.FocusedDropDownButton`|  
|![검색 삭제&#45;다운 단추 포커스가 있음](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![검색 삭제&#45;다운 단추 포커스가 있음](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **드롭다운 단추**|테두리|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **포커스 없음**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 없는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **활성 입력 필드**|배경|`SearchControl.SearchActiveBackground`|  
|![포커스가 없는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **활성 입력 필드**|전경(텍스트)|`SearchControl.SearchActiveBackground`|  
|![포커스가 없는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **활성 입력 필드**|테두리|`SearchControl.UnfocusedBorder`|  
|![포커스가 없는 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **활성 입력 필드**|구분 기호|`SearchControl.DropDownSeparator`|  
|![포커스가 없고 비활성화된 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-1_SearchInputFieldUnfocusedInactive")<br /><br /> **비활성 입력 필드**|배경|`SearchControl.Unfocused`|  
|![포커스가 없고 비활성화된 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-1_SearchInputFieldUnfocusedInactive")<br /><br /> **비활성 입력 필드**|전경(텍스트)|`SearchControl.Unfocused`|  
|![포커스가 없고 비활성화된 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-1_SearchInputFieldUnfocusedInactive")<br /><br /> **비활성 입력 필드**|테두리|`SearchControl.UnfocusedBorder`|  
|![포커스가 없고 비활성화된 검색어 입력 필드](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-1_SearchInputFieldUnfocusedInactive")<br /><br /> **비활성 입력 필드**|구분 기호|`SearchControl.DropDownSeparator`|  
|![포커스가 없는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **작업 단추**|배경|N/A|  
|![포커스가 없는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **작업 단추**|전경(검색 문자 모양)|`SearchControl.SearchGlyph`|  
|![포커스가 없는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **작업 단추**|전경(중지 문자 모양)|`SearchControl.StopGlyph`|  
|![포커스가 없는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **작업 단추**|전경(지우기 문자 모양)|`SearchControl.ClearGlyph`|  
|![포커스가 없는 검색 작업 단추](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **작업 단추**|테두리|N/A|  
|![검색 삭제&#45;아래로 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **드롭다운 단추**|배경|`SearchControl.UnfocusedDropDownButton`|  
|![검색 삭제&#45;아래로 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![검색 삭제&#45;아래로 단추 포커스가 없는](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **드롭다운 단추**|테두리|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![검색 작업 단추 누름](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-1_SearchActionButtonPressed")<br /><br /> **작업 단추**|배경|`SearchControl.ActionButtonMouseDown`|  
|![검색 작업 단추 누름](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-1_SearchActionButtonPressed")<br /><br /> **작업 단추**|전경(문자 모양)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![검색 작업 단추 누름](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-1_SearchActionButtonPressed")<br /><br /> **작업 단추**|테두리|`SearchControl.ActionButtonMouseDownBorder`|  
|![검색 삭제&#45;아래로 단추 누름](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-2_SearchDropdownButtonPressed")<br /><br /> **드롭다운 단추**|배경|`SearchControl.MouseDownDropDownButton`|  
|![검색 삭제&#45;아래로 단추 누름](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-2_SearchDropdownButtonPressed")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![검색 삭제&#45;아래로 단추 누름](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-2_SearchDropdownButtonPressed")<br /><br /> **드롭다운 단추**|테두리|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **강조 표시됨(텍스트)**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![검색어 입력 필드 강조 표시](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **텍스트가 강조 표시된 입력 필드**|배경|`SearchControl.Selection`|  
|![검색어 입력 필드 강조 표시](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **텍스트가 강조 표시된 입력 필드**|전경(텍스트)|`SearchControl.FocusedBackground`|  
|![검색어 입력 필드 강조 표시](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **텍스트가 강조 표시된 입력 필드**|테두리|None|  
|![검색어 입력 필드 강조 표시](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **텍스트가 강조 표시된 입력 필드**|구분 기호|`SearchControl.FocusedDropDownSeparator`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![검색어 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **입력 필드**|배경|`SearchControl.Disabled`|  
|![검색어 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **입력 필드**|전경(텍스트)|`SearchControl.Disabled`|  
|![검색어 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **입력 필드**|테두리|`SearchControl.DisabledBorder`|  
|![검색어 입력 필드 사용 안 함](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **입력 필드**|구분 기호|`SearchControl.DropDownSeparator`|  
|![검색 작업 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **작업 단추**|배경|None|  
|![검색 작업 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **작업 단추**|전경(문자 모양)|`SearchControl.ActionButtonDisabledGlyph`|  
|![검색 작업 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **작업 단추**|테두리|None|  
|![&#45;드롭다운 검색 드롭다운 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **드롭다운 단추**|배경|None|  
|![&#45;드롭다운 검색 드롭다운 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **드롭다운 단추**|전경(문자 모양)|`SearchControl.DisabledDownButtonGlyph`|  
|![&#45;드롭다운 검색 드롭다운 단추 사용 안 함](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **드롭다운 단추**|테두리|None|  
  
##### <a name="search-drop-down-lists"></a>검색 드롭다운 목록  
 검색 상자 드롭다운 메뉴는 Visual Studio의 다른 드롭다운 메뉴보다 약간 더 복잡해질 수 있습니다. "추천 검색어" 및 "검색 옵션" 섹션이 메뉴에 단독으로 또는 함께 표시될 수 있으며, 각 섹션에 색이 별도로 지정됩니다. 또한 함께 표시되는 경우 이러한 두 섹션이 줄로 구분되며, 테두리가 전체 드롭다운 메뉴를 둘러쌉니다.  
  
 ![검색 삭제&#45;down 검토](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
사용  
- 사용자 지정 검색 드롭다운 목록을 만드는 경우  

- 올바른 목록 구성 요소에 대해 올바른 토큰 이름 사용  

사용 안 함  
- 다른 컨텍스트에서 표시되는 드롭다운 목록의 경우  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값(다른 상태 없음)**  
  
|요소|토큰 이름: Category.color|  
|-------------|--------------------------------|  
|테두리|`SearchControl.PopupBorder`|  
|구분 기호|`SearchControl.PopupSectionHeaderSeparator`|  
|그림자|`Environment.DropShadowBackground`|  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![제안 검색](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **추천 검색어**|배경|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![제안 검색](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **추천 검색어**|전경(텍스트)|`SearchControl.PopupItemText`|  
|![검색 확인란](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **검색 옵션(확인란)**|배경|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![search 옵션](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **검색 옵션(링크)**|배경|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 확인란](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **검색 옵션(확인란)**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxText`|  
|![search 옵션](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **검색 옵션(링크)**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxText`|  
|![검색 확인란](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **검색 옵션(확인란)**|전경(링크 텍스트)|`SearchControl.PopupButtonText`|  
|![search 옵션](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **검색 옵션(링크)**|전경(링크 텍스트)|`SearchControl.PopupButtonText`|  
|![검색 확인란](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **검색 옵션(확인란)**|머리글 배경|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![search 옵션](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **검색 옵션(링크)**|머리글 배경|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 확인란](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **검색 옵션(확인란)**|전경(머리글 텍스트)|`SearchControl.PopupSectionHeaderText`|  
|![search 옵션](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **검색 옵션(링크)**|전경(머리글 텍스트)|`SearchControl.PopupSectionHeaderText`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![제안 검색 가리키기](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **추천 검색어**|배경|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![제안 검색 가리키기](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **추천 검색어**|전경(텍스트)|`SearchControl.PopupMouseOverItemText`|  
|![제안 검색 가리키기](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **추천 검색어**|테두리|`SearchControl.PopupControlMouseOverBorder`|  
|![검색 확인란 가리키기](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **추천 검색어(확인란)**|배경|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 옵션 가리키기](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **search 옵션**|배경|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 확인란 가리키기](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **추천 검색어(확인란)**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxMouseDownText`|  
|![검색 옵션 가리키기](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **search 옵션**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxMouseDownText`|  
|![검색 확인란 가리키기](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **추천 검색어(확인란)**|전경(링크 텍스트)|`SearchControl.PopupButtonMouseDownText`|  
|![검색 옵션 가리키기](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **search 옵션**|전경(링크 텍스트)|`SearchControl.PopupButtonMouseDownText`|  
|![검색 확인란 가리키기](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **추천 검색어(확인란)**|테두리|`SearchControl.PopupControlMouseOverBorder`|  
|![검색 옵션 가리키기](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **search 옵션**|테두리|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![제안 검색 누름](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **추천 검색어(확인란)**|확인란 배경|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 옵션 누름](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **search 옵션**|확인란 배경|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![제안 검색 누름](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **추천 검색어(확인란)**|확인란 배경|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 옵션 누름](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **search 옵션**|확인란 배경|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![제안 검색 누름](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **추천 검색어(확인란)**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxMouseDownText`|  
|![검색 옵션 누름](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **search 옵션**|전경(확인란 텍스트)|`SearchControl.PopupCheckboxMouseDownText`|  
|![제안 검색 누름](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **추천 검색어(확인란)**|링크 배경|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![검색 옵션 누름](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **search 옵션**|링크 배경|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> 최신 테마 UI에서는 사용되지 않지만 이 배경에 대한 그라데이션 중지점 및 값이 있습니다.|  
|![제안 검색 누름](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **추천 검색어(확인란)**|전경(링크 텍스트)|`SearchControl.PopupButtonMouseDownText`|  
|![검색 옵션 누름](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **search 옵션**|전경(링크 텍스트)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 하이퍼링크는 전경/배경 쌍이 없는 컨트롤입니다. 모든 경우에, 진한 회색 및 흰색 배경에서 올바르게 표시되는 하이퍼링크 전경색을 사용합니다. 하이퍼링크 컨트롤에 대한 색 토큰을 사용하지 않는 경우 빨간색으로 깜박이는 "누름"의 기본 시스템 색이 표시됩니다. 이는 컨트롤이 올바른 환경 색 토큰을 사용하지 않음을 나타냅니다.  
  
 ![하이퍼링크 검토](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 사용  
 사용자 지정 하이퍼링크를 만들어야 하는 경우  
  
 사용 안 함  
 하이퍼링크가 아닌 모든 항목  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![하이퍼링크 기본값](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|전경(텍스트)|`Environment.PanelHyperlink`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![하이퍼링크 가리키기](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|전경(텍스트)|`Environment.PanelHyperlinkHover`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![하이퍼링크 누름](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|전경(텍스트)|`Environment.PanelHyperlinkPressed`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![하이퍼링크 사용 안 함](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|전경(텍스트)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>정보 표시줄  
 정보 표시줄은 지정된 컨텍스트에 대한 자세한 정보를 제공하는 데 사용되며, 항상 문서 창이나 도구 창의 맨 위에 나타납니다.  
  
 ![정보 표시줄 검토](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 사용  
 사용자 지정 정보 표시줄을 만드는 경우  
  
 사용 안 함  
 정보 표시줄과 유사하지 않은 UI 요소  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![정보 표시줄](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **정보 표시줄**|배경|`Environment.InfoBackground`|  
|![정보 표시줄](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **정보 표시줄**|전경(텍스트)|`Environment.InfoText`|  
|![정보 표시줄](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **정보 표시줄**|테두리|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>스크롤 막대  
 스크롤 막대는 Visual Studio 환경에서 스타일이 지정되며 테마를 적용할 필요가 없습니다. 그러나 UI가 항상 Visual Studio 환경의이 부분과 일관 되 게 나타나도록 스크롤 막대에 사용 된 색을 활용할 수 있습니다.  
  
 ![스크롤 막대 검토](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 사용  
 Visual Studio 스크롤 막대와 일치시키려는 UI를 만드는 경우  
  
 사용 안 함  
 항상 스크롤 막대 UI와 일치시키지 않으려는 모든 항목  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![스크롤 막대](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **스크롤 막대**|스크롤 막대|`Environment.ScrollBarBackground`|  
|![스크롤 막대](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **스크롤 막대**|전경(Thumb)|`Environment.ScrollBarThumbBackground`|  
|![스크롤 막대 화살표](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **스크롤 화살표**|배경|`Environment.ScrollBarArrowBackground`<br /><br /> 스크롤 막대와 동일한 색으로 설정됨|  
|![스크롤 막대 화살표](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **스크롤 화살표**|전경(문자 모양)|`Environment.ScrollBarArrowGlyph`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![스크롤 막대 가리키기](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **스크롤 막대**|스크롤 막대|`Environment.ScrollBarBackground`|  
|![스크롤 막대 가리키기](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **스크롤 막대**|전경(Thumb)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![스크롤 막대 화살표 가리키기](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **스크롤 화살표**|배경|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> 스크롤 막대와 동일한 색으로 설정됨|  
|![스크롤 막대 화살표 가리키기](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **스크롤 화살표**|전경(문자 모양)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![스크롤 막대 누름](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **스크롤 막대**|스크롤 막대|`Environment.ScrollBarBackground`|  
|![스크롤 막대 누름](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **스크롤 막대**|전경(Thumb)|`Environment.ScrollBarThumbPressedBackground`|  
|![스크롤 막대 화살표 누름](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **스크롤 화살표**|배경|`Environment.ScrollBarArrowPressedBackground`<br /><br /> 스크롤 막대와 동일한 색으로 설정됨|  
|![스크롤 막대 화살표 누름](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **스크롤 화살표**|전경(문자 모양)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>트리 뷰  
 솔루션 탐색기, 서버 탐색기 및 클래스 뷰를 포함하여 여러 도구 창은 TreeView 범주의 색 이름으로 색이 제어되는 계층적 조직 체계를 구현합니다. 트리 뷰의 모든 항목에는 배경색과 텍스트 색이 있습니다. 중첩된 자식 요소가 있는 항목에는 항목이 확장 또는 축소되었는지 여부를 나타내는 문자 모양도 있습니다.  
  
 ![트리 뷰 검토](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 사용  
 계층적 조직 뷰를 구현해야 하는 모든 위치  
  
사용 안 함  
- 트리 뷰와 유사하지 않은 모든 항목  

- 지정된 배경/전경 조합 이외의 모든 조합  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![트리 보기](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|배경|`TreeView.Background`|  
|![트리 보기](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|전경(텍스트)|`TreeView.Background`|  
|![트리 보기](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|전경(문자 모양)|`TreeView.Glyph`|  
|![트리 보기](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|테두리|None|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|배경|`TreeView.Background`|  
|![트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|전경(텍스트)|`TreeView.Background`|  
|![트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|전경(문자 모양)|`TreeView.GlyphMouseOver`|  
|![트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|테두리|None|  
  
 **위로 끌기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![트리 뷰 끌기](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|배경|`TreeView.DragOverItem`|  
|![트리 뷰 끌기](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|전경(텍스트)|`TreeView.DragOverItem`|  
|![트리 뷰 끌기](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|전경(문자 모양)|`TreeView.DragOverItemGlyph`|  
|![트리 뷰 끌기](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|테두리|None|  
  
 **Selected**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 트리 뷰](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|배경|`TreeView.SelectedItemActive`|  
|![포커스가 있는 트리 뷰](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|전경(텍스트)|`TreeView.SelectedItemActive`|  
|![포커스가 있는 트리 뷰](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|전경(문자 모양)|`TreeView.SelectedItemActiveGlyph`|  
|![포커스가 있는 트리 뷰](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|테두리|`TreeView.FocusVisualBorder`|  
|![포커스가 없는 트리 뷰](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **포커스 없음**|배경|`TreeView.SelectedItemInactive`|  
|![포커스가 없는 트리 뷰](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **포커스 없음**|전경(텍스트)|`TreeView.SelectedItemInactive`|  
|![포커스가 없는 트리 뷰](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **포커스 없음**|전경(문자 모양)|`TreeView.SelectedItemInactiveGlyph`|  
|![포커스가 없는 트리 뷰](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **포커스 없음**|테두리|None|  
  
 **선택한 항목 가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|배경|`TreeView.SelectedItemActive`|  
|![포커스가 있는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|전경(텍스트)|`TreeView.SelectedItemActive`|  
|![포커스가 있는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|전경(문자 모양)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![포커스가 있는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|테두리|없음`TreeView.FocusVisualBorder`|  
|![포커스가 없는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **포커스 없음**|배경|`TreeView.SelectedItemInactive`|  
|![포커스가 없는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **포커스 없음**|전경(텍스트)|`TreeView.SelectedItemInactive`|  
|![포커스가 없는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **포커스 없음**|전경(문자 모양)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![포커스가 없는 트리 뷰 가리키기](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **포커스 없음**|테두리|None|  
  
#### <a name="button-controls"></a>단추 컨트롤  
 ![단추 컨트롤 검토](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 사용  
 Visual Studio 테마(밝게, 어둡게, 파랑 또는 시스템 고대비 테마)와 통합하려는 문서 저장소의 단추  
  
 사용 안 함  
 Visual Studio 테마에 속하지 않는 사용자 지정 배경에 표시되는 단추  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|단추|`CommonControls.Button`|  
|![Button](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|단추 테두리|`CommonControls.ButtonBorder`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![단추 사용 안 함](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|단추|`CommonControls.ButtonDisabled`|  
|![단추 사용 안 함](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|단추 테두리|`CommonControls.ButtonBorderDisabled`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![단추 가리키기](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|단추|`CommonControls.ButtonHover`|  
|![단추 가리키기](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|단추 테두리|`CommonControls.ButtonBorderHover`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![단추 누름](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|단추|`CommonControls.ButtonPressed`|  
|![단추 누름](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|단추 테두리|`CommonControls.ButtonBorderPressed`|  
  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 단추](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|단추|`CommonControls.ButtonFocused`|  
|![포커스가 있는 단추](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|단추 테두리|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>확인란 컨트롤  
 ![확인란 검토](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 사용  
 문서 저장소 내에 포함된 확인란 컨트롤  
  
 사용 안 함  
 확인란 컨트롤이 아닌 모든 UI  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![확인란](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|배경|`CommonControls.CheckBoxBackground`|  
|![확인란](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|테두리|`CommonControls.CheckBoxBorder`|  
|![확인란](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|텍스트|`CommonControls.CheckBoxText`|  
|![확인란](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|문자 모양|`CommonControls.CheckBoxGlyph`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![확인란 사용 안 함](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|배경|`CommonControls.CheckBoxBackgroundDisabled`|  
|![확인란 사용 안 함](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|테두리|`CommonControls.CheckBoxBorderDisabled`|  
|![확인란 사용 안 함](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|텍스트|`CommonControls.CheckBoxTextDisabled`|  
|![확인란 사용 안 함](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|문자 모양|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![확인란 가리키기](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|배경|`CommonControls.CheckBoxBackgroundHover`|  
|![확인란 가리키기](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|테두리|`CommonControls.CheckBoxBorderHover`|  
|![확인란 가리키기](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|텍스트|`CommonControls.CheckBoxTextHover`|  
|![확인란 가리키기](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|문자 모양|`CommonControls.CheckBoxGlyphHover`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![확인란 누름](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|배경|`CommonControls.CheckBoxBackgroundPressed`|  
|![확인란 누름](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|테두리|`CommonControls.CheckBoxBorderPressed`|  
|![확인란 누름](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|텍스트|`CommonControls.CheckBoxTextPressed`|  
|![확인란 누름](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|문자 모양|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 확인란](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|배경|`CommonControls.CheckBoxBackgroundFocused`|  
|![포커스가 있는 확인란](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|테두리|`CommonControls.CheckBoxBorderFocused`|  
|![포커스가 있는 확인란](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|텍스트|`CommonControls.CheckBoxTextFocused`|  
|![포커스가 있는 확인란](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|문자 모양|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>드롭 상자/콤보 상자 컨트롤  
 ![드롭다운&#45;&#47;콤보 상자 검토](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
사용  
문서 저장소에 속하는 드롭다운 및 콤보 상자  

사용 안 함  
- 드롭다운 또는 콤보 상자가 아닌 모든 UI  

- 명령 모음의 [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) 또는 [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) 에 대해  
  
  **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|배경|`CommonControls.ComboBoxBackground`|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|테두리|`CommonControls.ComboBoxBorder`|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|텍스트|`CommonControls.ComboBoxText`|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|구분 기호|`CommonControls.ComboBoxSeparator`|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|문자 모양|`CommonControls.ComboBoxGlyph`|  
|![드롭다운&#45;&#47;콤보 상자](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|문자 모양 배경|`CommonControls.ComboBoxGlyphBackground`|  
  
 **사용 안 함**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|배경|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|테두리|`CommonControls.ComboBoxBorderDisabled`|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|텍스트|`CommonControls.ComboBoxTextDisabled`|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|구분 기호|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|문자 모양|`CommonControls.ComboBoxGlyphDisabled`|  
|![Drop&#45;down&#47;콤보 상자 사용 안 함](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|문자 모양 배경|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|배경|`CommonControls.ComboBoxBackgroundHover`|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|테두리|`CommonControls.ComboBoxBorderHover`|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|텍스트|`CommonControls.ComboBoxTextHover`|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|구분 기호|`CommonControls.ComboBoxSeparatorHover`|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|문자 모양|`CommonControls.ComboBoxGlyphHover`|  
|![마우스로 가리키기&#47;콤보 상자&#45;드롭다운](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|문자 모양 배경|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|배경|`CommonControls.ComboBoxBackgroundPressed`|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|테두리|`CommonControls.ComboBoxBorderPressed`|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|텍스트|`CommonControls.ComboBoxTextPressed`|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|구분 기호|`CommonControls.ComboBoxSeparatorPressed`|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|문자 모양|`CommonControls.ComboBoxGlyphPressed`|  
|![드롭다운&#45;드롭다운&#47;콤보 상자 누름](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|문자 모양 배경|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Focused**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|배경|`CommonControls.ComboBoxBackgroundFocused`|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|테두리|`CommonControls.ComboBoxBorderFocused`|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|텍스트|`CommonControls.ComboBoxTextFocused`|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|구분 기호|`CommonControls.ComboBoxSeparatorFocused`|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|문자 모양|`CommonControls.ComboBoxGlyphFocused`|  
|![포커스를&#45;&#47;콤보 상자에 포커스 놓기](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|문자 모양 배경|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **텍스트 입력 선택**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![드롭다운&#45;&#47;콤보 상자 텍스트 입력](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|강조 표시|`CommonControls.ComboBoxTextInputSelection`|  
  
 **누름 – 목록 항목 보기**  
  
|구성 요소|요소|토큰 이름: Color.category|  
|---------------|-------------|--------------------------------|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|배경|`CommonControls.ComboBoxListBackground`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|배경|`CommonControls.ComboBoxListBackgroundHover`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|배경|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|배경|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|테두리|`CommonControls.ComboBoxListBorder`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|테두리|`CommonControls.ComboBoxListBorderHover`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|테두리|`CommonControls.ComboBoxListBorderPressed`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|테두리|`CommonControls.ComboBoxListBorderFocused`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|항목 텍스트|`CommonControls.ComboBoxListItemText`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|항목 텍스트|`CommonControls.ComboBoxListItemTextHover`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|항목 텍스트|`CommonControls.ComboBoxListItemTextPressed`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|항목 텍스트|`CommonControls.ComboBoxListItemTextFocused`|  
|![드롭다운&#45;&#47;콤보 상자 목록 뷰](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|배경 그림자|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>표 형식 데이터(그리드) 컨트롤  
 표 형식 데이터 컨트롤은 그리드 컨트롤이라고도 하며, 여러 열에 많은 양의 데이터를 표시하는 데 사용할 수 있는 Visual Studio의 공용 컨트롤입니다. 표준 표 형식 데이터 컨트롤은 오류 목록 도구 창, IntelliTrace 보고서, 메모리 힙 보기 등 Visual Studio 내의 여러 위치에서 찾을 수 있습니다. 항상 제공된 표준 표 형식 데이터 컨트롤을 사용합니다. 드물긴 하지만 표준 표 형식 데이터 컨트롤에 액세스할 수 없는 경우도 있습니다. 이러한 경우 다음 토큰 이름을 사용하여 Visual Studio의 다른 표 형식 데이터 컨트롤과 UI의 일관성을 유지합니다.  
  
 ![표 형식 데이터 &#40;표 형태 컨트롤&#41; 검토](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 사용  
 표 형식 또는 그리드 컨트롤  
  
 사용 안 함  
 표 형식 또는 그리드 컨트롤이 아닌 모든 UI  
  
##### <a name="column-headers"></a>열 머리글  
 열 머리글은 배경, 테두리, 제목 텍스트 및 그리드가 해당 열을 기준으로 정렬된 경우 일반적으로 사용되는 선택적 문자 모양으로 구성됩니다.  
  
|시스템 상태|요소|토큰 이름: Category.color|  
|-----------|-------------|--------------------------------|  
|기본값|배경|`Header.Default`|  
|기본값|전경(텍스트)|`Environment.CommandBarTextActive`|  
|기본값|전경(문자 모양)|`Header.Glyph`|  
|기본값|테두리|`Header.SeparatorLine`|  
|가리키기|배경|`Header.MouseOver`|  
|가리키기|전경(텍스트)|`Environment.CommandBarTextHover`|  
|가리키기|전경(문자 모양)|`Header.MouseOverGlyph`|  
|가리키기|테두리|`Header.SeparatorLine`|  
|누름|배경|`CommonControls.CheckBoxBackgroundPressed`|  
|누름|전경(텍스트)|`CommonControls.CheckBoxBorderPressed`|  
|누름|전경(문자 모양)|`CommonControls.CheckBoxTextPressed`|  
|누름|테두리|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>목록 뷰 항목  
 목록 뷰 항목은 배경과 콘텐츠로 구성됩니다. 콘텐츠는 텍스트, 아이콘 또는 둘 다일 수 있습니다.  
  
|시스템 상태|요소|토큰 이름: Category.color|  
|-----------|-------------|--------------------------------|  
|기본값|배경|투명|  
|기본값|전경(텍스트)|`Environment.CommandBarTextActive`|  
|기본값|테두리|None|  
|선택됨(활성)|배경|`TreeView.SelectedItemActive`|  
|선택됨(활성)|전경(텍스트)|`TreeView.SelectedItemActiveText`|  
|선택됨(활성)|테두리|None|  
|선택됨(비활성)|배경|`TreeView.SelectedItemInactive`|  
|선택됨(비활성)|전경(텍스트)|`TreeView.SelectedItemInactiveText`|  
|선택됨(비활성)|테두리|None|  
  
### <a name="manifest-designer"></a>매니페스트 디자이너  
 매니페스트 디자이너는 Windows 8 및 Windows Phone 8 프로젝트에서 매니페스트 파일을 보다 쉽게 편집할 수 있도록 하는 하나의 방법으로 설계되었습니다. 사용할 수 있는 공유 프레임워크가 없는 동안에는 방향/탐색 탭의 디자인 레이아웃 및 색과 전체적인 구조를 일치시키는 것이 좋습니다. 레이아웃 정보에 대한 자세한 내용은 [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md)을 참조하세요.  
  
 ![매니페스트 디자이너 검토](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
사용  
- 매니페스트 디자이너와 유사한 디자이너  

- 문서 저장소 내에서 편집기 맨 위에 있는 공용 탭 컨트롤을 사용하는 대신  

사용 안 함  
- 6개가 넘는 탭이 있는 경우  

- 매니페스트 디자이너처럼 구조화되지 않은 모든 UI  
  
|시스템 상태|구성 요소|요소|토큰 이름: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|기본값(선택됨)|탭|배경|`ManifestDesigner.TabActive`|  
|기본값(선택됨)|탭|테두리|None|  
|기본값(선택됨)|설명 창|배경|`ManifestDesigner.DescriptionPane`|  
|기본값(선택됨)|콘텐츠 페이지|배경|`ManifestDesigner.Background`|  
|기본값(선택됨)|콘텐츠 페이지|대화 상자 도우미 텍스트|`ManifestDesigner.WatermarkText`<br /><br /> 이 토큰 이름은 해당 기능과 일치하지 않습니다.|  
|선택되지 않음|탭|배경|`ManifestDesigner.Tab.Inactive`|  
|가리키기|탭|배경|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>태그 지정  
 Visual Studio는 사용자가 추적을 위해 검색 가능한 키워드를 선언할 수 있는 태깅을 지원합니다. 예를 들어 프로젝트 관리자와 개발자는 TFS(Team Foundation Server)를 사용하여 작업 항목에 태깅할 수 있습니다. 아래 표에서는 태그 자체와 가리키기 및 선택한 상태에서 표시되는 "닫기 아이콘" 문자 모양에 대한 색 이름을 제공합니다.  
  
 ![태그 지정 검토](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 사용  
 태깅을 지원하는 UI  
  
 사용 안 함  
 다른 모든 유형의 UI  
  
#### <a name="tag"></a>태그  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **기본값**|배경|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **기본값**|전경(텍스트)|`Tag.Background`|  
|![태그 가리키기](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **가리키기**|배경|`Tag.HoverBackground`|  
|![태그 가리키기](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **가리키기**|전경(텍스트)|`Tag.HoverBackgroundText`|  
|![태그 누름](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|배경|`Tag.PressedBackground`|  
|![태그 누름](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|전경(텍스트)|`Tag.PressedBackgroundText`|  
|![선택한 태그](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selected**|배경|`Tag.SelectedBackground`|  
|![선택한 태그](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selected**|전경(텍스트)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>문자 모양(닫기 아이콘)  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![태그 &#40;문자 모양&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **기본값(태그 기본값)**|배경|N/A|  
|![태그 &#40;문자 모양&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **기본값(태그 기본값)**|전경(문자 모양)|`Tag.TagHoverGlyph`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![태그 &#40;문자 모양&#41; 가리키기](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **가리키기(태그 기본값)**|배경|`Tag.TagHoverGlyphHoverBackground`|  
|![태그 &#40;문자 모양&#41; 가리키기](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **가리키기(태그 기본값)**|전경(문자 모양)|`Tag.TagHoverGlyphHover`|  
|![태그 &#40;문자 모양&#41; 가리키기](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **가리키기(태그 기본값)**|테두리|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Pressed**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![태그 &#40;문자 모양&#41; 누름](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **누름(태그 기본값)**|배경|`Tag.TagHoverGlyphPressedBackground`|  
|![태그 &#40;문자 모양&#41; 누름](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **누름(태그 기본값)**|전경(문자 모양)|`Tag.TagHoverGlyphPressed`|  
|![태그 &#40;문자 모양&#41; 누름](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **누름(태그 기본값)**|테두리|`Tag.TagHoverGlyphPressedBorder`|  
  
 **선택한 태그/문자 모양 기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![선택한 태그](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **기본값(선택한 태그)**|배경|N/A|  
|![선택한 태그](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **기본값(선택한 태그)**|전경(문자 모양)|`Tag.TagSelectedGlyph`|  
  
 **선택한 태그/문자 모양 가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![선택한 태그 가리키기](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **가리키기(선택한 태그)**|배경|`Tag.TagSelectedGlyphHoverBackground`|  
|![선택한 태그 가리키기](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **가리키기(선택한 태그)**|전경(문자 모양)|`Tag.TagSelectedGlyphHover`|  
|![선택한 태그 가리키기](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **가리키기(선택한 태그)**|테두리|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **선택한 태그/문자 모양 누름**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![선택한 태그 누름](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **누름(선택한 태그)**|배경|`Tag.TagSelectedGlyphPressedBackground`|  
|![선택한 태그 누름](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **누름(선택한 태그)**|전경(문자 모양)|`Tag.TagSelectedGlyphPressed`|  
|![선택한 태그 누름](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **누름(선택한 태그)**|테두리|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>셸  
  
#### <a name="background"></a>배경  
 환경 배경은 두 계층으로 이루어져 있습니다. 아래쪽 계층은 전체 IDE에 적용되는 단색입니다. 위쪽 계층은 명령 선반 아래와 IDE의 왼쪽 및 오른쪽 가장자리에서 도구 창 자동 숨기기 채널 사이에 적용됩니다. Visual Studio 2013에서는 위쪽 및 아래쪽 배경 계층이 밝은 테마와 어두운 테마에서 동일한 색으로 설정됩니다.  
  
 ![셸 배경 검토](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 사용  
 Visual Studio 환경의 배경과 일치시키려는 위치  
  
사용 안 함  
- 배경 화면이 아닌 위치에 대한 채우기  

- 전경 요소를 배치하려는 배경  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|아래쪽 계층|배경|`Environment.EnvironmentBackground`|  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|위쪽 계층|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|위쪽 계층|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|위쪽 계층|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|위쪽 계층|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>명령 선반  
 명령 선반 배경에는 두 가지 토큰 이름 집합이 사용되며, 각각 메뉴 모음이 있는 위치와 명령 모음이 있는 위치에 사용됩니다. 개별 명령 모음 그룹에는 자체 배경색 값이 있으며, "명령 모음" 섹션에서 자세히 설명합니다. 메뉴 모음 및 명령 모음 텍스트는 각각 메뉴 및 명령 모음 섹션에서 설명합니다.  
  
 ![명령 선반 검토](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
사용  
- 메뉴 또는 도구 모음을 배치하는 영역  

- 올바른 배경/전경 토큰 이름 조합을 사용 합니다.  
  
  사용 안 함  
  명령 선반과 유사하지 않은 영역  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|메뉴 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfHighlightGradientBegin`|  
|메뉴 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|메뉴 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfHighlightGradientEnd`|  
|명령 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|명령 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|명령 모음|배경<br /><br /> *그라데이션 중지점은 Visual Studio 2013 밝은 테마 및 어두운 테마에서 동일한 색 값으로 설정됩니다.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>도구 상자  
 도구 상자는 Visual Studio에서 자주 사용되는 공통 도구 창 중 하나입니다. 기본적으로 특수 테마와 스타일이 적용된 트리 컨트롤입니다.  
  
 ![도구 상자 검토](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 사용  
 항상 셸 도구 상자와 일치시키려는 도구 창을 디자인하는 경우  
  
 사용 안 함  
 도구 상자 UI와 유사하지 않은 모든 항목 또는 셸 도구 상자 색이 변경되면 UI에서 문제가 발생하는지 여부가 확실하지 않은 경우  
  
 **기본값**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **부모 노드**|배경|`Environment.ToolboxContent`<br /><br /> 제목<br /><br /> `Environment.ToolWindowBackground`<br /><br /> 개별 항목 또는 사용할 수 있는 컨트롤이 없는 경우 전체 창|  
|![도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **자식 노드**|배경|`Environment.ToolboxContent`<br /><br /> 제목<br /><br /> `Environment.ToolWindowBackground`<br /><br /> 개별 항목 또는 사용할 수 있는 컨트롤이 없는 경우 전체 창|  
|![도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **부모 노드**|테두리|None|  
|![도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **자식 노드**|테두리|None|  
|![도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **부모 노드**|전경(문자 모양)|`Environment.ToolboxContent`|  
|![도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **자식 노드**|전경(문자 모양)|`Environment.ToolboxContent`|  
|![도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **부모 노드**|전경(텍스트)|`Environment.ToolboxContent`|  
|![도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **자식 노드**|전경(텍스트)|`Environment.ToolboxContent`|  
  
 **가리키기**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![도구 상자 자식 노드 가리키기](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **도구 상자 자식 노드 가리키기**|배경|`Environment.ToolboxContentMouseOver`<br /><br /> 개별 항목만|  
|![도구 상자 자식 노드 가리키기](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **도구 상자 자식 노드 가리키기**|테두리|None|  
|![도구 상자 자식 노드 가리키기](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **도구 상자 자식 노드 가리키기**|전경(텍스트)|`Environment.ToolboxContentMouseOver`<br /><br /> 개별 항목만|  
  
 **Selected**  
  
|구성 요소|요소|토큰 이름: Category.color|  
|---------------|-------------|--------------------------------|  
|![포커스가 있는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **포커스가 있는 부모 노드**|배경|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **포커스가 있는 자식 노드**|배경|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **포커스가 있는 부모 노드**|테두리|`TreeView.FocusVisualBorder`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **포커스가 있는 자식 노드**|테두리|`TreeView.FocusVisualBorder`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **포커스가 있는 부모 노드**|전경(문자 모양)|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **포커스가 있는 자식 노드**|전경(문자 모양)|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **포커스가 있는 부모 노드**|전경(텍스트)|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 있는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **포커스가 있는 자식 노드**|전경(텍스트)|`TreeView.SelectedItemActive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **포커스가 없는 부모 노드**|배경|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **포커스가 없는 자식 노드**|배경|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **포커스가 없는 부모 노드**|테두리|None|  
|![포커스가 없는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **포커스가 없는 자식 노드**|테두리|None|  
|![포커스가 없는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **포커스가 없는 부모 노드**|전경(문자 모양)|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **포커스가 없는 자식 노드**|전경(문자 모양)|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 부모 노드](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **포커스가 없는 부모 노드**|전경(텍스트)|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
|![포커스가 없는 도구 상자 자식 노드](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **포커스가 없는 자식 노드**|전경(텍스트)|`TreeView.SelectedItemInactive`<br /><br /> [Tree view](../misc/shared-colors.md#BKMK_TreeView) 범주|  
  
## <a name="color-value-reference"></a>색 값 참조  
  
|구성 요소|부분|요소|시스템 상태|밝게|어둡게|파랑|고대비|
|---------|----|-------|-----|-----|----|----|----|  
|구분선|||기본값|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Expander 문자 모양||전경|기본값|||||  
|Expander 문자 모양||전경|가리키기|||||  
|Expander 문자 모양||배경|기본값|||||  
|Expander 문자 모양||배경|가리키기|||||  
|Expander 문자 모양||테두리|기본값|||||  
|Expander 문자 모양||테두리|가리키기|||||