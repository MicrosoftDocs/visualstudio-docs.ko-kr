---
title: IComparable을 구현하는 형식에 대한 비교 연산자 생성
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290908"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>IComparable을 구현하는 형식에 대한 비교 연산자 생성

이 코드 생성은 다음에 적용됩니다.

- C#

**내용:** IComparable을 구현하는 형식에 대한 **비교 연산자**를 생성할 수 있습니다.

**시기:** IComparable을 구현하는 형식이 있으면 비교 연산자가 자동으로 추가됩니다.

**이유:** 값 형식을 구현하는 경우에는 ValueType에서 **Equals** 메서드의 기본 구현에 대한 성능을 향상시키기 위해 Equals 메서드를 재정의하는 것을 고려해야 합니다.

## <a name="how-to"></a>방법

1. 클래스 내부 또는 IComparable 키워드에 커서를 놓습니다.

2. 다음 작업 중 하나를 수행합니다.

   - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.

   - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![비교 연산자 생성](media/generate-comparison-operators.png)

3. 드롭다운 메뉴에서 **Equals(object) 생성**을 선택합니다.

## <a name="see-also"></a>참조

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
