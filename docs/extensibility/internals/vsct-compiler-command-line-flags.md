---
title: VSCT 컴파일러 Command-Line 플래그 | Microsoft Docs
description: Visual Studio 명령 테이블 컴파일러는 .vsct 파일을 성공적으로 컴파일할 수 있는 명령줄 옵션을 제공합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898897"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 컴파일러 명령줄 플래그
VSCT(Visual Studio 명령 테이블) 컴파일러는 .vsct 파일을 성공적으로 컴파일할 수 있도록 명령줄 스위치를 제공합니다.

## <a name="command-line-parameters"></a>명령줄 매개 변수
 명령 창에서 기본 VSCT 도움말을 보려면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Tools\Bin\ 폴더로 이동하여 다음을 입력합니다.

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
> (대시) 및 /(슬래시) 문자는 모두 명령줄 매개 변수를 나타내는 표기입니다.

 허용되는 플래그 및 그 의미는 다음과 같습니다.

|스위치|Description|
|------------|-----------------|
|-d|정의된 추가 기호를 지정합니다.|
|-I|파일 참조를 확인할 때 사용해야 하는 추가 포함 경로를 나타냅니다.|
|-l|<xref:System.Globalization.CultureInfo>문화권 이름(예: "en-US")을 지정합니다.|
|-E|명령 항목에 대해 지정된 네임스페이스에서 C# 개체를 내보낸 다음 [C&#124;H&#124;N]:*filename* where C = C#, H = C++ header, N = namespace. C#에는 네임스페이스가 필요합니다.|
|-v|자세한 출력입니다.|

 -L 스위치는 지정된 문화권 이름에 해당하는 이진 .cto 파일을 생성할 문자열 그룹을 선택하도록 컴파일러에 <xref:System.Globalization.CultureInfo> 지시합니다. 지정된 문화권 이름은 .vsct 파일에 있는 하나 이상의 [Strings 요소에](../../extensibility/strings-element.md) 대한 Language 특성과 일치해야 합니다. Strings 요소에 Language 특성이 없으면 포함하는 [CommandTable 요소](../../extensibility/commandtable-element.md)에서 상속됩니다.

 .vsct 파일에는 여러 Strings 요소가 있을 수 있으며 각각 다른 Language 특성이 있을 수 있습니다. 세계화는 VSCT 컴파일러를 여러 번 실행하고 각 문화권 이름에 대해 -L 스위치를 변경하여 달성됩니다.

 -L 스위치로 지정된 문화권 이름이 Strings 요소의 Language 특성과 일치하지 않으면 컴파일러는 지역이 아닌 언어와 일치하려고 시도합니다. 예를 들어 "en-US"를 찾을 수 없는 경우 컴파일러는 대신 "en"을 시도합니다. 실패하면 운영 체제의 현재 문화권이 시도됩니다. 실패하면 찾은 첫 번째 Strings 요소가 컴파일됩니다.

 -E 스위치는 명령 테이블에서 사용되는 기호가 포함된 C 스타일 헤더 파일을 내보내거나 명령 기호에 대한 개체가 포함된 C# 파일을 내보내는 데 사용할 수 있습니다.

 -D 및 -I 스위치에는 이름이 같은 Cl.exe C 전처리기 플래그의 구문이 있습니다. X=Y 형식의 -D 정의는 특성에서 XML 기반 \<Defined> 테스트의 확장에 `Condition` 사용됩니다. -포함 경로는 , 및 파일 참조를 해결하는 데 \<Include> \<Extern> \<Bitmap> 사용됩니다. 자세한 내용은 [VSCT XML 스키마 참조 를 참조하세요.](../../extensibility/vsct-xml-schema-reference.md)

 VSCT 컴파일러는 이전에 빌드한 이진 파일을 디컴파일할 수도 있습니다. 이렇게 하려면 에 대한 이진 파일을 \<infile> 제공하십시오.   VSCT 컴파일러에서 이진 파일을 생성한 경우 해당 기호가 이미 포함되어 있고 출력의 섹션에 기호 이름이 포함된 \<Symbols> 출력이 생성됩니다. CTC 컴파일러에서 이진을 생성한 경우 출력에 실제GUID 및 ID가 포함됩니다. 현재 버전의 Ctc.exe 의해 생성된 *.ctsym 파일이 이진 입력 파일과 동일한 폴더에 있는 경우 해당 파일에서 기호가 로드되고 출력에 사용됩니다.

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
