---
title: 관리 코드 경고에 대한 코드 분석
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8238de0760f300b6fa418a5e3eb47eac3db77272
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509018"
---
# <a name="net-code-analysis-rules"></a>.NET 코드 분석 규칙
관리 코드 분석 도구는 관리 코드 라이브러리의 규칙 위반을 나타내는 경고를 제공합니다. 경고는 디자인, 지역화, 성능, 보안 등의 규칙 영역으로 구성됩니다. 각 경고는 관리 코드 분석 규칙을 위반했음을 나타냅니다. 이 섹션에서는 각 관리 코드 분석 경고에 대한 자세한 논의와 예제를 제공합니다.

 다음 표에서 각 경고에 대해 제공되는 정보의 형식을 보여 줍니다.

|항목|Description|
|----------|-----------------|
|형식|규칙의 TypeName입니다.|
|CheckId|규칙의 고유 식별자입니다. 소스에서 경고를 표시하지 않으려는 경우에 사용되는 CheckId 및 범주입니다.|
|범주|경고의 범주입니다.|
|주요 변경 내용|규칙의 위반에 대한 수정이 주요 변경 내용인지 여부입니다. 주요 변경 내용은 위반의 원인이 된 대상에 대해 종속성이 있으며 새로 수정된 버전으로 다시 컴파일되지 않거나 변경으로 인해 런타임에 실패할 수 있는 어셈블리를 의미합니다. 여러 픽스를 사용할 수 있고 하나 이상의 수정이 주요 변경 사항이 며 한 가지 픽스는 그렇지 않으면 ' 중단 ' 및 ' 중단 '이 모두 지정 됩니다.|
|원인|규칙에서 경고를 생성하게 만드는 특정 관리 코드입니다.|
|Description|경고 뒤에 있는 문제를 설명합니다.|
|위반 문제를 해결하는 방법|규칙을 충족하고 경고 생성을 방지하는 소스 코드 변경 방법을 설명합니다.|
|경고를 표시하지 않는 경우|규칙에서 경고를 표시하지 않아도 안전한 경우에 대해 설명합니다.|
|코드 예|규칙을 위반하는 예제와 규칙을 충족하는 수정된 예제입니다.|
|관련 경고|관련 경고입니다.|

## <a name="in-this-section"></a>섹션 내용

|범주|Description|
|-|-|
|[ID 별 규칙](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|RuleID의 모든 규칙을 나열 합니다.|
|[디자인 규칙](../code-quality/design-warnings.md)|.NET 디자인 지침에 지정 된 대로 올바른 라이브러리 디자인을 지 원하는 규칙|
|[설명서 규칙](../code-quality/documentation-warnings.md)|XML 문서 주석을 올바르게 사용 하 여 잘 문서화 된 라이브러리 디자인을 지 원하는 규칙|
|[전역화 규칙](../code-quality/globalization-warnings.md)|전 세계에서 사용할 수 있는 라이브러리 및 응용 프로그램을 지 원하는 규칙|
|[유지 관리 규칙](../code-quality/maintainability-warnings.md)|라이브러리 및 응용 프로그램 유지 관리를 지 원하는 규칙|
|[명명 규칙](../code-quality/naming-warnings.md)|.NET 디자인 지침의 명명 규칙 준수를 지 원하는 규칙|
|[성능 규칙](../code-quality/performance-warnings.md)|고성능 라이브러리 및 응용 프로그램을 지 원하는 규칙|
|[이식성 및 상호 운용성 규칙](../code-quality/interoperability-warnings.md)|여러 플랫폼 간의 이식성을 지 원하는 규칙과 COM 클라이언트와의 상호 작용을 지원 합니다.|
|[게시 규칙](../code-quality/publish-warnings.md)|적절 한 .NET 응용 프로그램 게시를 지 원하는 규칙|
|[안정성 규칙](../code-quality/reliability-warnings.md)|올바른 메모리 및 스레드 사용과 같은 라이브러리 및 응용 프로그램 안정성을 지 원하는 규칙|
|[보안 규칙](../code-quality/security-warnings.md)|더 안전한 라이브러리 및 응용 프로그램을 지 원하는 규칙|
|[사용 규칙](../code-quality/usage-warnings.md)|.NET의 적절 한 사용을 지 원하는 규칙|
