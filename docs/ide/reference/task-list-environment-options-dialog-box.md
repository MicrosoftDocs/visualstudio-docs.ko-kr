---
title: 옵션 대화 상자, 환경, 작업 목록
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e28b3b9c3fe4d6e89228dc18ba8b98aa5e0d2e76
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233124"
---
# <a name="options-dialog-box-environment--task-list"></a>옵션 대화 상자: 환경 \> 작업 목록

이 옵션 페이지에서는 **작업 목록** 미리 알림을 생성하는 주석 토큰을 추가, 삭제 및 변경할 수 있습니다. 이러한 설정을 표시하려면 **도구** 메뉴에서 **옵션**을 선택하고 **환경** 폴더를 확장한 후 **작업 목록**을 선택합니다.

## <a name="task-list-tokens"></a>작업 목록 토큰

텍스트가 **토큰 목록**에 있는 토큰으로 시작되는 주석을 코드에 삽입하는 경우 해당 파일이 편집용으로 열릴 때마다 **작업 목록**에 주석이 새 항목으로 표시됩니다. **작업 목록** 항목을 클릭하면 코드에서 해당 주석 줄로 바로 이동합니다. 자세한 내용은 [작업 목록 사용](../../ide/using-the-task-list.md)을 참조하세요.

토큰 목록\
토큰의 목록을 표시하고 사용자 지정 토큰을 추가하거나 제거할 수 있게 합니다. 주석 토큰은 C# 및 C++에서 대/소문자를 구분하지만 Visual Basic에서는 구분하지 않습니다.

> [!NOTE]
> 원하는 토큰을 토큰 목록에서 표시된 대로 정확히 입력하지 않으면 **작업 목록**에 주석 작업이 표시되지 않습니다.

우선 순위\
선택한 토큰을 사용하는 작업의 우선 순위(낮음, 보통 또는 높음)를 설정합니다. 이 토큰으로 시작되는 작업 주석에 **작업 목록**에서 지정된 우선 순위가 자동으로 할당됩니다.

이름\
여기에 토큰 문자열을 입력하고 **추가**를 클릭하여 토큰 목록에 문자열을 추가합니다.

추가\
새 **이름**을 입력하면 사용할 수 있게 됩니다. **이름** 및 **우선 순위** 필드에 입력된 값을 사용하여 새로운 토큰 문자열을 추가하려면 이 옵션을 클릭합니다.

삭제\
토큰 목록에서 선택한 토큰을 삭제하려면 클릭합니다. 기본 주석 토큰은 삭제할 수 없습니다.

변경\
**이름** 및 **우선 순위** 필드에 입력된 값을 사용하여 기존 토큰을 변경하려면 이 옵션을 클릭합니다.

> [!NOTE]
> 기본 주석 토큰을 삭제하거나 이름을 바꿀 수는 없지만 해당 우선 순위 수준을 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [작업 목록 사용](../../ide/using-the-task-list.md)
- [코드에 책갈피 설정](../../ide/setting-bookmarks-in-code.md)
