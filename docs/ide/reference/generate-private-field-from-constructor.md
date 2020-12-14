---
title: 생성자에서 전용 필드 및 속성 생성
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 생성자에서 프라이빗 필드 또는 속성을 생성하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617463"
---
# <a name="generate-private-field-and-property-from-constructor"></a>생성자에서 전용 필드 및 속성 생성

이 리팩터링은 다음에 적용됩니다. 

- C# 

**내용:** 생성자에서 전용 필드 또는 속성을 생성합니다. 

**시기:** 생성자에서 전용 필드 또는 속성을 신속하게 추가하고 초기화하려고 합니다.

**이유:** 전용 필드 및 속성 작성은 시간이 오래 걸리고 반복적인 작업이 될 수 있습니다. 이 리팩터링을 사용하면 더 빠르고 프로그램을 더욱 강력하게 만들 수 있습니다.

## <a name="how-to"></a>방법 

1. 생성자 내의 매개 변수 이름에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   
3. 다음 중 하나를 선택합니다.

- **필드 만들기 및 초기화** 또는 **속성 만들기 및 초기화**

   ![생성자에서 전용 필드 생성](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>참조 

- [리팩터링](../refactoring-in-visual-studio.md)
