---
title: '워크플로 디자이너-방법: 인수 디자이너 사용'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c3c0fe3de3a9ab74ed09c1be45e0d39a71a5b7c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817452"
---
# <a name="how-to-use-the-argument-designer"></a>방법: 인수 디자이너 사용

인수 디자이너를 사용 하면 데이터를 쉽게 작업에서 주고 처리할 수 있습니다. 디자인 캔버스의 왼쪽 아래 모서리에 있는 **인수** 단추를 클릭 하 여 디자이너에 액세스 합니다. 이 디자이너에는 테이블 형식으로 표시 되 고 각 열 머리글을 기준으로 정렬할 수 있는 인수 목록이 포함 되어 있습니다 ( **기본값** 열 제외). 각 인수에는 이름, in/out/in-out/속성 방향, 형식 및 기본 식 값(있는 경우)이 포함됩니다. 이름 및 기본 식 값은 편집할 수 있는 텍스트 필드이며, 형식과 방향은 드롭다운입니다. 자세한 내용은 [변수 및 인수 (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)를 참조 하세요.

## <a name="to-create-a-new-argument"></a>새 인수를 만들려면

1. Visual Studio에서 워크플로 또는 활동 솔루션을 엽니다.

2. 디자인 캔버스의 왼쪽 아래 모퉁이에 있는 **인수** 단추를 클릭 하 여 인수 디자이너를 엽니다. 인수 디자이너가 나타납니다.

3. **인수 만들기**라는 빈 행을 클릭 합니다. 그러면 다음 **기본값을 사용**하 여 새 인수를 사용 하 여 새 행을 추가 합니다 **. 여기서 x는 초기** 값이 1 인 정수 **입니다. 여기서**x는 고유 인수 이름을 만들기 위해 자동으로 증가 하는 **정수입니다.** **String** **기본값**에는 값이 추가 되지 않습니다. 워크플로 디자인 프로세스 중 언제라도 이러한 값을 변경할 수 있습니다.

    > [!NOTE]
    > 인수를 삭제 하려면 인수를 클릭 하 여 선택한 다음 **delete** 키를 누릅니다.

## <a name="see-also"></a>참고 항목

- [워크플로 디자이너 사용](developing-applications-with-the-workflow-designer.md)
- [변수 및 인수](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
