---
title: switch 문을 switch 식으로 변환
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 switch 문을 C# 8.0 switch 식으로 변환하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: add43010fcec04cbe12889672f561f22057efb8c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305526"
---
# <a name="convert-switch-statement-to-switch-expression"></a>switch 문을 switch 식으로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** [switch 문](/dotnet/csharp/language-reference/keywords/switch)을 C# 8.0 [switch 식](/dotnet/csharp/whats-new/csharp-8#switch-expressions)으로 변환

**시기:** `switch` 문을 `switch` 식으로 변환하거나 그 반대로 변환하려는 경우 

**이유:** 식만 사용하는 경우, 이 리팩터링을 통해 기존의 `switch` 문에서 쉽게 전환할 수 있습니다.

## <a name="how-to"></a>방법

1. `switch` 식은 새로운 C# 8.0 기능이므로 프로젝트 파일에서 [언어 버전을 미리 보기로 설정](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file)합니다.
2. 커서를 `switch` 키워드에 놓고 **Ctrl**+ **.** 을 누릅니다. **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. **switch 문을 식으로 변환** 을 선택합니다.

   ![switch 문을 switch 식으로 변환](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
