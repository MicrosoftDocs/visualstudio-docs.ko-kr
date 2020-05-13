---
title: 형식을 일치하는 파일 리팩터링으로 이동
description: 같은 이름을 가진 별도의 파일로 형식을 이동합니다. 형식을 마우스 오른쪽 단추로 클릭하고 빠른 작업 및 리팩터링를 선택한 다음 <TypeName>.cs로 형식 이동을 선택합니다.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba082e90c2447d1da7510ce16f888f67a52b5ac0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585273"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>형식을 일치하는 파일 리팩터링으로 이동

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 선택한 형식을 같은 이름을 가진 별도의 파일로 이동할 수 있습니다.

**시기:** 동일한 파일에 구분하려는 여러 클래스, 구조체, 인터페이스 등이 있습니다.

**이유:** 같은 파일에 여러 형식을 넣으면 이러한 형식을 찾기 어려울 수 있습니다. 형식을 같은 이름을 가진 파일로 이동하면 코드를 더 쉽게 읽고 탐색할 수 있습니다.

## <a name="how-to"></a>방법

1. 커서를 정의된 형식의 이름 안에 놓습니다. 다음은 그 예입니다.

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. 다음 작업 중 하나를 수행합니다.

   - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러
   - 형식 이름을 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링**을 선택합니다.

1. 메뉴에서 **형식을 *TypeName*.cs로 이동**을 선택합니다. 여기서 *TypeName*은 선택한 형식의 이름입니다.

   형식과 동일한 이름을 가진 프로젝트의 새 파일로 형식이 이동됩니다.

   - C#:

      ![인라인 결과 - C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![인라인 결과 - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
