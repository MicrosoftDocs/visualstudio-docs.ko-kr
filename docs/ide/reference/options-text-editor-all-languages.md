---
title: 옵션, 텍스트 편집기, 모든 언어
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9815bdec94ce32a3bfcc170dd95d834bc43ea58f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566880"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>옵션 대화 상자: 텍스트 편집기 \> 모든 언어

이 대화 상자에서는 코드 편집기의 기본 동작을 변경할 수 있습니다. 이러한 설정은 HTML 디자이너의 소스 뷰와 같이 코드 편집기를 기반으로 하는 다른 편집기에도 적용됩니다. 이 대화 상자를 열려면 **도구** 메뉴에서 **옵션**을 선택합니다. **텍스트 편집기** 폴더 내에서 **모든 언어** 하위 폴더를 확장하고 **일반**을 선택합니다.

> [!CAUTION]
> 이 페이지에서는 모든 개발 언어에 대한 기본 옵션을 설정합니다. 이 대화 상자에서 옵션을 다시 설정하면 여기서 선택한 항목이 무엇이든 모든 언어의 일반 옵션이 다시 설정됩니다. 하나의 언어에 대한 텍스트 편집기 옵션만 변경하려면 해당 언어의 하위 폴더를 확장하고 해당 옵션 페이지를 선택합니다.

일부 프로그래밍 언어에 대한 일반 옵션 페이지에서만 옵션이 선택된 경우 회색으로 표시된 확인 표시가 표시됩니다.

## <a name="statement-completion"></a>문 완성

**멤버 목록 자동 표시**

이 옵션을 선택하면 사용자가 편집기에서 입력할 때 IntelliSense에 의해 사용 가능한 멤버, 속성, 값 또는 메서드의 팝업 목록이 표시됩니다. 팝업 목록에서 항목을 선택하여 코드에 삽입합니다. 이 옵션을 선택하면 **고급 멤버 숨기기** 옵션이 사용하도록 설정됩니다.

**고급 멤버 숨기기**

이 옵션을 선택하면 가장 일반적으로 사용되는 항목만 표시되므로 팝업 문 완성 목록이 축소됩니다. 다른 항목은 목록에서 필터링됩니다.

**매개 변수 정보**

이 옵션을 선택하면 현재 선언 또는 프로시저에 대한 전체 구문이 사용할 수 있는 모든 매개 변수와 함께 편집기의 삽입 지점 아래에 표시됩니다. 다음에 할당할 수 있는 매개 변수는 굵게 표시됩니다.

## <a name="settings"></a>설정

**가상 공간 활성화**

이 옵션을 선택하고 **자동 줄 바꿈**의 선택을 취소하면 코드 편집기에서 줄 끝 뒤에 있는 어느 위치든 클릭하여 내용을 입력할 수 있습니다. 이 기능은 코드 옆의 일관된 위치에 주석을 배치하는 데도 사용할 수 있습니다.

**단어 줄 바꿈**

이 옵션을 선택하면 줄이 편집기에서 가로로 볼 수 있는 영역을 벗어나는 경우에 자동으로 다음 줄에 표시됩니다. 또한 이 옵션을 선택하면 **자동 줄 바꿈 시각 문자 표시** 확인란을 사용할 수 있게 됩니다.

> [!NOTE]
> **자동 줄 바꿈**이 켜져 있는 동안에는 **가상 공간** 기능이 꺼집니다.

**자동 줄 바꿈 시각 문자 표시**

이 옵션을 선택하면 긴 줄이 다음 줄로 줄 바꿈되는 위치에 줄 바꿈 화살표 표시기가 표시됩니다.

![LineBreakSymbol 스크린 샷](../../ide/reference/media/linebreak.gif)

이러한 표시기를 표시하지 않으려면 이 옵션의 선택을 취소합니다.

> [!NOTE]
> 이러한 알림 화살표는 코드에 추가되거나 인쇄되지 않습니다. 참조용으로만 사용됩니다.

**줄 번호**

이 옵션을 선택하면 각 코드 줄 옆에 줄 번호가 나타납니다.

> [!NOTE]
> 이러한 줄 번호는 코드에 추가되거나 인쇄되지 않으며 참조용으로만 사용됩니다.

**한 번 클릭으로 URL 탐색 사용**

이 옵션을 선택하면 편집기에서 마우스 커서가 URL 위를 지날 때마다 가리키는 손 모양으로 변합니다. URL을 클릭하면 표시된 페이지가 웹 브라우저에서 열립니다.

**탐색 모음**

이 옵션을 선택하면 코드 편집기 맨 위에 **탐색 모음**이 표시됩니다. **개체** 및 **멤버** 드롭다운 목록을 사용하여 코드에서 특정 개체를 선택하고, 멤버 중에서 선택하고, 코드 편집기에서 선택된 멤버의 선언으로 이동할 수 있습니다.

**선택 영역이 없는 경우 잘라내기 또는 복사 명령을 빈 줄에 적용**

이 옵션은 삽입 지점을 빈 줄에 배치하고 아무것도 선택하지 않은 다음, [복사] 또는 [잘라내기]를 선택한 경우 편집기의 동작을 설정합니다.

- 이 옵션을 선택하면 빈 줄이 복사되거나 잘립니다. 그런 다음 붙여넣기를 수행하면 빈 줄이 새로 삽입됩니다.

- 이 옵션의 선택을 취소하고 [잘라내기] 명령을 선택하면 빈 줄이 제거됩니다. 그러나 클립보드의 데이터는 유지됩니다. 따라서 이후 [붙여넣기] 명령을 사용하면 최근에 클립보드에 복사된 콘텐츠가 붙여넣어집니다. 전에 아무것도 복사하지 않았으면 아무것도 붙여넣지 않습니다.

이 설정은 줄이 비어 있지 않은 경우의 [복사] 또는 [잘라내기]에 영향을 미치지 않습니다. 선택한 내용이 없는 경우에는 줄 전체가 복사되거나 잘립니다. 그런 다음 [붙여넣기]를 수행하면 줄 전체의 텍스트와 해당 줄 끝 문자가 붙여넣어집니다.

> [!TIP]
> 공백, 탭 및 줄 끝에 대한 표시기를 나타내어 완전히 비어 있는 줄과 들여쓴 줄을 구분하려면 **편집** 메뉴에서 **고급**을 선택하고 **공백 보기**를 선택합니다.

## <a name="see-also"></a>참조

- [옵션, 텍스트 편집기, 모든 언어, 탭](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
