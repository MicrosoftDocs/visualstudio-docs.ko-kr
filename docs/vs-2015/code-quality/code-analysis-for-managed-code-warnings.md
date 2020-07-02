---
title: 관리 코드 경고에 대 한 코드 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5294840e4669f28f4e8a04978274ad130d1397ee
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535735"
---
# <a name="code-analysis-for-managed-code-warnings"></a>관리 코드 경고에 대한 코드 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 코드 분석 도구는 관리 코드 라이브러리의 규칙 위반을 나타내는 경고를 제공합니다. 경고는 디자인, 지역화, 성능, 보안 등의 규칙 영역으로 구성됩니다. 각 경고는 관리 코드 분석 규칙을 위반했음을 나타냅니다. 이 섹션에서는 각 관리 코드 분석 경고에 대한 자세한 논의와 예제를 제공합니다.

 다음 표에서 각 경고에 대해 제공되는 정보의 형식을 보여 줍니다.

|항목|설명|
|----------|-----------------|
|형식|규칙의 TypeName입니다.|
|CheckId|규칙의 고유 식별자입니다. 소스에서 경고를 표시하지 않으려는 경우에 사용되는 CheckId 및 범주입니다.|
|범주|경고의 범주입니다.|
|변경 수준|규칙의 위반에 대한 수정이 주요 변경 내용인지 여부입니다. 주요 변경 내용은 위반의 원인이 된 대상에 대해 종속성이 있으며 새로 수정된 버전으로 다시 컴파일되지 않거나 변경으로 인해 런타임에 실패할 수 있는 어셈블리를 의미합니다. 여러 수정 사항을 사용할 수 있고 그중에 주요 변경 내용과 그렇지 않은 것이 각각 하나 이상 있는 경우에는 '주요 변경'과 '주요 변경 아님'이 모두 지정됩니다.|
|원인|규칙에서 경고를 생성하게 만드는 특정 관리 코드입니다.|
|설명|경고 뒤에 있는 문제를 설명합니다.|
|위반 문제를 해결하는 방법|규칙을 충족하고 경고 생성을 방지하는 소스 코드 변경 방법을 설명합니다.|
|경고를 표시하지 않는 경우|규칙에서 경고를 표시하지 않아도 안전한 경우에 대해 설명합니다.|
|코드 예|규칙을 위반하는 예제와 규칙을 충족하는 수정된 예제입니다.|
|관련 경고|관련 경고입니다.|

## <a name="in-this-section"></a>섹션 내용

|항목|값|
|-|-|
|[CheckId 별 경고](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|CheckId별로 모든 경고 나열|
|[암호화 경고](../code-quality/cryptography-warnings.md)|암호화를 올바르게 사용하여 더 안전한 라이브러리 및 애플리케이션을 지원하는 경고입니다.|
|[디자인 경고](../code-quality/design-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 디자인 지침에 지정된 것과 같이 올바른 라이브러리 디자인을 지원하는 경고입니다.|
|[세계화 경고](../code-quality/globalization-warnings.md)|지역화에 대비한 라이브러리 및 애플리케이션을 지원하는 경고입니다.|
|[상호 운용성 경고](../code-quality/interoperability-warnings.md)|COM 클라이언트와의 상호 작용을 지원하는 경고입니다.|
|[유지 관리 경고](../code-quality/maintainability-warnings.md)|라이브러리 및 애플리케이션 유지 관리를 지원하는 경고입니다.|
|[이동성 경고](../code-quality/mobility-warnings.md)|효율적인 전원 사용을 지원하는 경고입니다.|
|[이름 지정 경고](../code-quality/naming-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 디자인 지침의 명명 규칙 준수를 지원하는 경고입니다.|
|[성능 경고](../code-quality/performance-warnings.md)|고성능 라이브러리 및 애플리케이션을 지원하는 경고입니다.|
|[이식성 경고](../code-quality/portability-warnings.md)|여러 플랫폼 간의 이식성을 지원하는 경고입니다.|
|[안정성 경고](../code-quality/reliability-warnings.md)|올바른 메모리 및 스레드 사용과 같은 라이브러리 및 애플리케이션 안정성을 지원하는 경고입니다.|
|[보안 경고](../code-quality/security-warnings.md)|더 안전한 라이브러리 및 애플리케이션을 지원하는 경고입니다.|
|[사용 경고](../code-quality/usage-warnings.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 적절한 사용을 지원하는 경고입니다.|
|[코드 분석 정책 오류](../code-quality/code-analysis-policy-errors.md)|체크 인할 때 코드 분석 정책이 충족되지 않은 경우에 발생하는 오류입니다.|
