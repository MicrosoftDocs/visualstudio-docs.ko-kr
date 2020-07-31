---
title: 가져오지 않은 형식 및 확장 메서드에 대한 IntelliSense 완성
description: 아직 `using` 지시문으로 가져오지 않은 형식 및 확장 메서드에 대해 IntelliSense 완성 기능을 사용하는 방법입니다.
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d6112bc3894424b9dfd3d060ed390960243b0f98
ms.sourcegitcommit: 4a77403b6bd33c5a6e66a3eefd42c81c39fb67ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87331000"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>가져오지 않은 형식 및 확장 메서드에 대한 IntelliSense 완성

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 가져오지 않은 형식 및 확장 메서드에 대해 IntelliSense에서 제공하는 완성 기능

**시기:** 이미 종속성이 있는 형식이나 확장 메서드를 프로젝트에서 사용하려고 하는데, using 문이 파일에 아직 추가되지 않은 경우 

**이유:** 파일에 using 문을 수동으로 추가할 필요가 없습니다.

## <a name="how-to"></a>방법

1. 종속성이 있는 형식이나 확장 메서드의 이름을 프로젝트에서 입력하기 시작하면 IntelliSense에서 제안 사항을 제공합니다. 가져오지 않은 네임스페이스의 항목에는 접미사로 표시되는 포함하는 네임스페이스가 있습니다.

   > [!TIP]
   > 완성 목록의 왼쪽 아래에 표시되는 **확장 단추(Alt+A)** 를 사용하여 필요 시 가져오지 않은 네임스페이스에서 항목을 표시하거나 숨길 수 있습니다. 기본 동작을 변경하려면 **도구** > **옵션** > **텍스트 편집기** > **C#**  / **Basic** > **IntelliSense**로 이동하여 **가져오지 않은 네임스페이스의 항목 표시**를 찾으세요.

2. 가져오지 않은 항목을 선택하여 커밋합니다. 

   using 문이 파일에 자동으로 추가됩니다.

   ![가져오지 않은 형식에 대한 IntelliSense 완성](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>참조

- [IntelliSense](../using-intellisense.md)
- [리팩터링](../refactoring-in-visual-studio.md)
