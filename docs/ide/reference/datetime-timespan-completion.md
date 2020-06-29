---
title: IntelliSense 메뉴를 통한 DateTime 및 TimeSpan 완성
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290911"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>IntelliSense 메뉴를 통한 DateTime 및 TimeSpan 완성

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** IntelliSense 메뉴를 통한 DateTime 및 TimeSpan 문자열 리터럴 완성

**시기:** DateTime 및 TimeSpan 문자열 리터럴을 작성하려는 경우입니다. IntelliSense는 각 문자의 의미에 대한 설명과 기본 완성 기능을 제공합니다. 

**이유:** DateTime 형식을 기억하기는 어려우며 IntelliSense를 활용하면 작성에 도움이 됩니다.

## <a name="how-to"></a>방법

1. DateTime 또는 TimeSpan 문자열 리터럴에 커서를 놓습니다.
2. **Ctrl**+**스페이스바**를 눌러 **IntelliSense** 메뉴를 실행합니다.
3. 추가할 문자를 선택합니다.

   ![DateTime 완성 IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
