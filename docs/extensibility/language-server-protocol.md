---
title: 언어 서버 프로토콜 개요 | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703109"
---
# <a name="language-server-protocol"></a>언어 서버 프로토콜

## <a name="what-is-the-language-server-protocol"></a>언어 서버 프로토콜 이란?

소스 코드 자동 완성 또는 편집기나 IDE에서 프로그래밍 언어에 대 한 **정의로 이동** 과 같은 다양 한 편집 기능을 지 원하는 것은 일반적으로 매우 어렵고 시간이 많이 소요 됩니다. 일반적으로 편집기나 IDE의 프로그래밍 언어로 도메인 모델 (스캐너, 파서, 유형 검사기, 작성기 등)을 작성 해야 합니다. 예를 들어 eclipse ide에서 C/c + +에 대 한 지원을 제공 하는 Eclipse CDT 플러그 인은 Eclipse IDE 자체가 Java로 작성 되었으므로 Java로 작성 됩니다. 이 접근 방식에 따라 Visual Studio용 TypeScript 코드에서 C/c + + 도메인 모델을 구현 하는 것을 의미 하 고 Visual Studio 용 c #에서 별도의 도메인 모델을 구현 합니다.

개발 도구에서 기존 언어별 라이브러리를 다시 사용할 수 있는 경우에도 언어 관련 도메인 모델을 만드는 것이 훨씬 더 쉽습니다. 그러나 이러한 라이브러리는 일반적으로 프로그래밍 언어 자체에서 구현 됩니다. 예를 들어 좋은 C/c + + 도메인 모델은 C/c + +에서 구현 됩니다. C/c + + 라이브러리를 TypeScript로 작성 된 편집기에 통합 하는 것은 기술적으로 가능 하지만 그렇게 어렵습니다.

### <a name="language-servers"></a>언어 서버

또 다른 방법은 자체 프로세스에서 라이브러리를 실행 하 고 프로세스 간 통신을 사용 하 여 통신 하는 것입니다. 반환 된 메시지는 프로토콜을 통해 전송 됩니다. LSP (언어 서버 프로토콜)는 개발 도구와 언어 서버 프로세스 간에 교환 되는 메시지를 표준화 하는 제품입니다. 언어 서버 또는 demons를 사용 하는 것은 새로운 또는 novel 아이디어가 아닙니다. Vim 및 Emacs과 같은 편집기에서는 의미 체계 자동 완성 기능을 제공 하기 위해 일정 시간 동안이 작업을 수행 했습니다. LSP의 목표는 이러한 종류의 통합을 간소화 하 고 다양 한 도구에 언어 기능을 노출 하기 위한 유용한 프레임 워크를 제공 하는 것입니다.

공용 프로토콜을 사용 하면 언어의 도메인 모델에 대 한 기존 구현을 다시 사용 하 여 프로그래밍 언어 기능을 최소 혼란의 개발 도구에 통합할 수 있습니다. PHP, Python 또는 Java로 언어 서버 백 엔드를 작성할 수 있으며 LSP를 사용 하면 다양 한 도구에 쉽게 통합할 수 있습니다. 프로토콜은 일반적인 추상화 수준에서 작동 하므로 도구는 기본 도메인 모델 관련 미묘한 차이을 완전히 이해할 필요 없이 풍부한 언어 서비스를 제공할 수 있습니다.

## <a name="how-work-on-the-lsp-started"></a>LSP에서 작업을 시작 하는 방법

LSP는 시간이 지남에 따라 진화 했으며 오늘 버전 3.0에 있습니다. OmniSharp에서 언어 서버의 개념을 선택 하 여 c #에 대 한 풍부한 편집 기능을 제공 하는 경우 시작 되었습니다. 처음에 OmniSharp는 JSON 페이로드에 HTTP 프로토콜을 사용 하 고 [Visual Studio Code](https://code.visualstudio.com)를 비롯 한 여러 편집기에 통합 되었습니다.

이와 동시에 Microsoft는 Emacs 언어 서버에서 작업을 시작 했습니다. Emacs 및 Sublime 텍스트와 같은 편집기에서 TypeScript를 지원 한다는 것을 알 수 있습니다. 이 구현에서 편집기는 TypeScript 서버 프로세스를 사용 하 여 stdin/stdout을 통해 통신 하 고 요청 및 응답에 대해 V8 debugger 프로토콜에 의해 영향을 받은 JSON 페이로드를 사용 합니다. Typescript 서버는 typescript Sublime 플러그 인에 통합 되었으며 풍부한 TypeScript 편집을 위해 VS Code 되었습니다.

두 개의 다른 언어 서버를 통합 한 후 VS Code 팀은 편집기와 Ide에 대 한 공용 언어 서버 프로토콜을 탐색 하기 시작 했습니다. 일반적인 프로토콜을 사용 하면 언어 공급자가 여러 Ide에서 사용할 수 있는 단일 언어 서버를 만들 수 있습니다. 언어 서버 소비자는 프로토콜의 클라이언트 쪽을 한 번만 구현 하면 됩니다. 이로 인해 언어 공급자와 언어 소비자 모두에 게 win win 상황이 발생 합니다.

언어 서버 프로토콜은 TypeScript 서버에서 사용 하는 프로토콜을 사용 하 여 시작 하 고 VS Code 언어 API에서 제공 하는 더 많은 언어 기능을 사용 하 여 확장 합니다. 프로토콜은 간단 하 고 기존 라이브러리로 인해 원격 호출에 대해 JSON RPC로 지원 됩니다.

VS Code 팀은 파일에 대 한 요청에 응답 하 고 검색 된 경고 및 오류 집합을 반환 하는 여러 개의 linter 서버를 구현 하 여 프로토콜을 프로토타입 합니다. 사용자가 문서에서 편집할 때 파일을 사용 하지 않는 것이 목표입니다 .이는 편집기 세션 중에 많은 lint 요청이 있음을 의미 합니다. 각 사용자 편집에 대해 새로운 lint 프로세스를 시작할 필요가 없도록 서버를 유지 하 고 실행 하는 것이 합리적입니다. VS Code의 ESLint 및 TSLint 확장을 포함 하 여 여러 개의 linter가 구현 되었습니다. 이러한 두 개의 서버는 TypeScript/JavaScript에서 구현 되 고 Node.js에서 실행 됩니다. 클라이언트와 프로토콜의 서버 부분을 구현 하는 라이브러리를 공유 합니다.

## <a name="how-the-lsp-works"></a>LSP 작동 방법

언어 서버는 자체 프로세스에서 실행 되 고 Visual Studio 또는 VS Code와 같은 도구는 JSON-RPC를 통해 언어 프로토콜을 사용 하 여 서버와 통신 합니다. 전용 프로세스에서 작동 하는 언어 서버의 또 다른 이점은 단일 프로세스 모델과 관련 된 성능 문제를 방지 하는 것입니다. 클라이언트와 서버가 모두 Node.js으로 작성 된 경우 실제 전송 채널은 stdio.h, 소켓, 명명 된 파이프 또는 노드 ipc 일 수 있습니다.

다음은 일상적인 편집 세션 중에 도구와 언어 서버가 통신 하는 방법에 대 한 예제입니다.

![lsp 흐름 다이어그램](media/lsp-flow-diagram.png)

* **사용자가 도구에서 문서 라고 하는 파일을 엽니다**. 도구는 문서가 열려 있음을 언어 서버에 알립니다 (' TextDocument/didOpen '). 지금부터 문서 내용에 대 한 사실은 더 이상 파일 시스템에는 없으며 도구에 의해 메모리에 보관 됩니다.

* **사용자가 편집 합니다**.이 도구는 서버에 문서 변경 내용 (' TextDocument/didChange ')을 알리고 언어 서버에서 프로그램의 의미 체계 정보를 업데이트 합니다. 이 경우 언어 서버에서이 정보를 분석 하 고 검색 된 오류 및 경고 (' textDocument/서버 진단 ')를 사용 하 여 도구에 알립니다.

* **사용자가 편집기에서 기호에 대 한 "정의로 이동"을 실행**합니다 .이 도구는 두 개의 매개 변수 (1)와 문서 URI, (2)로 이동 요청이 서버에 시작 된 텍스트 위치의 ' textDocument/Definition ' 요청을 보냅니다. 서버는 문서 URI와 문서 내의 기호 정의 위치를 사용 하 여 응답 합니다.

* **사용자가 문서 (파일)를 닫습니다**. 도구에서 ' TextDocument/didClose ' 알림이 전송 됩니다 .이 알림은 언어 서버에 문서가 더 이상 메모리가 없고 현재 콘텐츠가 파일 시스템에서 최신 상태 라고 알립니다.

이 예제에서는 프로토콜이 "정의로 이동", "모든 참조 찾기"와 같은 편집기 기능 수준에서 언어 서버와 통신 하는 방법을 보여 줍니다. 프로토콜에서 사용 하는 데이터 형식은 현재 열려 있는 텍스트 문서와 같은 편집기 또는 IDE의 ' 데이터 형식 ' 및 커서의 위치입니다. 데이터 형식은 일반적으로 추상 구문 트리와 컴파일러 기호 (예: 확인 된 형식, 네임 스페이스, ...)를 제공 하는 프로그래밍 언어 도메인 모델의 수준이 아닙니다. 이렇게 하면 프로토콜이 크게 간소화 됩니다.

이제 ' textDocument/definition ' 요청에 대해 자세히 살펴보겠습니다. 다음은 c + + 문서에서 "정의로 이동" 요청에 대 한 클라이언트 도구와 언어 서버 간에 이동 하는 페이로드입니다.

요청은 다음과 같습니다.

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

응답은 다음과 같습니다.

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

돌아보면에서 프로그래밍 언어 모델 수준 대신 편집기 수준에서 데이터 형식을 설명 하는 것은 언어 서버 프로토콜의 성공 원인 중 하나입니다. 여러 프로그래밍 언어에서 추상 구문 트리 및 컴파일러 기호를 표준화 하는 것과 비교 하 여 텍스트 문서 URI 또는 커서 위치를 표준화 하는 것이 훨씬 더 간단 합니다.

사용자가 다른 언어로 작업 하는 경우 VS Code은 일반적으로 각 프로그래밍 언어에 대 한 언어 서버를 시작 합니다. 아래 예제에서는 사용자가 Java 및 SASS 파일에서 작업 하는 세션을 보여 줍니다.

![java 및 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>기능

모든 언어 서버에서 프로토콜이 정의한 모든 기능을 지원할 수 있는 것은 아닙니다. 따라서 클라이언트와 서버는 ' 기능 '을 통해 지원 되는 기능을 설정 합니다. 예를 들어 서버는 ' textDocument/definition ' 요청을 처리할 수 있다는 것을 나타내지만 ' 작업 영역/기호 ' 요청을 처리 하지 않을 수 있습니다. 마찬가지로, 클라이언트는 문서를 저장 하기 전에 ' 저장 하기 ' 알림을 제공할 수 있음을 알릴 수 있습니다. 그러면 서버에서 편집 된 문서의 서식을 자동으로 지정 하는 텍스트 편집을 계산할 수 있습니다.

## <a name="integrating-a-language-server"></a>언어 서버 통합

언어 서버를 특정 도구에 실제로 통합 하는 것은 언어 서버 프로토콜에 의해 정의 되지 않으며 도구 구현자으로 유지 됩니다. 일부 도구는 일반적으로 모든 종류의 언어 서버를 시작 하 고 통신할 수 있는 확장을 포함 하 여 언어 서버를 통합 합니다. VS Code와 같이 다른 사용자는 언어 서버당 사용자 지정 확장을 만들어 확장에서 일부 사용자 지정 언어 기능을 계속 제공할 수 있습니다.

언어 서버 및 클라이언트의 구현을 간소화 하기 위해 클라이언트 및 서버 파트에 대 한 라이브러리 또는 Sdk가 있습니다. 이러한 라이브러리는 다양 한 언어로 제공 됩니다. 예를 들어 언어 서버를 VS Code 확장 프로그램으로 쉽게 통합 하 고 다른 [언어 서버 npm 모듈](https://www.npmjs.com/package/vscode-languageserver) 을 사용 하 여 Node.js를 사용 하 여 언어 서버를 작성할 수 있는 [언어 client npm 모듈이](https://www.npmjs.com/package/vscode-languageclient) 있습니다. 지원 라이브러리의 현재 [목록](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) 입니다.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Visual Studio에서 언어 서버 프로토콜 사용

* [언어 서버 프로토콜 확장 추가](adding-an-lsp-extension.md) -언어 서버를 Visual Studio에 통합 하는 방법에 대해 알아봅니다.
