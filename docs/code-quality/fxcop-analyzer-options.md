---
title: FxCop 분석기 구성 옵션
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d6b56bec2174ca71cc66f5424b7bdc309330d95
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248793"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>FxCop 분석기에 대 한 규칙 범위 옵션

일부 FxCop analyzer 규칙을 사용 하 여 코드 베이스에서 적용 해야 하는 부분을 구체화할 수 있습니다. 이 페이지에서는 사용 가능한 범위 구성 옵션, 허용 되는 값 및 적용할 수 있는 규칙을 나열 합니다. 이러한 옵션을 사용 하려면 [Editorconfig 파일](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)에서 지정 합니다.

이러한 구성 옵션은 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 패키지의 버전 2.6.3부터 사용할 수 있습니다.

> [!TIP]
> 지정 된 버전의 FxCopAnalyzers 패키지에 사용할 수 있는 옵션의 전체 목록을 보려면 패키지의 *문서* 폴더에서 *Analyzer Configuration.md* 파일을 확인 합니다. 이 파일은 *% USERPROFILE% \\ . Nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version\> \documentation\analyzer*에 있습니다. 이 구성 문서 파일은 버전 2.6.5에서 시작 하 여 패키지의 각 버전에 포함 되어 있습니다. 다음은 *Analyzer Configuration.md* 파일에 옵션을 설명 하는 방법의 예입니다.
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
| 메서드에 전달 된 인수의 유효성을 검사 하는 null 검사 유효성 검사 메서드의 이름이 null이 아닙니다. | 허용 되는 메서드 이름 형식 (로 구분 `|` ):<br/> -메서드 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 메서드 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `M:` | None | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 추가 문자열 형식 지정 메서드의 이름 | 허용 되는 메서드 이름 형식 (로 구분 `|` ):<br/> -메서드 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 메서드 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `M:` | None | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 형식 이름 (형식 및 모든 파생 형식이 분석에 대해 제외 됨) | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -형식 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 형식 포함).<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)에 있는 정규화 된 이름 (옵션 접두사 포함) `T:` | None | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석을 위해 제외 된 기호 이름 | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -기호 이름에만 해당 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 기호 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)으로 정규화 된 이름입니다. 각 기호 이름에는 "M:" 메서드의 접두사, "T:" 형식의 접두사, "N:" 네임 스페이스에 대 한 접두사 등의 기호 종류 접두사가 필요 합니다.<br/> - `.ctor` 생성자 및 `.cctor` for static 생성자의 경우 | None | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) [CA5376 CA5377 CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석 컨텍스트에서 허용 되지 않는 기호의 이름입니다. | 허용 되는 기호 이름 형식 (로 구분 `|` ):<br/> -기호 이름에만 해당 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 기호 포함)<br/> -기호의 [설명서 ID 형식](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)으로 정규화 된 이름입니다. 각 기호 이름에는 "M:" 메서드의 접두사, "T:" 형식의 접두사, "N:" 네임 스페이스에 대 한 접두사 등의 기호 종류 접두사가 필요 합니다.<br/> - `.ctor` 생성자 및 `.cctor` for static 생성자의 경우 | None | [CA1031](ca1031.md) |
