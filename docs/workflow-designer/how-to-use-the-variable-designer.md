---
title: '워크플로 디자이너-방법: 변수 디자이너 사용'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02aab6c5ecf545e0f754f1a88fa7e26a88f206d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817413"
---
# <a name="how-to-use-the-variable-designer"></a>방법: 변수 디자이너 사용

변수 디자이너는 데이터 바인딩 시나리오 및 조건문에 사용할 변수를 만드는 데 사용됩니다. 디자인 캔버스의 왼쪽 아래 모퉁이에 있는 **변수** 단추를 클릭 하 여 디자이너에 액세스 합니다. 이 디자이너에는 테이블 형식으로 표시 되 고 **기본** 열을 제외 하 고 각 열 머리글을 기준으로 정렬할 수 있는 변수 목록이 포함 되어 있습니다. 각 변수에는 이름, 변수 형식, 범위 및 기본값(있는 경우)이 포함됩니다. 이름 및 기본값은 편집 가능한 텍스트 필드이며 형식과 범위는 드롭다운입니다. 범위란 변수 디자이너를 호출할 때 선택한 활동입니다. 선택 항목의 범위 안에서 변수를 만들 수 없는 경우, 선택 항목과 가장 근접하면서 변수를 만들 수 있는 상위 활동 범위가 기본 범위로 사용됩니다. 자세한 내용은 [변수 및 인수 (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)를 참조 하세요.

 정렬 순서는 사용자가 정렬 컨트롤 중 하나를 명시적으로 사용하거나, 변수 디자이너를 닫았다가 다시 열거나, 다른 변수를 만들어야 적용됩니다.

## <a name="to-create-a-new-variable"></a>새 변수를 만들려면

1. Visual Studio에서 워크플로 또는 활동 솔루션을 엽니다.

2. 디자인 캔버스의 워크플로에서 활동을 선택합니다.

3. 디자인 캔버스의 왼쪽 아래 모퉁이에 있는 **변수** 단추를 클릭 하 여 변수 디자이너를 엽니다. 변수 디자이너가 나타납니다.

4. **변수 만들기**라는 빈 행을 클릭 합니다. 그러면 다음 기본값을 사용 하 여 새 변수를 사용 하 여 새 행을 **추가 합니다. 여기서 x** 는 초기 값이 1 인 정수입니다. 여기서 x는 고유 변수 이름, **변수 형식**에 대 한 문자열, **범위** **에 대 한** **문자열** 을 만들기 위해 자동으로 증가 하는 정수 variablex. **기본값**에는 값이 추가 되지 않습니다. 워크플로 디자인 프로세스 중 언제라도 이러한 값을 변경할 수 있습니다.

    > [!NOTE]
    > 변수를 삭제 하려면 변수를 클릭 하 여 선택한 다음 **delete** 키를 누릅니다.

## <a name="see-also"></a>추가 정보

- [워크플로 디자이너 사용](developing-applications-with-the-workflow-designer.md)
- [변수 및 인수](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [방법: 인수 디자이너 사용](../workflow-designer/how-to-use-the-argument-designer.md)
