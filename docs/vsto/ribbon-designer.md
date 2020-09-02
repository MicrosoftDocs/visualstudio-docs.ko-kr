---
title: 리본 디자이너
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985622"
---
# <a name="ribbon-designer"></a>리본 디자이너
  리본 디자이너는 시각적 디자인 캔버스입니다. 리본 디자이너를 사용 하 여 Microsoft Office 응용 프로그램의 리본 메뉴에 사용자 지정 탭, 그룹 및 컨트롤을 추가할 수 있습니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 리본 디자이너를 열려면 프로젝트에 **리본 (비주얼 디자이너)** 항목을 추가 합니다. 그런 다음 디자인 도구를 사용 하 여 다음 작업을 수행할 수 있습니다.

- [리본 레이아웃 디자인](#DesigningRibbonLayout)

- [이벤트 처리 및 컨트롤 속성 설정](#HandleEventsSetProperties)

- [Backstage 보기에 컨트롤 추가](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> 리본 디자이너를 사용 하 여 수행할 수 없는 몇 가지 작업이 있습니다. 이러한 작업 및 이러한 작업을 수행 하는 방법에 대 한 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>프로젝트에 리본 (비주얼 디자이너) 항목 추가
 리본 디자이너를 사용 하려면 프로젝트에 새 **리본 (비주얼 디자이너)** 항목을 추가 합니다. 자세한 내용은 [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)을 참조 하세요.

 새 **리본 (비주얼 디자이너)** 항목을 추가 하면 visual Studio에서 자동으로 다음 파일을 프로젝트에 추가 합니다.

- 리본 코드 파일. 이 파일은 **새 항목 추가** 대화 상자에서 **리본 (비주얼 디자이너)** 항목에 대해 지정한 이름을 갖습니다. 이 파일에 대 한 리본 이벤트를 처리 하는 코드를 추가 합니다.

- 리본 디자이너 코드 파일입니다. 이 파일은 리본 디자이너에 의해 생성 된 코드를 포함 하며 직접 편집 하면 안 됩니다.

- 리소스 파일입니다. 이 파일에는 리본의 각 컨트롤에 대 한 속성 값이 포함 되어 있습니다.

  다른 프로젝트의 **리본 (비주얼 디자이너)** 항목이 이미 있는 경우 **기존 항목 추가** 대화 상자를 사용 하 여 현재 프로젝트에서 다시 사용할 수 있습니다.

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> 리본 디자인
 리본 디자이너를 여는 방법에는 다음 세 가지가 있습니다.

- **솔루션 탐색기**에서 리본 코드 파일을 두 번 클릭 합니다.

- **솔루션 탐색기**에서 리본 코드 파일을 마우스 오른쪽 단추로 클릭 한 다음 **디자이너 보기**를 클릭 합니다.

- **솔루션 탐색기**에서 리본 코드 파일을 선택 하 고 **보기** 메뉴에서 **디자이너** 를 클릭 합니다.

  리본 디자이너에는 기본 탭과 그룹이 있습니다. 리본 디자이너에서 기본 탭 및 그룹을 제거할 수 있습니다. 기본 그룹을 제거 하려면 **Group1**을 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다. 기본 탭을 제거 하려면 디자인 화면의 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **리본 탭 제거**를 클릭 합니다.

  리본 디자이너에 사용자 지정 탭, 그룹 및 컨트롤을 추가할 수도 있습니다. 이러한 컨트롤은 **도구 상자**의 **Office 리본 컨트롤** 그룹에서 찾을 수 있습니다. **Office 리본 컨트롤** 그룹에서 리본 디자이너에 컨트롤을 추가 하는 방법에는 다음 세 가지가 있습니다.

- 리본 디자이너의 적절 한 영역으로 컨트롤을 끌어 옵니다.

- 컨트롤을 클릭 한 다음 리본 디자이너에서 적절 한 영역을 클릭 합니다.

- 디자이너에서 적절 한 영역을 선택 하 고 **도구 상자**에서 컨트롤을 두 번 클릭 합니다.

### <a name="ribbon-design-workflow"></a>리본 디자인 워크플로
 다음 기본 단계에 따라 리본 레이아웃을 디자인 합니다.

1. [리본에 사용자 지정 탭을 추가](#AddTabToRibbon)합니다.

2. [탭에 그룹을 추가](#AddGroupsToTab)합니다.

3. [그룹에 컨트롤을 추가](#AddControlsToGroups)합니다.

   컨트롤은 그룹 에서만 삭제할 수 있습니다. 컨트롤을 탭 이나 리본으로 직접 끌 수는 없습니다. 그룹은 탭 에서만 삭제할 수 있습니다. 그룹을 리본으로 직접 끌 수 없습니다.

   컨트롤을 올바른 위치로 끌어 정렬 합니다. **속성** 창을 사용 하 여 컨트롤의 속성을 설정할 수 있습니다.

   리본의 컨트롤을 한 탭에서 다른 탭으로 끌 수 없습니다. 컨트롤을 다른 탭으로 이동 하려면 **잘라내기** 명령을 사용 하 여 한 탭에서 컨트롤을 제거 하 고 다른 탭에 컨트롤을 붙여 넣어야 합니다. 컨트롤을 잘라내어 붙여넣으면 이벤트 처리기의 작동이 중지 됩니다. **속성** 창에서 이벤트 처리기를 다시 연결할 수 있습니다. 자세한 내용은 [속성 창](../ide/reference/properties-window.md)를 참조 하세요.

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> 리본에 사용자 지정 탭 추가
 리본에 사용자 지정 탭을 추가 하는 방법에는 다음 세 가지가 있습니다.

- **도구 상자**에서 탭을 추가 합니다.

- 리본 디자이너를 마우스 오른쪽 단추로 클릭 한 다음 **리본 탭 추가**를 클릭 합니다.

- **탭 컬렉션 편집기**를 열고 **추가**를 클릭 합니다.

   **탭 컬렉션 편집기**를 열려면 **속성** 창에서 **탭** 속성을 선택 하 고 줄임표 단추 ![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")를 클릭 합니다.

  탭을 추가한 후에는 컨트롤을 포함 하는 그룹을 추가할 수 있습니다.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>리본 메뉴에서 사용자 지정 탭 제거
 리본 메뉴에서 사용자 지정 탭을 제거 하는 방법에는 다음 세 가지가 있습니다.

- 디자이너를 마우스 오른쪽 단추로 클릭 한 다음 **리본 탭 제거**를 클릭 합니다.

- **속성** 창의 **명령** 창에서 **리본 탭 제거**를 클릭 합니다.

- **탭 컬렉션 편집기**를 열고 탭을 선택한 다음 **제거**를 클릭 합니다.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>리본에서 탭의 위치 변경
 리본 메뉴에서 사용자 지정 탭의 순서를 변경할 수 있습니다. 리본 메뉴의 기본 제공 탭 앞 이나 뒤에 사용자 지정 탭을 배치할 수도 있습니다. 자세한 내용은 [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)을 참조 하세요.

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>리본의 기본 제공 탭 사용자 지정
 기본 제공 탭은 Microsoft Office 응용 프로그램의 리본에 이미 있는 탭입니다. 예를 들어 **데이터** 탭은 Excel의 기본 제공 탭입니다.

 기본 제공 탭에 그룹 및 컨트롤을 추가할 수 있습니다. 기본적으로 사용자 지정 그룹은 기본 제공 탭에서 마지막 그룹으로 표시 되지만 탭의 기본 제공 그룹 전후에 이동할 수도 있습니다.

 기본 제공 그룹은 제거할 수 없습니다.

 기본 제공 탭을 사용자 지정 하는 방법에 대 한 자세한 내용은 [방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)을 참조 하세요.

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> 탭에 그룹 추가
 그룹은 리본에서 컨트롤을 논리적으로 구성 합니다. 탭에 그룹을 추가 합니다. 다른 모든 컨트롤을 그룹에 추가 합니다.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> 그룹에 컨트롤 추가
 하나 이상의 컨트롤을 그룹에 추가 합니다. 다음 표에서는 각 컨트롤에 대해 설명 합니다.

|제어|설명|
|-------------|-----------------|
|**Box**|그룹의 컨트롤을 구성 하는 컨테이너입니다. 구분 기호, 그룹 또는 탭을 제외 하 고 상자에 컨트롤을 추가할 수 있습니다. 상자는 가로 또는 세로 방향으로 지정할 수 있습니다.|
|**Button**|작업을 시작 하는 단추입니다. 그룹, 단추 그룹, 드롭다운 목록, 갤러리, 메뉴 또는 분할 단추에 단추를 추가할 수 있습니다.|
|**ButtonGroup**|하나 이상의 단추, 토글 단추, 메뉴, 분할 단추 및 갤러리가 포함 된 그룹입니다. 그룹 또는 메뉴에 단추 그룹을 추가할 수 있습니다.|
|**CheckBox**|옵션을 설정 하거나 해제 하기 위해 선택 하거나 선택 취소 하는 상자입니다.|
|**ComboBox**|목록 상자가 연결 된 입력란입니다. 사용자는 선택 항목을 입력 하거나 선택할 수 있습니다. 상자에는 현재 선택 항목이 표시 됩니다. <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A>리본이 Office 응용 프로그램에 로드 되기 전이나 후에 런타임에 항목을 추가 및 제거 하려면 속성을 사용 합니다.|
|**DropDown**|사용자가 선택할 수 있는 항목의 목록입니다. 사용자는 드롭다운 목록에 새 항목을 입력할 수 없습니다.<br /><br /> 속성을 사용 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> 하 여 목록에 항목을 추가 합니다. 런타임에 항목을 추가 하 고 제거할 수 있습니다.<br /><br /> 속성을 사용 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> 하 여 목록에 단추를 추가 합니다. 그러나 리본이 Office 응용 프로그램에 로드 된 후에는 런타임에 단추를 추가 하 고 제거할 수 없습니다.|
|**입력란**|사용자가 텍스트를 입력할 수 있는 상자입니다.|
|**갤러리**|사용자가 선택할 수 있는 시각적 항목의 배열 또는 그리드를 표시 하는 메뉴입니다. 메뉴에서 선택 영역의 레이아웃을 제어할 수 있습니다. <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>및 속성을 사용 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 하 여 갤러리의 항목 및 단추를 표시 하는 행 및 열 수를 지정 합니다.|
|**레이블**|리본 메뉴에서 컨트롤을 식별 하는 데 사용할 수 있는 텍스트입니다.|
|**메뉴**|다음 컨트롤을 포함할 수 있는 드롭다운 목록입니다.<br /><br /> -단추<br />-확인란<br />-갤러리<br />-메뉴<br />-분할 단추<br />-토글 단추<br />-구분 기호<br /><br /> 리본 디자이너의 메뉴에 컨트롤을 추가 하려면 메뉴의 아래쪽 화살표를 클릭 하 여 메뉴 디자인 화면을 표시 합니다. 그런 다음 **도구 상자** 의 리본 컨트롤을 메뉴에 끌어다 놓을 수 있습니다. 컨트롤을 정렬 하려면 원하는 위치로 끕니다.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>리본이 Office 응용 프로그램에 로드 된 후 컨트롤을에 추가 하려면 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 리본 메뉴가 로드 되기 전에 속성을 **true** 로 설정 해야 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)를 참조 하세요.|
|**구분줄**|목록에서 항목을 구분 하는 데 사용 되는 씬 막대입니다. 그룹에 추가 된 막대는 세로 막대입니다. 메뉴에 추가 된 막대는 가로 막대입니다.|
|**SplitButton**|메뉴가 연결 된 단추입니다. 분할 단추에는 다음 컨트롤이 포함 될 수 있습니다.<br /><br /> -단추<br />-확인란<br />-갤러리<br />-메뉴<br />-분할 단추<br />-토글 단추<br />-구분 기호<br /><br /> 메뉴와 마찬가지로 분할 단추에는 자체 디자인 화면이 있습니다. 그러나 메뉴와 달리 리본이 Office 응용 프로그램에 로드 되기 전에는 분할 단추의 항목만 업데이트할 수 있습니다. 분할 단추에서 항목을 업데이트 하는 방법에 대 한 자세한 내용은 [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)를 참조 하세요.|
|**ToggleButton**|눌러져 있거나 누르지 않은 상태로 표시 되는 단추입니다.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> 이벤트 처리 및 속성 설정
 리본 디자이너를 사용 하면 디자인 타임에 **속성** 창을 사용 하 여 컨트롤 속성을 설정할 수 있습니다. 또한 리본 메뉴는 런타임에 리본 컨트롤의 속성을 가져오고 설정 하는 데 사용할 수 있는 강력한 형식의 개체 모델을 노출 합니다.

 디자이너에서 컨트롤을 두 번 클릭 하 여 컨트롤의 기본 이벤트에 대 한 이벤트 처리기를 열 수 있습니다. **속성** 창을 사용 하 여 다른 모든 컨트롤 이벤트에 대 한 이벤트 처리기를 만들 수 있습니다.

 리본 이벤트와 속성은 <xref:Microsoft.Office.Tools.Ribbon> 네임 스페이스에 있습니다. **리본 (비주얼 디자이너)** 항목은 프로젝트에이 어셈블리에 대 한 참조를 자동으로 추가 하 고 리본 코드 파일의 맨 위에 적절 한 **using** 또는 **Imports** 문을 삽입 합니다.

 런타임에 리본 이벤트를 처리 하 고 리본 컨트롤의 속성을 설정 하는 방법에 대 한 자세한 내용은 [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)를 참조 하세요.

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Backstage 보기 사용자 지정
 리본 디자이너를 사용 하 여 **파일** 탭을 클릭할 때 열리는 메뉴에 컨트롤을 추가할 수 있습니다. 이 메뉴를 Backstage 보기 라고 합니다.

 리본 디자이너를 사용 하 여 기본 제공 컨트롤 전후에 컨트롤을 배치할 수 없습니다. 기본 제공 컨트롤은 Backstage 보기에 이미 표시 된 컨트롤입니다. 기본 제공 컨트롤 전후에 컨트롤을 배치 하려면 리본 XML을 사용 해야 합니다. **리본 (xml)** 에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요. Backstage 보기를 사용자 지정 하는 방법에 대 한 자세한 내용은 [개발자를 위한 office 2010 backstage 보기 소개](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) 및 [개발자를 위한 office 2010 Backstage 보기 사용자 지정](/previous-versions/office/developer/office-2010/ee815851(v=office.14))을 참조 하세요.

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Backstage 보기에 컨트롤을 추가 하는 방법에 대 한 자세한 내용은 [방법: backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)를 참조 하세요.

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> 리본 디자이너의 내게 필요한 옵션
 바로 가기 키를 사용 하 여 리본 디자이너에서 컨트롤을 이동할 수 있습니다. 일부 바로 가기 키는 모든 컨트롤에 적용 되며, 일부는 메뉴가 있는 컨트롤에만 적용 됩니다.

 모든 컨트롤에 적용 되는 바로 가기 키는 다음 표에 나와 있습니다.

|작업|키보드 바로 가기 키|
|------------|-----------------------|
|목록의 이전 컨트롤 앞에 컨트롤을 이동 합니다.|**Ctrl** + **Up**<br /><br /> **Ctrl** + **왼쪽**|
|목록의 다음 컨트롤 뒤에 컨트롤을 이동 합니다.|**Ctrl** + **다운**<br /><br /> **Ctrl** + **오른쪽**|
|동일한 그룹의 한 컨트롤에서 다른 컨트롤로 선택 영역을 이동 합니다. 드롭다운 패널의 경우 부모 컨트롤과 드롭다운 패널의 컨트롤 사이를 이동 합니다.|**위로**<br /><br /> **아래로**|
|모든 컨트롤을 앞으로 반복 합니다.|**탭**|
|모든 컨트롤을 역순으로 반복 합니다.|**Shift**+**Tab**|
|선택한 컨트롤 또는 컨트롤 집합을 삭제 합니다.|**Delete**|
|선택한 컨트롤을 복사 합니다.|**Ctrl** + **C**|
|선택한 컨트롤을 잘라냅니다.|**Ctrl** + **X**|
|클립보드에서 컨트롤을 붙여넣습니다.|**Ctrl** + **V**|
|**도구 상자**를 선택 합니다.|**Ctrl** + **Alt** + **X**|
|부모 구성 요소를 선택 합니다.|**Esc**|

 다음 표에는 Microsoft Office 메뉴, 및에만 적용 되는 바로 가기 키 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 가 나와 있습니다.

|작업|키보드 바로 가기 키|
|------------|-----------------------|
|드롭다운 패널이 열려 있고 드롭다운 패널에서 컨트롤이 선택 되어 있는 경우 부모 컨트롤을 선택 합니다.|**비어**|
|드롭다운 패널이 열려 있고 부모 컨트롤이 선택 되어 있는 경우 드롭다운 패널을 닫습니다.|**비어**|
|드롭다운 패널을 엽니다.|**오른쪽**|
|드롭다운 패널이 열려 있는 경우 드롭다운 패널의 첫 번째 컨트롤을 선택 합니다.|**오른쪽**|
|드롭다운 패널을 닫습니다.|**Esc**|

## <a name="see-also"></a>추가 정보

- [리본 개요](../vsto/ribbon-overview.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [방법: 리본 디자이너에서 리본 XML로 리본 메뉴 내보내기](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
