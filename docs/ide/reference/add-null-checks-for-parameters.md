---
title: 모든 (매개 변수)에 대한 null 검사 추가
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782344"
---
# <a name="add-null-checks-for-all-parameters"></a>모든 매개 변수에 대한 null 검사 추가 

이 리팩터링은 다음에 적용됩니다. 

- C# 

**내용:** 확인되지 않은 모든 nullable 매개 변수의 nullity를 확인하는 `if` 문을 만들고 추가합니다. 

**시기:** 해당하는 모든 메서드 매개 변수에 대한 null 검사를 빠르게 추가하려고 합니다.

**이유:** 많은 매개 변수에 대해 null 검사를 작성하는 것은 시간이 오래 걸리고 반복적인 작업입니다. 이 리팩터링을 사용하면 더 빠르고 프로그램을 더욱 강력하게 만들 수 있습니다.  

## <a name="how-to"></a>방법 

1. 메서드 내의 매개 변수에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![빠른 작업 및 리팩터링](media/add-null-checks-for-all-parameters.png)
   
3. **모든 매개 변수에 대한 null 검사 추가** 옵션을 선택합니다.

   ![모든 항목에 대해 null 검사 추가](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>참조 

- [리팩터링](../refactoring-in-visual-studio.md)
