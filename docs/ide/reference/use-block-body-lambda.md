---
title: 람다 식 또는 블록 본문 사용
description: 빠른 작업 및 리팩터링 메뉴를 사용하여, 식 본문 또는 블록 본문을 사용하도록 람다 식을 리팩터링하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 505a76a2300f2e3ddb9c1513ee64c2a17abb10ab
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480176"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>람다 식에 식 본문 또는 블록 본문 사용

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 식 본문 또는 블록 본문을 사용하도록 람다 식을 리팩터링할 수 있습니다.

**시기:** 식 본문 또는 블록 본문 중 하나를 사용하려면 람다 식을 사용하는 것이 좋습니다.

**이유:** 사용자 기본 설정에 따라 가독성을 개선하기 위해 람다 식을 리팩터링할 수 있습니다.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>람다 식 본문 또는 블록 본문 리팩터링

1. 람다 연산자의 오른쪽에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

  ![람다 식/블록 본문 사용](media/block-body-lambda.png)

3. **람다 식에 블록 본문 사용** 또는 **람다 식에 식 본문 사용** 을 선택합니다.

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [.NET 개발자를 위한 팁](../csharp-developer-productivity.md)