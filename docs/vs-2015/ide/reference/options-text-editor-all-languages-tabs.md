---
title: 옵션, 텍스트 편집기, 모든 언어, 탭 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662392"
---
# <a name="options-text-editor-all-languages-tabs"></a>옵션, 텍스트 편집기, 모든 언어, 탭
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 대화 상자에서는 코드 편집기의 기본 동작을 변경할 수 있습니다. 이러한 설정은 HTML 디자이너의 소스 뷰와 같이 코드 편집기를 기반으로 하는 다른 편집기에도 적용됩니다. 이러한 옵션을 표시하려면 **도구** 메뉴에서 **옵션**을 선택합니다. **텍스트 편집기** 폴더 내에서 **모든 언어** 하위 폴더를 확장하고 **탭**을 선택합니다.

> [!CAUTION]
> 이 페이지에서는 모든 개발 언어에 대한 기본 옵션을 설정합니다. 이 대화 상자에서 옵션을 다시 설정하면 여기서 선택한 항목이 무엇이든 모든 언어의 탭 옵션이 다시 설정됩니다. 하나의 언어에 대한 텍스트 편집기 옵션만 변경하려면 해당 언어의 하위 폴더를 확장하고 해당 옵션 페이지를 선택합니다.

 특정 프로그래밍 언어에 대한 탭 옵션 페이지에서 다른 설정을 선택하면 여러 **들여쓰기** 옵션의 경우 “개별 텍스트 형식에 대한 들여쓰기 설정이 서로 충돌합니다.” 메시지가 표시되고 여러 **탭** 옵션의 경우 “개별 텍스트 형식에 대한 탭 설정이 서로 충돌합니다.” 메시지가 표시됩니다. 예를 들어 Visual Basic에 대해 **스마트 들여쓰기** 옵션이 선택되지만 Visual C++에 대해 **들여쓰기 차단**이 선택될 경우 이 미리 알림이 표시됩니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="indenting"></a>들여쓰기
 없음을 선택 하면 새 줄이 들여쓰기 되지 않습니다. 삽입 지점이 새 줄의 첫 번째 열에 배치됩니다.

 차단 선택 하면 새 줄이 자동으로 들여쓰기 됩니다. 삽입 지점은 이전 줄과 동일한 시작 지점에 배치됩니다.

 스마트 이 옵션을 선택하면 개발 언어에 대한 기타 코드 서식 설정 및 IntelliSense 규칙에 따라 코드 컨텍스트에 맞게 새 줄이 배치됩니다. 이 옵션을 모든 개발 언어에 사용할 수는 없습니다.

 예를 들어 여는 중괄호({)와 닫는 중괄호(}) 사이에 포함된 줄은 정렬된 중괄호 위치에서 자동으로 탭 정지 하나만큼 추가로 들여쓰기될 수 있습니다.

## <a name="tabs"></a>탭
 탭 크기 탭 정지 간의 거리를 공백 수로 설정합니다. 기본값은 공백 4개입니다.

 들여쓰기 크기 자동 들여쓰기의 크기를 공백 수로 설정합니다. 기본값은 공백 4개입니다. 탭 문자나 공백 문자 또는 두 가지 문자 모두를 삽입하여 지정한 크기를 채웁니다.

 공백 삽입 선택 하면 들여쓰기 작업을 수행 하면 탭 문자가 아닌 공백 문자만 삽입 됩니다. 예를 들어 **들여쓰기 크기**를 5로 설정하면 Tab 키를 누르거나 **서식** 도구 모음에서 **들여쓰기 늘리기** 단추를 누를 때마다 공백 문자 다섯 개가 삽입됩니다.

 탭 유지 선택 하면 들여쓰기 작업은 가능한 한 많은 탭 문자를 삽입 합니다. 각 탭 문자는 **탭 크기**에 지정 된 공백 수를 채웁니다. **들여쓰기 크기**가 **탭 크기**의 짝수 배수가 아니면 공백 문자가 추가되어 차이를 메꿉니다.

## <a name="see-also"></a>관련 항목
 옵션 [대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md) [옵션, 텍스트 편집기, 모든 언어](../../ide/reference/options-text-editor-all-languages.md)
