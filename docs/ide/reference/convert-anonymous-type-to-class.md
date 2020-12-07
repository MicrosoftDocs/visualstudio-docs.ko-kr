---
title: 익명 형식을 클래스로 변환
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 Visual Studio에서 무명 형식을 클래스로 변환하는 방법을 알아봅니다.
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040787"
---
# <a name="convert-anonymous-type-to-class"></a>무명 형식을 클래스로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 익명 형식을 클래스로 변환합니다.

**시기:** 클래스에서 계속 빌드하려는 익명 형식이 있습니다.

**이유:** 익명 형식은 로컬에서만 사용하는 경우에 유용합니다. 코드가 증가함에 따라 클래스로 승격시키는 쉬운 방법이 있습니다.

## <a name="how-to"></a>방법

1. 익명 형식으로 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![익명 형식을 클래스로 변환](media/convert-anon-to-class.png)

2. **Enter** 를 눌러 리팩터링을 수락합니다.

   ![익명 형식을 허용하는 클래스로 변환](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
