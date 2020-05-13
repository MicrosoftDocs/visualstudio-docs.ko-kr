---
title: 비주얼 스튜디오용 레이아웃 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698398"
---
# <a name="layout-for-visual-studio"></a>Visual Studio의 레이아웃
대부분의 Visual Studio 대화 상자는 표준 Windows 데스크톱 대화 [상자 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)원칙을 따르는 테마가 없는 대화 상자인 유틸리티 대화 상자 [레이아웃입니다.](/windows/desktop/uxguide/win-dialog-box) Visual Studio가 UI를 새로 고치기 위해 이동함에 따라 더 눈에 띄는 대화 상자 중 일부는 제품 정의 환경으로 설정하는 새로운 디자인을 갖습니다. 이러한 [테마 대화 상자 레이아웃에는](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 테마 모양이 있습니다.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>유틸리티 대화 상자 레이아웃

- 유틸리티 대화 상자 내의 모든 컨트롤은 위쪽/왼쪽에서 시작하여 아래쪽으로 흐르야 합니다.

- 대화 상자에서 컨트롤을 중앙에 두지 마십시오.

- 모든 대화 상자 텍스트에 환경 글꼴을 사용합니다. 시각적 사양을 작성할 때특정 글꼴과 크기를 선택하는 대신 환경 글꼴을 지정합니다. [환경 글꼴을](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)참조하십시오.

- 일관된 제어 간격과 배치를 사용하여 장인 정신의 품질 목표를 지원합니다.

- 대화 상자는 더 많은 수의 컨트롤, 고유한 컨트롤 의 병치 또는 둘 다에서 더 복잡해질 수 있습니다. 이러한 복잡한 상황에서는 컨트롤 그룹 간에 적절한 공간을 허용하여 사용자에게 구문 분석할 논리적 흐름을 제공합니다.

### <a name="utility-dialog-layout-examples"></a>유틸리티 대화 상자 레이아웃 예제
 모든 치수는 픽셀로 표현됩니다.

 ![컨트롤 위의 레이블에 대한 대화 상자 간격 조정](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **그림 08.01-a: 컨트롤 위의 레이블이 있는 유틸리티 대화 상자에 대한 간격 지침**

 ![컨트롤 왼쪽의 레이블에 대한 대화 상자 간격 조정](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **그림 08.01-b: 컨트롤 왼쪽에 레이블이 있는 유틸리티 대화 상자에 대한 간격 지침**

### <a name="layout-details"></a>레이아웃 세부 정보

#### <a name="margins"></a>여백

- 모든 대화 상자에는 모든 가장자리 주위에 12픽셀 테두리가 있어야 합니다.

- 그룹 프레임 내의 여백은 프레임 가장자리에서 9픽셀이어야 합니다.

- 탭 컨트롤 내의 여백은 탭 컨트롤의 가장자리에서 6픽셀이어야 합니다.

#### <a name="command-buttons"></a>명령 단추

- 명령 단추는 콘텐츠가 아닌 대화 상자 프레임에서 작동합니다. 오른쪽 하단에 배치해야 하며 단추를 뚜렷하게 구분할 수 있는 충분한 가변 공간이 있어야 합니다.

- 대화 상자 내에서 작동하는 가로 단추가 있는 경우 대체 명령 단추 구성은 오른쪽 상단에 있는 세로 스택입니다. 아래의 [내부 명령 버튼을](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 참조하십시오.

- 명령 단추의 왼쪽(대화 상자의 왼쪽 아래/가운데)의 공간은 대화 상자 작업 컨트롤의 "밴드"의 일부로 간주됩니다. 해당 공간에 침입해야 하는 유일한 방법은 전체 작업 또는 대화 상자와 관련된 도움말 링크입니다.

- 명령 단추는 75x23 픽셀이어야 합니다.

- 명령 버튼은 6 픽셀 떨어져 있어야합니다.

  ![기본 단추 맞춤](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **그림 08.01-c: 기본 버튼 정렬**

#### <a name="labels"></a>레이블

- 모든 레이블을 왼쪽에 정렬합니다.

- 컨트롤 위에 있는 레이블의 경우 컨트롤 아래의 컨트롤과 정확하게 좌측 정렬해야 하며 레이블 의 맨 아래는 다른 컨트롤의 위쪽(예: 콤보 상자)의 위쪽 5픽셀이어야 합니다.

- 컨트롤의 왼쪽에 있는 레이블의 경우 레이블과 입력 컨트롤 사이의 최소 너비는 10픽셀입니다. 텍스트 상자, 콤보 상자 또는 기타 컨트롤을 정렬하기 위해 암시적 두 번째 열을 설정해야 합니다.

- 레이블은 문장 대/소문자이며 그 뒤에 콜론이 있습니다. [텍스트 스타일을](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)참조하십시오.

#### <a name="distance-between-controls"></a>컨트롤 사이의 거리
 스택컨트롤이 합리적으로 제어됩니다. 누적된 컨트롤 사이의 간격에 대한 절대 지침은 없습니다. 컨트롤 간의 압박감은 대화 상자마다 약간 다를 수 있습니다. 권장 간격은 세로 제어/레이블 쌍의 경우 20픽셀, 수평 제어/레이블 쌍의 경우 9픽셀입니다. 가로 쌍의 최소 제어 간격은 6픽셀입니다.

 ![컨트롤 사이의 권장 거리](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **그림 08.01-d: 컨트롤 간의 거리에 대한 권장 사항**

#### <a name="control-indentation"></a>제어 들여쓰기
 컨트롤이 중첩되면 내부 컨트롤을 위의 컨트롤의 왼쪽 가장자리(일반적으로 레이블)와 수평으로 정렬합니다.

 ![중첩된 컨트롤 맞춤](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **그림 08.01-e: 중첩 된 컨트롤 정렬**

#### <a name="control-width"></a>제어 너비
 텍스트 상자 또는 기타 유사한 컨트롤의 너비는 필드의 평균 입력보다 더 이상 없어야 합니다. 평균 영어 단어는 5자입니다. 예를 들어 긴 경로 이름이 필요한 텍스트 상자는 가로 레이아웃이 허용하는 한 길어야 하며 플랫폼 이름에 대한 드롭다운은 가장 긴 항목을 허용하는 길이여야 합니다.

#### <a name="helper-text"></a>도우미 텍스트

- 대화 상자에는 대화 상자의 목적에 대한 자세한 정보를 제공하는 도우미 텍스트가 표시될 수 있습니다. 이것은 일반적으로 상단에 앉아 1-2 문장이 될 수 있습니다.

- 선 길이는 사용자가 구문 분석하고 읽을 수 있는 편안한 너비여야 합니다. 중간 대화 상자의 너비는 550픽셀이 넘지 않아야 합니다.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>내부 명령 버튼
 보다 복잡한 대화 상자에서 내부 컨트롤에는 자체 관련 단추가 있을 수 있으며, 이 단추는 대화 상자의 커밋 단추의 위치에 영향을 줄 수 있습니다.

- 오른쪽 아래 모서리에서 수평**방향이** **정상 취소가**/있을 때 내부 단추의 수직 정렬(열)을 사용합니다.

- **OK**/**취소가** 오른쪽 위 모서리에서 수직 방향으로 조정되는 경우 내부 단추의 수평 정렬(행)을 사용합니다. 이 상황은 덜 일반적입니다.

- 내부 버튼 크기는 75x23 픽셀의 표준 버튼 크기를 대상으로해야하며 가능한 경우 **OK**/**취소** 버튼의 크기와 일치합니다. 단추 레이블로 인해 단추가 표준 단추 크기를 초과하면 해당 집합의 다른 단추는 더 넓은 크기와 정렬되어야 합니다.

  ![가로 확인 및 취소 단추](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **그림 08.01-f: 수평 확인/취소가 있는 수직 내부 버튼**

  ![세로 확인 및 취소 단추](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **그림 08.01-g: 수직 OK/취소가 있는 수평 내부 버튼**

#### <a name="browse-button"></a>[찾아보기...] 단추
 **[찾아보기...]** 텍스트 상자를 따르는 단추는 "찾아보기..." 타원을 포함하여 전체적으로. 공간이 좁거나 화면에 **[찾아보기...]** 버튼이 여러 개 있는 경우 단추를 타원으로만 줄일 수 있습니다.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>테마대화상자 레이아웃
 Visual Studio의 테마 대화 상자는 모양이 더 밝고 공백이 더 넓습니다. 타이포그래피는 더 많은 강조와 흥미를 제공하므로 더 많은 열린 줄 간격과 글꼴 크기와 가중치의 변형을 제공합니다. 가능한 경우 크롬 및 제목 표시줄이 축소되거나 제거되었습니다. 이러한 대화 상자의 레이아웃은 다음 기본 패턴을 따라야 합니다.

1. 대화 상자의 배경은 흰색입니다.

2. 중간 값 회색의 1픽셀 규칙 테두리가 있습니다.

3. 대화 상자 제목은 더 이상 제목 표시줄에 있지 않지만 더 큰 포인트 크기에서 시각적 관심과 강조를 제공합니다. (텍스트 [스타일의](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)글꼴 크기 섹션을 참조하십시오.)

4. 설명과 같은 추가 텍스트와 결합된 레이블은 **환경 글꼴 + 굵게**표시되어야 합니다.

5. 내부 열은 밝은 회색으로 1픽셀 규칙으로 구분됩니다.

6. 기본 링크에는 밑줄이 없습니다. 가리키고 누른 상태는 색상 변화와 밑줄이 있습니다.

7. 커밋 단추(예: **OK**/**취소)는**오른쪽 아래 모서리에 있습니다.

### <a name="themed-dialog-layout-examples"></a>테마대화상자 레이아웃 예제
 ![테마가 지정된 대화 상자 레이아웃](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **그림 08.01-h: 테마 대화 상자**

 ![테마가 지정된 대화 크기](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **그림 08.01-i: 테마 대화 상자 - 차원**

 ![테마가 지정된 대화 상자 글꼴](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **그림 08.01-j: 테마 대화 상자 - 글꼴**

 ![테마가 지정된 대화 상자 색](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **그림 08.01-k: 테마 대화 상자 - 색상**

## <a name="see-also"></a>참조
- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [컨트롤(윈도우)](/windows/desktop/uxguide/controls)
- [대화 상자 (윈도우)](/windows/desktop/uxguide/win-dialog-box)
