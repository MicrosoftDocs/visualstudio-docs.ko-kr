---
title: 옵션, 텍스트 편집기, C/C++, 서식
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: d7a6029058ab0bc02a623df0e1733eb8548102d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596257"
---
# <a name="options-text-editor-cc-formatting"></a>옵션, 텍스트 편집기, C/C++, 서식

이러한 속성 페이지를 사용하여 C 또는 C++로 프로그래밍할 때 코드 편집기의 기본 동작을 변경할 수 있습니다.

![C++ Formatting 속성 페이지](media/cpp-formatting.png)

이 페이지에 액세스하려면 왼쪽 창의 **옵션** 대화 상자에서 **텍스트 편집기**, **C/C++** 를 차례로 확장한 다음 **서식**을 클릭합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="general-page"></a>일반 페이지

이 페이지에는 명령문과 블록을 입력할 때 서식을 지정하는 옵션이 있습니다.

::: moniker range="vs-2017"

**Visual Studio 2017 버전 15.7 이상:**

::: moniker-end

이 페이지에는 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) 버전 5.0에 대한 지원을 구성하는 옵션도 있습니다. ClangFormat은 .clang-format 또는 _clang-format 파일로 구성할 수 있는 규칙 집합을 기반으로 코드의 스타일과 서식을 쉽게 지정할 수 있는 유틸리티입니다.

### <a name="configuring-clangformat-options"></a>ClangFormat 옵션 구성

::: moniker range="vs-2017"

**Visual Studio 2017 버전 15.7 이상:**

::: moniker-end

ClangFormat 지원은 기본적으로 활성화되어 있습니다. LLVM, Google, Chromium, Mozilla 또는 WebKit 등 모든 프로젝트에 적용할 수 있는 공통의 서식 지정 규칙을 선택할 수 있습니다. 또한 사용자 지정 서식 정의 .clang-format 또는 _clang-format 파일을 만들 수도 있습니다. 이러한 파일이 프로젝트 폴더에 있는 경우 Visual Studio는 이 파일을 사용하여 해당 폴더 및 하위 폴더의 모든 소스 코드 파일에 서식을 지정합니다.

기본적으로 Visual Studio는 clangformat.exe를 백그라운드에서 실행하여 입력과 동시에 서식을 적용합니다. 수동으로 호출된 서식 명령 **문서 서식(Ctrl+K, Ctrl+D)** 또는 **선택 영역 서식(Ctrl + K, Ctrl + F)** 에 대해서만 실행하도록 지정할 수도 있습니다.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>들여쓰기, 새 줄, 간격, 페이지 줄 바꿈

이러한 페이지를 통해 사용자 지정에 대해 다양한 서식을 지정할 수 있지만 ClangFormat이 사용된 경우에는 무시됩니다.

## <a name="see-also"></a>참고 항목

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
