---
title: IntelliSense를 통한 정규식 완성 메뉴
description: IntelliSense 메뉴에서 IntelliSense를 사용하여 정규식을 작성하는 방법을 알아봅니다.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 25243e5fbdd06a734d17158ba9200f8b56a6b040
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958130"
---
# <a name="regex-completion-through-intellisense-menu"></a>IntelliSense를 통한 정규식 완성 메뉴

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** IntelliSense를 통한 정규식(regex) 완성 메뉴

**시기:** IntelliSense의 도움을 받아 정규식을 작성하려는 경우. IntelliSense는 각 정규식 문자의 의미에 대한 설명과 기본 완성 기능을 제공합니다. 

**이유:** 정규식은 작성하기 어려우며, IntelliSense를 사용하면 작성하는 데 도움이 됩니다.

## <a name="how-to"></a>방법

1. 정규식 문자열에 커서를 놓습니다.
2. **Ctrl**+**스페이스바** 를 눌러 **IntelliSense** 메뉴를 실행합니다.
3. 정규식 문자열에 추가할 문자를 선택합니다.

   ![정규식 완성 IntelliSense](../media/regex-completion-intellisense.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
