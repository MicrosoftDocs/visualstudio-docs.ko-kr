---
title: 매개 변수 리팩터링 생성
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 메서드 매개 변수를 자동으로 생성하는 방법을 알아봅니다.
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
ms.openlocfilehash: 21e209f5be9072390df58e78db34811f886fa9c5
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617151"
---
# <a name="generate-parameter"></a>매개 변수 생성

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 자동으로 메서드 매개 변수 생성

**시기:** 현재 컨텍스트에 없는 변수를 메서드에서 참조하여 오류가 표시되는 경우. 코드 수정으로 매개 변수를 생성할 수 있습니다. 

**이유:** 컨텍스트를 유지하면서 메서드 시그니처를 빠르게 수정할 수 있습니다.

## <a name="how-to"></a>방법

1. 변수 이름에 커서를 놓고 **Ctrl**+ **.** 을 누릅니다. **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
1. **매개 변수 생성** 을 선택합니다.

   ![매개 변수 생성](media/generate-parameter.png) 

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
