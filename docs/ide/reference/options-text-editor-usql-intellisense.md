---
title: 옵션, 텍스트 편집기, U-SQL, IntelliSense
description: U-SQL 섹션의 IntelliSense 페이지를 사용하여 U-SQL에 대한 텍스트 편집기 IntelliSense 설정을 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.IntelliSense
- VS.ToolsOptionsPages.Text_Editor.HQL.IntelliSense
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1aea741c91f38be9d5b423226e635b77e440d9e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040201"
---
# <a name="options-text-editor-u-sql-intellisense"></a>옵션, 텍스트 편집기, U-SQL, IntelliSense

**IntelliSense** 옵션 페이지를 사용하여 U-SQL의 일부 텍스트 편집기 설정을 수정합니다. 이 옵션 페이지에 액세스하려면 **도구** > **옵션** 을 선택한 다음, **텍스트 편집기** > **U-SQL** > **IntelliSense** 를 선택합니다.

## <a name="intellisense-settings"></a>IntelliSense 설정

**요약 정보** 또는 **Intellisense** 를 사용하도록 설정하려면 이 확인란을 선택합니다. 요약 정보는 마우스 커서로 변수를 가리킬 때 전체 선언을 표시합니다.

## <a name="completion-lists"></a>완성 목록

- **문자가 입력된 후 완성 목록 표시**

   이 옵션을 선택하면 입력하기 시작할 때 IntelliSense에서 자동으로 완성 목록을 표시합니다. 이 옵션을 선택하지 않으면 IntelliSense 완성은 IntelliSense 메뉴를 선택하거나 **Ctrl** + **스페이스바** 를 눌러 사용할 수 있습니다.

- **완성 목록에 키워드 배치**

   이 옵션을 선택할 경우 IntelliSense는 완성 목록에 키워드를 포함합니다.

- **완성 목록에 코드 조각 배치**

   이 옵션을 선택할 경우 IntelliSense는 완성 목록에 코드 조각을 포함합니다.

## <a name="selection-in-completion-list"></a>완성 목록의 선택

- **다음 문자를 입력하여 커밋**

   이 필드는 현재 강조 표시된 완성 목록 제안이 커밋되도록 하는 문자를 표시합니다. 이 목록에서 문자를 추가하거나 제거할 수 있습니다.

- **스페이스바를 눌러 커밋**

   이 옵션을 선택하면 스페이스바를 눌러 강조 표시된 완성 목록 제안을 커밋할 수 있습니다.

- **단어를 모두 입력한 후 Enter 키를 누르면 새 줄 추가**

   선택할 경우 새 줄이 자동으로 추가되고 완성 목록 제안의 모든 문자를 입력하면 커서가 새 줄로 이동합니다.

## <a name="see-also"></a>참조

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)