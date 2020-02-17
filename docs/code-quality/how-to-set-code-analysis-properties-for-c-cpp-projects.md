---
title: '방법: C/C++ 프로젝트의 코드 분석 속성 설정'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 1c517674bb3aba58caa865a02b384e9d90af8a10
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271700"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>방법: C/C++ 프로젝트의 코드 분석 속성 설정

코드 분석 도구에서 프로젝트의 각 구성에서 코드를 분석 하는 데 사용 하는 규칙을 구성할 수 있습니다. 또한 타사 도구를 통해 생성 되 고 프로젝트에 추가 된 코드에서 발생 하는 경고를 표시 하지 않도록 코드 분석을 지시할 수 있습니다.

## <a name="code-analysis-property-page"></a>코드 분석 속성 페이지

**코드 분석** 속성 페이지에는 MSBuild 프로젝트에 대 한 모든 코드 분석 구성 설정이 포함 되어 있습니다. **솔루션 탐색기**에서 프로젝트에 대 한 코드 분석 속성 페이지를 열려면 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 그런 다음 **구성 속성** 을 확장 하 고 **코드 분석** 탭을 선택 합니다.

## <a name="project-configuration-and-platform"></a>프로젝트 구성 및 플랫폼

창 맨 위에 있는 **구성** 목록 및 **플랫폼** 목록을 사용 하면 다른 프로젝트 구성 및 플랫폼 조합에 다른 코드 분석 설정을 적용할 수 있습니다. 예를 들어, 디버그 빌드에 대해 프로젝트에 한 가지 규칙 집합을 적용 하 고 릴리스 빌드에 다른 집합을 적용 하도록 코드 분석을 지시할 수 있습니다.

## <a name="enabling-code-analysis"></a>코드 분석 사용

**Microsoft 코드 분석 사용** 및 **Clang 사용 설정** 옵션을 설정/해제 하 여 프로젝트에 대해 코드 분석을 사용 하도록 설정 하 고 **빌드 시 코드 분석 사용**을 선택 하 여 빌드에서 실행 되는 경우 추가로 구성할 수 있습니다. 예를 들어 **구성** 목록과 함께 디버그 빌드에 대해 코드 분석을 사용 하지 않도록 설정 하 고 릴리스 빌드에 대해 사용 하도록 설정할 수 있습니다.

코드 분석은 코드의 품질을 향상 시키고 일반적인 문제를 방지할 수 있도록 설계 되었습니다. 따라서 코드 분석을 사용 하지 않을 지 여부를 신중 하 게 고려해 야 합니다. 일반적으로 프로젝트에 적용 하지 않으려는 규칙 집합, 개별 규칙 또는 개별 검사를 사용 하지 않도록 설정 하는 것이 좋습니다.

## <a name="cmake-configuration"></a>CMake 구성

CMake 프로젝트에서 `enableMicrosoftCodeAnalysis` 값을 변경 하 고 `CMakeSettings.json` 내에서 키를 `enableClangTidyCodeAnalysis` 하 여 코드 분석을 활성화 하거나 비활성화 합니다. 자세한 내용은 [Visual Studio에서 Clang 사용](../code-quality/clang-tidy.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [관리 코드 품질 분석](../code-quality/code-analysis-for-managed-code-overview.md)
- [C/C++용 코드 분석 경고](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [코드에 대 C++ 한 규칙 집합](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Clang 사용](../code-quality/clang-tidy.md)
