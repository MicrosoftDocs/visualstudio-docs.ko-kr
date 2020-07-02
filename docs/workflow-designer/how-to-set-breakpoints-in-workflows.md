---
title: '워크플로 디자이너-방법: 워크플로에 중단점 설정'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9530e7ec018a89c3648f61660a5651eddaace805
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817491"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>방법: 워크플로에 중단점 설정

워크플로 디자이너를 사용 하는 경우 Visual Basic 또는 c # 코드에서 수행 하는 것 처럼 그래픽 워크플로에 중단점을 설정할 수 있습니다. 예상대로 설정한 각 중단점에서 워크플로 실행이 중지됩니다.

중단점에는 *Pending*, *Bound*및 *Error*의 세 가지 상태가 있습니다. 새로 설정한 중단점은 보류 중 상태가 되고 단색의 빨간색 아이콘으로 표시됩니다. 런타임 시 워크플로 형식을 로드한 경우 중단점은 바인딩됨 상태가 됩니다. 유효하지 않은 활동 이름과 같이 중단점에 대해 잘못된 형식을 지정하면 오류 창이 나타납니다. 그래도 중단점 창에 중단점이 추가되기는 하지만 소문자 "x"로 표시됩니다.

> [!NOTE]
> 호출된 워크플로에는 중단점을 설정할 수 없습니다.

> [!NOTE]
> 디버깅 하기 전에 **도구**옵션 디버깅 메뉴에서 **내 코드만 사용 (관리 전용)** 옵션을 선택 했는지 확인  >  **Options**  >  **Debugging** 합니다. 이 옵션을 선택 하지 않은 경우 두 개의 시퀀스가 다른 시퀀스 내에 중첩 되어 있고 첫 번째 내부 시퀀스에서 중단점을 설정 하는 경우 **F11** 키를 누르면 두 번째 내부 시퀀스로 디버깅 되지 않습니다.

> [!NOTE]
> XAML 파일에 대 한 전체 경로 속성을 정확 하 게 찾지 못하면 워크플로의 중단점이 적중 되지 않습니다. 프로젝트나 솔루션을 다른 폴더나 다른 컴퓨터로 이동한 후에는 XAML 파일의 전체 경로가 정확 하지 않습니다. **Ctrl** + **S** 를 선택 하 여 전체 경로 속성을 저장 하 고 업데이트 합니다.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>디자인 뷰에서 활동의 중단점을 설정하려면

1. 디버거를 중단할 활동을 선택합니다.

2. **디버그** 메뉴에서 **중단점 설정/해제**를 선택 합니다. 활동의 왼쪽 위에 빨간색 아이콘이 표시됩니다.

   또는 활동을 선택한 후 **F9** 키를 누르거나, 활동을 마우스 오른쪽 단추로 클릭 한 다음 **Breakpoint**  >  오른쪽 클릭 메뉴에서 중단점**삽입** 중단점을 선택할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [워크플로 디자이너로 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [방법: Workflow Designer로 XAML 디버그](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
