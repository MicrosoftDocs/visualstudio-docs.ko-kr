---
title: 텍스트 및 다중 캐럿 선택 영역 찾기 및 바꾸기
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc31a0d0e2b6878b5dd5173a35ce4f538e135be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590347"
---
# <a name="find-and-replace-text"></a>텍스트 찾기 및 바꾸기

[찾기 및 바꾸기](#find-and-replace-control)(**Ctrl**+**F** 또는 **Ctrl**+**H**) 또는 [파일에서 찾기/바꾸기](#find-in-files-and-replace-in-files)(**Ctrl**+**Shift**+**F** 또는 **Ctrl**+**Shift**+**H**)를 사용하여 Visual Studio 편집기에서 텍스트를 찾아 바꿀 수 있습니다. *[다중 캐럿 선택 영역](#multi-caret-selection)* 을 사용하여 패턴의 *일부* 인스턴스만 찾아 바꿀 수 있습니다.

> [!TIP]
> 변수 및 메서드 등의 코드 기호의 이름을 바꾸는 경우 찾기 및 바꾸기를 사용하는 것보다 *[리팩터링](../ide/reference/rename.md)* 하는 것이 좋습니다. 리팩터링은 지능형이고 범위를 이해하지만 찾기 및 바꾸기는 모든 항목을 무조건 바꿉니다.

찾기 및 바꾸기 기능은 편집기, 특정 텍스트 기반 창(예: **찾기 결과** 창), 디자이너 창(예: XAML 디자이너, Windows Forms 디자이너) 및 도구 창에서 사용할 수 있습니다.

검색 범위를 현재 문서, 현재 솔루션 또는 사용자 지정 폴더 집합으로 지정할 수 있습니다. 다중 파일 검색을 위해 파일 이름 확장명 집합을 지정할 수도 있습니다. .NET [정규식](../ide/using-regular-expressions-in-visual-studio.md)을 사용하여 검색 구문을 사용자 지정합니다.

> [!TIP]
> [찾기/명령](../ide/find-command-box.md) 상자를 도구 모음 컨트롤로 사용할 수 있지만 이 상자는 기본적으로 표시되지 않습니다. **찾기/명령** 상자를 표시하려면 **표준** 도구 모음에서 **단추 추가/제거**를 선택하고 나서 **찾기**를 선택합니다.

## <a name="find-and-replace-control"></a>찾기 및 바꾸기 컨트롤

- 현재 파일에서 문자열을 *찾으려면* 바로 가기로 **Ctrl**+**F**를 누룹니다.
- 현재 파일에서 문자열을 *찾아서 바꾸려면* 바로 가기로 **Ctrl**+**H**를 누룹니다.

**찾기 및 바꾸기** 컨트롤은 코드 편집기 창의 오른쪽 위 모퉁이에 표시됩니다. 현재 문서에서 지정된 검색 문자열의 모든 항목을 즉시 강조 표시합니다. 발생 항목 간에 이동하려면 검색 컨트롤에서 **다음 찾기** 단추 또는 **이전 찾기** 단추를 선택합니다.

![Visual Studio의 찾기 및 바꾸기](media/find-and-replace-box.png)

바꾸기 옵션에 액세스하려면 **찾기** 텍스트 상자 옆의 단추를 선택합니다. 한 번에 하나를 바꾸려면 **바꾸기** 텍스트 상자 옆의 **다음 찾기** 단추를 선택합니다. 모든 일치 항목을 바꾸려면 **모두 바꾸기** 단추를 선택합니다.

일치 항목의 강조 색을 변경하려면 **도구** 메뉴를 선택하고, **옵션**, **환경**을 차례로 선택하고 나서, **글꼴 및 색**을 선택합니다. **설정 표시** 목록에서 **텍스트 편집기**를 선택하고, **표시 항목** 목록에서 **강조 찾기(확장)** 를 선택합니다.

### <a name="search-tool-windows"></a>검색 도구 창

**편집** > **찾기 및 바꾸기**를 선택하거나 **Ctrl+F**를 눌러 **출력** 창, **찾기 결과** 창과 같은 코드 또는 텍스트 창에서 **찾기** 컨트롤을 사용할 수 있습니다.

특정 버전의 **찾기** 컨트롤을 일부 도구 창에서 사용할 수도 있습니다. 예를 들어 검색 상자에 텍스트를 입력하면 **도구 상자** 창에서 컨트롤 목록을 필터링할 수 있습니다. 현재 포함된 콘텐츠를 검색할 수 있는 기타 도구 창에는 **솔루션 탐색기**, **속성** 창 및 **팀 탐색기**가 포함됩니다.

## <a name="find-in-files-and-replace-in-files"></a>파일에서 찾기 및 파일에서 바꾸기

- 여러 파일에서 문자열을 *찾으려면* 바로 가기로 **Ctrl**+**Shift**+**F**를 누릅니다.
- 여러 파일에서 문자열을 *찾아서 바꾸려면* 바로 가기로 **Ctrl**+**Shift**+**H**를 누룹니다.

**파일에서 찾기/바꾸기**는 검색 범위를 정의할 수 있다는 점을 제외하고 **찾기 및 바꾸기** 컨트롤과 비슷하게 작동합니다. 편집기에서 현재 열린 파일을 검색할 수 있을 뿐만 아니라 모든 열린 문서, 전체 솔루션, 현재 프로젝트 및 선택한 폴더 집합을 검색할 수도 있습니다. 파일 이름 확장명을 기준으로 검색할 수도 있습니다. **파일에서 찾기/바꾸기** 대화 상자에 액세스하려면 **편집** 메뉴에서 **찾기 및 바꾸기**를 선택하거나 **Ctrl**+**Shift**+**F**를 누릅니다.

![Visual Studio의 파일에서 찾기](media/find-in-files-box.png)

### <a name="find-results"></a>찾기 결과

**모두 찾기**를 선택하면 **찾기 결과** 창이 열리고 검색과 일치하는 항목이 나열됩니다. 목록에서 결과를 선택하면 연결된 파일이 표시되고 일치 항목이 강조 표시됩니다. 해당 파일이 편집하도록 열려 있지 않으면 탭 오른쪽의 미리 보기 탭에서 열립니다. **찾기** 컨트롤을 사용하여 **찾기 결과** 목록을 검색할 수 있습니다.

### <a name="create-custom-search-folder-sets"></a>사용자 지정 검색 폴더 집합 만들기

**찾는 위치** 상자 옆에 있는 **검색 폴더 선택** 단추(**...** 과 같이 표시됨)를 선택하여 검색 범위를 정의할 수 있습니다. **검색 폴더 선택** 대화 상자에서 검색할 폴더 집합을 지정할 수 있고 해당 지정 내용을 저장하여 나중에 다시 사용할 수도 있습니다.

> [!TIP]
> 원격 컴퓨터의 드라이브를 로컬 컴퓨터에 매핑한 경우 원격 컴퓨터에서 검색할 폴더를 지정할 수 있습니다.

### <a name="create-custom-component-sets"></a>사용자 지정 구성 요소 집합 만들기

**찾는 위치** 상자 옆에 있는 **사용자 지정 구성 요소 집합 편집** 단추를 선택하여 구성 요소 집합을 검색 범위로 정의할 수 있습니다. 설치된 .NET 또는 COM 구성 요소, 솔루션에 포함된 Visual Studio 프로젝트, 혹은 어셈블리나 형식 라이브러리( *.dll*, *.tlb*, *.olb*, *.exe* 또는 *.ocx*)를 지정할 수 있습니다. 참조를 검색하려면 **참조에서 찾기** 상자를 선택합니다.

## <a name="multi-caret-selection"></a>다중 캐럿 선택 영역

> [!NOTE]
> 이 섹션은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [블록 선택](/visualstudio/mac/block-selection)을 참조하세요.

**Visual Studio 2017 버전 15.8에 도입됨**

*다중 캐럿 선택 영역*을 사용하여 동시에 둘 이상의 위치에서 동일하게 편집합니다. 예를 들어 동시에 동일한 텍스트를 삽입하거나 여러 위치에서 기존 텍스트를 수정할 수 있습니다.

다음 스크린샷에서는 세 가지 위치에서 `-0000`을 선택합니다. 사용자가 **삭제**를 누른 경우 모든 세 가지 선택 항목이 삭제됩니다.

![Visual Studio의 XML 파일에서 다중 캐럿 선택 영역](media/multi-caret-selection.png)

여러 캐럿을 선택하려면 일반적으로 첫 번째 텍스트 선택 영역을 클릭하거나 만든 다음, 각 추가 위치에서 텍스트를 클릭하거나 선택하는 동안 **Alt**를 누릅니다. 일치하는 텍스트를 추가 선택 영역으로 자동으로 추가하거나 텍스트 상자를 선택하여 각 줄에서 동일하게 편집할 수도 있습니다.

> [!TIP]
> **도구** > **옵션**에서 마우스 클릭 정의로 이동에 대해 **Alt**를 보조 키로 선택한 경우 다중 캐럿 선택 영역을 사용하지 않습니다.

### <a name="commands"></a>명령

다중 캐럿 선택 영역 동작에 대해 다음 키 및 작업을 사용합니다.

|바로 가기|작업|
|-|-|
|**Ctrl**+**Alt** + 클릭|보조 캐럿 추가|
|**Ctrl**+**Alt** + 두 번 클릭|보조 단어 선택 영역 추가|
|**Ctrl**+**Alt** + 클릭 + 끌어오기|보조 선택 영역 추가|
|**Shift**+**Alt**+ **.**|선택 항목으로 일치하는 다음 텍스트 추가|
|**Ctrl**+**Shift**+**Alt**+ **,**|선택 항목으로 일치하는 모든 텍스트 추가|
|**Shift**+**Alt**+ **,**|마지막으로 선택한 발생 항목 제거|
|**Ctrl**+**Shift**+**Alt**+ **.**|일치하는 다음 발생 항목 건너뛰기|
|**Alt** + 클릭|상자 선택 영역 추가|
|**Esc** 또는 클릭|모든 선택 영역 지우기|

명령 중 일부는 **다중 캐럿** 아래의 **편집** 메뉴에서 사용할 수도 있습니다.

![Visual Studio에서 다중 캐럿 플라이아웃 메뉴](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>참조

- [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)
- [Visual Studio에서 코드 리팩터링](../ide/refactoring-in-visual-studio.md)
- [블록 선택(Mac용 Visual Studio)](/visualstudio/mac/block-selection)
