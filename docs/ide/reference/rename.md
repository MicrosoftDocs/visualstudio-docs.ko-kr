---
title: 리팩터링 이름 바꾸기
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8d5b3d32b23b336dc86a92c33bcb97d02312f2dc
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182961"
---
# <a name="rename-a-code-symbol-refactoring"></a>코드 기호 이름 바꾸기 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 필드, 지역 변수, 메서드, 네임스페이스, 속성 및 형식과 같은 코드 기호의 식별자 이름을 바꿀 수 있습니다.

**시기:** 모든 인스턴스를 찾지 않고도 안전하게 이름을 바꾸고 새 이름을 복사하여 붙여넣으려고 합니다.

**이유:** 전체 프로젝트에 새 이름을 복사하여 붙여넣으면 오류가 발생할 수 있습니다. 이 리팩터링 도구는 이름 바꾸기 작업을 정확하게 수행합니다.

## <a name="how-to"></a>방법

1. 이름을 바꿀 항목을 강조 표시하거나 항목 내부에 텍스트 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 - C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 - Visual Basic](media/rename-highlight-vb.png)

2. 이제 다음과 같이 키보드나 마우스를 사용합니다.

   - **키보드**
      - **Ctrl+R**을 누른 다음 **Ctrl+R**을 누릅니다. 바로 가기 키는 선택한 프로필에 따라 다를 수 있습니다.
   - **마우스**
      - **편집 > 리팩터링 > 이름 바꾸기**를 선택합니다.
      - 코드를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.

3. 항목의 이름을 바꾸려면 새 이름을 입력하면 됩니다.

   - C#:

      ![애니메이션 이름 바꾸기 - C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![이름 바꾸기 - VB](media/rename-rename-vb.png)

   > [!TIP]
   > 또한 이 새 이름을 사용하도록 주석과 기타 문자열을 업데이트할 뿐만 아니라, 편집기의 오른쪽 위에 표시되는 **이름 바꾸기** 상자의 확인란을 사용하여 저장하기 전에 [변경 내용을 미리 볼](../../ide/preview-changes.md) 수도 있습니다.

4. 변경 내용에 만족할 경우 **적용** 단추를 선택하거나 **Enter** 키를 누르면 변경 내용이 커밋됩니다.

## <a name="remarks"></a>설명

- Visual Studio 2019 버전 16.3부터, 형식이 포함된 파일의 이름과 일치하도록 형식의 이름을 바꿀 때 파일 이름을 동시에 바꿀 수 있는 확인란이 표시됩니다. 이 옵션은 클래스, 인터페이스 또는 열거형의 이름을 바꾸는 경우에도 표시됩니다. 여러 정의가 포함된 부분 형식에서는 이 옵션이 지원되지 않습니다.

   ![파일을 사용하여 애니메이션 이름 바꾸기 - C#](media/rename-with-file-animated-cs.gif)

- 충돌을 일으키는 기존 이름을 사용할 경우 **이름 바꾸기** 상자에 경고가 표시됩니다.

   ![이름 바꾸기 충돌](media/rename-conflict-cs.png)

- 기호의 이름을 바꾸는 다른 방법은 편집기에서 해당 이름을 변경하는 것입니다. 그런 다음 커서를 기호 이름에 놓고 **Ctrl**+**을 누릅니다.** 또는 나타나는 전구 아이콘 메뉴를 확장한 후 **\<old name>을 \<new name>으로 이름 바꾸기**를 선택합니다.

   ![편집기에서 이름 바꾸기](media/rename-with-editor-cs.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
