---
title: 다른 언어에 대 한 편집기 지원 추가 | Microsoft Docs
ms.date: 11/15/2016
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548111"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>다른 언어에 대한 Visual Studio 편집기 지원 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 편집기에서 다양한 컴퓨터 언어 읽기 및 탐색을 지원하는 방법과 다른 언어에 대한 Visual Studio 편집기 지원을 추가하는 방법을 알아봅니다.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>구문 색 지정, 문 완성 및 탐색 지원
 구문 색 지정, 문 완성, 탐색 등의 Visual Studio 편집기 기능은 쉽게 코드를 읽고 만들고 편집하는 데 도움이 됩니다. 다음 스크린샷은 Visual Studio에서 Perl 스크립트를 편집하는 예를 보여 줍니다. 구문에 자동으로 색이 지정됩니다. 예를 들어 코드의 주석은 녹색, 코드는 검은색, 경로는 빨간색, 문은 파란색으로 표시됩니다. Visual Studio 편집기는 지원하는 모든 언어에 자동으로 구문 색 지정을 적용합니다. 또한 알려진 언어 키워드 또는 개체를 입력하기 시작하면 문 완성 기능을 통해 가능한 문 및 개체 목록이 표시됩니다. 문 완성 기능은 보다 빠르고 쉽게 코드를 만드는 데 도움이 됩니다.

 ![Perl 스크립트의 구문 색 지정](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Visual Studio는 현재 [TextMate 문법](https://manual.macromates.com/en/language_grammars)을 사용하여 다음 언어에 대해 구문 색 지정 및 기본 문 완성을 지원합니다. 자주 사용하는 언어가 표에 없는 경우 걱정하지 마세요. 직접 추가할 수 있습니다.

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

- Go

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  지정된 언어에 대한 지원이 아직 설치되지 않은 경우에도 이러한 모든 파일 형식에는 앞에서 설명한 기능이 있습니다. 일부 언어에 대한 특수 지원을 설치하면 IntelliSense 등의 추가 언어 지원이나 전구 등의 기타 고급 언어 기능이 제공됩니다.

## <a name="adding-support-for-non-supported-languages"></a>지원되지 않는 언어에 대한 지원 추가
 Visual Studio 2015 업데이트 1 이상 버전에서는 [TextMate 문법](https://manual.macromates.com/en/language_grammars)을 사용하여 편집기의 언어 지원을 제공합니다. 자주 사용하는 프로그래밍 언어가 현재 Visual Studio 편집기에서 지원되지 않는 경우 먼저 웹을 검색하세요. 해당 언어에 대한 TextMate 번들이 있을 수도 있습니다. 해당 번들이 없는 경우 Visual Studio 2015 업데이트 1 이상에서는 언어 문법과 코드 조각에 대한 TextMate 번들 모델을 만들어 직접 지원을 추가할 수 있습니다.

 Visual Studio에 대한 새 TextMate 문법을 다음 폴더에 추가합니다.

 %userprofile%\\.vs\Extensions

 상황에 적용되는 경우 다음 폴더를 이 기본 경로 아래에 추가합니다.

|폴더 이름|설명|
|-----------------|-----------------|
|\\*\<language name>*|언어 폴더입니다. *\<language name>* 언어의 이름으로 대체 합니다. 예를 들어 **\Matlab**으로 바꿉니다.|
|\Syntaxes|문법 폴더입니다. 언어의 문법 .json 파일(예: **Matlab.json**)이 들어 있습니다.|
|\Snippets|코드 조각 폴더입니다. 언어의 코드 조각이 들어 있습니다.|

 Windows 에서% userprofile%은 c:\Users 경로를 확인 합니다. \\ *\<user name>* 시스템에 extensions 폴더가 없는 경우 새로 만들어야 합니다. 폴더가 이미 있는 경우 숨겨집니다.

 TextMate 문법을 만드는 방법에 대 한 자세한 내용은 [textmate – 언어 문법 소개: HTML에 포함 된 소스 코드 구문 강조 표시를 추가 하는 방법](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) 및 [textmate 번들에 대 한 언어 문법 및 사용자 지정 테마를 만드는 방법에 대 한 참고 사항](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)을 참조 하세요.

## <a name="see-also"></a>참고 항목
 [Visual Studio 2013 탐색 향상](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md) [연습: 문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)
