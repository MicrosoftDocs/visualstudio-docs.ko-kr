---
title: 생성자에서 전용 필드 생성
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
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094021"
---
# <a name="generate-private-field-from-constructor"></a>생성자에서 전용 필드 생성

이 리팩터링은 다음에 적용됩니다. 

- C# 

- Visual Basic

**내용:** 생성자에서 프라이빗 필드를 생성합니다. 

**시기:** 생성자에서 프라이빗 필드를 빠르게 추가하려고 합니다.

**이유:** 프라이빗 필드 작성에는 시간이 오래 걸리고 반복적인 작업이 될 수 있습니다. 이 리팩터링을 사용하면 더 빠르고 프로그램을 더욱 강력하게 만들 수 있습니다.

## <a name="how-to"></a>방법 

1. 생성자 내의 매개 변수 이름에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   
3. **필드 만들기 및 초기화** 옵션을 선택합니다.

   ![생성자에서 전용 필드 생성](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>참조 

- [리팩터링](../refactoring-in-visual-studio.md)
