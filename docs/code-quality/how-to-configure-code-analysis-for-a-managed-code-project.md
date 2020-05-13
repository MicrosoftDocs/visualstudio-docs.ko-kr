---
title: 코드 분석 구성
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431354"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>방법: 관리 코드에 대한 레거시 분석 구성

Visual Studio에서 관리되는 코드 프로젝트에 적용할 코드 분석 [규칙 집합](../code-quality/rule-set-reference.md) 목록에서 선택할 수 있습니다. 기본적으로 Microsoft **최소 권장 규칙** 규칙 집합이 선택되지만 원하는 경우 다른 규칙 집합을 적용할 수 있습니다. 규칙 집합은 솔루션의 하나 또는 여러 프로젝트에 적용할 수 있습니다.

> [!NOTE]
> 이 문서는 [.NET 컴파일러 플랫폼 기반 코드 분석기가](use-roslyn-analyzers.md)아닌 레거시 분석에 적용됩니다.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET 프레임워크 프로젝트에 대한 규칙 집합 구성

1. 프로젝트의 속성 페이지에서 **코드 분석** 탭을 엽니다. 다음 방법 중 하나로 이 작업을 수행할 수 있습니다.

   - **솔루션 탐색기에서**프로젝트를 선택합니다. 메뉴 모음에서 > ** \<프로젝트 이름>** 대해 코드**분석 구성** **을** > 선택합니다.

   - **솔루션 탐색기에서** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성을**선택한 다음 **코드 분석** 탭을 선택합니다.

2. **구성** 및 **플랫폼** 목록에서 빌드 구성 및 대상 플랫폼을 선택합니다.

::: moniker range="vs-2017"

3. 선택한 구성을 사용하여 프로젝트를 빌드할 때마다 코드 분석을 실행하려면 **빌드에서 코드 분석 활성화를**선택합니다.  > **Run Code Analysis** >  **Analyze****또한 프로젝트 이름>실행 코드 분석 실행 코드 분석 분석을 선택하여 코드 분석을 \< **수동으로 실행할 수도 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. 선택한 구성을 사용하여 프로젝트를 빌드할 때마다 코드 분석을 실행하려면 **이진 분석기** 섹션에서 **빌드 시 실행을** 선택합니다. 레거시 코드 분석을 수동으로 실행할 수도 있고, 자세한 내용은 [관리 코드에 대해 레거시 코드 분석을 수동으로 실행하는 방법을 참조하세요.](how-to-run-legacy-code-analysis-manually-for-managed-code.md)

::: moniker-end

4. 생성된 코드에서 경고를 보려면 **생성된 코드에서 결과 표시 를** 선택 취소합니다.

    > [!NOTE]
    > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 양식이나 템플릿의 소스 코드를 보고 유지 관리할 수 있으며 덮어쓰지 않습니다.

::: moniker range="vs-2017"

5. 이 **규칙 집합 실행** 목록에서 다음 중 하나를 수행합니다.

::: moniker-end

::: moniker range=">=vs-2019"

5. 활성 **규칙** 목록에서 다음 중 하나를 수행합니다.

::: moniker-end

   - 사용할 규칙 집합을 선택합니다.

   - ** \<>찾아보기를** 선택하여 목록에 없는 기존 사용자 지정 규칙 집합을 찾습니다.

   - 사용자 [지정 규칙 집합을](../code-quality/how-to-create-a-custom-rule-set.md)정의합니다.

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>솔루션의 여러 프로젝트에 대한 규칙 집합 지정

기본적으로 솔루션의 관리되는 모든 *프로젝트에는 Microsoft 최소 권장 규칙* 코드 분석 규칙 집합이 할당됩니다. 솔루션에 대한 **속성** 대화 상자에서 솔루션의 프로젝트에 할당된 규칙 집합을 변경할 수 있습니다.

1. Visual Studio에서 솔루션을 엽니다.

2. **분석** 메뉴에서 **솔루션에 대한 코드 분석 구성을**선택합니다.

3. 필요한 경우 **공통 속성을**확장한 다음 **코드 분석 설정을**선택합니다.

4. 하나 이상의 프로젝트에 대한 규칙 집합을 지정할 수 있습니다.

    - 개별 프로젝트에 대한 규칙 집합을 지정하려면 프로젝트 이름을 선택합니다.

    - 여러 프로젝트에 대한 규칙 집합을 지정하려면 **Ctrl을** 길게 누르고 프로젝트 이름을 선택합니다.

    - 솔루션의 모든 프로젝트를 지정하려면 **Shift를** 길게 누르고 프로젝트 목록을 클릭합니다.

5. 프로젝트의 **규칙 집합** 필드를 선택한 다음 적용할 규칙 집합의 이름을 선택합니다.

## <a name="see-also"></a>참고 항목

- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)
