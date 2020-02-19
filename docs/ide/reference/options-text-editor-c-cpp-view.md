---
title: 옵션, 텍스트 편집기, C/C++, 보기
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 95963245b15828f374e9812a9bb09d015b21a94b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278686"
---
# <a name="options-text-editor-cc-view"></a>옵션, 텍스트 편집기, C/C++, 보기

이러한 속성 페이지를 사용하여 C 또는 C++로 프로그래밍할 때 코드 편집기의 기본 동작을 변경할 수 있습니다.

이 속성 페이지에 액세스하려면 **도구** > **옵션**을 선택하고, **텍스트 편집기** 및 **C/C++** 를 확장한 다음, **보기**를 선택합니다.

## <a name="code-squiggles"></a>코드 오류 표시선

다음 설정을 활성화하거나 비활성화하여 텍스트 편집기가 C 및 C++에 대한 코드 오류 표시선을 처리하는 방법을 관리할 수 있습니다.

- **건너뛴 검색 영역의 매크로** - 정의에 중괄호가 포함되는 매크로 등 검색 데이터베이스에 의해 건너뛴 영역 내에 있는 매크로를 강조 표시하는 방법을 정의합니다.

- **constexpr로 변환 가능한 매크로** - `constexpr` 정의로 변환할 수 있는 매크로 정의를 강조하는 방법을 정의합니다.

## <a name="inactive-code"></a>비활성 코드

- **비활성 블록 표시** - 전처리기 비활성 블록이 다른 색으로 표시됩니다.

- **비활성 코드 불투명 사용 안 함** - 비활성 코드 블록에 불투명 대신 단색을 사용합니다.

- **비활성 코드 불투명도** - 비활성 코드 블록에 대한 불투명도입니다.

## <a name="miscellaneous"></a>기타

- **주석 작업 열거** - VS 토큰의 오픈 소스 파일을 검색하고 작업 목록 창에서 보고합니다.

- **일치 토큰 강조 표시** - 커서의 위치와 일치하는 묶여 있는 중괄호 또는 구문을 강조 표시합니다.

## <a name="outlining"></a>개요

- **개요 사용** - 개요 모드로 파일을 엽니다.

- **Pragma 영역 개요** - `#pragma` 영역 블록 개요를 자동으로 지정합니다.

- **명령문 블록 개요** - 명령문 블록 개요를 자동으로 지정합니다.

## <a name="see-also"></a>참조

- [언어별 편집기 옵션 설정](../../ide/reference/setting-language-specific-editor-options.md)
- [C++에서의 리팩터링(VC 블로그)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
