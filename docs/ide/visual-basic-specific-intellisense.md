---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118de9ec05bcd5c56376376619bea0c5148d36ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594190"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Visual Basic 코드 파일에 대한 IntelliSense

Visual Basic 소스 코드 편집기는 다음과 같은 IntelliSense 기능을 제공합니다.

## <a name="syntax-tips"></a>구문 팁

구문 팁은 입력하는 문의 구문을 표시합니다. [선언](/dotnet/visual-basic/language-reference/statements/declare-statement)과 같은 문에 유용합니다.

## <a name="automatic-completion"></a>자동 완성

- 다양한 키워드에 대한 완성

     예를 들어 `goto` 및 공백을 입력하는 경우 IntelliSense는 드롭다운 메뉴에서 정의된 레이블 목록을 표시합니다. 지원되는 다른 키워드에는 `Exit`, `Implements`, `Option` 및 `Declare`가 포함됩니다.

- `Enum` 및 `Boolean` 완료

    문이 열거형의 멤버를 참조하는 경우 IntelliSense는 `Enum`의 멤버 목록을 표시합니다. 문이 `Boolean`을 참조하는 경우 IntelliSense는 true-false 드롭다운 메뉴를 표시합니다.

**Visual Basic** 폴더의 **일반** 속성 페이지에서 **멤버 목록 자동 표시**의 선택을 해제하여 완료를 기본적으로 끌 수 있습니다.

멤버 목록, 단어 자동 완성 또는 **Alt**+**오른쪽 화살표**를 호출하여 완료를 수동으로 실행할 수 있습니다. 자세한 내용은 [IntelliSense 사용](../ide/using-intellisense.md)을 참조하세요.

## <a name="intellisense-in-zone"></a>영역 내 IntelliSense

영역 내 IntelliSense는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]를 통해 애플리케이션을 배포해야 하는 Visual Basic 개발자에게 도움을 주며 부분 신뢰 설정으로 제한됩니다. 이 기능:

- 애플리케이션을 실행할 사용 권한을 선택할 수 있습니다.

- 선택한 영역의 API를 멤버 목록에서 사용할 수 있는 상태로 표시하고, 추가 사용 권한이 필요한 API를 사용할 수 없는 상태로 표시합니다.

자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.

## <a name="filtered-completion-lists"></a>필터링된 완성 목록

Visual Basic의 경우 IntelliSense 완성 목록에는 목록의 맨 아래에 두 개의 탭 컨트롤이 있습니다. 기본적으로 선택되는 **공통** 탭에는 작성 중인 문을 완성하는 데 가장 자주 사용한 항목이 표시됩니다. **모든** 탭에는 **공통** 탭에도 있는 항목을 포함하여 자동 완성에 사용할 수 있는 모든 항목이 표시됩니다.

## <a name="see-also"></a>참고 항목

- [IntelliSense 사용](../ide/using-intellisense.md)
