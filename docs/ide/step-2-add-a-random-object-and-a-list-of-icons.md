---
title: '2단계: 임의의 개체 및 아이콘 목록 추가'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579424"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2단계: 임의의 개체 및 아이콘 목록 추가

이 단계에서는 게임에 사용할 일치하는 기호의 집합을 만듭니다. 각 기호는 폼의 TableLayoutPanel에 있는 임의의 두 셀에 추가됩니다. 이렇게 하려면 두 개의 `new` 문을 사용하여 두 개체를 만듭니다. 첫 번째 개체는 수학 퀴즈 게임에서 사용한 것과 비슷한 <xref:System.Random> 개체입니다. 이 개체는 TableLayoutPanel의 셀을 임의로 선택하기 위해 이 코드에 사용됩니다. 두 번째 개체는 사용자에게 새로울 수도 있는데, 임의로 선택한 기호를 저장하는 데 사용되는 <xref:System.Collections.Generic.List%601> 개체입니다.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>임의의 개체 및 아이콘 목록을 추가하려면

1. **솔루션 탐색기**에서, C#을 사용 중인 경우 *Form1.cs*를 선택하고 Visual Basic을 사용 중인 경우 *Form1.vb*를 선택한 다음, 메뉴 모음에서 **보기** > **코드**를 선택합니다. 또는 **F7** 키를 선택하거나 **솔루션 탐색기**에서 **Form1**을 두 번 클릭하면 됩니다.

     이렇게 하면 Form1 뒤의 코드 모듈이 표시됩니다.

2. 기존 코드에 다음 코드를 추가합니다.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > 이 페이지의 오른쪽 위에 있는 프로그래밍 언어 컨트롤을 사용하여 C# 코드 조각 또는 Visual Basic 코드 조각을 볼 수 있습니다.<br><br>![Docs.Microsoft.com에 대한 프로그래밍 언어 컨트롤](../ide/media/docs-programming-language-control.png)

      C#을 사용 중인 경우 클래스 선언(`public partial class Form1 : Form`) 바로 다음에 여는 중괄호를 먼저 입력하고 코드를 추가해야 합니다. Visual Basic을 사용 중인 경우에는 클래스 선언(`Public Class Form1`) 바로 다음에 코드를 추가합니다.

3. List 개체를 추가하는 경우 **IntelliSense** 창이 열리는 것을 확인할 수 있습니다. 다음은 C# 예시이지만 Visual Basic에서 목록을 추가할 때에도 이와 비슷한 텍스트가 나타납니다.

     ![Click 이벤트가 표시된 속성 창](../ide/media/express_listintellisense.png)<br/>***IntelliSense** 창*

    > [!NOTE]
    > IntelliSense 창은 코드를 수동으로 입력하는 경우에만 나타납니다. 복사한 코드를 붙여 넣는 경우에는 표시되지 않습니다.

     작은 섹션의 코드(및 설명)를 보면 더 쉽게 이해할 수 있습니다. 프로그램에서는 목록 개체를 사용하여 서로 다른 형식의 여러 항목을 추적할 수 있습니다. 목록에는 숫자, true/false 값, 텍스트 또는 다른 개체가 포함될 수 있습니다. 목록 개체에 다른 목록 개체가 포함될 수도 있습니다. 목록의 항목은 요소라고 하며 각 목록에는 같은 형식의 요소만 포함됩니다. 따라서 숫자 목록에는 숫자만 포함될 수 있으며 해당 목록에 텍스트를 추가할 수 없습니다. 마찬가지로 true/false 값 목록에 숫자를 추가할 수 없습니다.

     `List` 문을 사용하여 `new` 개체를 만드는 경우 목록에 저장할 데이터의 종류를 지정해야 합니다. 이를 위해 **IntelliSense** 창의 맨 위에 있는 도구 설명에서 목록의 요소 형식을 보여 줍니다. 또한 `List<string>`(C#의 경우) 및 `List(Of String)`(Visual Basic의 경우)는 `string` 데이터 형식의 요소를 포함하는 `List` 개체임을 나타냅니다. 문자열은 **IntelliSense** 창 오른쪽에 있는 도구 설명에서 알려 주는 텍스트를 저장하기 위해 프로그램에서 사용합니다.

4. Visual Basic에서는 먼저 임시 배열을 만들어야 하지만 C#에서는 하나의 문으로 목록을 만들 수 있습니다. 이는 C# 언어에 값을 받아들이는 목록을 준비하는 *컬렉션 이니셜라이저*가 포함되어 있기 때문입니다. Visual Basic에서도 컬렉션 이니셜라이저를 사용할 수 있습니다. 그러나 이전 버전의 Visual Basic과의 호환성을 위해 위의 코드를 사용하는 것이 좋습니다.

     `new` 문에 컬렉션 이니셜라이저를 사용하면 새 List 개체가 만들어진 후 프로그램에서 중괄호 내에 있는 사용자 제공 데이터로 개체를 채웁니다. 이 경우에는 아이콘이라는 문자열 목록이 만들어지고 이 목록은 16개의 문자열이 포함되도록 초기화됩니다. 각 문자열은 단일 문자이며 모두 레이블에 포함될 아이콘에 해당합니다. 따라서 이 게임에는 느낌표, 대문자 N, 쉼표 등이 각각 쌍으로 포함됩니다. 이러한 문자는 Webdings 글꼴로 설정되며, 버스, 오토바이, 거미 등의 기호로 나타납니다. 목록 개체에는 TableLayoutPanel 패널의 각 셀에 하나씩 모두 16개의 문자열이 포함됩니다.

    > [!NOTE]
    > Visual Basic에서도 같은 결과가 나타나지만 먼저 문자열이 임시 배열에 추가된 다음, 목록 개체로 변환됩니다. 배열은 목록과 비슷하지만 고정 크기로 만들어진다는 차이가 있습니다. 목록은 필요에 따라 축소 또는 확장할 수 있으며 이는 프로그램에서 중요한 내용입니다.

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 [**3단계: 각 레이블에 임의 아이콘 할당**](../ide/step-3-assign-a-random-icon-to-each-label.md)을 참조하세요.

- 이전 자습서 단계로 돌아가려면 [1단계: 프로젝트 만들기 및 양식에 테이블 추가](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)를 참조하세요.
