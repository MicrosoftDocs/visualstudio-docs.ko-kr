---
title: Editorconfig를 사용 하 여 .NET 코드 품질 분석기 구성
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035432"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>EditorConfig를 사용 하 여 .NET 코드 품질 분석 구성

`CA`구성 가능한 옵션을 통해 코드 베이스의 일부에 적용 되도록 각 코드 품질 분석기 (규칙 id로 시작)를 구체화할 수 있습니다. 각 옵션은 [Editorconfig](https://editorconfig.org) 파일에 키-값 쌍을 추가 하 여 지정 합니다. 구성 파일은 파일, 프로젝트, 솔루션 또는 전체 리포지토리에 특정 될 수 있습니다.

> [!TIP]
> **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 새 항목 **추가**를 선택 하 여 프로젝트에 editorconfig 파일을 추가  >  **New Item**합니다. **새 항목 추가** 창에서 검색 상자에 **editorconfig** 를 입력 합니다. **Editorconfig 파일 (기본)** 템플릿을 선택 하 고 **추가**를 선택 합니다.
>
> ![Visual Studio에서 프로젝트에 EditorConfig 파일 추가](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

규칙의 심각도를 구성 하는 방법 (예: 오류 또는 경고)에 대 한 자세한 내용은 [EditorConfig 파일에서 규칙 심각도 설정](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)을 참조 하세요. 또는 기본 제공 [Editorconfig 파일 또는 규칙 집합](analyzer-rule-sets.md) 중 하나를 선택 하 여 규칙 범주를 신속 하 게 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

::: moniker-end

이 문서의 나머지 부분에서는 .NET 코드 품질 분석기가 적용 되는 위치를 구체화 하는 옵션에 대 한 일반적인 구문에 대해 설명 합니다.

## <a name="option-scopes"></a>옵션 범위

모든 규칙, 규칙 범주 (예: 보안 또는 디자인) 또는 특정 규칙에 대해 각 구체화 옵션을 구성할 수 있습니다.

### <a name="all-rules"></a>모든 규칙

*모든* 규칙에 대 한 옵션을 구성 하는 구문은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>규칙 범주

규칙 *범주* 에 대 한 옵션을 구성 하는 구문 (예: 이름 지정, 디자인 또는 성능)은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality. RuleCategory OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>특정 규칙

*특정* 규칙에 대 한 옵션을 구성 하는 구문은 다음과 같습니다.

|구문|예제|
|-|-|
| dotnet_code_quality. RuleId OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>EditorConfig 기반 구성 사용

EditorConfig 기반 분석기 구성은 다음 범위에 대해 사용 하도록 설정할 수 있습니다.

- 특정 문서
- 특정 폴더
- 특정 프로젝트
- 특정 솔루션
- 전체 리포지토리

구성을 사용 하도록 설정 하려면 해당 디렉터리의 옵션을 사용 하 여 *editorconfig* 파일을 추가 합니다. 이 파일에는 EditorConfig 기반 진단 심각도 구성 항목이 포함 될 수도 있습니다. 자세한 내용은 [여기](use-roslyn-analyzers.md#configure-severity-levels)를 참조하세요.

## <a name="enable-a-category-of-rules"></a>규칙 범주 사용

분석기 패키지는 보안 또는 설계 규칙과 같은 규칙 범주를 빠르고 쉽게 사용할 수 있도록 미리 정의 된 [Editorconfig](use-roslyn-analyzers.md#configure-severity-levels) 및/또는 [규칙 집합](using-rule-sets-to-group-code-analysis-rules.md) 파일을 포함할 수 있습니다. [Microsoft CodeAnalysis](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer 패키지에는 editorconfig 파일과 규칙 집합이 모두 포함 되어 있습니다. 규칙의 특정 범주를 사용 하도록 설정 하면 대상 문제 및 특정 조건을 식별할 수 있습니다.

> [!NOTE]
> Visual Studio 2019 버전 16.3부터 분석기 규칙을 사용 하도록 설정 하 고 EditorConfig 파일을 사용 하 여 심각도를 설정 하는 것이 지원 됩니다.

NetAnalyzers NuGet 패키지에는 다음 규칙 범주에 대 한 미리 정의 된 EditorConfig 파일 및 규칙 집합이 포함 되어 있습니다.

- 모든 규칙
- 데이터 흐름
- 디자인
- 설명서
- 전역화
- 상호 운용성
- 유지 관리
- 이름 지정
- 성능
- FxCop에서 이식
- 안정성
- 보안
- 사용량

이러한 각 규칙 범주에는 다음에 대 한 EditorConfig 또는 rule set 파일이 있습니다.

- 범주에 있는 모든 규칙을 사용 하도록 설정 하 고 다른 모든 규칙을 사용 하지 않도록 설정 합니다.
- 각 규칙의 기본 심각도를 사용 하 고 기본적으로 사용 하도록 설정 (및 다른 모든 규칙 사용 안 함)

> [!TIP]
> "모든 규칙" 범주에는 모든 규칙을 사용 하지 않도록 설정 하는 추가 EditorConfig 또는 규칙 집합 파일이 있습니다. 이 파일을 사용 하 여 프로젝트에서 분석기 경고 또는 오류를 신속 하 게 제거할 수 있습니다.

> [!TIP]
> 레거시 "FxCop" 분석에서 .NET Compiler Platform 기반 코드 분석으로 마이그레이션하는 경우 EditorConfig 및 규칙 집합 파일을 사용 하 여 [이전에 사용한](rule-set-reference.md)것과 비슷한 규칙 구성을 계속 해 서 사용할 수 있습니다.

## <a name="predefined-editorconfig-files"></a>미리 정의 된 EditorConfig 파일

Microsoft CodeAnalysis. NetAnalyzers 분석기 패키지에 대 한 미리 정의 된 EditorConfig 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \editorconfig* 디렉터리에 있습니다. 예를 들어 모든 보안 규칙을 사용 하도록 설정 하는 EditorConfig 파일은 *% USERPROFILE% \\ . Nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \\ Orom\omom\securityststststststst\securitystc\securityst\*

선택한 editorconfig 파일을 프로젝트의 루트 디렉터리에 복사 합니다.

## <a name="predefined-rule-sets"></a>미리 정의된 규칙 집합

Microsoft CodeAnalysis. NetAnalyzers 분석기 패키지에 대 한 미리 정의 된 규칙 집합 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \\ststoml* 디렉터리에 있습니다. 예를 들어 모든 보안 규칙을 사용 하도록 설정 하는 규칙 집합 파일은 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*에 있습니다.

하나 이상의 규칙 집합을 복사 하 고 Visual Studio 프로젝트를 포함 하는 디렉터리 또는 **솔루션 탐색기**에 직접 붙여 넣습니다.

[미리 정의 된 규칙 집합](how-to-create-a-custom-rule-set.md) 을 기본 설정으로 사용자 지정할 수도 있습니다. 예를 들어 위반이 **오류 목록**에 오류 또는 경고로 표시 되도록 하나 이상의 규칙의 심각도를 변경할 수 있습니다.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>.NET 코드 품질 분석기에 대 한 규칙 범위 옵션

[Editorconfig 파일](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)에서 옵션을 지정할 수 있습니다. 예를 들어 다음 옵션을 지정할 수 있습니다.

> [!TIP]
> 사용할 수 있는 옵션의 전체 목록을 보려면이 [Analyzer Configuration.md 파일](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)을 참조 하세요. 다음은 *Analyzer Configuration.md* 파일에 옵션을 설명 하는 방법의 예입니다.
>
> 옵션 이름: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> 옵션 값: 정수 값 \
> 기본값: 각 구성 가능한 규칙 (대부분의 규칙에 대해 기본적으로 ' 10만 ')에 한정 됩니다.
> 예: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석할 API 표면의 부분 | `public`<br/>`internal` 또는 `friend`<br/>`private`<br/>`all`<br/><br/>여러 값을 쉼표 (,)로 구분 합니다. | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 값을 반환 하지 않는 비동기 메서드를 무시할지 여부 | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 분석기 패키지의 2.6.3 이전 버전에서는이 옵션의 이름이로 지정 되었습니다 `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 에서와 같이 단일 문자 [형식 매개 변수](/dotnet/csharp/programming-guide/generics/generic-type-parameters) 를 규칙에서 제외할지 여부 `S``Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 분석기 패키지의 2.6.3 이전 버전에서는이 옵션의 이름이로 지정 되었습니다 `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 이 어셈블리 유형을 생성 하는 프로젝트의 코드를 분석 해야 함을 지정 합니다. | 열거형의 하나 이상의 필드 <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>여러 값을 쉼표 (,)로 구분 합니다. | 모든 출력 종류 | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석 되어야 하는 Api에 대 한 필수 한정자를 지정 합니다. | 허용 되는 한정자 테이블에서 하나 이상의 값<br/><br/>여러 값을 쉼표 (,)로 구분 합니다. | 각 규칙에 따라 다름 | [CA1802](ca1802.md) |

| 허용 되는 한정자 | 요약 |
| --- | --- |
| `none` | 한정자 요구 사항 없음 |
| `static` 또는 `Shared` | ' Static ' (Visual Basic의 ' Shared ')으로 선언 해야 합니다. |
| `const` | ' Const '로 선언 해야 합니다. |
| `readonly` | ' Readonly '로 선언 해야 합니다. |
| `abstract` | ' Abstract '로 선언 해야 합니다. |
| `virtual` | ' Virtual '로 선언 해야 합니다. |
| `override` | ' Override '로 선언 해야 합니다. |
| `sealed` | ' Sealed '로 선언 해야 합니다. |
| `extern` | ' Extern '으로 선언 해야 합니다. |
| `async` | ' Async '로 선언 해야 합니다. |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 확장 메서드의 매개 변수에 대 한 분석을 건너뛸지 여부 `this` | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 메서드에 전달 된 인수의 유효성을 검사 하는 null 검사 유효성 검사 메서드의 이름이 null이 아닙니다. | 허용 되는 메서드 이름 형식 (로 구분 `|` ):<br/> -메서드 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 메서드 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `M:` | 없음 | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 추가 문자열 형식 지정 메서드의 이름 | 허용 되는 메서드 이름 형식 (로 구분 `|` ):<br/> -메서드 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 메서드 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `M:` | 없음 | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 형식 이름 (형식 및 모든 파생 형식이 분석에 대해 제외 됨) | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -형식 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 형식 포함).<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `T:` | 없음 | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석을 위해 제외 된 기호 이름 | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -기호 이름에만 해당 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 기호 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)으로 정규화 된 이름입니다. 각 기호 이름에는 "M:" 메서드의 접두사, "T:" 형식의 접두사, "N:" 네임 스페이스에 대 한 접두사 등의 기호 종류 접두사가 필요 합니다.<br/> - `.ctor` 생성자 및 `.cctor` for static 생성자의 경우 | 없음 | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) [CA5376 CA5377 CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석 컨텍스트에서 허용 되지 않는 기호의 이름입니다. | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -기호 이름에만 해당 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 기호 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)으로 정규화 된 이름입니다. 각 기호 이름에는 "M:" 메서드의 접두사, "T:" 형식의 접두사, "N:" 네임 스페이스에 대 한 접두사 등의 기호 종류 접두사가 필요 합니다.<br/> - `.ctor` 생성자 및 `.cctor` for static 생성자의 경우 | 없음 | [CA1031](ca1031.md) |

## <a name="see-also"></a>참고 항목

- [분석기 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig에 대 한 .NET 코딩 규칙](../ide/editorconfig-code-style-settings-reference.md)
