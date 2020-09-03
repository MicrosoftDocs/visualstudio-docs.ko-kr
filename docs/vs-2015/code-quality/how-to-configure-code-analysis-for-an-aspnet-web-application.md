---
title: '방법: ASP.NET 웹 응용 프로그램에 대 한 코드 분석 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657459"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>방법: ASP.NET 웹 애플리케이션에 대한 코드 분석 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]및에서는 [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] 코드 분석 *규칙 집합* 목록에서 선택 하 여 웹 응용 프로그램에 적용할 수 있습니다 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . 기본 규칙 집합은 Microsoft Mininimum 권장 규칙입니다. 다른 규칙 집합을 선택 하 여 웹 사이트에 적용할 수 있습니다.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>ASP.NET 페이지 프레임워크 프로젝트에 대한 규칙 집합을 구성하려면

1. **솔루션 탐색기**에서 웹 사이트를 선택 합니다.

2. **분석** 메뉴에서 **웹 사이트에 대 한 코드 분석 구성**을 클릭 합니다.

3. 솔루션을 선택 하 고 솔루션에 프로젝트가 두 개 이상 있는 경우 **구성** 및 **플랫폼** 목록에서 빌드 구성 및 대상 운영 체제를 선택 합니다.

4. 솔루션의 각 프로젝트에 대해 **규칙 집합** 열을 클릭 한 다음 실행할 규칙 집합의 이름을 클릭 합니다.

5. 기본적으로 코드 분석은 솔루션의 모든 프로젝트에 대해 실행 됩니다. 특정 프로젝트에 대해 코드 분석을 사용 하지 않거나 사용 하도록 설정 하려면 다음 단계를 수행 합니다.

    1. 프로젝트 이름을 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 합니다.

    2. **코드 분석 사용** 확인란을 선택 하거나 선택 취소 합니다. **분석** 메뉴에서 **웹 사이트에 대해 코드 분석 실행** 을 선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다.

6. **이 규칙 집합 실행** 드롭다운 목록에서 다음 단계를 수행 합니다.

    - 사용할 규칙 집합을 선택 합니다.

    - **\<Browse>** 목록에 없는 기존 사용자 지정 규칙 집합을 지정 하려면 선택 합니다.

    - 사용할 규칙 집합을 선택합니다. 자세한 내용은 [사용자 지정 규칙 집합 만들기](../code-quality/creating-custom-code-analysis-rule-sets.md)를 참조 하세요.
