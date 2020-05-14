---
title: 인터페이스 추출 리팩터링
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5055f50d07cf9362c9be1bdc8135e31240a7cc66
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595672"
---
# <a name="extract-an-interface-refactoring"></a>인터페이스 추출 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 클래스, 구조체 또는 인터페이스에서 기존 멤버를 사용하여 인터페이스를 만들 수 있습니다.

**시기:** 다른 클래스, 구조체 또는 인터페이스로 상속될 수 있는 클래스, 구조체 또는 인터페이스의 멤버가 있습니다.

**이유:** 인터페이스는 개체 지향 설계에 적합한 구문입니다. Eat, Drink, Sleep과 같은 공통 메서드를 모두 포함할 수 있는 다양한 동물(Dog, Cat, Bird)에 대한 클래스를 상상해 보세요. IAnimal 같은 인터페이스를 사용하면 Dog, Cat 및 Bird가 이러한 메서드에 대해 공통 “시그니처”를 가질 수 있습니다.

## <a name="extract-an-interface-refactoring"></a>인터페이스 추출 리팩터링

1. 커서를 클래스 이름에 놓습니다.

   - C#:

       ![강조 표시된 코드 - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 - Visual Basic](media/extractinterface-highlight-vb.png)

2. 다음으로, 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - **Ctrl+R**을 누른 다음 **Ctrl+I**를 누릅니다. (바로 가기 키는 선택한 프로필에 따라 다를 수 있습니다.)
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **인터페이스 추출**을 선택합니다.
   - **마우스**
      - **편집 > 리팩터링 > 인터페이스 추출**을 선택합니다.
      - 클래스 이름을 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **인터페이스 추출**을 선택합니다.

3. 표시되는 **인터페이스 추출** 대화 상자에서 요청된 정보를 입력합니다.

   ![인터페이스 추출](media/extractinterface-dialog-same-file.png)

   | 필드 | 설명 |
   | - | - |
   | **새 인터페이스 이름** | 만들려는 인터페이스의 이름입니다. 이름은 기본적으로 I*ClassName*으로 설정됩니다. 여기서 *ClassName*은 위에서 선택한 클래스의 이름입니다. |
   | **새 파일 이름** | 인터페이스를 포함할 생성된 파일의 이름입니다. 인터페이스 이름과 마찬가지로 이 름은 기본적으로 I*ClassName*으로 설정됩니다. 여기서 *ClassName*은 위에서 선택한 클래스의 이름입니다. **현재 파일에 추가** 옵션을 선택할 수도 있습니다. |
   | **인터페이스를 구성할 공용 멤버 선택** | 인터페이스로 추출할 항목입니다. 원하는 만큼 선택할 수 있습니다. |

4. **확인**을 선택합니다.

   지정된 이름의 파일에 인터페이스가 만들어집니다. 또한 선택한 클래스가 해당 인터페이스를 구현합니다.

   - C#:

      ![결과 클래스 - C#](media/extractinterface-class-cs.png)

      ![결과 인터페이스 - C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![결과 클래스 - Visual Basic](media/extractinterface-class-vb.png)

      ![결과 인터페이스 - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
- [.NET 개발자를 위한 팁](../csharp-developer-productivity.md)
