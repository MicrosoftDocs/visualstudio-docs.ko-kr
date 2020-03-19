---
title: 시작 환경 변경
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281a0c43c0163d158151683e9fdc483dfc1709f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567218"
---
# <a name="customize-startup"></a>시작 사용자 지정

가장 최근의 솔루션을 열거나 빈 개발 환경을 여는 것과 같은 여러 가지 방법으로 Visual Studio의 시작 환경을 사용자 지정할 수 있습니다.

::: moniker range="vs-2017"

도구 창에서 실행되는 WPF(Windows Presentation Foundation) XAML 페이지인 사용자 지정 시작 페이지를 표시하고 Visual Studio 내부에 있는 명령을 실행할 수도 있습니다.

::: moniker-end

## <a name="to-change-the-startup-item"></a>시작 항목을 변경하려면

1. 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

2. **환경**을 확장한 다음 **시작**을 선택합니다.

::: moniker range="vs-2017"

3. **시작 시** 목록에서 Visual Studio가 시작된 후 표시할 항목을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. **시작 시 열기** 목록에서 Visual Studio 시작 후에 수행할 작업을 선택합니다. **시작 창**(새 프로젝트 또는 기존 프로젝트를 열 수 있음), **최근 솔루션** 또는 **빈 환경** 중에서 선택할 수 있습니다.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>사용자 지정 시작 페이지를 표시하려면

Visual Studio SDK를 사용하여 [사용자 지정 시작 페이지를 만들거나](../extensibility/creating-a-custom-start-page.md), 다른 사용자가 이미 만든 시작 페이지를 사용할 수 있습니다. 예를 들어 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads)에서 사용자 지정 시작 페이지를 찾을 수 있습니다.

사용자 지정 시작 페이지를 설치하려면 *.vsix* 파일을 열거나 시작 페이지 파일을 복사하여 컴퓨터의 *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* 폴더에 붙여넣습니다.

### <a name="to-select-which-custom-start-page-to-display"></a>표시할 사용자 지정 시작 페이지를 선택하려면

1. 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

1. **환경**을 확장한 다음 **시작**을 선택합니다.

1. **시작 페이지 사용자 지정** 목록에서 원하는 페이지를 선택합니다.

> [!TIP]
> 사용자 지정 시작 페이지에 오류가 있어 Visual Studio에 크래시가 발생하면 안전 모드로 Visual Studio를 열고 기본 시작 페이지를 사용하도록 설정할 수 있습니다. [/SafeMode(devenv.exe)](../ide/reference/safemode-devenv-exe.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
