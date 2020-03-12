---
title: FxCop 코드 분석 및 FxCop 분석기
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d8e1df93fa9e865bb9b9136b9d0a0e07f1a485ea
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937509"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop 및 FxCop 분석기에 대한 질문과 대답

레거시 FxCop와 FxCop 분석기 간의 차이점을 이해이해하는 것은 다소 혼동을 일으킬 수 있습니다. 이 문서에서는 사용자가 가질 수 있는 일부 질문을 해결하려고 합니다.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>레거시 FxCop와 FxCop 분석기 간의 차이점은?

레거시 FxCop는 컴파일된 어셈블리에서 빌드 후 분석을 실행합니다. **FxCopCmd.exe**라는 별도 실행 파일로 실행됩니다. FxCopCmd.exe는 컴파일된 어셈블리를 로드하고, 코드 분석을 실행한 다음, 결과(또는 *진단*)를 보고합니다.

FxCop 분석기는 .NET Compiler Platform("Roslyn")을 기반으로 합니다. 프로젝트 또는 솔루션에서 참조되는 [NuGet 패키지로 설치](install-fxcop-analyzers.md#nuget-package)합니다. 컴파일러 실행 동안 FxCop 분석기는 소스 코드 기반 분석을 실행합니다. FxCop 분석기는 **csc.exe** 또는 **vbc.exe**의 컴파일러 프로세스 내에서 호스팅되며, 프로젝트가 빌드될 때 분석을 실행합니다. 분석기 결과는 컴파일러 결과와 함께 보고됩니다.

> [!NOTE]
> [Visual Studio 확장으로 FxCop 분석기를 설치](install-fxcop-analyzers.md#vsix)할 수도 있습니다. 이 경우 분석기는 코드 편집기에 입력한 대로 실행하지만 빌드 시 실행하지 않습니다. CI(지속적인 통합)의 일부로 FxCop 분석기를 실행하려는 경우 NuGet 패키지로 대신 설치합니다.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>코드 분석 실행 명령은 FxCop 분석기를 실행하나요?

아니요. **분석** > **실행 코드 분석**을 선택 하면 레거시 분석이 실행 됩니다. **코드 분석 실행**은 Roslyn 기반 FxCop 분석기를 포함하여 Roslyn 기반 분석기에 적용되지 않습니다.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 프로젝트 속성은 분석기를 실행하나요?

아니요. 프로젝트 파일에서 **RunCodeAnalysis** 속성(예: *.csproj*)은 레거시 FxCop 실행에만 사용됩니다. **FxCopCmd.exe**를 호출하는 빌드 후 msbuild 작업을 실행합니다. 이는 Visual Studio에서 **분석** > **코드 분석 실행**을 선택하는 것과 같습니다.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>그러면 FxCop 분석기를 어떻게 실행하나요?

FxCop 분석기를 실행하려면 먼저 [NuGet 패키지를 설치합니다](install-fxcop-analyzers.md). 그런 다음, Visual Studio에서 또는 msbuild를 사용하여 프로젝트 또는 솔루션을 빌드합니다. FxCop 분석기가 생성하는 경고 및 오류는 **오류 목록** 또는 명령 창에 표시됩니다.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>FxCop 분석기 NuGet 패키지를 설치한 후에도 경고 CA0507이 표시됨

FxCop 분석기를 설치 했지만 경고가 계속 표시 되는 경우 **"" 코드 분석 실행 "은 빌드 중에 실행 되는 FxCop 분석기를 위해 더 이상 사용 되지 않으므로** [프로젝트 파일](../ide/solutions-and-projects-in-visual-studio.md#project-file) 의 **runcodeanalysis** msbuild 속성을 **false**로 설정 해야 할 수 있습니다. 그렇지 않으면 각 빌드 후에 레거시 분석이 실행 됩니다.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>FxCop 분석기로 이식 된 규칙은 무엇 인가요?

[Fxcop 분석기](install-fxcop-analyzers.md)로 이식 된 레거시 분석 규칙에 대 한 자세한 내용은 [fxcop 규칙 포트 상태](fxcop-rule-port-status.md)를 참조 하세요.

## <a name="code-analysis-warnings-are-treated-as-errors"></a>코드 분석 경고는 오류로 처리 됩니다.

프로젝트에서 빌드 옵션을 사용 하 여 경고를 오류로 처리 하는 경우 FxCop 분석기 경고가 오류로 나타날 수 있습니다. 코드 분석 경고가 오류로 처리 되지 않도록 하려면 [코드 분석 FAQ](../code-quality/analyzers-faq.md#treat-warnings-as-errors)의 단계를 따르세요.

## <a name="see-also"></a>참고 항목

- [.NET Compiler Platform 분석기 개요](roslyn-analyzers-overview.md)
- [FxCop 분석기로 마이그레이션](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [FxCop 분석기 설치](install-fxcop-analyzers.md)
