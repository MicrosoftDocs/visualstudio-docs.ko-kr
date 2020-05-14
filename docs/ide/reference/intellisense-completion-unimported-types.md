---
title: 가져오지 않은 형식에 대한 IntelliSense 완성
description: '`using` 지시문으로 아직 가져오지 않은 형식에 대해 IntelliSense 완성 기능을 사용하는 방법입니다.'
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
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094263"
---
# <a name="intellisense-completion-for-unimported-types"></a>가져오지 않은 형식에 대한 IntelliSense 완성

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 가져오지 않은 형식에 대해 IntelliSense 완성 기능 사용

**시기:** 이미 종속성이 있는 형식을 프로젝트에 추가하려고 하는데, import 문이 파일에 아직 추가되지 않은 경우 

**이유:** 파일에 import 문을 수동으로 추가할 필요가 없습니다.

## <a name="how-to"></a>방법

1. 종속성이 있는 형식을 프로젝트에서 사용하기 시작하면 IntelliSense에서 제안을 제공합니다.
2. **Tab** 키를 누릅니다. 

   import 문이 파일에 추가됩니다.

   ![가져오지 않은 형식에 대한 IntelliSense 완성](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
