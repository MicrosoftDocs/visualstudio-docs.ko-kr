---
title: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7167368128cb5946118a7692c50c15109feb79a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371900"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>방법: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트

코드 분석 체크 인 정책을 사용 하 여 Azure DevOps 프로젝트의 모든 코드 프로젝트에 대해 코드 분석을 실행 하도록 요구할 수 있습니다. 코드 분석을 요구 하면 코드 베이스에 체크 인 한 코드의 품질을 향상 시킬 수 있습니다.

> [!NOTE]
> 이 기능은 Team Foundation Server를 사용 하는 경우에만 사용할 수 있습니다.

코드 분석 체크 인 정책은 프로젝트 설정에서 설정 되며 각 코드 프로젝트에 적용 됩니다. 코드 분석 실행은 코드 프로젝트에 대 한 프로젝트 (. 하지만에서는 .xxproj) 파일의 코드 프로젝트에 대해 구성 됩니다. 코드 분석 실행은 로컬 컴퓨터에서 수행 됩니다. 코드 분석 체크 인 정책을 사용 하도록 설정 하는 경우 체크 인 되는 코드 프로젝트의 파일은 마지막 편집 및 코드 분석 실행 후에 컴파일해야 합니다. 최소한 프로젝트 설정의 규칙은 변경 내용이 적용 된 컴퓨터에서 수행 되어야 합니다.

- 관리 코드의 경우 코드 분석 규칙의 하위 집합을 포함 하는 *규칙 집합* 을 지정 하 여 체크 인 정책을 설정 합니다.

- C/c + + 코드의 경우 Visual Studio 2017 버전 15.6 이전 버전에서는 체크 인 정책에 모든 코드 분석 규칙이 실행 되어야 합니다. 사전 프로세서 지시문을 추가 하 여 Azure DevOps 프로젝트에서 개별 코드 프로젝트에 대 한 특정 규칙을 사용 하지 않도록 설정할 수 있습니다. 15.7 이상에서는 **/analyze: 규칙 집합** 을 사용 하 여 실행할 규칙을 지정할 수 있습니다. 자세한 내용은 [규칙 집합을 사용 하 여 실행할 c + + 규칙 지정](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)을 참조 하세요.

관리 코드에 대 한 체크 인 정책을 지정 하 고 나면 팀 멤버가 코드 프로젝트의 코드 분석 설정을 Azure DevOps 프로젝트 정책 설정에 동기화 할 수 있습니다.

## <a name="to-open-the-check-in-policy-editor"></a>체크 인 정책 편집기를 열려면

1. 팀 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 **프로젝트 설정**을 가리킨 다음 **소스 제어**를 클릭 합니다.

1. **원본 제어** 대화 상자에서 **체크 인 정책** 탭을 선택 합니다.

1. 다음 중 하나를 수행합니다.

    - **추가** 를 클릭 하 여 새 체크 인 정책을 만듭니다.

    - 정책 **유형** 목록에서 기존 **코드 분석** 항목을 두 번 클릭 하 여 정책을 변경 합니다.

## <a name="to-set-policy-options"></a>정책 옵션을 설정 하려면

다음 옵션을 선택 하거나 선택 취소 합니다.

|옵션|설명|
|------------|-----------------|
|**현재 솔루션에 속하는 파일만 포함 하도록 체크 인을 적용 합니다.**|코드 분석은 솔루션 및 프로젝트 구성 파일에 지정 된 파일에 대해서만 실행할 수 있습니다. 이 정책은 솔루션의 일부인 모든 코드가 분석 됨을 보장 합니다.|
|**C/c + + 코드 분석 (/analyze) 적용**|코드 분석을 체크 인하기 전에 실행 하려면 모든 C 또는 c + + 프로젝트를/analyze 컴파일러 옵션으로 빌드해야 합니다.|
|**관리 코드에 대 한 코드 분석 적용**|모든 관리 되는 프로젝트를 체크 인하기 전에 코드 분석을 실행 하 고 빌드해야 합니다.|

## <a name="to-specify-a-managed-rule-set"></a>관리 되는 규칙 집합을 지정 하려면

**이 규칙 집합 실행** 목록에서 다음 방법 중 하나를 사용 합니다.

- Microsoft 표준 규칙 집합을 선택 합니다.

- 을 클릭 하 여 사용자 지정 규칙 집합을 선택 **\<Select Rule Set from Source Control...>** 합니다. 그런 다음 소스 제어 브라우저에서 규칙 집합의 버전 제어 경로를 입력 합니다. 버전 제어 경로의 구문은 다음과 같습니다.

   **$/** `TeamProjectName` **/** `VersionControlPath`

사용자 지정 체크 인 정책 규칙 집합을 만들고 구현 하는 방법에 대 한 자세한 내용은 [관리 코드에 대 한 사용자 지정 체크 인 정책 구현](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [관리 코드에 대한 사용자 지정 코드 분석 체크 인 정책 구현](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
