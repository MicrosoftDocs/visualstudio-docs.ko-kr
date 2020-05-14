---
title: 사용되지 않는 값 및 매개 변수
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531870"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>사용되지 않은 값 할당, 변수 및 매개 변수

이 리팩터링은 다음에 적용됩니다.

- C#
- Visual Basic

**내용:** 사용되지 않는 매개 변수를 페이드 아웃하고 사용하지 않는 식 값에 대한 경고를 생성합니다. 또한 컴파일러는 흐름 분석을 수행하여 사용되지 않는 값 할당을 찾습니다. 사용되지 않는 값 할당이 페이드 아웃하고 중복 할당을 제거하기 위해 [빠른 작업](../quick-actions.md)으로 전구가 나타납니다. 알 수 없는 값을 가진 사용되지 않는 변수에 [빠른 작업](../quick-actions.md) 대신 [무시 항목](/dotnet/csharp/discards)을 사용할 것을 제안합니다. (무시 항목은 애플리케이션 코드에서 의도적으로 사용되지 않는 임시 더미 변수입니다. 메모리 할당을 줄이고 코드를 더 쉽게 읽을 수 있습니다.)

**시기:** 사용되지 않는 값 할당, 매개 변수 또는 식 값이 있습니다.

**이유:** 값 할당, 변수 또는 매개 변수가 더 이상 사용되지 않는지 구별하기 어려운 경우가 있습니다. 이러한 값을 페이딩 아웃하거나 경고를 생성하여 삭제할 수 있는 코드를 시각적으로 알 수 있습니다.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>사용되지 않는 식 값 및 매개 변수 진단

1. 사용되지 않는 값 할당, 변수 또는 매개 변수를 지정합니다.
2. 사용되지 않는 값 할당 또는 매개 변수가 희미하게 표시됩니다. 사용되지 않는 식 값은 경고를 생성합니다.

  ![사용되지 않는 매개 변수](media/unused-parameter.png)
  ![사용되지 않는 값](media/unused-value.png)
  ![사용되지 않는 값 할당](media/unused-value-assignment.png)
  ![사용되지 않는 값 삭제](media/unused-value-discard.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
- [.NET 개발자를 위한 팁](../csharp-developer-productivity.md)
