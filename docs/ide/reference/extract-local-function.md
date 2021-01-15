---
title: 로컬 함수 추출
description: 코드를 선택하고 Ctrl+R, Ctrl+M을 입력하여 코드 조각을 고유한 함수로 전환합니다.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129460"
---
# <a name="extract-local-function-refactoring"></a>로컬 함수 추출 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 기존 메서드의 코드 조각을 로컬 함수로 전환할 수 있습니다.

**시기:** 로컬 함수에서 호출해야 하는 일부 메서드에 기존 코드 조각이 있습니다.

**이유:** 해당 코드를 복사하여 붙여넣을 수 있지만 중복이 발생합니다. 더 나은 솔루션은 해당 조각을 자체 로컬 함수로 리팩터링하는 것입니다.

## <a name="how-to"></a>방법

1. 추출할 코드를 강조 표시합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다. 

3. **로컬 함수 추출** 을 선택합니다.

    ![줄이 강조 표시된 Visual Studio 코드 창의 스크린샷 빠른 작업 및 리팩터링 메뉴가 열리고 로컬 함수 추출이 선택됩니다.](media/extract-local-function.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
