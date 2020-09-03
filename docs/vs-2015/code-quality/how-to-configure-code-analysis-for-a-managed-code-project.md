---
title: '방법: 관리 코드 프로젝트에 대 한 코드 분석 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658853"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>방법: 관리 코드 프로젝트에 대한 코드 분석 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 및에서는 [!INCLUDE[vsPro](../includes/vspro-md.md)] 코드 분석 *규칙 집합* 목록에서 선택 하 여 관리 코드 프로젝트에 적용할 수 있습니다. 기본 규칙 집합은 Microsoft 최소 권장 규칙입니다. 프로젝트 또는 솔루션의 모든 프로젝트에 다른 규칙 집합을 적용할 수 있습니다.

> [!NOTE]
> ASP.NET 웹 응용 프로그램에 대 한 규칙 집합을 구성 하는 방법에 대 한 자세한 내용은 [방법: ASP.NET 웹 응용 프로그램에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)을 참조 하세요.

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework 프로젝트에 대 한 규칙 집합을 구성 하려면

1. **솔루션 탐색기**에서 프로젝트를 클릭 합니다.

2. **분석** 메뉴에서 *ProjectName* **에 대 한 코드 분석 구성** 을 클릭 합니다.

3. **구성** 및 **플랫폼** 목록에서 빌드 구성 및 대상 플랫폼을 클릭 합니다.

4. 선택한 구성을 사용 하 여 프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 **빌드 시 코드 분석 사용 (CODE_ANALYSIS 상수 정의)** 확인란을 선택 합니다. **분석** 메뉴를 열고 *ProjectName* **에 대해 코드 분석 실행** 을 클릭 하 여 코드 분석을 수동으로 실행할 수도 있습니다.

5. 기본적으로 외부 도구에 의해 자동으로 생성된 코드에서 발생한 경고는 코드 분석 시 보고되지 않습니다. 생성 된 코드에서 발생 한 경고를 보려면 **생성 된 코드에서 결과 표시 안 함** 확인란의 선택을 취소 합니다.

    > [!NOTE]
    > 이 옵션을 선택하더라도 폼 및 템플릿에 오류와 경고가 나타날 경우에는 생성된 코드에서 발생한 코드 분석 오류 및 경고가 계속 표시됩니다. 폼이나 템플릿의 소스 코드를 볼 수도 있고 유지 관리할 수도 있습니다.

6. **이 규칙 집합 실행** 목록에서 다음 중 하나를 수행 합니다.

    - 사용할 규칙 집합을 클릭 합니다.

    - **\<Browse...>** 목록에 없는 기존 사용자 지정 규칙 집합을 지정 하려면 클릭 합니다.

    - 사용할 규칙 집합을 선택합니다.

         자세한 내용은 [사용자 지정 규칙 집합 만들기](../code-quality/creating-custom-code-analysis-rule-sets.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [연습: 사용자 지정 규칙 집합 구성 및 사용](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
