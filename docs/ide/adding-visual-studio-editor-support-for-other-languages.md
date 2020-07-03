---
title: 다른 언어에 대한 편집기 지원 추가
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 247567030d47a55b29a3fca901e12948ddd85916
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533759"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>다른 언어에 대한 Visual Studio 편집기 지원 추가

Visual Studio 편집기에서 다양한 컴퓨터 언어 읽기 및 탐색을 지원하는 방법과 다른 언어에 대한 Visual Studio 편집기 지원을 추가하는 방법을 알아봅니다.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>구문 색 지정, 문 완성 및 탐색 지원

구문 색 지정, 명령문 완성(IntelliSense라고도 함) 및 _탐색 대상_와 같은 Visual Studio 편집기의 기능을 사용하면 코드를 보다 쉽게 작성, 읽기 및 편집할 수 있습니다. 다음 스크린샷은 Visual Studio에서 Perl 스크립트를 편집하는 예를 보여 줍니다. 구문에 자동으로 색이 지정됩니다. 예를 들어 코드의 주석은 녹색, 코드는 검은색, 경로는 빨간색, 문은 파란색으로 표시됩니다. Visual Studio 편집기는 지원하는 모든 언어에 자동으로 구문 색 지정을 적용합니다. 또한 알려진 언어 키워드 또는 개체를 입력하기 시작하면 문 완성 기능을 통해 가능한 문 및 개체 목록이 표시됩니다. 명령문 완성 기능은 코드 작성을 보다 쉽고 빠르게 도와줍니다.

![Perl 스크립트의 구문 색 지정](../ide/media/vside_perledit.png)

Visual Studio는 현재 [TextMate 문법](https://manual.macromates.com/en/language_grammars)을 사용하여 다음 언어에 대해 구문 색 지정 및 기본 문 완성을 지원합니다. 자주 사용하는 언어가 표에 없는 경우 걱정하지 마세요.&mdash;직접 추가할 수 있습니다.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- 이동
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Make
- Ruby
- TypeScript
- YAML

구문 색 지정 및 기본 문 완성 기능 외에도 Visual Studio에는 [탐색](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/) 기능이 있습니다. 이 기능을 사용하면 코드 파일, 파일 경로 및 코드 기호를 빠르게 검색할 수 있습니다. Visual Studio는 다음 언어에 대해 탐색 기능을 지원합니다.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- 이동

- Java

- PHP

지정된 언어에 대한 지원이 아직 설치되지 않은 경우에도 이러한 모든 파일 형식에는 앞에서 설명한 기능이 있습니다. 일부 언어에 대한 특수 지원을 설치하면 IntelliSense 등의 추가 언어 지원이나 전구와 같은 기타 고급 언어 기능이 제공됩니다.

## <a name="add-support-for-non-supported-languages"></a>지원되지 않는 언어에 대한 지원 추가

Visual Studio에서는 [TextMate 문법](https://manual.macromates.com/en/language_grammars)을 사용하여 편집기의 언어 지원을 제공합니다. 자주 사용하는 프로그래밍 언어가 현재 Visual Studio 편집기에서 지원되지 않는 경우 먼저 웹을 검색하세요. 해당 언어에 대한 TextMate 번들이 이미 있을 수도 있습니다. 해당 번들이 없는 경우 언어 문법과 코드 조각에 대한 TextMate 번들 모델을 만들어 직접 지원을 추가할 수 있습니다.

Visual Studio에 대한 새 TextMate 문법을 다음 폴더에 추가합니다.

*%userprofile%\\.vs\Extensions*

상황에 적용되는 경우 다음 폴더를 이 기본 경로 아래에 추가합니다.

|폴더 이름|설명|
|-----------------|-----------------|
|\\*\<language name>*|언어 폴더입니다. *\<language name>* 을 언어 이름으로 바꿉니다. 예를 들어 *\Matlab*으로 바꿉니다.|
|*\Syntaxes*|문법 폴더입니다. 언어의 문법 *.json* 파일(예: *Matlab.json*)이 들어 있습니다.|
|*\Snippets*|코드 조각 폴더입니다. 언어의 코드 조각이 들어 있습니다.|

Windows에서 *%userprofile%* 은 *c:\Users\\\<user name>* 경로로 확인됩니다. 시스템에 *Extensions* 폴더가 없는 경우 새로 만들어야 합니다. 폴더가 이미 있는 경우 숨겨집니다.

> [!TIP]
> 편집기에 파일이 열려 있는 경우 TextMate 문법을 추가한 후 구문 강조 표시를 확인하려면 해당 파일을 닫고 다시 열어야 합니다.

TextMate 문법을 만드는 방법에 대한 자세한 내용은 [TextMate – Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/)(TextMate – 언어 문법 소개) 및 [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)(Textmate 번들의 언어 문법 및 사용자 지정 테마를 만드는 방법에 대한 참고 사항)을 참조하세요.

## <a name="see-also"></a>참조

- [언어 서버 프로토콜 확장 추가](../extensibility/adding-an-lsp-extension.md)
- [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md)
- [연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)
- [예제 코드: TextMate 문법](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [예제 코드: 사용자 지정 언어 지원](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)