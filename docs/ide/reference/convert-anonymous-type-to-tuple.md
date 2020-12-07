---
title: 익명 형식을 튜플로 변환
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 Visual Studio에서 무명 형식을 튜플로 변환하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040864"
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
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![익명 형식을 튜플로 변환](media/convert-anon-to-tuple.png)

2. **Enter** 를 눌러 리팩터링을 수락합니다.

   ![무명 형식을 허용된 튜플로 변환](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
