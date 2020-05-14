---
title: Auto 속성과 full 속성 간 변환
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395738"
---
# <a name="convert-between-auto-property-and-full-property"></a>Auto 속성과 full 속성 간 변환

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 자동 구현 속성과 전체 속성 간에 변환합니다.

**시기:** 속성의 논리가 변경된 경우.

**이유:** 자동 구현 속성과 전체 속성 간에 수동으로 변환할 수 있지만 이 기능은 변환 작업으로 자동으로 해 줍니다. 

## <a name="how-to"></a>방법

1. 속성 이름 위에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. 다음 두 옵션 중에서 선택합니다. 

    **전체 속성으로 변환**을 선택합니다.

   ![자동 속성을 전체 속성으로 변환](media/convert-auto-property-to-full-property.png) 

    **auto 속성 사용**을 선택합니다. 

    ![전체 속성을 auto 속성으로 변환](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
