---
title: 생성자 생성 빠른 작업
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c8259841af4511bd782bca1be222353634638f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79306790"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Visual Studio에서 생성자 생성

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 클래스에서 새 생성자에 대한 코드를 즉시 생성할 수 있습니다.

**시기**: 새 생성자를 소개하고 자동으로 생성자를 제대로 선언하거나 기존 생성자를 수정하려고 합니다.

**이유:** 생성자를 사용하기 전에 사용자가 생성자를 선언할 수 있지만, 이 기능은 적절한 매개 변수를 사용하여 생성자를 자동으로 생성합니다. 또한 이 기능을 사용하여 자동으로 업데이트하지 않는 한, 기존 생성자를 수정하려면 모든 호출 사이트를 업데이트해야 합니다.

**방법:** 여러 가지 방법으로 생성자를 생성할 수 있습니다.

- [생성자 생성 및 멤버 선택](#pick)
- [선택한 필드에서 생성자 생성](#selection)
- [새 사용에서 생성자 생성](#usage)
- [기존 생성자에 매개 변수 추가](#addparameter)
- [생성자 매개 변수에서 필드/속성 만들기 및 초기화](#create)

## <a id = "pick"></a> 생성자 생성 및 멤버 선택(C#만 해당)

1. 클래스의 빈 줄에 커서를 놓습니다.

   ![빈 줄의 커서](media/constructor1-highlight-cs.png)

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](media/screwdriver.png) 아이콘을 클릭합니다.

   ![생성자 생성 미리 보기](media/constructor1-preview-cs.png)

1. 드롭다운 메뉴에서 **생성자 생성**을 선택합니다.

   **멤버 선택** 대화 상자가 열립니다.

1. 생성자 매개 변수로 포함할 멤버를 선택합니다. 위쪽 및 아래쪽 화살표를 사용하여 이들을 순서 설정할 수 있습니다. **확인**을 선택합니다.

   ![멤버 선택 대화 상자](media/constructor1-dialog-cs.png)

   > [!TIP]
   > **null 검사 추가** 확인란을 선택하여 생성자 매개 변수에 대한 null 검사를 자동으로 생성할 수 있습니다.

   지정한 매개 변수를 사용하여 생성자가 만들어집니다.

   ![생성자 생성 결과](media/constructor1-result-cs.png)

## <a id="selection"></a> 선택한 필드에서 생성자 생성(C#만 해당)

1. 생성된 생성자에 포함할 멤버를 강조 표시합니다.

   ![멤버를 강조 표시](media/constructor2-highlight-cs.png)

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](media/screwdriver.png) 아이콘을 클릭합니다.

      ![생성자 생성 미리 보기](media/constructor2-preview-cs.png)

1. 드롭다운 메뉴에서 **생성자 'TypeName(...)' 생성**을 선택합니다.

   선택한 매개 변수를 사용하여 생성자가 만들어집니다.

   ![생성자 생성 결과](media/constructor2-result-cs.png)

## <a id="usage"></a> 새 사용에서 생성자 생성(C# 및 Visual Basic)

1. 빨간색 구부러진 곡선이 있는 줄에 커서를 놓습니다. 빨간색 구부러진 곡선은 아직 존재하지 않는 생성자 호출을 나타냅니다.

   - C#:

       ![강조 표시된 코드 C#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 VB](media/constructor-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 빨간색 구부러진 곡선 위로 마우스를 이동하고 표시되는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.

      ![생성자 생성 미리 보기](media/constructor-preview-cs.png)

3. 드롭다운 메뉴에서 **'*TypeName*'에 생성**을 선택합니다.

   > [!TIP]
   > 미리 보기 창 맨 아래에 있는 **변경 내용 미리 보기** 링크를 사용하여 선택하기 전에 적용될 [모든 변경 내용을 확인](../../ide/preview-changes.md)합니다.

   해당 사용에서 추론된 매개 변수를 사용하여 생성자가 만들어집니다.

   - C#:

       ![메서드 생성 결과 C#](media/constructor-result-cs.png)

   - Visual Basic:

       ![메서드 생성 결과 VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> 기존 생성자에 매개 변수 추가(C#만 해당)

1. 기존 생성자 호출에 매개 변수를 추가합니다.

2. 존재하지 않는 생성자를 사용했음을 나타내는 빨간색 구부러진 곡선이 있는 줄에 커서를 놓습니다.

    ![생성자 생성 강조 표시](media/constructor4-highlight-cs.png)

3. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 빨간색 구부러진 곡선 위로 마우스를 이동하고 표시되는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.

      ![생성자 생성 미리 보기](media/constructor4-preview-cs.png)

4. 드롭다운 메뉴에서 **'TypeName(...)'에 매개 변수 추가**를 선택합니다.

   매개 변수는 해당 사용에서 추론된 형식을 사용하여 생성자에 추가됩니다.

   ![생성자 생성 결과](media/constructor4-result-cs.png)

기존 메서드에 매개 변수를 추가할 수도 있습니다. 자세한 내용은 [메서드에 매개 변수 추가](add-parameter.md)를 참조하세요.

## <a id="create"></a> 생성자 매개 변수에서 필드 또는 속성 만들기 및 초기화(C#만 해당)

1. 기존 생성자를 찾고 매개 변수를 추가합니다.

   ![생성자 생성 강조 표시](media/constructor5-highlight-cs.png)

1. 새로 추가된 매개 변수에 커서를 놓습니다.

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](media/screwdriver.png) 아이콘을 클릭합니다.

   ![생성자 생성 미리 보기](media/constructor5-preview-cs.png)

1. 드롭다운 메뉴에서 **속성 만들기 및 초기화** 또는 **필드 만들기 및 초기화**를 선택합니다.

   필드 또는 속성이 만들어지고 사용자 형식과 일치하도록 자동으로 이름이 지정됩니다. 또한 생성자 본문의 필드 또는 속성을 초기화하기 위해 코드 줄이 추가됩니다.

   ![생성자 생성 결과](media/constructor5-result-cs.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
