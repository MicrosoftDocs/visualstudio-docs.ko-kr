---
title: '빠른 시작: C/C + +에 대 한 코드 분석 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278486"
---
# <a name="quick-start-code-analysis-for-cc"></a>퀵 스타트: C/C++용 코드 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C 또는 C++ 코드에 대한 코드 분석을 정기적으로 실행하여 애플리케이션의 품질을 향상시킬 수 있습니다. 이 테스트를 통해 발견 하기 어려운 결함 또는 프로그래밍 관행의 위반의 일반적인 문제를 찾을 수 있습니다. 코드 분석은 유효하지만 해당 코드를 사용하는 당사자나 다른 사용자에게 계속 문제를 일으킬 수 있는 특정 코드 패턴을 검색하므로, 코드 분석 경고는 컴파일러 오류 및 경고와 다릅니다.  
  
## <a name="in-this-topic"></a>항목 내용  
  
- [프로젝트에 대한 규칙 집합 구성](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [코드 분석 실행](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [코드 분석 경고를 분석하고 해결합니다.](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [코드 분석 경고 표시하지 않기](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [코드 분석 경고에 대한 작업 항목 만들기](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [코드 분석 결과 검색 및 필터링](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="configure-rule-sets-for-a-project"></a><a name="BKMK_ConfigureRuleSets"></a> 프로젝트에 대 한 규칙 집합 구성  
  
1. **솔루션 탐색기**에서 프로젝트 이름에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.  
  
2. 다음 단계는 선택 사항입니다.  
  
    1. **구성** 및 **플랫폼** 목록에서 빌드 구성 및 대상 플랫폼을 선택 합니다.  
  
    2. 기본적으로 외부 도구에 의해 자동으로 생성된 코드에서 발생한 경고는 코드 분석 시 보고되지 않습니다. 생성 된 코드에서 발생 한 경고를 보려면 **생성 된 코드에서 결과 표시 안 함** 확인란의 선택을 취소 합니다.  
  
        > [!NOTE]
        > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 폼이나 템플릿의 소스 코드를 볼 수도 있고 유지 관리할 수도 있습니다.  
  
3. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **빌드할 때 C/c + +에 코드 분석 사용** 확인란을 선택 합니다. **분석** 메뉴를 열고 *ProjectName* **에 대해 코드 분석 실행** 을 선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다.  
  
4. **이 규칙 집합 실행** 목록에서 다음 중 하나를 수행 합니다.  
  
    - 사용할 규칙 집합을 선택합니다.  
  
    - **\<Browse...>** 목록에 없는 기존 사용자 지정 규칙 집합을 지정 하려면 선택 합니다.  
  
    - 사용할 규칙 집합을 선택합니다.  
  
         자세한 내용은 [사용자 지정 규칙 집합 만들기](../code-quality/creating-custom-code-analysis-rule-sets.md)를 참조 하세요.  
  
### <a name="standard-cc-rule-sets"></a>표준 C/C++ 규칙 집합  
 Visual Studio에는 네이티브 코드에 대한 두 가지 표준 규칙 집합이 포함되어 있습니다.  
  
|규칙 집합|설명|  
|--------------|-----------------|  
|Microsoft 네이티브 최소 권장 규칙|이러한 규칙은 잠재적 보안 허점 및 애플리케이션 충돌을 포함하여 네이티브 코드의 가장 중요한 문제 설정에 중점을 둡니다. 네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.|  
|Microsoft 네이티브 권장 규칙|이 규칙 집합에서는 다양한 문제를 다룹니다. Microsoft 기본 최소 권장 규칙의 모든 규칙을 포함합니다.|  
  
## <a name="run-code-analysis"></a><a name="BKMK_Run"></a> 코드 분석 실행  
 프로젝트 속성 페이지의 코드 분석 페이지에서 프로젝트를 빌드할 때마다 실행할 코드 분석을 구성할 수 있습니다. 수동으로 코드 분석을 실행할 수도 있습니다.  
  
 솔루션에 대한 코드 분석을 실행하려면  
  
- **빌드** 메뉴에서 **솔루션에서 코드 분석 실행**을 선택합니다.  
  
  프로젝트에 대한 코드 분석을 실행하려면  
  
- 솔루션 탐색기에서 프로젝트 이름을 선택합니다.  
  
- **빌드** 메뉴에서 *프로젝트 이름* **에 대해 코드 분석 실행** 을 선택 합니다.  
  
  프로젝트 또는 솔루션이 컴파일되고 코드 분석이 실행됩니다. 코드 분석 창에 결과가 나타납니다.  
  
## <a name="analyze-and-resolve-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> 코드 분석 경고 분석 및 해결  
 특정 경고를 분석하려면 코드 분석 창에서 경고 제목을 선택합니다. 경고가 확장되어 문제에 대한 자세한 정보가 표시됩니다. 가능한 경우 코드 분석에서는 경고를 발생시킨 분석 논리와 줄 번호를 표시합니다. 문제의 가능한 해결 방법을 비롯하여 경고에 대한 자세한 내용을 보려면 경고 ID를 선택하여 메시지에 대한 MSND 라이브러리의 도움말 항목을 표시하세요.  
  
 경고를 확장하면 Visual Studio 코드 편집기에 경고를 발생시킨 코드 줄이 강조 표시됩니다.  
  
 문제를 파악한 후 코드에서 해결할 수 있습니다. 그런 다음 코드 분석을 다시 실행하여 코드 분석 창에 더 이상 경고가 나타나지 않는지와 수정으로 인해 새로운 경고가 발생하지 않는지 확인합니다.  
  
> [!TIP]
> 코드 분석 창에서 코드 분석을 다시 실행할 수 있습니다. **분석 단추를** 선택 하 고 분석 범위를 선택 합니다. 전체 솔루션 또는 선택한 프로젝트에 대한 분석을 다시 실행할 수 있습니다.  
  
## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> 코드 분석 경고 표시 안 함  
 코드 분석 경고를 수정하지 않도록 결정하는 경우가 있습니다. 경고를 해결하려면 코드의 실제 구현에서 문제가 발생할 가능성과 관련하여 너무 많은 기록이 필요하다고 판단할 수 있습니다. 또는 경고에 사용되는 분석이 특정 컨텍스트에 적절하지 않다고 판단할 수도 있습니다. 코드 분석 창에 개별 경고가 나타나지 않도록 개별 경고를 표시하지 않을 수 있습니다.  
  
 경고를 표시하지 않으려면 다음을 수행합니다.  
  
1. 자세한 정보가 표시되지 않으면 경고 제목을 선택하여 확장합니다.  
  
2. 경고 아래쪽에서 **작업** 링크를 선택합니다.  
  
3. **메시지 표시 안 함** 을 선택한 다음 **원본에서를**선택 합니다.  
  
   메시지를 표시 하지 않으면 `#pragma warning (disable:` *WarningId* `)` 코드 줄에 대 한 경고를 표시 하지 않는 않는 warningid가 삽입 됩니다.  
  
## <a name="creating-work-items-for-code-analysis-warnings"></a><a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> 코드 분석 경고에 대 한 작업 항목 만들기  
 작업 항목 추적 기능을 사용하여 Visual Studio에서 버그를 기록할 수 있습니다. 이 기능을 사용하려면 Team Foundation Server 인스턴스에 연결해야 합니다.  
  
 **하나 이상의 C/C++ 코드 경고에 대한 작업 항목을 만들려면**  
  
1. 코드 분석 창에서 경고를 확장하고 선택합니다.  
  
2. 경고에 대 한 바로 가기 메뉴에서 **작업 항목 만들기**를 선택한 다음 작업 항목 형식을 선택 합니다.  
  
3. Visual Studio에서 선택한 경고에 대한 단일 작업 항목을 만들고 IDE의 문서 창에 작업 항목을 표시합니다.  
  
4. 추가 정보를 추가한 다음 **작업 항목 저장**을 선택 합니다.  
  
## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> 코드 분석 결과 검색 및 필터링  
 긴 경고 메시지 목록을 검색하고 다중 프로젝트 솔루션에서 경고를 필터링할 수 있습니다.  
  
1. **제목 또는 경고 id를 기준으로 경고를 필터링 하려면** **필터** 텍스트 상자에 키워드를 입력 합니다.  
  
2. **프로젝트별로 경고를 필터링 하려면**: 다중 프로젝트 솔루션에서 코드 분석 창의 오른쪽 위에 있는 목록에서 하나 이상의 프로젝트를 선택 합니다. 솔루션 이름을 선택하면 모든 경고가 표시됩니다.  
  
3. **심각도 별로 경고를 필터링 하려면**: 기본적으로 코드 분석 메시지에는 **경고**의 심각도가 할당 됩니다. 사용자 지정 규칙 집합에서 하나 이상의 메시지 심각도를 **오류로** 할당할 수 있습니다. 각 심각도가 할당 된 메시지만 표시 하려면 **경고** 또는 **오류** 를 선택 합니다. 모든 메시지를 표시 하려면 **모두** 를 선택 합니다.
