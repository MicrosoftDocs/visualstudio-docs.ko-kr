---
title: IDE 사용자 지정
ms.date: 11/20/2017
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39c9edbf5e96a59912c0cf16d7b4178f6fba2a62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585745"
---
# <a name="personalize-the-visual-studio-ide"></a>Visual Studio IDE 개인 설정

사용자 고유의 개발 스타일 및 요구 사항을 가장 효과적으로 지원하기 위해 다양한 방식으로 Visual Studio를 개인 설정할 수 있습니다. 많은 설정이 Visual Studio 인스턴스에서 사용자와 함께 로밍됩니다.&mdash;[동기화 설정](../ide/synchronized-settings-in-visual-studio.md)을 참조하세요. 이 문서에서는 다양한 개인 설정과 추가 정보를 확인할 수 있는 위치를 간략하게 설명합니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio IDE 사용자 지정](/visualstudio/mac/customizing-the-ide)을 참조하세요.

## <a name="default-settings"></a>기본 설정

개발 유형에 맞게 Visual Studio를 최적화하는 기본 설정 컬렉션을 선택할 수 있습니다. 자세한 내용은 [환경 설정](environment-settings.md)을 참조하세요.

## <a name="general-environment-options"></a>일반 환경 옵션

다수의 개인 설정 옵션이 [환경 옵션](../ide/reference/general-environment-options-dialog-box.md) 대화 상자를 통해 표시됩니다. 이러한 대화 상자에 액세스하는 방법은 두 가지입니다.

- 메뉴 모음에서 **도구** > **옵션**을 선택하고, **환경** 노드가 아직 확장되지 않은 경우 확장합니다.

- **Ctrl**+**Q**를 누르고 검색 상자에 **환경**을 입력한 다음, 결과에서 **환경 > 일반**을 선택합니다.

> [!TIP]
> 옵션 대화 상자가 표시되면 **F1** 키를 눌러 해당 페이지의 다양한 설정에 대한 도움말을 볼 수 있습니다.

## <a name="environment-color-themes"></a>환경 색 테마

밝게, 어둡게 및 파란색 중에서 색 테마를 변경하려면 검색 상자에 **환경**을 입력하고 **환경 > 일반**을 선택합니다. **옵션** 대화 상자에서 **색 테마** 옵션을 변경합니다.

편집기에서 색 지정 옵션을 변경하려면 검색 상자에 **환경**을 입력하고 **환경 > 글꼴 및 색**을 선택합니다. [방법: 글꼴 및 색 변경](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)을 참조하세요.

### <a name="main-menu-casing"></a>주 메뉴 대/소문자 구분

주 메뉴 대/소문자 구분을 **단어의 첫 글자를 대문자로**("File")와 **모두 대문자로**(예: "FILE") 사이에서 변경할 수 있습니다. 검색 상자에 **환경**을 입력하고 **환경 > 일반**을 선택한 다음, **메뉴 모음에 ‘단어의 첫 글자를 대문자’로 스타일 적용** 옵션을 변경합니다.

### <a name="customize-menus-and-toolbars"></a>메뉴 및 도구 모음 사용자 지정

메뉴 또는 도구 모음 항목을 추가하거나 제거하려면 [방법: 메뉴 및 도구 모음 사용자 지정](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)을 참조하세요.

::: moniker range="vs-2017"

## <a name="start-page"></a>시작 페이지

사용자와 사용자의 팀을 위한 사용자 지정 시작 페이지를 만들려면 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)을 참조하세요.

::: moniker-end

## <a name="window-layouts"></a>창 레이아웃

여러 창 레이아웃을 정의하고 저장할 수 있으며 창 레이아웃 간을 전환할 수 있습니다. 예를 들어 코딩용 레이아웃과 디버깅용 레이아웃을 정의할 수 있습니다. 창 위치 및 동작을 정렬하고 사용자 지정 레이아웃을 저장하려면 [창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

## <a name="external-tools"></a>외부 도구

외부 도구를 시작하려면 **도구** 메뉴를 사용자 지정할 수 있습니다. 자세한 내용은 [외부 도구 관리](../ide/managing-external-tools.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [환경 설정](environment-settings.md)
- [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)
- [빠른 시작: 먼저 Visual Studio IDE 살펴보기](../ide/quickstart-ide-orientation.md)
- [Mac용 Visual Studio IDE 사용자 지정](/visualstudio/mac/customizing-the-ide)
