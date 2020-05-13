---
title: 익명 형식을 튜플로 변환
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094282"
---
# <a name="convert-anonymous-type-to-tuple"></a>익명 형식을 튜플로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 익명 형식을 튜플로 변환합니다.

**시기:** 튜플로 한정된 익명 형식이 있습니다.

**이유:** [튜플](/dotnet/csharp/tuples)은 간단한 구문을 유지하는 데 도움이 됩니다. 이 빠른 작업을 통해 C# 기능을 더 쉽게 이용할 수 있습니다.

## <a name="how-to"></a>방법

1. 익명 형식으로 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![익명 형식을 튜플로 변환](media/convert-anon-to-tuple.png)

2. **Enter**를 눌러 리팩터링을 수락합니다.

   ![익명 형식을 튜플로 변환](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
