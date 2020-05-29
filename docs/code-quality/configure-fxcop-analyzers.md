---
title: Editorconfig를 사용 하 여 FxCop 분석기 구성
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 182042db9a744d037e295a8448f8c49a9c7b3a97
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184798"
---
# <a name="configure-fxcop-analyzers"></a>FxCop 분석기 구성

[FxCop 분석기 패키지](install-fxcop-analyzers.md) 는 레거시 분석에서 .NET Compiler Platform 기반 코드 분석기로 변환 된 가장 중요 한 "FxCop" 규칙으로 구성 됩니다. 특정 FxCop 규칙의 경우 [구성 가능한 옵션](fxcop-analyzer-options.md)을 통해 코드 베이스에서 적용 해야 하는 부분을 구체화할 수 있습니다. 각 옵션은 [Editorconfig](https://editorconfig.org) 파일에 키-값 쌍을 추가 하 여 지정 합니다. 구성 파일은 [프로젝트에 특정](#per-project-configuration) 하거나 둘 이상의 프로젝트 간에 [공유](#shared-configuration) 될 수 있습니다.

> [!TIP]
> **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 새 항목 **추가**를 선택 하 여 프로젝트에 editorconfig 파일을 추가  >  **New Item**합니다. **새 항목 추가** 창에서 검색 상자에 **editorconfig** 를 입력 합니다. **Editorconfig 파일 (기본)** 템플릿을 선택 하 고 **추가**를 선택 합니다.
>
> ![Visual Studio에서 프로젝트에 editorconfig 파일 추가](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

규칙의 심각도를 구성 하는 방법 (예: 오류 또는 경고)에 대 한 자세한 내용은 [EditorConfig 파일에서 규칙 심각도 설정](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)을 참조 하세요. 또는 기본 제공 [Editorconfig 파일 또는 규칙 집합](analyzer-rule-sets.md) 중 하나를 선택 하 여 규칙 범주를 신속 하 게 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

::: moniker-end

이 문서의 나머지 부분에서는 FxCop 규칙이 적용 되는 위치를 [구체화 하는 옵션](fxcop-analyzer-options.md) 에 대 한 일반적인 구문에 대해 설명 합니다.

> [!NOTE]
> EditorConfig 파일을 사용 하 여 레거시 FxCop 규칙을 구성할 수 없습니다. 레거시 분석과 FxCop 분석기 간의 차이점에 대 한 자세한 내용은 [fxcop 분석기 FAQ](fxcop-analyzers-faq.md)를 참조 하십시오.

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

### <a name="vs2019-163-and-later--fxcopanalyzers-package-version-33x-and-later"></a>VS2019 16.3 이상 + FxCopAnalyzers 패키지 버전 3.3. x 이상

EditorConfig 기반 분석기 구성은 다음 범위에 대해 사용 하도록 설정할 수 있습니다.

- 특정 문서
- 특정 폴더
- 특정 프로젝트
- 특정 솔루션
- 전체 리포지토리

구성을 사용 하도록 설정 하려면 해당 디렉터리의 옵션을 사용 하 여 *editorconfig* 파일을 추가 합니다. 이 파일에는 EditorConfig 기반 진단 심각도 구성 항목이 포함 될 수도 있습니다. 자세한 내용은 [여기](use-roslyn-analyzers.md#rule-severity)를 참조하세요.

### <a name="prior-to-vs2019-163-or-using-an-fxcopanalyzers-package-version-prior-to-33x"></a>VS2019 16.3 이전 또는 3.3. x 이전의 FxCopAnalyzers 패키지 버전 사용

#### <a name="per-project-configuration"></a>프로젝트별 구성

특정 프로젝트에 대 한 EditorConfig 기반 분석기 구성을 사용 하려면 프로젝트의 루트 디렉터리에 *editorconfig* 파일을 추가 합니다.

#### <a name="shared-configuration"></a>공유 구성

두 개 이상의 프로젝트 간에 FxCop analyzer 구성에 대 한 editorconfig 파일을 공유할 수 있지만 몇 가지 추가 단계가 필요 합니다.

1. 일반 위치에 *editorconfig* 파일을 저장 합니다.

2. 다음 콘텐츠를 사용 하 여 *props* 파일을 만듭니다.

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. *.Csproj* 또는 *.vbproj* 파일에 줄을 추가 하 여 이전 단계에서 만든 *props* 파일을 가져옵니다. 이 줄은 FxCop 분석기 *. props* 파일을 가져오는 모든 줄 앞에 배치 해야 합니다. 예를 들어, props 파일의 이름이 *editorconfig. props*인 경우:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. 프로젝트를 다시 로드 합니다.

> [!NOTE]
> 여기서 설명 하는 EditorConfig 파일의 임의로 공유 된 위치는 특정 FxCop 분석기 규칙의 범위를 구성 하는 경우에만 적용 됩니다. 규칙 심각도, 일반 편집기 설정 및 코드 스타일과 같은 다른 설정의 경우에는 항상 EditorConfig 파일을 프로젝트 폴더 또는 부모 폴더에 배치 해야 합니다.

## <a name="see-also"></a>참고 항목

- [FxCop 분석기에 대 한 규칙 범위 옵션](fxcop-analyzer-options.md)
- [분석기 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop 분석기](install-fxcop-analyzers.md)
- [EditorConfig에 대 한 .NET 코딩 규칙](../ide/editorconfig-code-style-settings-reference.md)
