---
title: 코드 분석 구성
ms.date: 04/04/2018
ms.topic: how-to
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
ms.openlocfilehash: a8c922f0fc952cede53b9961e2e772e71a19cbb9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371952"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 레거시 분석 구성

Visual Studio에서 코드 분석 [규칙 집합](../code-quality/rule-set-reference.md) 목록 중에서 선택 하 여 관리 코드 프로젝트에 적용할 수 있습니다. 기본적으로 **Microsoft 최소 권장 규칙** 규칙 집합이 선택 되어 있지만 원하는 경우 다른 규칙 집합을 적용할 수 있습니다. 규칙 집합은 솔루션의 하나 또는 여러 프로젝트에 적용할 수 있습니다.

> [!NOTE]
> 이 문서는 레거시 분석에 적용 되며 [.NET Compiler Platform 기반 코드 분석기](use-roslyn-analyzers.md)에는 적용 되지 않습니다.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework 프로젝트에 대 한 규칙 집합 구성

1. 프로젝트의 속성 페이지에서 **코드 분석** 탭을 엽니다. 다음 방법 중 하나로 이 작업을 수행할 수 있습니다.

   - **솔루션 탐색기**에서 프로젝트를 선택 합니다. 메뉴 모음에서 **분석**  >  **구성 코드 분석**  >  **을 \<projectname> **선택 합니다.

   - **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택한 다음 **코드 분석** 탭을 선택 합니다.

2. **구성** 및 **플랫폼** 목록에서 빌드 구성 및 대상 플랫폼을 선택 합니다.

::: moniker range="vs-2017"

3. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **빌드 시 코드 분석 사용**을 선택 합니다. **분석**  >  **실행 코드 분석**실행  >  **코드 분석 실행을 \<projectname> **선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **이진 분석기** 섹션에서 **빌드 시 실행** 을 선택 합니다. 레거시 코드 분석을 수동으로 실행할 수도 있습니다. 자세한 내용은 [방법: 관리 코드에 대 한 레거시 코드 분석 수동 실행](how-to-run-legacy-code-analysis-manually-for-managed-code.md) 을 참조 하세요.

::: moniker-end

4. 생성 된 코드에서 발생 한 경고를 보려면 **생성 된 코드에서 결과 표시 안 함** 확인란의 선택을 취소 합니다.

    > [!NOTE]
    > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 양식이 나 템플릿에 대 한 소스 코드를 보고 유지 관리할 수 있으며 해당 코드를 덮어쓰지 않습니다.

::: moniker range="vs-2017"

5. **이 규칙 집합 실행** 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

5. **활성 규칙** 목록에서 다음 중 하나를 수행 합니다.

::: moniker-end

   - 사용할 규칙 집합을 선택 합니다.

   - **\<Browse>** 목록에 없는 기존 사용자 지정 규칙 집합을 찾으려면 선택 합니다.

   - [사용자 지정 규칙 집합](../code-quality/how-to-create-a-custom-rule-set.md)을 정의 합니다.

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>솔루션의 여러 프로젝트에 대 한 규칙 집합 지정

기본적으로 솔루션의 모든 관리 되는 프로젝트에는 *Microsoft 최소 권장 규칙* 코드 분석 규칙 집합이 할당 됩니다. 솔루션에 대 한 **속성** 대화 상자에서 솔루션의 프로젝트에 할당 된 규칙 집합을 변경할 수 있습니다.

1. Visual Studio에서 솔루션을 엽니다.

2. **분석** 메뉴에서 **솔루션에 대 한 코드 분석 구성**을 선택 합니다.

3. 필요한 경우 **공용 속성**을 확장 한 다음 **코드 분석 설정**을 선택 합니다.

4. 하나 이상의 프로젝트에 대 한 규칙 집합을 지정할 수 있습니다.

    - 개별 프로젝트에 대 한 규칙 집합을 지정 하려면 프로젝트 이름을 선택 합니다.

    - 여러 프로젝트에 대 한 규칙 집합을 지정 하려면 **Ctrl 키** 를 누른 상태에서 프로젝트 이름을 선택 합니다.

    - 솔루션의 모든 프로젝트를 지정 하려면 **Shift 키** 를 누른 채 프로젝트 목록을 클릭 합니다.

5. 프로젝트의 **규칙 집합** 필드를 선택한 다음 적용 하려는 규칙 집합의 이름을 선택 합니다.

## <a name="see-also"></a>참조

- [코드 분석 규칙 집합 참조](../code-quality/rule-set-reference.md)
