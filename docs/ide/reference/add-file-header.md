---
title: 파일 헤더 추가
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44c3b64d9fb8944a578d054b7d98d4bf39bde3bc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810378"
---
# <a name="add-file-header"></a>파일 헤더 추가

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)를 사용하여 기존 파일, 프로젝트 및 솔루션에 파일 헤더를 추가합니다.

**시기:** 파일, 프로젝트 및 솔루션에 파일 헤더를 쉽게 추가하려고 합니다.

**이유:** 팀에서 저작권을 위해 파일 헤더를 포함하도록 요구합니다. 

## <a name="how-to"></a>방법

1. 프로젝트 또는 솔루션에 [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)를 추가합니다(아직 없는 경우).

2. EditorConfig 파일에 다음 규칙을 추가합니다. *file_header_template*.

3. 규칙 값을 적용하려는 헤더 텍스트와 같게 설정합니다. `{fileName}`을 파일 이름의 자리 표시자로 사용할 수 있습니다.

    ![EditorConfig 파일 헤더 규칙](media/add-file-header-rule.png)

    > [!NOTE]
    > EditorConfig에 명시적 multiline을 사용할 수 없으며 Unix 줄 바꿈 문자를 사용하여 새 줄을 삽입해야 합니다.

4. 또는 C# 또는 Visual Basic 파일의 첫 번째 줄에 캐럿을 추가합니다.

5. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

6. **파일 헤더 추가**를 선택합니다. 

    ![EditorConfig 파일 헤더 규칙](media/add-file-header.png)

7. 전체 프로젝트 또는 솔루션에 파일 헤더를 적용하려면 **다음 위치에서 모든 발생 수정** 옵션 아래에서 **프로젝트** 또는 **솔루션**을 선택합니다.

8. 변경 내용을 미리 볼 수 있는 **모든 발생 수정** 대화 상자가 열립니다.

    ![모든 발생 수정 대화 상자](media/file-header-preview-changes.png)

8. **적용**을 선택하여 변경 내용을 적용합니다.

## <a name="see-also"></a>참조

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)