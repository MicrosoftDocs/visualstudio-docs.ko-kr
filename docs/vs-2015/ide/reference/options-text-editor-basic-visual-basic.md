---
title: 옵션, 텍스트 편집기, 기본(Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662380"
---
# <a name="options-text-editor-basic-visual-basic"></a>옵션, 텍스트 편집기, 기본(Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**옵션**(**도구** 메뉴), **텍스트 편집기**의 **기본** 폴더에 있는 **VB 관련** 속성 페이지 대화 상자에는 다음 속성이 포함되어 있습니다.

 **맺음 구문 자동 삽입** 예를 들어, 프로시저 선언의 첫 번째 줄 `Sub Main—`을(를) 입력하고 ENTER 키를 누르면 텍스트 편집기는 일치하는 `End Sub` 줄을 추가합니다. 마찬가지로, [For](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) 루프를 추가하면 텍스트 편집기는 일치하는 `Next` 문을 추가합니다. 이 옵션을 선택하면 코드 편집기는 종료 구문을 자동으로 추가합니다.

 **코드 서식 다시 적용** 텍스트 편집기는 코드 서식을 적절하게 다시 지정합니다. 이 옵션을 선택하면 코드 편집기는 다음을 수행합니다.

- 올바른 탭 위치에 코드 정렬

- 키워드, 변수 및 개체를 올바른 대소문자로 다시 지정

- `If...Then` 문에 누락된 `Then` 추가

- 함수 호출에 괄호를 추가합니다.

- 문자열에 누락된 끝 따옴표 추가

- 지수 표기법 서식 다시 지정

- 날짜 서식 다시 지정

  **개요 모드 사용** 코드 편집기에서 파일을 열면 개요 모드에서 문서를 볼 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요. 이 옵션을 선택하고 파일을 열면 개요 기능이 활성화됩니다.

  **인터페이스 및 MustOverride 멤버 자동 삽입** `Implements` `Inherits` 클래스에 대 한 문이나 문을 커밋하면 텍스트 편집기에서 각각 구현 하거나 재정의 해야 하는 멤버에 대 한 프로토타입을 삽입 합니다.

  **프로시저 줄 구분 기호 표시** 텍스트 편집기는 프로시저의 시각적 범위를 나타냅니다. 다음 표에 나열된 위치에서 프로젝트의 .vb 소스 파일에 줄이 그려집니다.

|.vb 소스 파일 내 위치|선 위치의 예|
|---------------------------------|------------------------------|
|블록 선언 구문의 닫기 뒤|-   클래스, 구조체, 모듈, 인터페이스 또는 열거형의 끝<br />-   속성, 함수 또는 하위 뒤<br />-   속성에서 get 및 set 절 사이 아님|
|일련의 한 줄 구문 뒤|-   가져오기 문 뒤, 클래스 파일에서 형식 정의 앞<br />-   클래스에서 선언된 모든 프로시저 뒤, 프로시저 앞|
|한 줄 선언 뒤(블록 수준 선언 외)|-   가져오기 문, 상속 문, 변수 선언, 이벤트 선언, 대리자 선언 및 DLL 선언 문에 이어서|

 **오류 수정 제안 사용** 텍스트 편집기는 일반적인 오류에 대 한 솔루션을 제안 하 고 코드에 적용 되는 적절 한 수정 사항을 선택할 수 있습니다.

 **참조 및 키워드 강조 표시 사용** 텍스트 편집기는, 또는와 같은 절에 있는 모든 키워드 또는 기호의 모든 인스턴스를 강조 표시할 수 `If..Then` 있습니다 `While...End While` `Try...Catch...Finally` . CTRL + SHIFT + 아래쪽 화살표 또는 CTRL + SHIFT + 위쪽 화살표 키를 눌러 강조 표시된 참조 또는 키워드 간에 탐색할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md) [옵션, 텍스트 편집기, 모든 언어, 탭](../../ide/reference/options-text-editor-all-languages-tabs.md)
