---
title: Editorconfig를 사용 하 여 .NET 코드 품질 분석기 구성
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800738"
---
# <a name="configure-net-code-quality-analyzers"></a>.NET 코드 품질 분석기 구성

특정 .NET 코드 품질 분석기 (규칙 Id가로 시작 하 `CA` 는)의 경우 [구성 가능한 옵션](fxcop-analyzer-options.md)을 통해 코드 베이스에서 적용 해야 하는 부분을 구체화할 수 있습니다. 각 옵션은 [Editorconfig](https://editorconfig.org) 파일에 키-값 쌍을 추가 하 여 지정 합니다. 구성 파일은 파일, 프로젝트, 솔루션 또는 전체 리포지토리에 특정 될 수 있습니다.

> [!TIP]
> **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 새 항목 **추가**를 선택 하 여 프로젝트에 editorconfig 파일을 추가  >  **New Item**합니다. **새 항목 추가** 창에서 검색 상자에 **editorconfig** 를 입력 합니다. **Editorconfig 파일 (기본)** 템플릿을 선택 하 고 **추가**를 선택 합니다.
>
> ![Visual Studio에서 프로젝트에 editorconfig 파일 추가](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

규칙의 심각도를 구성 하는 방법 (예: 오류 또는 경고)에 대 한 자세한 내용은 [EditorConfig 파일에서 규칙 심각도 설정](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)을 참조 하세요. 또는 기본 제공 [Editorconfig 파일 또는 규칙 집합](analyzer-rule-sets.md) 중 하나를 선택 하 여 규칙 범주를 신속 하 게 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

::: moniker-end

이 문서의 나머지 부분에서는 .NET 코드 품질 분석기가 적용 되는 위치를 [구체화 하는 옵션](fxcop-analyzer-options.md) 에 대 한 일반적인 구문에 대해 설명 합니다.

## <a name="option-scopes"></a>옵션 범위

각 구체화 옵션은 규칙 범주 (예: 이름 지정 또는 디자인) 또는 특정 규칙에 대해 모든 규칙에 대해 구성할 수 있습니다.

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

## <a name="enabling-editorconfig-based-configuration"></a>Editorconfig 기반 구성 사용

EditorConfig 기반 분석기 구성은 다음 범위에 대해 사용 하도록 설정할 수 있습니다.

- 특정 문서
- 특정 폴더
- 특정 프로젝트
- 특정 솔루션
- 전체 리포지토리

구성을 사용 하도록 설정 하려면 해당 디렉터리의 옵션을 사용 하 여 *editorconfig* 파일을 추가 합니다. 이 파일에는 EditorConfig 기반 진단 심각도 구성 항목이 포함 될 수도 있습니다. 자세한 내용은 [여기](use-roslyn-analyzers.md#rule-severity)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [.NET 코드 품질 분석기에 대 한 규칙 범위 옵션](fxcop-analyzer-options.md)
- [분석기 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig에 대 한 .NET 코딩 규칙](../ide/editorconfig-code-style-settings-reference.md)
