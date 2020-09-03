---
title: '방법: 활동 디자이너 라이브러리 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662867"
---
# <a name="how-to-create-an-activity-designer-library"></a>방법: 활동 디자이너 라이브러리 만들기
사용자 지정 활동 디자이너를 사용하여 표준 또는 사용자 지정 활동을 위한 사용자 인터페이스를 만들 수 있습니다. 사용자 인터페이스의 복잡성을 조절하고 한 가지 활동에 대해 두 개 이상의 활동 디자이너를 만들 수 있습니다. 이 시나리오에서는 여러 대상에 맞게 조정한 디자이너를 만들 수 있습니다.

### <a name="to-create-an-activity-designer-library"></a>활동 디자이너 라이브러리를 만들려면

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트 ...** 를 선택 합니다. **새 프로젝트** 대화 상자를 엽니다.

3. **프로젝트 형식** 창에서 원하는 언어에 따라 **Visual c #** 또는 **Visual Basic** 그룹의 **워크플로** 를 선택 합니다.

4. **템플릿** 창에서 **활동 디자이너 라이브러리**를 선택 합니다.

5. **이름** 상자에 프로젝트에 대 한 설명이 포함 된 이름을 입력 하 여 쉽게 식별할 수 있도록 합니다.

6. **위치** 상자에 프로젝트를 저장할 디렉터리를 입력 하거나 **찾아보기** 를 클릭 하 여 이동 합니다.

7. **솔루션** 상자에서 솔루션에 대 한 설명이 포함 된 이름을 입력 하 고 **확인**을 클릭 합니다.

    > [!NOTE]
    > 기존 솔루션에 워크플로 콘솔 응용 프로그램을 추가 하려면에서 해당 솔루션을 열고 [!INCLUDE[vs2010](../includes/vs2010-md.md)] **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **추가**, **새 프로젝트** ...를 차례로 선택 합니다. **새 프로젝트** 대화 상자를 엽니다. 그런 다음 이 절차의 윗부분에 설명된 대로 진행합니다.

8. 프로젝트 템플릿이 XAML로 활동 디자이너 정의를 만들고 코드 숨김 구현 파일을 소스 코드로 만듭니다. [!INCLUDE[wfd1](../includes/wfd1-md.md)]가 열리고 활동 디자이너의 캔버스가 표시됩니다.

9. [!INCLUDE[avalon1](../includes/avalon1-md.md)] **도구 상자** 에서 디자인 화면으로 컨트롤을 끌어 사용자 지정 활동 디자이너에서 사용할 수 있습니다.  사용자 지정 활동 디자이너를 구현 하는 방법에 대 한 예제는 [방법: 사용자 지정 활동 디자이너 만들기](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31)를 참조 하세요.

    > [!WARNING]
    > 사용자 지정 활동 디자이너는 기본 활동 뿐만 아니라 사용자 지정 활동에도 사용할 수 있습니다 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

## <a name="see-also"></a>관련 항목
 [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)