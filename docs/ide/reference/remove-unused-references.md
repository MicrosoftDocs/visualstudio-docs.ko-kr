---
title: 사용하지 않는 참조 제거
description: 새로운 사용하지 않는 참조 제거 명령을 사용하여 사용하지 않는 프로젝트 참조 및 NuGet 패키지를 정리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352114"
---
# <a name="remove-unused-references"></a>사용하지 않는 참조 제거

이 리팩터링은 다음에 적용됩니다.

- C#
- Visual Basic

**대상:** 사용하지 않는 참조를 제거할 수 있습니다.

**시기:** 사용하지 않는 프로젝트 참조 및 NuGet 패키지를 정리하려고 합니다. 

**이유:** 각 모듈을 로드하려면 시간이 걸리고 컴파일러에서 사용되지 않는 메타데이터를 로드할 필요가 없기 때문에 사용하지 않는 프로젝트 참조를 제거하면 공간을 절약하고 애플리케이션의 시작 시간을 단축할 수 있습니다.

## <a name="how-to"></a>방법

1. 솔루션 탐색기에서 프로젝트 이름 또는 종속성 노드를 마우스 오른쪽 단추로 클릭합니다.

2. **사용하지 않는 참조 제거** 를 선택합니다.

    ![사용하지 않는 참조 제거 명령](media/remove-unused-references-command.png)

3. **사용하지 않는 참조 제거** 대화 상자가 열리고 소스 코드에서 사용하지 않는 참조가 표시됩니다. 작업 드롭다운에서 `Keep`을 선택하여 참조를 유지하는 옵션을 사용하면 사용하지 않는 참조는 제거하도록 미리 선택됩니다.

    ![사용하지 않는 참조 제거 대화 상자](media/remove-unused-references-dialog.png)

5. `Apply`를 클릭하여 선택한 참조를 제거합니다. 

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)