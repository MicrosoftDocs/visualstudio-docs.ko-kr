---
title: VSCT 컴파일러 명령줄 플래그 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703964"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 컴파일러 명령줄 플래그
VSCT(Visual Studio 명령 테이블) 컴파일러는 .vsct 파일을 성공적으로 컴파일할 수 있도록 명령줄 스위치를 제공합니다.

## <a name="command-line-parameters"></a>명령줄 매개변수
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **명령** 창에서 기본 VSCT 도움말을 보려면 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Tools\Bin\ 폴더 및 유형으로 이동합니다.

```
vsct /?
```

 반환 결과

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
> 문자 - (대시) 및 / (정방향 슬래시)는 모두 명령줄 매개 변수를 나타내는 허용 된 표기입니다.

 허용되는 플래그와 그 의미는 다음과 같습니다.

|스위치|설명|
|------------|-----------------|
|-d|정의된 기호를 추가로 지정합니다.|
|-I|파일 참조를 확인할 때 사용해야 하는 추가 포함 경로를 나타냅니다.|
|-l|<xref:System.Globalization.CultureInfo> 문화권 이름(예: "en-US")을 지정합니다.|
|-E|명령 항목에 대해 지정된 네임스페이스에 C# 개체를 내보내면 [C&#124;H&#124;N]: C = C#, H = C++ 헤더, N = 네임스페이스가 있는*파일 이름.* C#에는 네임스페이스가 필요합니다.|
|-v|자세한 출력.|

 -L 스위치는 컴파일러가 지정된 <xref:System.Globalization.CultureInfo> 문화권 이름에 해당하는 이진 .cto 파일을 생성하는 문자열 그룹을 선택하도록 지시합니다. 지정된 문화권 이름은 .vsct 파일에서 하나 이상의 [문자열 요소의](../../extensibility/strings-element.md) 언어 특성과 일치해야 합니다. 문자열 요소에 언어 특성이 없는 경우 포함 된 [CommandTable 요소에서](../../extensibility/commandtable-element.md)상속 됩니다.

 .vsct 파일에는 여러 Strings 요소가 있을 수 있으며 각 파일에는 다른 언어 특성이 있을 수 있습니다. 세계화는 VSCT 컴파일러를 여러 번 실행하고 각 문화권 이름에 대한 -L 스위치를 변경하여 달성됩니다.

 -L 스위치에서 지정한 문화권 이름이 Strings 요소의 Language 특성과 일치하지 않으면 컴파일러는 해당 영역이 아닌 언어와 일치하도록 시도합니다. 예를 들어 "en-US"를 찾을 수 없는 경우 컴파일러는 대신 "en"을 시도합니다. 실패하면 운영 체제의 현재 문화권이 시도됩니다. 실패하면 찾은 첫 번째 문자열 요소를 컴파일합니다.

 -E 스위치는 명령 테이블에서 사용되는 기호를 포함하는 C 스타일 헤더 파일을 내보내거나 명령 기호에 대한 개체가 포함된 C# 파일을 내보내도록 사용할 수 있습니다.

 -D 및 -I 스위치에는 이름이 같은 Cl.exe C 전처리기 플래그의 구문이 있습니다. -X=Y 형식이 있는 D 정의는 특성에서 XML \<기반 정의 `Condition`> 테스트의 확장에 사용됩니다. -나는> 포함, \< \<Extern> 및 \<비트 맵> 파일 참조를 해결하는 데 사용되는 경로를 포함한다. 자세한 내용은 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)를 참조하십시오.

 VSCT 컴파일러는 이전에 빌드된 이진 파일을 디컴파일할 수도 있습니다. 이렇게 하려면 \<인파일> 대한 이진 파일을 제공하십시오.   이진 파일이 VSCT 컴파일러에 의해 생성된 경우 해당 기호가 이미 포함되고 출력의 \<기호> 섹션에 기호 이름이 있는 출력이 생성됩니다. CTC 컴파일러에서 바이너리를 생성한 경우 출력에는 실제 GUID와 ID가 포함됩니다. Ctc.exe의 현재 버전에서 생성되는 *.ctsym 파일이 이진 입력 파일과 동일한 폴더에 있으면 해당 파일에서 기호가 로드되어 출력에 사용됩니다.

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
