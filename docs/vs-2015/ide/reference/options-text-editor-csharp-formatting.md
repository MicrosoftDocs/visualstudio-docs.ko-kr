---
title: 옵션, 텍스트 편집기, C#, 서식 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662281"
---
# <a name="options-text-editor-c-formatting"></a>옵션, 텍스트 편집기, C#, 서식
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**서식** 속성 페이지 대화 상자를 사용하여 코드 편집기의 서식 코드에 대한 옵션을 설정합니다. 이 대화 상자에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고, **텍스트 편집기**를 확장하고, **C#** 을 확장하고, **서식**을 클릭합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="general-settings"></a>General Settings(일반 설정)
 일반 설정은 코드 편집기가 서식 옵션을 코드에 적용하는 방법에 영향을 미칩니다.

## <a name="uielement-list"></a>UI 요소 목록

|레이블|Description|
|-----------|-----------------|
|**; 입력 시 완성 문에 서식 자동 지정**|이 옵션을 선택하면 코드 편집기에 대해 선택된 서식 옵션에 따라 완성 시 문에 서식이 지정됩니다. 코드 편집기가 문을 변경하지 않도록 하려면 이 상자의 선택을 취소합니다.|
|**} 입력 시 완성 블록에 서식 자동 지정**|이 옵션을 선택하면 코드 블록을 완료하면 바로 코드 편집기에 대해 선택된 서식 옵션에 따라 코드 블록에 서식이 지정됩니다. 코드 편집기가 블록을 변경하지 않도록 하려면 이 상자의 선택을 취소합니다.|
|**붙여넣을 때 들여쓰기 조정**|이 옵션을 선택하면 코드 편집기에 대해 선택된 서식 옵션에 맞게 코드 편집기에 붙여넣는 텍스트에 서식이 지정됩니다. 붙여넣은 텍스트가 변경되지 않도록 하려면 이 상자의 선택을 취소합니다.|

## <a name="preview-window"></a>미리 보기 창
 **들여쓰기**, **줄 추가**, **간격** 및 **줄 바꿈** 옵션 창에는 각각 미리 보기 창이 표시됩니다. 미리 보기 창에는 각 옵션의 효과가 표시됩니다. 미리 보기 창을 사용하려면 서식 옵션을 선택합니다. 미리 보기 창에는 선택된 옵션의 예제가 표시됩니다. 설정을 변경할 경우(예: 확인란을 선택하거나 선택 취소할 경우) 미리 보기 창이 업데이트되어 새 설정의 효과가 표시됩니다.

## <a name="remarks"></a>설명
 각 언어에 대한 **탭** 페이지의 들여쓰기 옵션은 줄 끝에서 Enter 키를 누를 때 코드 편집기에서 커서가 배치되는 위치만 결정합니다. **서식** 아래 들여쓰기 옵션은 코드 서식이 자동으로 지정되는 경우 적용됩니다(예: **붙여넣을 때 들여쓰기 조정**이 선택된 동안 코드를 파일에 붙여넣을 경우, 서식 지정되는 블록이 수동으로 입력되는 경우).

## <a name="see-also"></a>관련 항목
 [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
