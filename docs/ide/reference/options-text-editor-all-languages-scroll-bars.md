---
title: 옵션, 텍스트 편집기, 모든 언어, 스크롤 막대
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54ce07537adc436f719de8596657d1367afcb87d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588800"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>옵션, 텍스트 편집기, 모든 언어, 스크롤 막대
이 대화 상자에서는 코드 편집기 스크롤 막대의 기본 동작을 변경할 수 있습니다. 이러한 옵션을 표시하려면 **도구** 메뉴에서 **옵션**을 선택합니다. **텍스트 편집기** 폴더 내에서 **모든 언어** 하위 폴더를 확장한 다음, **스크롤 막대**를 선택합니다.

> [!CAUTION]
> 이 페이지에서는 모든 개발 언어에 대한 기본 옵션을 설정합니다. 이 대화 상자에서 옵션을 다시 설정하면 여기서 선택한 항목이 무엇이든 모든 언어의 스크롤 막대 옵션이 다시 설정됩니다. 하나의 언어에 대한 텍스트 편집기 옵션만 변경하려면 해당 언어의 하위 폴더를 확장하고 해당 옵션 페이지를 선택합니다.

## <a name="show-horizontal-scroll-bar"></a>가로 스크롤 막대 표시

이 옵션을 선택하면 좌우로 스크롤하여 편집기의 보기 영역을 벗어나는 요소를 볼 수 있도록 가로 스크롤 막대가 표시됩니다. 가로 스크롤 막대를 사용할 수 없는 경우 커서 키를 사용하여 스크롤할 수 있습니다.

## <a name="show-vertical-scroll-bar"></a>세로 스크롤 막대 표시

이 옵션을 선택하면 위아래로 스크롤하여 편집기의 보기 영역을 벗어나는 요소를 볼 수 있도록 세로 스크롤 막대가 표시됩니다. 세로 스크롤 막대를 사용할 수 없는 경우 Page Up, Page Down 및 커서 키를 사용하여 스크롤할 수 있습니다.

## <a name="display"></a>디스플레이

### <a name="show-annotations-over-vertical-scroll-bar"></a>세로 스크롤 막대 위에 주석 표시

세로 스크롤 막대에 다음 주석을 표시할지 여부를 선택합니다.

- 변경 내용
- 표시
- 오류
- 캐럿 위치

> [!TIP]
> **표식 표시** 옵션에는 중단점 및 책갈피가 포함됩니다.

큰 코드 파일을 열고 파일의 여러 위치에서 발생하는 일부 텍스트를 바꿔 보세요. 스크롤 막대에 바꾸기 결과가 표시되므로, 작업을 잘못 바꾼 경우 변경 내용을 취소할 수 있습니다.

코드를 편집할 때 다양한 색 및 기호의 의미는 [향상된 스크롤 막대](https://blogs.msdn.microsoft.com/cdnstudents/2014/01/21/visual-studio-tips-and-tricks-enhanced-scroll-bar/) 블로그 게시물을 참조하세요.

## <a name="behavior"></a>동작

스크롤 막대에는 막대 모드와 지도 모드라는 두 가지 모드가 있습니다.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>세로 스크롤 막대에 막대 모드 사용

‘막대 모드’에서는 스크롤 막대에 주석 표시기가 표시됩니다.  스크롤 막대를 클릭하면 페이지가 위아래로 스크롤되지만 파일의 해당 위치로 점프하지는 않습니다.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>세로 스크롤 막대에 지도 모드 사용

‘지도 모드’에서는 스크롤 막대의 한 위치를 클릭하면 커서가 페이지 위나 아래로 스크롤하는 대신 파일의 해당 위치로 이동합니다.  코드 줄이 축소되어 스크롤 막대에 표시됩니다. **소스 개요**에서 값을 선택하여 지도 열의 너비를 선택할 수 있습니다. 지도에 포인터를 놓을 때 코드 미리 보기를 더 크게 표시하려면 **미리 보기 도구 설명 표시** 옵션을 선택합니다. 축소된 영역은 다르게 회색으로 표시되며, 두 번 클릭하면 확장됩니다.

> [!TIP]
> **소스 개요**를 **끔**으로 설정하여 지도 모드에서 축소 코드 보기를 끌 수 있습니다. **미리 보기 도구 설명 표시**를 선택한 경우에도 스크롤 막대를 포인터로 가리키면 해당 위치의 코드 미리 보기가 표시되며, 클릭하면 커서가 파일의 해당 위치로 이동합니다.

## <a name="see-also"></a>참고 항목

- [방법: 스크롤 막대 사용자 지정](../how-to-track-your-code-by-customizing-the-scrollbar.md)
