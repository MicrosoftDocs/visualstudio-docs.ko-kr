---
title: 멤버를 정적으로 설정
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 멤버를 정적으로 설정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561021"
---
# <a name="make-member-static"></a>멤버를 정적으로 설정

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 멤버를 정적으로 설정합니다.

**시기:** 정적이 아닌 멤버를 정적 멤버로 만들려고 합니다.

**이유:** 정적 멤버는 가독성을 높입니다. 특정 코드가 격리되었다는 것을 알고 있으면 보다 쉽게 이해하고, 다시 읽고, 다시 사용할 수 있습니다. 

## <a name="how-to"></a>방법

1. 멤버 이름에 캐럿을 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![멤버를 정적으로 설정](media/make-member-static.png)

3. **정적으로 만들기** 를 선택합니다.

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
