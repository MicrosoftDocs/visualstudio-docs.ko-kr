---
title: Visual Studio 검색 사용
description: Visual Studio 검색을 사용하여 설정, 메뉴, 코드를 찾는 방법을 알아봅니다.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873907"
---
# <a name="use-visual-studio-search"></a>Visual Studio 검색 사용

Visual Studio IDE(통합 개발 환경)에는 다양한 메뉴, 옵션, 기능이 있어 기억하기 어려울 수 있습니다. Visual Studio 검색 기능은 개발자가 코드도 검색하면서 IDE 메뉴와 옵션을 찾을 수 있는 단일 검색 상자입니다. Visual Studio를 처음 접하는 개발자나 숙련된 개발자 모두 이 기능을 통해 IDE 기능과 코드를 빠르게 검색할 수 있습니다.

**Ctrl**+**Q** 바로 가기 키를 사용하여 검색 상자에 액세스하거나 기본적으로 메뉴 모음 옆에 있는 Visual Studio 검색 입력 상자를 클릭합니다.

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio 검색 상자" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Visual Studio 검색에 의해 실행되는 명령은 `Window.QuickLaunch`이며, 이 기능은 빠른 검색 또는 빠른 실행이라고 표시될 수도 있습니다.

파일에서 찾기 또는 솔루션 탐색기 검색과 같은 다른 검색 기능과 달리 Visual Studio 결과 검색에는 IDE 기능, 메뉴 옵션, 파일 이름 등이 포함됩니다. 다음 섹션에서는 Visual Studio 검색에서 찾을 수 있는 다양한 유형의 결과를 설명합니다.

## <a name="search-menus-options-and-windows"></a>메뉴, 옵션, 창 검색

Visual Studio 검색 상자를 사용하여 설정 및 옵션과 유사한 구성 항목을 찾을 수 있습니다. 예를 들어 다음 스크린샷에 나온 것처럼 *change theme* 을 검색하여 Visual Studio 색 테마를 변경할 수 있는 대화 상자를 빠르게 찾아 엽니다.

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Visual Studio 설정 및 옵션 검색":::

> [!TIP]
> 대부분의 경우 Visual Studio 검색 결과로 각 항목의 메뉴, 바로 가기 키, 위치가 표시됩니다.

Visual Studio 검색 상자를 사용하여 메뉴 항목 및 명령을 찾을 수 있습니다. 예를 들어 *clean sol* 을 검색하여 솔루션 정리 명령을 빨리 찾아 실행합니다. 또한 검색 결과로 다음 스크린샷에서처럼 메뉴에서 이 명령을 찾을 수 있는 위치가 표시됩니다.

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Visual Studio 메뉴 항목 및 명령 검색":::

마지막으로, 실수로 닫았을 수도 있는 창이나 패널을 검색할 수 있습니다. 예를 들어 *test* 를 검색하여 테스트 탐색기 창을 찾아 엽니다.

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Visual Studio 창 및 패널 검색":::

## <a name="search-files-and-code"></a>파일 및 코드 검색

Visual Studio 검색은 솔루션 항목에서 파일 이름, 코드, 메서드 및 기타 일치 항목도 검색합니다. 다음 스크린샷에서는 *markdown* 을 검색하여 솔루션 내에서 MarkdownMetaExtractor.cs 파일, `MarkdownMetaExtractor` 클래스, 메서드 두 개를 찾았습니다.

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Visual Studio 검색으로 파일 검색":::

“카멜식 대/소문자” 검색을 수행할 수도 있습니다. 다음 스크린샷에서는 *FSS* 를 검색하여 **F** older **S** ize **S** canner 파일과 클래스 및 메서드를 찾았습니다.

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="카멜식 대/소문자 검색으로 Visual Studio 검색":::

## <a name="see-also"></a>참조

- [Visual Studio 명령](reference/visual-studio-commands.md)