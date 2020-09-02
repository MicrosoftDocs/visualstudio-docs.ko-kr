---
title: Layout
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09656b9afac82eec8981f8573af87391c99a3688
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179683"
---
# <a name="layout-for-visual-studio"></a>Visual Studio의 레이아웃
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

대부분의 Visual Studio 대화 상자는 표준 [Windows 바탕 화면 대화 상자 레이아웃 원칙](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)에 따라 테마가 적용 되지 않은 대화 인 [유틸리티 대화 상자 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)입니다. Visual Studio가 UI를 새로 고치기 위해 이동 하는 경우 더 두드러진 대화 상자 중 일부에는 제품 정의 환경으로 설정 하는 새로운 디자인이 있습니다. 이러한 [테마 대화 상자 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 에는 테마가 적용 된 모양이 있습니다.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> 유틸리티 대화 상자 레이아웃

- 유틸리티 대화 상자에 있는 모든 컨트롤은 위쪽/왼쪽에서 시작 하 고 아래로 이동 해야 합니다.

- 대화 상자에 컨트롤을 배치 하 여 크게 영역을 채우지 않습니다.

- 모든 대화 상자 텍스트에 환경 글꼴을 사용 합니다. 시각적 사양을 작성할 때 특정 글꼴 및 크기를 선택 하는 대신 환경 글꼴을 지정 합니다. [환경 글꼴을](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)참조 하세요.

- 일관 된 제어 간격과 배치를 사용 하 여 craftsmanship의 품질 목표를 지원 합니다.

- 대화는 다 수의 컨트롤, 고유 juxtaposition 컨트롤 또는 둘 다에서 복잡 해질 수 있습니다. 이러한 복잡 한 경우에는 컨트롤 그룹화 사이에 적절 한 공간을 허용 하 여 사용자에 게 구문 분석할 논리 흐름을 제공 합니다.

### <a name="utility-dialog-layout-examples"></a>유틸리티 대화 상자 레이아웃 예
 모든 차원은 픽셀로 표현 됩니다.

 ![컨트롤 위의 레이블에 대한 대화 상자 간격 조정](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **그림 08.01-a: 컨트롤 위의 레이블이 있는 유틸리티 대화 상자의 간격 지침**

 ![컨트롤 왼쪽의 레이블에 대한 대화 상자 간격 조정](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **그림 08.01-b: 컨트롤의 왼쪽에 레이블이 있는 유틸리티 대화 상자의 간격 지침**

### <a name="layout-details"></a>레이아웃 정보

#### <a name="margins"></a>여백

- 모든 대화 상자에는 모든 가장자리 주위에 12 픽셀 테두리가 있어야 합니다.

- 그룹 프레임 내의 여백은 프레임 가장자리에서 9 픽셀 사이 여야 합니다.

- 탭 컨트롤 내의 여백은 탭 컨트롤의 가장자리에서 6 픽셀 사이 여야 합니다.

#### <a name="command-buttons"></a>명령 단추

- 명령 단추는 콘텐츠가 아닌 대화 상자 프레임에서 작동 합니다. 이러한 단추는 오른쪽 아래에 배치 해야 하며, 단추를 별도로 설정 하기 위한 충분 한 변수 공간이 있어야 합니다.

- 대화 상자 내에서 작동 하는 가로 단추가 있는 경우 대체 명령 단추 구성은 오른쪽 위에 있는 세로 스택입니다. 아래의 [내부 명령 단추](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 를 참조 하세요.

- 명령 단추 (대화 상자의 왼쪽 아래)의 왼쪽에 있는 공간은 대화 작업 컨트롤의 "밴드"의 일부로 간주 됩니다. 해당 공간에 방해가 하는 유일한 사항은 전체 작업 또는 대화 상자와 관련 된 도움말 링크입니다.

- 명령 단추는 75x23 픽셀 이어야 합니다.

- 명령 단추는 6 픽셀 떨어져 있어야 합니다.

  ![기본 단추 맞춤](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801-c_ButtonAlign")

  **그림 08.01-c: 기본 단추 맞춤**

#### <a name="labels"></a>레이블

- 모든 레이블을 왼쪽 맞춤 합니다.

- 컨트롤 위에 있는 레이블의 경우 해당 레이블은 아래에 있는 컨트롤을 정확 하 게 왼쪽에 맞추고 레이블 아래쪽은 다른 컨트롤 (예: 콤보 상자)의 위쪽에서 5 픽셀 이어야 합니다.

- 컨트롤의 왼쪽에 있는 레이블의 경우 레이블과 입력 컨트롤 사이의 최소 너비는 10 픽셀입니다. 텍스트 상자, 콤보 상자 또는 기타 컨트롤을 정렬 하기 위해 암시 된 두 번째 열을 설정 해야 합니다.

- 레이블은 문장의 대/소문자 이며 그 뒤에 콜론이 나옵니다. [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)을 참조 하세요.

#### <a name="distance-between-controls"></a>컨트롤 간 거리
 제어를 제어 하는 것이 합리적입니다. 누적 된 컨트롤 간의 간격에 대 한 절대 지침은 없습니다. 컨트롤 간의 tightness는 대화 상자 간에 조금씩 다를 수 있습니다. 권장 간격은 세로 컨트롤/레이블 쌍의 경우 20 픽셀, 가로 컨트롤/레이블 쌍의 경우 9 픽셀입니다. 가로 쌍의 최소 컨트롤 간격은 6 픽셀입니다.

 ![컨트롤 사이의 권장 거리](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801-d_ControlDistance")

 **그림 08.01-d: 컨트롤 간의 거리에 대 한 권장 사항**

#### <a name="control-indentation"></a>컨트롤 들여쓰기
 컨트롤이 중첩 된 경우 내부 컨트롤을 위에서 컨트롤의 왼쪽 가장자리 (일반적으로 레이블)와 맞춥니다.

 ![중첩된 컨트롤 맞춤](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801-e_ControlAlign")

 **그림 08.01-e: 중첩 컨트롤 맞춤**

#### <a name="control-width"></a>컨트롤 너비
 텍스트 상자 또는 기타 유사한 컨트롤의 너비는 필드의 평균 입력 보다 길면 안 됩니다. 평균 영어 단어는 5 자입니다. 예를 들어 긴 경로 이름을 필요로 하는 입력란은 가로 레이아웃에서 허용 되는 길이 여야 하 고, 플랫폼 이름에 대 한 드롭다운은 가장 긴 항목을 허용 하는 길이 여야 합니다.

#### <a name="helper-text"></a>도우미 텍스트

- 대화 상자에는 대화의 용도에 대 한 자세한 정보를 제공 하는 도우미 텍스트가 표시 될 수 있습니다. 이는 일반적으로 맨 위에 있고 1-2 문장이 될 수 있습니다.

- 사용자가 구문 분석 하 고 읽을 수 있도록 줄 길이는 편한 너비 여야 합니다. 중간 대화 상자는 너비가 550 픽셀이 하 여야 합니다.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> 내부 명령 단추
 더 복잡 한 대화 상자에서 내부 컨트롤에는 대화 상자의 커밋 단추가 있는 위치에 영향을 줄 수 있는 고유한 관련 단추가 있을 수 있습니다.

- **확인** / **취소가** 가로 방향의 오른쪽 모서리에서 가로 방향인 경우 내부 단추의 세로 맞춤 (열)을 사용 합니다.

- **확인** / **취소가** 세로 방향 오른쪽 모서리에 세로 방향으로 있는 경우 내부 단추의 가로 맞춤 (행)을 사용 합니다. 이 상황은 일반적이 아닙니다.

- 내부 단추 크기는 가능한 경우 **확인** / **취소** 단추의 크기와 일치 하는 표준 단추 크기인 75x23 픽셀을 대상으로 해야 합니다. 단추 레이블이 표준 단추 크기를 초과 하는 경우 해당 집합의 다른 단추가 더 넓은 크기와 일치 해야 합니다.

  ![가로 확인 및 취소 단추](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801-f_HorizOKCan")

  **그림 08.01-f: 가로 확인/취소를 사용 하는 세로 내부 단추**

  ![세로 확인 및 취소 단추](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801-g_VertOKCan")

  **그림 08.01-g: 세로 확인/취소를 사용 하는 가로 내부 단추**

#### <a name="browse-button"></a>[찾아보기 ...] 단추만
 **[찾아보기 ...]** 텍스트 상자 다음에 오는 단추는 "찾아보기 ..." 전체에서 줄임표 (...)를 포함 합니다. 공간이 부족 하거나 화면에 여러 **[찾아보기 ...]** 단추가 있는 경우 단추를 줄임표로만 줄일 수 있습니다.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> 테마가 적용 되는 대화 상자 레이아웃
 Visual Studio의 테마 대화 상자는 더 간단한 모양이 며 더 많은 공백을 제공 합니다. 입력 체계는 더 많은 강조를 제공 하 고, 더 많은 줄 간격을 제공 하 고, 글꼴 크기와 가중치를 변형 합니다. 가능 하면 chrome 및 제목 표시줄이 축소 되거나 제거 되었습니다. 이러한 대화 상자의 레이아웃은 다음 기본 패턴을 따라야 합니다.

1. 대화 상자의 배경은 흰색입니다.

2. 중간 값 회색에는 1 픽셀 규칙 테두리가 있습니다.

3. 대화 상자 제목은 더 이상 제목 표시줄에 표시 되지 않지만 시각적 효과를 제공 하 고 더 큰 점 크기를 강조 합니다. [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)의 글꼴 크기 섹션을 참조 하십시오.

4. 설명과 같이 추가 텍스트와 결합 된 레이블은 **환경 글꼴 + 굵게 표시**되어야 합니다.

5. 내부 열은 밝은 회색으로 표시 된 1 픽셀 규칙으로 구분 됩니다.

6. 기본 링크에는 밑줄이 없습니다. 가리키기 및 누름 상태에는 색 변경 및 밑줄만 있습니다.

7. 오른쪽 아래 모퉁이의 커밋 단추 (예: **확인** / **취소**)가 있습니다.

### <a name="themed-dialog-layout-examples"></a>테마가 적용 되는 대화 상자 레이아웃 예제
 ![테마가 지정된 대화 상자 레이아웃](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801-h_ThemedDialog")

 **그림 08.01-h: 테마가 적용 되는 대화 상자**

 ![테마가 지정된 대화 크기](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **그림 08.01-i: 테마가 적용 되는 대화 상자-차원**

 ![테마가 지정된 대화 상자 글꼴](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **그림 08.01-j: 테마가 적용 되는 대화 상자-글꼴**

 ![테마가 지정된 대화 상자 색](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801-k_ThemedDialogColors")

 **그림 08.01-k: 테마가 적용 되는 대화 상자-색**

## <a name="see-also"></a>관련 항목
 [Visual Studio 컨트롤용 응용 프로그램 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md) [(Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) [대화 상자 (windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)
