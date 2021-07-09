---
title: 솔루션 탐색기 도구 창에 대해 알아보기
description: Visual Studio에서 솔루션 탐색기 도구 창을 사용하여 파일, 프로젝트, 솔루션을 만들고 관리하는 방법을 알아봅니다.
ms.date: 06/29/2021
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbbae8b974a7e88abffd9a12eb253dfea6c7165b
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280495"
---
# <a name="how-to-use-solution-explorer"></a>솔루션 탐색기 사용법

솔루션 탐색기 도구 창을 사용하여 솔루션과 프로젝트를 만들고 관리할 수 있으며 코드를 보고 조작할 수 있습니다. 이 문서에서는 이러한 작업을 수행하는 데 도움이 되는 UI(사용자 인터페이스) 옵션에 대해 자세히 설명합니다.

> [!NOTE]
> 이 토픽은 Windows에서 Visual Studio에만 적용됩니다.

## <a name="solution-explorer-tool-window"></a>솔루션 탐색기 도구 창

먼저 두 개의 프로젝트가 있는 C# 콘솔 솔루션이 열려 있는 [Visual Studio IDE](../get-started/visual-studio-ide.md)의 솔루션 탐색기 도구 창을 살펴보겠습니다.

[![Visual Studio의 솔루션 탐색기 도구 창.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

도구 창은 다음과 같은 UI(사용자 인터페이스) 요소를 포함합니다.

- **메뉴 모음**: 파일이 표시되는 방식을 제어할 수 있습니다.
- **검색 표시줄**: 특정 파일과 파일 형식을 검색할 수 있습니다.
- **주 창**: 파일, 프로젝트, 솔루션을 보고 관리할 수 있습니다.
- **솔루션 노드**: 솔루션을 관리할 수 있습니다.
- **프로젝트 노드**: 프로젝트를 관리할 수 있습니다.
- **종속성 노드**: 솔루션과 프로젝트 종속성을 관리할 수 있습니다.
- **프로그램 노드**: 프로그램 또는 애플리케이션(앱)을 보고, 편집하고, 관리할 수 있습니다.
- **[Git 변경 탭](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** : Visual Studio 내에서 Git 및 GitHub를 사용하여 팀과 프로젝트에서 협업할 수 있습니다.

> [!TIP]
> 솔루션 탐색기 도구 창이 표시되지 않으면 **보기** > **솔루션 탐색기** 를 사용하거나 **Ctrl**+**Alt**+**L** 을 눌러 Visual Studio 메뉴 모음에서 열 수 있습니다.

## <a name="solution-explorer-menu-bar"></a>솔루션 탐색기 메뉴 모음

이번에는 솔루션 탐색기 메뉴 모음을 자세히 살펴보겠습니다.

![Visual Studio의 솔루션 탐색기 메뉴 모음.](media/solution-explorer-menu-bar.png)

메뉴 모음은 왼쪽에서 오른쪽으로 다음과 같은 UI 요소를 포함합니다.

- **뒤로** 단추: 검색 결과 간에 전환합니다.
- **앞으로** 단추: 검색 결과 간에 전환합니다.
- **홈** 단추: 기본 보기로 돌아갑니다.
- **전환** 단추: 솔루션과 사용 가능한 보기 간에 전환합니다.
- **보류 중인 변경 내용 필터** 단추 및 드롭다운 메뉴: 보류 중인 변경 내용이 있는 열려 있는 파일을 봅니다.
- **활성 문서와 동기화** 단추: 코드 편집기에서 파일을 찾습니다.
- **새로 고침** 단추: 함수 또는 패키지와 같은 종속성을 선택할 때만 나타납니다.
- **모두 축소**  단추: 기본 창에서 파일 보기를 축소합니다.
- **모든 파일 표시** 단추: [언로드된 프로젝트](filtered-solutions.md#toggle-unloaded-project-visibility) 포함하여 모든 파일을 봅니다.
- **속성** 단추: 특정 파일 및 구성 요소의 설정을 보고 변경합니다.
- **선택한 항목 미리 보기** 단추: 코드 편집기에서 선택한 파일 또는 구성 요소를 봅니다.

### <a name="solution-explorer-right-click-context-menu"></a>솔루션 탐색기의 마우스 오른쪽 단추로 클릭하여 여는 상황에 맞는 메뉴

솔루션 탐색기에는 마우스 오른쪽 단추로 클릭하여 여는 상황에 맞는 메뉴에서 사용할 수 있는 몇 가지 파일 속성이 있습니다. 마우스 오른쪽 단추로 클릭하여 여는 상황에 맞는 메뉴 옵션에 대한 자세한 내용은 [프로젝트 및 솔루션 속성 관리](managing-project-and-solution-properties.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 솔루션 및 프로젝트란?](solutions-and-projects-in-visual-studio.md)
- [Visual Studio에서 창 레이아웃 사용자 지정](customizing-window-layouts-in-visual-studio.md)
