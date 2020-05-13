---
title: U-SQL 편집기 서식 옵션
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 200ec41a1295178f1127d10053985384a7813158
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568271"
---
# <a name="options-text-editor-u-sql-formatting"></a>옵션, 텍스트 편집기, U-SQL, 서식

**서식 지정** 옵션 페이지를 사용하여 코드 편집기의 코드를 서식 지정하기 위한 옵션을 설정합니다. 이 옵션 페이지에 액세스하려면 **도구** > **옵션**을 선택합니다. **옵션** 대화 상자에서 **텍스트 편집기** > **U-SQL** > **서식**을 선택합니다.

## <a name="general-page"></a>일반 페이지

### <a name="general-settings"></a>일반 설정

이 설정은 코드 편집기가 서식 옵션을 코드에 적용하는 *시기*에 영향을 미칩니다.

- **세미콜론 입력 시 완성 문에 서식 자동 지정**

   이 옵션을 선택하면 편집기에 대해 선택된 서식 옵션에 따라 세미콜론 키를 선택하면 문에 서식이 지정됩니다.

- **붙여넣을 때 서식 자동 지정**

   이 옵션을 선택하면 편집기에 대해 선택된 서식 옵션에 맞게 편집기에 붙여넣는 텍스트에 서식이 지정됩니다.

## <a name="preview-windows"></a>미리 보기 창

**들여쓰기**, **줄 추가** 및 **간격** 하위 페이지에는 아래에 각각 미리 보기 창이 표시됩니다. 미리 보기 창에는 각 옵션의 효과가 표시됩니다. 미리 보기 창을 사용하려면 서식 옵션을 선택합니다. 미리 보기 창에는 선택된 옵션의 예제가 표시됩니다. 확인란을 선택하여 설정을 변경하면 미리 보기 창이 업데이트되어 새 설정의 효과가 표시됩니다.

### <a name="indentation-remarks"></a>들여쓰기 설명

각 언어에 대한 **탭** 페이지의 들여쓰기 옵션은 줄 끝에서 **Enter** 키를 누를 때 코드 편집기에서 커서를 배치하는 위치만을 결정합니다. **서식** 아래 들여쓰기 옵션은 코드 서식이 자동으로 지정되는 경우 적용됩니다(예:

- **붙여넣을 때 들여쓰기 조정**이 선택된 동안 코드를 파일에 붙여넣을 경우,
- 서식 지정되는 블록이 수동으로 입력되는 경우).

## <a name="see-also"></a>참고 항목

- [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md)
