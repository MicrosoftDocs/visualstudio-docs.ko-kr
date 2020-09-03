---
title: 규칙 집합을 사용 하 여 코드 분석 규칙 그룹화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603475"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>규칙 집합을 사용하여 코드 분석 규칙 그룹화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, 또는에서 코드 분석을 구성 하 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 는 경우 [!INCLUDE[vsPro](../includes/vspro-md.md)] Microsoft 기본 제공 *규칙 집합*목록에서 선택할 수 있습니다. 규칙 집합은 대상 문제 및 특정 조건을 식별 하는 코드 분석 규칙의 논리적 그룹입니다. 예를 들어 공개적으로 사용 가능한 API에 대한 코드를 검색하도록 디자인된 규칙 집합을 적용하거나 최소한의 권장 규칙만 포함하는 규칙 집합을 적용할 수 있습니다. 또한 모든 규칙이 포함된 규칙 집합을 적용할 수도 있습니다.

 규칙을 추가 하거나 삭제 하 여 규칙 집합을 사용자 지정 하거나 **오류 목록** 창에 경고 또는 오류로 표시 되도록 규칙을 변경할 수 있습니다. 사용자 지정 된 규칙 집합은 특정 개발 환경에 대 한 요구 사항을 충족할 수 있습니다. 규칙 집합을 사용자 지정할 때 규칙 집합 페이지에서는 프로세스에 도움이 되는 검색 및 필터링 도구를 제공 합니다.

## <a name="common-tasks"></a>일반 태스크

|작업|관련 내용|
|----------|---------------------|
|**실습 실습:** 코드 분석 도구를 사용 하 여 간단한 .NET Framework 응용 프로그램에서 문제를 찾고 수정할 수 있는 사용자 지정 규칙 집합을 지정 합니다.|-   [연습: 사용자 지정 규칙 집합 구성 및 사용](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**프로젝트에 대 한 코드 분석 구성:** 프로젝트, 웹 사이트 또는 솔루션에 대 한 기존 규칙 집합을 선택 합니다.|-   [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [규칙 집합을 사용 하 여 실행할 c + + 규칙 지정](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [방법: ASP.NET 웹 응용 프로그램에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [방법: 솔루션의 여러 프로젝트에 대 한 규칙 집합 지정](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**규칙 집합 사용자 지정:** 프로젝트에 적용할 규칙을 지정 합니다.|-   [사용자 지정 규칙 집합 만들기](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**기본 제공 규칙 집합 이해:** 기본 제공 규칙 집합을 구성 하는 코드 분석 규칙을 확인 합니다.|-   [코드 분석 규칙 집합 참조](../code-quality/code-analysis-rule-set-reference.md)|
|**Team Foundation Server와 코드 분석 통합:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 체크 인 정책을 사용 하면 개발 팀이 모든 코드 체크 인이 일반적인 코드 분석 표준 집합을 충족 하는지 확인할 수 있습니다.|-   [방법: 코드 프로젝트 규칙 집합을 팀 프로젝트 체크 인 정책과 동기화](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
