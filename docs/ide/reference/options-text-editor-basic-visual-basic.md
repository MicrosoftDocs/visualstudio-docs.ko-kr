---
title: 옵션, 텍스트 편집기, 기본(VB), 고급
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 562358ca90e223a07926aaa383ded41a5f7557cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431477"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>옵션, 텍스트 편집기, 기본(Visual Basic), 고급
**옵션**(**도구** 메뉴), **텍스트 편집기**의 **Basic** 폴더에 있는 **VB 관련** 속성 페이지 대화 상자에는 다음 속성이 포함되어 있습니다.

## <a name="analysis"></a>분석

- 실시간 코드 분석 또는 백그라운드 분석 범위

   관리 코드에 대한 백그라운드 분석 범위를 구성합니다. 자세한 내용은 [방법: 관리 코드에 대한 실시간 코드 분석 범위를 구성합니다](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Using 지시문

- using 정렬 시 ‘System’ 지시문 먼저 배치

   선택한 경우, 마우스 오른쪽 단추 클릭 메뉴의 **using 제거 및 정렬** 명령은 `using` 지시문을 정렬하고 '시스템' 네임스페이스를 목록의 맨 위에 배치합니다.

- Using 지시문 그룹 구분

   선택한 경우, 마우스 오른쪽 단추 클릭 메뉴의 **using 제거 및 정렬** 명령은 동일한 루트 네임스페이스를 가진 지시문 그룹 사이에 빈 줄을 삽입하여 `using` 지시문을 구분합니다.

- 참조 어셈블리의 형식에 대한 using 제안
- NuGet 패키지의 형식에 대한 using 제안

   이러한 옵션을 선택한 경우 [빠른 작업](../quick-actions.md)을 사용하여 NuGet 패키지를 설치하고 참조되지 않은 형식에 대한 `using` 지시문을 추가할 수 있습니다.

   ![Visual Studio의 NuGet 패키지 설치 빠른 작업](media/nuget-lightbulb.png)

## <a name="highlighting"></a>강조 표시

 **참조 및 키워드의 강조 표시 사용**

텍스트 편집기는 기호의 모든 인스턴스 또는 `If..Then`, `While...End While` 또는 `Try...Catch...Finally` 등의 절에 있는 모든 키워드를 강조 표시할 수 있습니다. **Ctrl** + **Shift** + **아래쪽 화살표** 또는 **Ctrl** + **Shift** + **위쪽 화살표**를 눌러 강조 표시된 참조 또는 키워드 간에 탐색할 수 있습니다.

## <a name="outlining"></a>개요

**태그 개요 사용**

코드 편집기에서 파일을 열면 개요 모드에서 문서를 볼 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요. 이 옵션을 선택하고 파일을 열면 개요 기능이 활성화됩니다.

**프로시저 줄 구분선 표시**

텍스트 편집기가 프로시저의 시각적 범위를 표시합니다. 다음 표에 나열된 위치에서 프로젝트의 *.vb* 소스 파일에 줄이 그려집니다.

|.vb 소스 파일 내 위치|선 위치의 예|
|---------------------------------|------------------------------|
|블록 선언 구문의 닫기 뒤|-   클래스, 구조체, 모듈, 인터페이스 또는 열거형의 끝<br />-   속성, 함수 또는 하위 뒤<br />-   속성에서 get 및 set 절 사이 아님|
|일련의 한 줄 구문 뒤|-   가져오기 문 뒤, 클래스 파일에서 형식 정의 앞<br />-   클래스에서 선언된 모든 프로시저 뒤, 프로시저 앞|
|한 줄 선언 뒤(블록 수준 선언 외)|-   가져오기 문, 상속 문, 변수 선언, 이벤트 선언, 대리자 선언 및 DLL 선언 문에 이어서|

## <a name="block-structure-guides"></a>블록 구조 가이드

선택할 경우 세로 선이 편집기에 개별 코드 블록을 쉽게 식별할 수 있는 정형 코드 블록과 함께 일렬로 표시됩니다. 예를 들어 `Sub` 문에서 `Sub`와 `EndSub` 사이에 줄이 하나 보일 것입니다.

## <a name="editor-help"></a>편집기 도움말

**코드 서식 다시 적용** 텍스트 편집기는 코드 서식을 적절하게 다시 지정합니다. 이 옵션을 선택하면 코드 편집기는 다음을 수행합니다.

- 올바른 탭 위치에 코드 정렬

- 키워드, 변수 및 개체를 올바른 대소문자로 다시 지정

- `If...Then` 문에 누락된 `Then` 추가

- 함수 호출에 괄호를 추가합니다.

- 문자열에 누락된 끝 따옴표 추가

- 지수 표기법 서식 다시 지정

- 날짜 서식 다시 지정

**맺음 구문 자동 삽입**

예를 들어 프로시저 선언의 첫 번째 줄 `Sub Main`을 입력하고 **Enter** 키를 누르면 텍스트 편집기는 일치하는 `End Sub` 줄을 추가합니다. 마찬가지로, [For](/dotnet/visual-basic/language-reference/statements/for-next-statement) 루프를 추가하면 텍스트 편집기는 일치하는 `Next` 문을 추가합니다. 이 옵션을 선택하면 코드 편집기는 종료 구문을 자동으로 추가합니다.

**Interface 및 MustOverride 멤버 자동 삽입**

클래스에 대한 `Implements` 문 또는 `Inherits` 문을 커밋하면 텍스트 편집기는 구현 또는 재정의해야 하는 멤버에 대한 프로토타입을 각각 삽입합니다.

**오류 수정 제안 사용**

텍스트 편집기는 일반적인 오류에 대한 솔루션을 제안하고 코드에 적용되는 적절한 수정을 선택할 수 있습니다.

## <a name="see-also"></a>참조

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [옵션, 텍스트 편집기, 모든 언어, 탭](../../ide/reference/options-text-editor-all-languages-tabs.md)
