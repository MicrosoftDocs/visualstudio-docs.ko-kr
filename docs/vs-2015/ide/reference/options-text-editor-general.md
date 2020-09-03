---
title: 일반, 텍스트 편집기, 옵션 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662256"
---
# <a name="options-text-editor-general"></a>일반, 텍스트 편집기, 옵션
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 대화 상자에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 코드 및 텍스트 편집기에 대한 전역 설정을 변경할 수 있습니다. 이 대화 상자를 표시하려면 **도구** 메뉴에서 **옵션**을 클릭하고, **텍스트 편집기** 폴더를 확장하고, **일반**을 클릭합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="settings"></a>설정
 텍스트 끌어서 놓기를 선택 하면 텍스트를 선택 하 고 마우스로 선택 하 여 현재 문서 또는 다른 열린 문서 내의 다른 위치로 끌어 텍스트를 이동할 수 있습니다.

 자동 구분 기호 강조 표시 선택한 경우 매개 변수 또는 항목-값 쌍을 구분 하는 구분 기호 문자 및 일치 하는 중괄호를 강조 표시 합니다.

 변경 내용 추적 코드 편집기를 선택 하면 파일을 가장 최근에 저장 한 이후 변경 된 코드를 표시 하기 위해 선택 영역 여백에 세로 노란색 선이 나타납니다. 변경 내용을 저장하면 세로 선이 녹색으로 바뀝니다.

 서명 없이 UTF-8 인코딩 자동 검색 기본적으로 편집기는 바이트 순서 표시 또는 문자 집합 태그를 검색 하 여 인코딩을 검색 합니다. 현재 문서에서 아무것도 찾을 수 없으면 코드 편집기에서는 바이트 시퀀스를 검색하여 UTF-8 인코딩을 자동 검색합니다. 인코딩 자동 검색을 사용하지 않으려면 이 옵션의 선택을 취소합니다.

## <a name="display"></a>표시
 선택 여백 선택 하면 편집기 텍스트 영역의 왼쪽 가장자리를 따라 세로 여백이 표시 됩니다. 이 여백을 클릭하여 전체 텍스트 줄을 선택하거나 클릭하고 끌어서 연속 텍스트 줄을 선택할 수 있습니다.

|선택 영역 여백 켜기|선택 영역 여백 끄기|
|-------------------------|--------------------------|
|![HTMLpageSelectionMarginOn 스크린 샷](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff 스크린 샷](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

 표시기 여백 선택 하면 편집기 텍스트 영역의 왼쪽 가장자리 밖에 세로 여백을 표시 합니다. 이 여백을 클릭하면 텍스트에 관련된 아이콘 및 도구 설명이 나타납니다. 예를 들어 중단점 또는 작업 목록 바로 가기가 표시기 여백에 나타납니다. 표시기 여백 정보는 인쇄되지 않습니다.

 세로 스크롤 막대 선택한 경우 위쪽 및 아래쪽으로 스크롤하여 편집기의 보기 영역을 벗어나는 요소를 볼 수 있도록 하는 세로 스크롤 막대를 표시 합니다. 세로 스크롤 막대를 사용할 수 없는 경우 Page Up, Page Down 및 커서 키를 사용하여 스크롤할 수 있습니다.

 가로 스크롤 막대 선택 하면 가로 스크롤 막대를 표시 하 여 편집기의 보기 영역을 벗어나는 요소를 볼 수 있도록 좌우로 스크롤할 수 있습니다. 가로 스크롤 막대를 사용할 수 없는 경우 커서 키를 사용하여 스크롤할 수 있습니다.

 현재 줄 강조 표시 선택한 경우 커서가 있는 코드 줄 주위에 회색 상자를 표시 합니다.

## <a name="see-also"></a>관련 항목
 [옵션, 텍스트 편집기, 모든 언어](../../ide/reference/options-text-editor-all-languages.md) [옵션, 텍스트 편집기, 모든 언어, 탭](../../ide/reference/options-text-editor-all-languages-tabs.md) [옵션, 텍스트 편집기, 파일 확장명](../../ide/reference/options-text-editor-file-extension.md) [사용자 지정 바로 가기 키 식별 및 사용자 지정](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [IntelliSense를 사용 하 여](../../ide/using-intellisense.md) [편집기 사용자 지정](../../ide/customizing-the-editor.md)
