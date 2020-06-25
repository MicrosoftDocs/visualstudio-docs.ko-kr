---
title: 체크 인 정책을 사용 하 여 프로젝트 규칙 집합 동기화
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e27987f7fa298ddcedf52a9f01a80f57d3d329f
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371783"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>방법: Azure DevOps 프로젝트 체크 인 정책을 사용 하 여 코드 프로젝트 규칙 집합 동기화

체크 인 정책에 대 한 규칙 집합에 지정 된 규칙을 하나 이상 포함 하는 규칙 집합을 지정 하 여 코드 프로젝트의 코드 분석 설정을 Azure DevOps 프로젝트에 대 한 체크 인 정책에 동기화 합니다. 개발자 리더가 체크 인 정책에 대 한 규칙 집합의 이름과 위치를 알려줄 수 있습니다. 다음 옵션 중 하나를 사용 하 여 프로젝트에 대 한 코드 분석이 올바른 규칙 집합을 사용 하는지 확인할 수 있습니다.

- 체크 인 정책에서 Microsoft 기본 제공 규칙 집합 중 하나를 사용 하는 경우 코드 프로젝트에 대 한 속성 대화 상자를 열고 코드 분석 페이지를 표시 한 다음 규칙 집합을 선택 합니다. Microsoft 표준 규칙 집합은 Visual Studio와 함께 자동으로 설치 되며, 읽기 전용으로 설정 되어 있으므로 편집 하면 안 됩니다. 규칙 집합을 편집 하지 않으면 정책 및 로컬 규칙 집합의 규칙이 일치 하도록 보장 됩니다.

- 체크 인 정책이 사용자 지정 규칙 집합을 사용 하는 경우 버전 제어에서 규칙 집합 파일에 대해 가져오기 작업을 수행 하 여 로컬 복사본을 만듭니다. 그런 다음 코드 프로젝트에 대 한 코드 분석 설정에서 해당 로컬 위치를 지정 합니다. 체크 인 정책에 대 한 규칙 집합이 최신 상태 이면 규칙이 일치 하도록 보장 됩니다.

     코드 프로젝트로 Azure DevOps 프로젝트 루트와 동일한 관계에 있는 로컬 폴더에 버전 제어 위치를 매핑하는 경우 규칙의 위치는 상대 경로를 사용 하 여 설정 됩니다. 상대 경로를 사용 하면 코드 분석에 대 한 코드 프로젝트 설정을 다른 컴퓨터로 이동할 수 있습니다.

- 코드 프로젝트에 대 한 체크 인 정책에 대 한 규칙 집합의 복사본을 사용자 지정 합니다. 새 규칙 집합에는 체크 인 정책의 모든 규칙과 포함 하려는 다른 규칙이 모두 포함 되어 있는지 확인 합니다. 규칙 집합에 체크 인 정책에 대 한 규칙 집합의 모든 규칙이 포함 되어 있는지 확인 해야 합니다.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Microsoft 표준 규칙 집합을 지정 하려면

1. **솔루션 탐색기**에서 코드 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. **코드 분석**을 클릭합니다.

::: moniker range="vs-2017"

3. **이 규칙 집합 실행** 목록에서 체크 인 정책 규칙 집합을 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

3. **활성 규칙** 목록에서 체크 인 정책 규칙 집합을 선택 합니다.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>사용자 지정 체크 인 정책 규칙 집합을 지정 하려면

1. 필요한 경우 체크 인 정책을 지정 하는 규칙 집합 파일에 대해 가져오기 작업을 수행 합니다.

2. **솔루션 탐색기**에서 코드 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

3. **코드 분석**을 클릭합니다.

::: moniker range="vs-2017"

4. **이 규칙 집합 실행** 목록에서을 클릭 **\<Browse>** 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. **활성 규칙** 목록에서를 클릭 **\<Browse>** 합니다.

::: moniker-end

5. **열기** 대화 상자에서 체크 인 정책 규칙 집합 파일을 지정 합니다.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>코드 프로젝트에 대 한 사용자 지정 규칙 집합을 만들려면

사용자 지정 규칙 집합을 만드는 방법에 대 한 자세한 내용은 [규칙 집합 사용자 지정](how-to-create-a-custom-rule-set.md)을 참조 하세요.
