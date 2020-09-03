---
title: VSCT 컴파일러 명령줄 플래그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703964"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 컴파일러 명령줄 플래그
Visual Studio 명령 테이블 (VSCT) 컴파일러는. vsct 파일을 성공적으로 컴파일하기 위해 명령줄 스위치를 제공 합니다.

## <a name="command-line-parameters"></a>명령줄 매개 변수
 명령 창에서 기본 VSCT 도움말을 보려면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Command** *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Tools\Bin\ 폴더로 이동 하 여 다음을 입력 합니다.

```
vsct /?
```

 반환 결과:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> 문자 (대시) 및/(슬래시)는 모두 명령줄 매개 변수를 나타내는 데 사용할 수 있는 표기법입니다.

 허용 되는 플래그 및 의미는 다음과 같습니다.

|스위치|Description|
|------------|-----------------|
|-d|정의 된 추가 기호를 지정 합니다.|
|-I|파일 참조를 확인할 때 사용 해야 하는 추가 포함 경로를 표시 합니다.|
|-l|<xref:System.Globalization.CultureInfo>문화권 이름을 지정 합니다 (예: "en-us").|
|-E|명령 항목에 대해 지정 된 네임 스페이스에 c # 개체를 내보내고, 그 다음에는 [C&#124;H&#124;N]:*filename*(c = c #, h = c + + 헤더, n = namespace)이 옵니다. 네임 스페이스는 c #에 필요 합니다.|
|-v|자세한 정보를 출력 합니다.|

 -L 스위치는 지정 된 문화권 이름에 해당 하는 이진 파일을 생성 하는 문자열 그룹을 선택 하도록 컴파일러에 지시 합니다 <xref:System.Globalization.CultureInfo> . 지정 된 문화권 이름은. vsct 파일에 있는 하나 이상의 [Strings 요소의](../../extensibility/strings-element.md) Language 특성과 일치 해야 합니다. Strings 요소에 언어 특성이 없으면 포함 하는 [Commandtable 요소](../../extensibility/commandtable-element.md)에서 상속 됩니다.

 . Vsct 파일에는 여러 개의 문자열 요소가 있을 수 있으며 각 요소에는 다른 언어 특성이 있을 수 있습니다. 세계화는 VSCT 컴파일러를 여러 번 실행 하 고 각 문화권 이름에 대 한-L 스위치를 변경 하 여 구현 됩니다.

 -L 스위치로 지정 된 문화권 이름이 Strings 요소의 Language 특성과 일치 하지 않는 경우 컴파일러는 지역이 아니라 언어를 찾으려고 시도 합니다. 예를 들어 "en-us"를 찾을 수 없는 경우 컴파일러는 대신 "en"을 시도 합니다. 실패 하면 운영 체제의 현재 문화권을 시도 합니다. 실패 하면 찾은 첫 번째 문자열 요소를 컴파일합니다.

 -E 스위치를 사용 하 여 명령 테이블에 사용 되는 기호를 포함 하는 C 스타일 헤더 파일을 내보내거나 명령 기호에 대 한 개체를 포함 하는 c # 파일을 내보낼 수 있습니다.

 -D 및-I 스위치에는 동일한 이름을 가진 Cl.exe C 전처리기 플래그의 구문이 있습니다. X = Y 형식인-D 정의는 특성에서 XML 기반 테스트를 확장 하는 데 사용 됩니다 \<Defined> `Condition` . -I를 확인 하는 데 사용 되는 경로 \<Include> \<Extern> 및 \<Bitmap> 파일 참조입니다. 자세한 내용은 [Vsct XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)를 참조 하세요.

 VSCT 컴파일러는 이전에 빌드한 이진 파일을 디컴파일 할 수도 있습니다. 이 작업을 수행 하려면에 대 한 이진 파일을 제공 \<infile> 합니다.   VSCT 컴파일러에서 이진 파일을 생성 한 경우 해당 기호는 이미 포함 되어 있고 출력의 한 섹션에 기호화 된 이름으로 출력을 생성 합니다 \<Symbols> . CTC 컴파일러에서 이진 파일을 생성 한 경우 출력에는 실제 Guid 및 Id가 포함 됩니다. Ctc.exe의 현재 버전에 의해 생성 된 *. .ctsym 파일이 이진 입력 파일과 같은 폴더에 있는 경우 해당 파일에서 기호가 로드 되 고 출력에 사용 됩니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블(.Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
