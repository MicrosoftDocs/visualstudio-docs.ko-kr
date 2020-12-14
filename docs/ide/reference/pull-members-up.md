---
title: 멤버 끌어오기
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 멤버를 기본 형식까지 풀하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616878"
---
# <a name="pull-members-up"></a>멤버 끌어오기

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 멤버를 기본 형식까지 끌어올 수 있습니다.

**시기:** 인터페이스를 구현했고 멤버를 기본 형식으로 이동하려고 합니다.

**이유:** 멤버를 끌어오면 인터페이스의 다른 구현도 해당 멤버에 상속할 수 있습니다.

## <a name="how-to"></a>방법

1. 구현된 인터페이스의 모든 멤버에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![멤버 끌어오기](media/pull-members-up.png)

2. **기본 형식까지 멤버 끌어오기** 를 선택합니다.

3. 대화 상자에서 선택한 인터페이스에 추가할 멤버를 선택합니다.

   ![멤버 끌어오기](media/pull-members-up-dialog.png)

4. **확인** 을 선택합니다. 선택한 멤버를 인터페이스로 끌어옵니다.

   ![멤버 끌어오기 완성](media/pull-members-up-completed.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
