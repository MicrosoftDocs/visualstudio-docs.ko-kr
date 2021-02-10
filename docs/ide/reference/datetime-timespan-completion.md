---
title: IntelliSense를 통한 DateTime 및 TimeSpan 완성
description: IntelliSense 메뉴를 사용하여 DateTime 및 TimeSpan 문자열 리터럴과 형식 문자열을 완성합니다.
ms.custom: SEO-VS-2020
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bf637106dbf89b533c90b86b2cc50649064fd577
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919574"
---
# <a name="datetime-and-timespan-completion-by-using-the-intellisense-menu"></a>IntelliSense 메뉴를 사용하여 DateTime 및 TimeSpan 완성

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** IntelliSense 메뉴를 통한 DateTime 및 TimeSpan 문자열 리터럴 및 형식 문자열 완성

**시기:** DateTime 및 TimeSpan 문자열 리터럴 및 형식 문자열을 작성한다고 가정하겠습니다. IntelliSense는 각 문자의 의미에 대한 설명과 기본 완성 기능을 제공합니다.

**이유:** DateTime 형식을 기억하기는 어려우며 IntelliSense를 활용하면 작성에 도움이 됩니다.

## <a name="how-to"></a>방법

1. DateTime 또는 TimeSpan 형식 문자열에 커서를 놓습니다.
2. **Ctrl**+**스페이스바** 를 눌러 **IntelliSense** 메뉴를 실행합니다.
3. 추가할 문자를 선택합니다.

   ![DateTime 완성 IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
