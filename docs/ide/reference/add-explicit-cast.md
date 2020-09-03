---
title: 명시적 캐스트 추가
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e159082266b848ce4742e436c706f3f71b2cc9ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182978"
---
# <a name="add-explicit-cast"></a>명시적 캐스트 추가

이 코드 생성은 다음에 적용됩니다.

- C#

**내용:** 용도에 따라 식에 명시적 캐스트를 자동으로 추가할 수 있습니다.

**시기:** 식에 명시적 캐스트를 추가하고 이를 자동으로 올바르게 할당하려는 경우.

**이유:** 식에 명시적 캐스트를 수동으로 추가할 수 있지만 이 기능은 코드 컨텍스트에 따라 명시적 캐스트를 자동으로 추가해 줍니다.

## <a name="how-to-use-it"></a>사용 방법

1. 오류 위에 캐럿을 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. **‘명시적 캐스트 추가’** 를 선택합니다.

   ![Visual Studio의 ‘명시적 캐스트 추가’ 빠른 작업](media/add-explicit-cast.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [리팩터링](../refactoring-in-visual-studio.md)
