---
title: 일반, 텍스트 편집기, 옵션
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebe526bbac859777edb4c2c78c65a1cdbd27fc85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568414"
---
# <a name="options-dialog-box-text-editor--general"></a>옵션 대화 상자: 텍스트 편집기 \> 일반

이 대화 상자에서는 Visual Studio 코드 및 텍스트 편집기에 대한 전역 설정을 변경할 수 있습니다. 이 대화 상자를 표시하려면 **도구** 메뉴에서 **옵션**을 선택하고, **텍스트 편집기** 폴더를 확장하고, **일반**을 선택합니다.

## <a name="settings"></a>설정

### <a name="drag-and-drop-text-editing"></a>텍스트 끌어서 놓기

이 옵션을 선택하면 텍스트를 선택하고 마우스로 현재 위치 내의 다른 위치 또는 다른 열린 문서에 끌어서 놓아 텍스트를 이동할 수 있습니다.

### <a name="automatic-delimiter-highlighting"></a>구분 기호 자동 강조

이 옵션을 선택하면 매개 변수 또는 항목-값 쌍을 분리하는 구분 기호 문자와 일치하는 중괄호가 강조 표시됩니다.

### <a name="track-changes"></a>변경 내용 추적

코드 편집기가 선택될 경우 파일이 가장 최근 저장된 후 변경된 코드를 표시하기 위해 노랑 세로 선이 선택 여백에 나타납니다. 변경 내용을 저장하면 세로 선이 녹색으로 바뀝니다.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>시그니처 없이 UTF-8 인코딩 자동 검색

기본적으로 편집기에서는 바이트 순서 표시 또는 문자 집합 태그를 검색하여 인코딩을 검색합니다. 현재 문서에서 아무것도 찾을 수 없으면 코드 편집기에서는 바이트 시퀀스를 검색하여 UTF-8 인코딩을 자동 검색합니다. 인코딩 자동 검색을 사용하지 않으려면 이 옵션의 선택을 취소합니다.

### <a name="follow-project-coding-conventions"></a>프로젝트 코딩 규칙 따름

선택할 경우 프로젝트의 지정된 코딩 규칙이 개인 프로젝트에서 사용하는 코딩 규칙을 재정의합니다.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>마우스 클릭을 사용하여 정의로 이동 수행

선택할 경우 **Ctrl** 키를 누르고 마우스를 클릭한 채 요소를 가리킬 수 있습니다. 이렇게 하면 선택한 요소의 정의로 이동합니다. **한정자 키 사용** 드롭다운에서 **Alt** 또는 **Ctrl** + **Alt**를 선택할 수도 있습니다.

코드 편집기에서 현재 위치를 벗어나지 않고 창에 요소의 정의를 표시하려면 **Peek 뷰에서 정의 열기** 확인란을 선택합니다.

## <a name="display"></a>표시

### <a name="selection-margin"></a>선택 영역 여백

이 옵션을 선택하면 편집기 텍스트 영역의 왼쪽 가장자리를 따라 세로 여백이 표시됩니다. 이 여백을 클릭하여 전체 텍스트 줄을 선택하거나 클릭하고 끌어서 연속 텍스트 줄을 선택할 수 있습니다.

|선택 영역 여백 켜기|선택 영역 여백 끄기|
| - | - |
|![HTMLpageSelectionMarginOn 스크린 샷](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff 스크린 샷](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>표시기 여백

이 옵션을 선택하면 편집기 텍스트 영역의 왼쪽 가장자리 외부에 세로 여백이 표시됩니다. 이 여백을 클릭하면 텍스트에 관련된 아이콘 및 도구 설명이 나타납니다. 예를 들어 중단점 또는 작업 목록 바로 가기가 표시기 여백에 나타납니다. 표시기 여백 정보는 인쇄되지 않습니다.

### <a name="highlight-current-line"></a>현재 줄 강조 표시

이 옵션을 선택하면 커서가 놓이는 코드 줄 주위에 회색 상자가 표시됩니다.

### <a name="show-structure-guide-lines"></a>구조 안내선 표시

선택할 경우 세로 선이 편집기에 개별 코드 블록을 쉽게 식별할 수 있는 정형 코드 블록과 함께 일렬로 표시됩니다.

## <a name="see-also"></a>참조

- [옵션, 텍스트 편집기, 모든 언어](../../ide/reference/options-text-editor-all-languages.md)
- [옵션, 텍스트 편집기, 모든 언어, 탭](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [옵션, 텍스트 편집기, 파일 확장명](../../ide/reference/options-text-editor-file-extension.md)
- [바로 가기 키 식별 및 사용자 지정](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [편집기 사용자 지정](../how-to-change-text-case-in-the-editor.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
