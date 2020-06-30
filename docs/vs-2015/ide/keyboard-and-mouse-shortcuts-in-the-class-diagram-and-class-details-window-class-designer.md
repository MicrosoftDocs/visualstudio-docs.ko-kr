---
title: 클래스 다이어그램 및 클래스 세부 내용 창의 키보드 및 마우스 바로 가기(클래스 디자이너) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5865059e60907397ae7d69b230676ac63a5c3386
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543119"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>클래스 다이어그램 및 클래스 세부 내용 창의 키보드 및 마우스 바로 가기(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

마우스 외에도 키보드를 사용하여 클래스 디자이너 및 **클래스 세부 내용** 창에서 탐색 작업을 수행할 수 있습니다.

 **항목 내용**

- [클래스 디자이너에서 마우스 사용](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)

- [클래스 세부 내용 창에서 마우스 사용](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)

- [클래스 디자이너에서 키보드 사용](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)

- [클래스 세부 내용 창에서 키보드 사용](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)

## <a name="using-the-mouse-in-class-designer"></a><a name="MouseClassDesigner"></a>클래스 디자이너에서 마우스 사용
 클래스 다이어그램에서는 다음과 같은 마우스 동작이 지원됩니다.

|마우스 조합|Context|설명|
|-----------------------|-------------|-----------------|
|두 번 클릭|Shape 요소|코드 편집기를 엽니다.|
||롤리팝 커넥터|롤리팝을 확장/축소합니다.|
||롤리팝 커넥터 레이블|**인터페이스 표시** 명령을 호출합니다.|
|마우스 휠|클래스 다이어그램|세로 방향으로 스크롤합니다.|
|Shift+마우스 휠|클래스 다이어그램|가로 방향으로 스크롤합니다.|
|Ctrl+마우스 휠|클래스 다이어그램|확대/축소합니다.|
|Ctrl+Shift+클릭|클래스 다이어그램|확대/축소합니다.|

## <a name="using-the-mouse-in-the-class-details-window"></a><a name="MouseClassDetails"></a> 클래스 세부 내용 창에서 마우스 사용
 마우스를 사용하여 클래스 세부 내용 창 및 창에 표시되는 데이터의 모양을 다음과 같은 방법으로 변경할 수 있습니다.

- 편집 가능한 셀을 클릭하면 해당 셀의 내용을 편집할 수 있습니다. 속성 창과 소스 코드를 포함하여 데이터가 저장되어 있거나 표시되는 모든 위치에서 변경 내용이 반영됩니다.

- 행의 셀을 클릭하면 해당 행이 나타내는 요소의 속성이 속성 창에 표시됩니다.

- 열 너비를 변경하려면 열이 원하는 너비가 될 때까지 열 머리글의 오른쪽 경계선을 끕니다.

- 행 왼쪽에 있는 화살표 기호를 클릭하여 구획 또는 속성 노드를 확장하거나 축소할 수 있습니다.

- 클래스 세부 내용 창에서는 현재 클래스에 새 멤버를 만들고 클래스 세부 내용 창 그리드에서 멤버 구획을 탐색하기 위한 여러 단추를 제공합니다. 자세한 내용은 클래스 세부 내용 창 단추를 참조하세요.

## <a name="using-the-keyboard-in-class-designer"></a><a name="KeyboardClassDesigner"></a>클래스 디자이너에서 키보드 사용
 클래스 다이어그램에서는 다음과 같은 키보드 동작이 지원됩니다.

|키|Context|설명|
|---------|-------------|-----------------|
|화살표 키|내부 형식 모양|모양 내용에 대한 트리 스타일 탐색(모양을 둘러싼 래핑이 지원됨) 왼쪽 및 오른쪽 키는 확장 가능한 경우 현재 항목을 확장/축소하고, 그렇지 않은 경우 부모로 이동합니다(자세한 동작은 트리 뷰 탐색 참조).|
||최상위 모양|다이어그램에서 모양 이동|
|Shift+화살표 키|내부 형식 모양|멤버, 중첩 형식 또는 구획과 같은 모양 요소로 구성된 연속 선택 영역 작성 이러한 바로 가기는 래핑을 지원하지 않습니다.|
|Home|내부 형식 모양|최상위 모양 제목으로 이동합니다.|
||최상위 모양|다이어그램의 첫 번째 모양으로 이동합니다.|
|End|내부 형식 모양|모양 내부에 보이는 마지막 요소로 이동합니다.|
||최상위 모양|다이어그램의 마지막 모양으로 이동합니다.|
|Shift+Home|내부 형식 모양|현재 항목부터 시작하고 동일한 모양의 최상위 항목으로 끝나는 모양 내의 요소를 선택합니다.|
|Shift+End|내부 형식 모양|Shift+Home과 동일하지만 하향식 방향입니다.|
|Enter 키|모든 컨텍스트|두 번 클릭을 통해서도 사용할 수 있는 모양에 대한 기본 동작을 호출합니다. 대부분의 경우 코드 보기이지만 일부 요소는 다르게(롤리팝, 구획 머리글, 롤리팝 레이블) 정의합니다.|
|+/-|모든 컨텍스트|현재 포커스가 있는 요소를 확장할 수 있는 경우 이러한 키는 요소를 확장명/축소합니다.|
|>|모든 컨텍스트|자식이 있는 요소에서 요소가 축소된 경우 요소를 확장하고 첫 번째 자식으로 이동합니다.|
|<|모든 컨텍스트|부모 요소로 이동합니다.|
|Alt+Shift+L|내부 형식 모양 + 형식 모양|있는 경우 현재 선택한 모양의 롤리팝으로 이동합니다.|
|Alt+Shift+B|내부 형식 모양 + 형식 모양|기본 형식 목록이 형식 모양에 표시되고 둘 이상의 항목이 있는 경우 목록의 확장 상태를 설정/해제(확장/축소)합니다.|
|Delete|형식 및 메모 모양|**다이어그램에서 제거** 명령을 호출합니다.|
||그 밖의 모든 항목|**코드에서 삭제** 명령을 호출합니다(멤버, 매개 변수, 연결, 상속, 롤리팝 레이블).|
|Ctrl+Delete|모든 컨텍스트|선택 영역에 대해 **코드에서 삭제** 명령을 호출합니다.|
|Tab|모든 컨텍스트|동일한 부모 내의 다음 자식으로 이동합니다(래핑 지원).|
|Shift+Tab|모든 컨텍스트|동일한 부모 내의 이전 자식으로 이동합니다(래핑 지원).|
|SPACE|모든 컨텍스트|현재 요소에 대한 선택을 설정/해제합니다.|

## <a name="using-the-keyboard-in-the-class-details-window"></a><a name="KeyboardClassDetails"></a> 클래스 세부 내용 창에서 키보드 사용

> [!NOTE]
> 다음 키 바인딩은 코드 입력 환경을 모방하기 위해 특별히 선택되었습니다.

 다음 키를 사용하여 클래스 세부 내용 창을 탐색합니다.

|키|결과|
|-|-|
|, (쉼표)|커서가 매개 변수 행에 있는 경우 쉼표를 입력하면 커서가 다음 매개 변수의 이름 필드로 이동합니다. 커서가 메서드의 마지막 매개 변수 행에 있으면 커서가 필드로 이동 하 여 \<add parameter> 새 매개 변수를 만드는 데 사용할 수 있습니다.<br /><br /> 커서가 클래스 세부 내용 창의 다른 곳에 있는 경우 쉼표를 입력하면 현재 필드에 쉼표가 리터럴로 추가됩니다.|
|; (세미콜론)<br /><br /> 를 실행하거나<br /><br /> ) (닫는 괄호)|클래스 세부 내용 창 그리드에서 다음 멤버 행의 이름 필드로 커서를 이동합니다.|
|탭|먼저 왼쪽에서 오른쪽으로 이동한 다음 위쪽에서 아래쪽으로 이동하여 커서를 다음 필드로 이동합니다. 커서가 텍스트를 입력한 필드에서 이동하는 경우 클래스 세부 내용 창에서 해당 텍스트를 처리하고 오류를 생성하지 않으면 저장합니다.<br /><br /> 커서가와 같은 빈 필드에 있는 경우 \<add parameter> Tab 키를 누르면 다음 행의 첫 번째 필드로 이동 합니다.|
|\<space>|먼저 왼쪽에서 오른쪽으로 이동한 다음 위쪽에서 아래쪽으로 이동하여 커서를 다음 필드로 이동합니다. 커서는와 같은 빈 필드에 있는 경우 \<add parameter> 다음 행의 첫 번째 필드로 이동 합니다. \<space>쉼표 바로 뒤에 입력 된는 무시 됩니다.<br /><br /> 커서가 요약 필드에 있는 경우 스페이스바를 입력하면 공백 문자가 추가됩니다.<br /><br /> 커서가 지정된 행의 숨기기 열에 있는 경우 스페이스바를 입력하면 숨기기 확인란의 값이 설정/해제됩니다.|
|Ctrl+Tab|다른 문서 창으로 전환합니다. 예를 들어 클래스 세부 내용 창에서 열려 있는 코드 파일로 전환합니다.|
|Esc(이스케이프)|필드에 텍스트 입력을 시작한 경우 Esc 키를 누르면 실행 취소 키로 동작하며 필드 내용을 이전 값으로 되돌립니다. 클래스 세부 내용 창에 일반 포커스가 있지만 포커스가 있는 특정 셀이 없는 경우 Esc 키를 누르면 포커스가 클래스 세부 내용 창에서 벗어납니다.|
|위쪽 화살표 및 아래쪽 화살표|이러한 키는 클래스 세부 내용 창 그리드에서 커서를 행 간에 세로로 이동합니다.|
|왼쪽 화살표|커서가 이름 열에 있는 경우 왼쪽 화살표를 누르면 계층 구조에서 현재 노드가 축소됩니다(열려 있는 경우).|
|오른쪽 화살표|커서가 이름 열에 있는 경우 오른쪽 화살표를 누르면 계층 구조에서 현재 노드가 확장됩니다(축소된 경우).|

## <a name="see-also"></a>참고 항목
 [형식 멤버 만들기 및 구성 (클래스 디자이너)](../ide/creating-and-configuring-type-members-class-designer.md)
