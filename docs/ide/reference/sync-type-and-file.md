---
title: 형식과 일치하도록 파일 이름 바꾸기
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5b7a42a174fecd078e804f2ab3c35fbe442364a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594398"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>형식을 파일 이름에 동기화 또는 파일 이름을 형식 리팩터링에 동기화

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 파일 이름과 일치하도록 형식 이름을 바꾸거나 포함된 형식과 일치하도록 파일 이름을 바꿀 수 있습니다.

**시기:** 파일 또는 형식의 이름이 바뀌었지만 일치시킬 해당 파일 또는 형식이 업데이트되지 않았습니다.

**이유:** 다른 이름의 파일로 형식을 저장하거나 그 반대로 저장하면 검색할 대상을 찾기 어렵습니다. 형식 또는 파일의 이름을 바꾸면 코드를 더 쉽게 읽고 탐색할 수 있습니다.

> [!NOTE]
> 이 리팩터링은 .NET Standard 및 .NET Core 프로젝트에서 아직 사용할 수 없습니다.

## <a name="how-to"></a>방법

1. 동기화할 형식 이름을 강조 표시하거나 형식 이름 내부에 텍스트 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 - C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 - Visual Basic](media/synctype-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 트리거에 **빠른 작업 및 리팩터링** 메뉴를 선택 **로 파일 이름 바꾸기 *TypeName*.cs** 미리 보기 창 팝업에서 위치 *TypeName* 은 선택한 형식의 이름입니다.
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **_Filename_으로 형식 이름 바꾸기**를 선택합니다. 여기서 *Filename*은 현재 파일의 이름입니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 ***TypeName*.cs로 파일 이름 바꾸기**를 선택합니다. 여기서 *TypeName*은 선택한 형식의 이름입니다.
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **_Filename_으로 형식 이름 바꾸기**를 선택합니다. 여기서 *Filename*은 현재 파일의 이름입니다.

   형식 또는 파일의 이름이 바뀝니다.

   - C#: 아래 예제에서는 **MyClass.cs** 파일의 이름이 형식 이름과 일치하도록 **MyNewClass.cs**로 바뀌었습니다.

       ![인라인 결과 C#](media/synctype-result-cs.png)

   - Visual Basic: 아래 예제에서는 **Employee.vb** 파일의 이름이 형식 이름과 일치하도록 **Person.vb**로 바뀌었습니다.

       ![인라인 결과 Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
