---
title: 옵션, 텍스트 편집기, 모든 언어, 탭
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc169960cf757e4e334d5f77b06ff70b0d6da7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594749"
---
# <a name="options-text-editor-all-languages-tabs"></a>옵션, 텍스트 편집기, 모든 언어, 탭

이 대화 상자에서는 코드 편집기의 기본 동작을 변경할 수 있습니다. 이러한 설정은 HTML 디자이너의 소스 뷰와 같이 코드 편집기를 기반으로 하는 다른 편집기에도 적용됩니다. 이러한 옵션을 표시하려면 **도구** 메뉴에서 **옵션**을 선택합니다. **텍스트 편집기** 폴더 내에서 **모든 언어** 하위 폴더를 확장하고 **탭**을 선택합니다.

> [!CAUTION]
> 이 페이지에서는 모든 개발 언어에 대한 기본 옵션을 설정합니다. 이 대화 상자에서 옵션을 다시 설정하면 여기서 선택한 항목이 무엇이든 모든 언어의 탭 옵션이 다시 설정됩니다. 하나의 언어에 대한 텍스트 편집기 옵션만 변경하려면 해당 언어의 하위 폴더를 확장하고 해당 옵션 페이지를 선택합니다.

특정 프로그래밍 언어에 대한 탭 옵션 페이지에서 다른 설정을 선택하면 여러 **들여쓰기** 옵션의 경우 “개별 텍스트 형식에 대한 들여쓰기 설정이 서로 충돌합니다.” 메시지가 표시되고 여러 **탭** 옵션의 경우 “개별 텍스트 형식에 대한 탭 설정이 서로 충돌합니다.” 메시지가 표시됩니다. 예를 들어 Visual Basic에 대해 **스마트 들여쓰기** 옵션이 선택되지만 Visual C++에 대해 **들여쓰기 차단**이 선택될 경우 이 미리 알림이 표시됩니다.

## <a name="indenting"></a>들여쓰기

None

이 옵션을 선택하면 새 줄이 들여쓰기되지 않습니다. 삽입 지점이 새 줄의 첫 번째 열에 배치됩니다.

Block

이 옵션을 선택하면 새 줄이 자동으로 들여쓰기됩니다. 삽입 지점은 이전 줄과 동일한 시작 지점에 배치됩니다.

스마트

이 옵션을 선택하면 개발 언어에 대한 기타 코드 서식 설정 및 IntelliSense 규칙에 따라 코드 컨텍스트에 맞게 새 줄이 배치됩니다. 이 옵션을 모든 개발 언어에 사용할 수는 없습니다.

예를 들어 여는 중괄호({)와 닫는 중괄호(}) 사이에 포함된 줄은 정렬된 중괄호 위치에서 자동으로 탭 정지 하나만큼 추가로 들여쓰기될 수 있습니다.

## <a name="tabs"></a>탭

탭 크기

탭 정지 간의 거리를 공백 수로 설정합니다. 기본값은 공백 4개입니다.

들여쓰기 크기

자동 들여쓰기의 크기를 공백 수로 설정합니다. 기본값은 공백 4개입니다. 탭 문자나 공백 문자 또는 두 가지 문자 모두를 삽입하여 지정한 크기를 채웁니다.

공백 삽입

이 옵션을 선택하고 들여쓰기 작업을 수행하면 탭 문자가 아닌 공백 문자만 삽입됩니다. 예를 들어 **들여쓰기 크기**를 5로 설정하면 Tab 키를 누르거나 **서식** 도구 모음에서 **들여쓰기 늘리기** 단추를 누를 때마다 공백 문자 다섯 개가 삽입됩니다.

탭 유지

이 옵션을 선택하고 들여쓰기 작업을 수행하면 가능한 최대 개수만큼 탭 문자가 삽입됩니다. 각 탭 문자는 **탭 크기**에 지정된 공백 수만큼 채웁니다. **들여쓰기 크기**가 **탭 크기**의 짝수 배수가 아니면 공백 문자가 추가되어 차이를 메꿉니다.

## <a name="see-also"></a>참고 항목

- [옵션, 텍스트 편집기, 모든 언어](../../ide/reference/options-text-editor-all-languages.md)
- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
