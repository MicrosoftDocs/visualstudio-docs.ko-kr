---
title: 정규식 사용
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568622"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio에서 정규식 사용

Visual Studio에서는 [.NET 정규식](/dotnet/standard/base-types/regular-expressions)을 사용하여 텍스트를 찾고 바꿉니다.

## <a name="regular-expression-examples"></a>정규식 예제

다음 표에는 일부 정규식 문자, 연산자, 구문 및 패턴 예가 나와 있습니다. 자세한 내용은 [정규식 언어](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조하세요.

|용도|식|예제|
|-------------|----------------|-------------|
|줄 바꿈 이외의 모든 단일 문자를 찾습니다. 자세한 내용은 [임의의 문자](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)를 참조하세요.|을 선택합니다.|`a.o`는 “around”의 “aro” 및 “about”의 “abo”와 일치하지만 “across”의 “acro”와 일치하지 않습니다.|
|이전 식에서 일치 항목 0개 이상을 찾습니다(가능한 한 많은 문자를 찾음). 자세한 내용은 [0번 이상 일치](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)를 참조하세요.|*|`a*r`는 "rack"의 "r", "ark"의 "ar", "aardvark"의 "aar"과 일치합니다.|
|임의의 문자를 0회 이상 찾습니다.|.*|`c.*e`는 “racket”의 “cke”, “comment”의 “comme”, “code”의 “code”와 일치합니다.|
|이전 식에서 일치 항목 1개 이상을 찾습니다(가능한 한 많은 문자를 찾음). 자세한 내용은 [1번 이상 일치](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)를 참조하세요.|+|`e+d`는 “feeder”의 “eed” 및 “faded”의 “ed”와 일치합니다.|
|임의 문자를 한 번 이상 찾습니다.|.+|`e.+e`는 “feeder”의 “eede”와 일치하지만 “feed”에서는 일치하는 항목을 찾지 않습니다.|
|이전 식에서 일치 항목 0개 이상을 찾습니다(가능한 한 적은 문자를 찾음). 자세한 내용은 [0번 이상 일치(지연 일치)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)를 참조하세요.|*?|`\w*?d`는 “faded”에서 “fad” 및 “ed”와 일치하지만 완전한 단어인 “faded”는 게으른 일치로 인해 찾지 않습니다.|
|이전 식에서 일치 항목 1개 이상을 찾습니다(가능한 한 적은 문자를 찾음). 자세한 내용은 [1번 이상 일치(지연 일치)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-)를 참조하세요.|+?|`e\w+?`는 “asleep”의 “ee” 및 “faded”의 “ed”와 일치하지만 “fade”에서는 일치하는 항목을 찾지 않습니다.|
|일치 문자열을 [줄 또는 문자열의 시작](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)에 고정합니다.|^|`^car`는 줄의 시작 부분에 나타날 때만 단어 “car”와 일치합니다.|
|일치 문자열을 [줄의 끝](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)에 고정합니다.|\r?$|`car\r?$`는 줄의 끝부분에 나타날 때만 “car”과 일치합니다.|
|일치 문자열을 파일 끝에 고정|$|`car$`는 파일의 끝에 나타날 때만 “car”과 일치합니다.|
|집합에 있는 단일 문자를 찾습니다.|[abc]|`b[abc]`는 “ba”, “bb”, “bc”와 일치합니다.|
|문자 범위에서 임의 문자를 찾습니다.|[a-f]|`be[n-t]`는 “between”의 “bet”, “beneath”의 “ben”, “beside”의 “bes”와 일치하지만 “below”에서는 일치하는 항목을 찾지 않습니다.|
|괄호 안에 포함된 식을 캡처하고 명시적으로 번호를 지정합니다.|()|`([a-z])X\1`은 "aXa" 및 "bXb"와 일치하지만 "aXb"와 일치하지 않습니다. " “\1”은 첫 번째 식 그룹 “[a-z]”를 나타냅니다. 자세한 내용은 [캡처 그룹 및 바꾸기 패턴](#capture-groups-and-replacement-patterns)을 참조하십시오. |
|일치를 무효화합니다.|(?!abc)|`real(?!ity)`는 "realty" 및 "really"의 "real"과 일치하지만 "reality"와 일치하지 않습니다. "realityreal"에서 두 번째 "real"도 찾지만 첫 번째 "real"은 찾지 않습니다.|
|지정된 문자 집합에 없는 모든 문자를 찾습니다. 자세한 내용은 [부정 문자 그룹](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)을 참조하세요.|[^abc]|`be[^n-t]`는 “before”의 “bef”, “behind”의 “beh”, “below”의 “bel”과 일치하지만 “beneath”에서는 일치하는 항목을 찾지 않습니다.|
|기호 앞 또는 기호 뒤에 있는 식을 찾습니다.|&#124;|`(sponge|mud) bath`는 “sponge bath” 및 “mud bath”와 일치합니다.|
|백슬래시 뒤의 [문자를 이스케이프](/dotnet/standard/base-types/character-escapes-in-regular-expressions)합니다.| \\ |`\^`는 ^ 문자와 일치합니다.|
|이전 문자 또는 그룹의 일치 항목 수를 지정합니다. 자세한 내용은 [정확하게 n번 일치](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)를 참조하세요.|{n}. 여기서 ‘n’은 일치 항목 수입니다.|`x(ab){2}x`는 “xababx”와 일치합니다.<br/>`x(ab){2,3}x`는 “xababx” 및 “xabababx”와 일치하지만 “xababababx”와는 일치하지 않습니다.|
|[유니코드 범주의 텍스트를 찾습니다](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). 유니코드 문자 클래스에 대한 자세한 내용은 [Unicode Standard 5.2 Character Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)(유니코드 표준 5.2 문자 속성)를 참조하세요.|\p{X}, 여기서 "X"는 유니코드 번호입니다.|`\p{Lu}`는 “Thomas Doe”의 “T” 및 “D”와 일치합니다.|
|[단어 경계를 찾습니다](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b).|\b(문자 클래스 `\b` 외부는 단어 경계를 지정하고 문자 클래스 `\b` 내부는 백스페이스를 지정합니다.)|`\bin`은 “inside”의 “in”과 일치하지만 “pinto”에서는 일치하는 항목을 찾지 않습니다.|
|줄 바꿈을 찾습니다(캐리지 리턴 뒤에 줄 바꿈이 있음).|\r?\n|`End\r?\nBegin`은 “End”가 줄의 마지막 문자열이고 “Begin”이 다음 줄의 첫 번째 문자열일 때만 “End” 및 “Begin”과 일치합니다.|
|[단어 문자](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)를 찾습니다.|\w|`a\wd`는 “add” 및 “a1d”와 일치하지만 “a d”와 일치하지 않습니다.|
|[공백 문자](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)를 찾습니다.|\s|`Public\sInterface`는 구 “Public Interface”와 일치합니다.|
|[10진수 문자](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)를 찾습니다.|\d|`\d`는 “wd40”의 “4” 및 “0”과 일치합니다.|

일부 연산자와 구문을 16진수와 일치하도록 결합하는 정규식 예제는 `\b0[xX]([0-9a-fA-F]+\)\b`입니다. 이 식은 “0xc67f”와 일치하지만 “0xc67g”와는 일치하지 않습니다.

> [!TIP]
> Windows 운영 체제에서 대부분 줄은 “\r\n”(캐리지 리턴 뒤에 줄 바꿈)으로 끝납니다. 이들 문자는 표시되지 않지만 편집기에 있고 .NET 정규식 서비스에 전달됩니다.

## <a name="capture-groups-and-replacement-patterns"></a>캡처 그룹 및 바꾸기 패턴

캡처 그룹은 정규식의 하위 식을 정의하고 입력 문자열의 부분 문자열을 캡처합니다. 캡처된 그룹을 정규식 자체(예: 반복 단어 검색) 또는 바꾸기 패턴에서 사용할 수 있습니다. 자세한 내용은 [정규식의 그룹화 구문](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)을 참조하세요.

번호가 매겨진 캡처 그룹을 만들려면 정규식 패턴에서 하위 식을 괄호로 묶습니다. 정규식에서 여는 괄호의 위치에 따라 왼쪽에서 오른쪽으로 자동으로 캡처에 번호가 매겨집니다. 캡처된 그룹에 액세스하려면

- **정규식 내에서** `\number`을 사용하십시오. 예를 들어 정규식 `(\w+)\s\1`의 `\1`은 첫 번째 캡처 그룹 `(\w+)`를 참조합니다.

- **바꾸기 패턴에서** `$number`을 사용하십시오. 예를 들어 그룹화된 정규식 `(\d)([a-z])`은 다음 두 그룹을 정의합니다. 첫 번째 그룹은 단일 10진수를 포함하고 두 번째 그룹은 **a**와 **z** 사이의 단일 문자를 포함합니다. 이 식은 다음 문자열에서 일치 항목 4개를 찾습니다. **1a 2b 3c 4d**. 대체 문자열 `z$1`은 첫 번째 그룹(`$1`)만 참조하고 문자열을 **z1 z2 z3 z4**로 변환합니다.

다음 그림에서 정규식은 `(\w+)\s\1`이고 대체 문자열은 `$1`입니다. 정규식과 바꾸기 패턴 모두, 자동으로 번호 1이 매겨진 첫 번째 캡처 그룹을 참조합니다. Visual Studio의 **빠른 바꾸기** 대화 상자에서 **모두 바꾸기**를 선택하면 반복 단어가 텍스트에서 제거됩니다.

![Visual Studio에서 번호가 매겨진 캡처 그룹이 표시된 빠른 바꾸기](media/numbered-capture-group.png)

> [!TIP]
> **빠른 바꾸기** 대화 상자에서 **정규식 사용** 단추가 선택되었는지 확인합니다.

### <a name="named-capture-groups"></a>명명된 캡처 그룹

캡처 그룹의 자동 번호 매기기를 사용하는 대신 이름을 지정할 수 있습니다. 명명된 캡처 그룹의 구문은 `(?<name>subexpression)`입니다.

번호가 매겨진 캡처 그룹과 마찬가지로, 명명된 캡처 그룹을 정규식 자체 또는 바꾸기 패턴에서 사용할 수 있습니다. 명명된 캡처 그룹에 액세스하려면

- **정규식 내에서** `\k<name>`을 사용하십시오. 예를 들어 정규식 `(?<repeated>\w+)\s\k<repeated>`의 `\k<repeated>`는 이름이 `repeated`이고 하위 식이 `\w+`인 캡처 그룹을 참조합니다.

- **바꾸기 패턴에서** `${name}`을 사용하십시오. 예: `${repeated}`.

예를 들어 다음 그림에서 정규식은 `(?<repeated>\w+)\s\k<repeated>`이고 대체 문자열은 `${repeated}`입니다. 정규식과 바꾸기 패턴 모두, 이름이 `repeated`인 캡처 그룹을 참조합니다. Visual Studio의 **빠른 바꾸기** 대화 상자에서 **모두 바꾸기**를 선택하면 반복 단어가 텍스트에서 제거됩니다.

![Visual Studio에서 명명된 캡처 그룹이 표시된 빠른 바꾸기](media/named-capture-group.png)

> [!TIP]
> **빠른 바꾸기** 대화 상자에서 **정규식 사용** 단추가 선택되었는지 확인합니다.

명명된 캡처 그룹에 대한 자세한 내용은 [명명된 일치하는 하위 식](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions)을 참조하세요. 바꾸기 패턴에서 사용되는 정규식에 대한 자세한 내용은 [정규식의 대체](/dotnet/standard/base-types/substitutions-in-regular-expressions)를 참조하세요.

## <a name="see-also"></a>참조

- [정규식 언어](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)
