---
title: 기본 클래스 추출
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8eb87ff8e3acc141c49a495b155fb769e03fb89b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403532"
---
# <a name="extract-base-class"></a>기본 클래스 추출

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 기본 클래스를 추출합니다.

**시기:** 선택한 클래스에서 새 기본 클래스로 멤버를 추출하려고 합니다.

**이유:** 수동으로 멤버를 풀할 때 시간이 오래 걸리고 워크플로에서 벗어날 수 있습니다. 

## <a name="how-to"></a>방법

1. 클래스 이름 또는 강조 표시된 멤버에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. **새 기본 클래스까지 멤버를 풀하세요...** 를 선택합니다.

    ![기본 클래스 추출 대화 상자](media/extract-base-class.png)

새 **기본 클래스 추출** 대화 상자가 열립니다. 여기서 기본 클래스의 이름과 기본 클래스를 배치해야 할 위치를 지정할 수 있습니다. 새 기본 클래스로 전송할 멤버를 선택하고 추상으로 지정 열에서 확인란을 선택하여 멤버를 추상으로 지정하도록 선택할 수 있습니다.

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
