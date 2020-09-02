---
title: '방법: C + + 프로젝트에 대 한 코드 분석 속성 설정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277990"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>방법: C/C++ 프로젝트의 코드 분석 속성 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 분석 도구에서 프로젝트의 각 구성에서 코드를 분석 하는 데 사용 하는 규칙을 구성할 수 있습니다. 또한 타사 도구를 통해 생성 되 고 프로젝트에 추가 된 코드에서 발생 하는 경고를 표시 하지 않도록 코드 분석을 지시할 수 있습니다.  
  
## <a name="code-analysis-property-page"></a>코드 분석 속성 페이지  
 **코드 분석** 속성 페이지에는 프로젝트에 대 한 모든 코드 분석 구성 설정이 포함 되어 있습니다. **솔루션 탐색기**에서 프로젝트에 대 한 코드 분석 속성 페이지를 열려면 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 그런 다음 **구성 속성** 을 확장 하 고 **코드 분석** 탭을 선택 합니다.  
  
## <a name="project-configuration-and-platform"></a>프로젝트 구성 및 플랫폼  
 **구성** 목록 및 **플랫폼** 목록을 사용 하면 다른 프로젝트 구성 및 플랫폼 조합에 다른 코드 분석 설정을 적용할 수 있습니다. 예를 들어, 디버그 빌드에 대해 프로젝트에 한 가지 규칙 집합을 적용 하 고 릴리스 빌드에 다른 집합을 적용 하도록 코드 분석을 지시할 수 있습니다.  
  
## <a name="enabling-code-analysis"></a>코드 분석 사용  
 **빌드할 때 C/c + +에 코드 분석 사용**을 선택 하 여 프로젝트에 대해 코드 분석을 사용할지 여부를 결정할 수 있습니다. 예를 들어 **구성** 목록과 함께 디버그 빌드에 대해 코드 분석을 사용 하지 않도록 설정 하 고 릴리스 빌드에 대해 사용 하도록 설정할 수 있습니다.  
  
 프로젝트에 관리 코드를 포함 하는 경우 **빌드 시 코드 분석 사용**을 선택 하 여 코드 분석을 사용할지 여부를 결정할 수 있습니다.  
  
 코드 분석은 코드의 품질을 향상 시키고 일반적인 문제를 방지할 수 있도록 설계 되었습니다. 따라서 코드 분석을 사용 하지 않을 지 여부를 신중 하 게 고려해 야 합니다. 일반적으로 프로젝트에 적용 하지 않으려는 규칙 집합 또는 개별 규칙을 사용 하지 않도록 설정 하는 것이 좋습니다.  
  
## <a name="generated-code"></a>생성된 코드  
 개발자는 자주 도구를 사용 하 여 응용 프로그램을 빠르게 개발할 수 있습니다. 이러한 도구는 프로젝트에 추가 되는 코드를 생성할 수 있습니다. 코드 분석이 생성 된 코드에서 검색 하는 규칙 위반을 확인 하는 것이 좋습니다. 그러나 코드를 유지 관리 하지 않으려는 경우에는이를 표시 하지 않을 수 있습니다.  
  
 **일반** 속성 페이지의 **생성 된 코드에서 결과 표시 안 함** 확인란을 사용 하면 타사 도구에서 생성 되는 관리 코드에서 코드 분석 경고를 표시할지 여부를 선택할 수 있습니다.  
  
## <a name="rule-sets"></a>규칙 집합  
 프로젝트에 관리 코드를 포함 하는 경우 **이 규칙 집합 실행** 목록에서 규칙 집합을 선택 하 여 코드 분석에 적용할 규칙을 선택할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 품질 분석](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/c + + 경고에 대 한 코드 분석](../code-quality/code-analysis-for-c-cpp-warnings.md)
