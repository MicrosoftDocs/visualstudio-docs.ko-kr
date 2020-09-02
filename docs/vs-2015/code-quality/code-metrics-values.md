---
title: 코드 메트릭 값 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667731"
---
# <a name="code-metrics-values"></a>코드 메트릭 값
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 메트릭은 개발자가 개발 중인 코드에 대해 더 정확히 파악할 수 있도록 하는 소프트웨어 측정 방법입니다. 개발자는 코드 메트릭을 활용 하 여 수정 하거나 더 철저 하 게 테스트 해야 하는 형식 및/또는 메서드를 이해할 수 있습니다. 개발 팀은 잠재적 위험을 식별 하 고, 프로젝트의 현재 상태를 파악 하 고, 소프트웨어 개발 과정에서 진행 상황을 추적할 수 있습니다.

## <a name="software-measurements"></a>소프트웨어 측정
 다음 목록에서는를 계산 하는 코드 메트릭 결과를 보여 줍니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

- **유지 관리 인덱스** – 코드를 유지 관리 하는 상대적 편의성을 나타내는 0에서 100 사이의 인덱스 값을 계산 합니다. 값이 높으면 유지 관리 효율성을 향상 시키는 것입니다. 색으로 구분 된 등급을 사용 하 여 코드에서 문제 지점을 빠르게 식별할 수 있습니다. 녹색 등급은 20에서 100 사이이 고 코드에 적절 한 유지 관리 가능성을 나타냅니다. 노랑 등급은 10과 19 사이 이며, 코드의 유지 관리가 보통 임을 나타냅니다. 빨간색 등급은 0에서 9 사이의 등급 이며, 낮은 유지 관리를 나타냅니다.

- **순환 복잡성** – 코드의 구조적 복잡성을 측정 합니다. 프로그램 흐름의 다른 코드 경로 수를 계산 하 여 생성 됩니다. 복잡 한 제어 흐름을 포함 하는 프로그램은 코드 검사를 수행 하는 데 더 많은 테스트가 필요 하며,이는 유지 관리가 더 떨어집니다.

    > [!NOTE]
    > 일부 경우에는의 메서드에 대 한 순환 복잡성 계산이 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 이전 버전과 다릅니다. 자세한 내용은 [코드 메트릭 문제 해결](../code-quality/troubleshooting-code-metrics-issues.md)의 "Visual Studio 2010 코드 복잡성 계산의 변경 내용" 섹션을 참조 하세요.

- **상속 수준** – 클래스 계층 구조의 루트로 확장 되는 클래스 정의의 수를 나타냅니다. 계층 구조를 심층적으로 하 여 특정 메서드와 필드가 정의 되거나 재정의 되는 위치를 이해 하는 것이 어려울 수 있습니다.

- **클래스 결합** – 매개 변수, 지역 변수, 반환 형식, 메서드 호출, 제네릭 또는 템플릿 인스턴스화, 기본 클래스, 인터페이스 구현, 외부 형식에 정의 된 필드 및 특성 데코레이션을 통해 고유 클래스에 대 한 결합을 측정 합니다. 좋은 소프트웨어 디자인은 유형과 메서드가 높은 응집 및 낮은 결합을 가져야 함을 나타냅니다. 높은 결합은 다른 형식에 대 한 많은 상호 종속성으로 인해 재사용 및 유지 관리가 어려운 디자인을 나타냅니다.

- **코드 줄** – 코드의 대략적인 줄 수를 나타냅니다. 이 개수는 IL 코드를 기반으로 하므로 소스 코드 파일의 정확한 줄 수가 아닙니다. 매우 높은 수는 형식 또는 메서드가 너무 많은 작업을 수행 하 고 있으며 분할 되어야 함을 나타낼 수 있습니다. 형식이 나 메서드를 유지 관리 하기 어려울 수도 있음을 나타낼 수 있습니다.

## <a name="anonymous-methods"></a>무명 메서드
 *무명 메서드* 는 이름이 없는 메서드입니다. 무명 메서드는 코드 블록을 대리자 매개 변수로 전달 하는 데 가장 자주 사용 됩니다. 메서드 또는 접근자와 같이 멤버에 선언 된 무명 메서드에 대 한 메트릭 결과는 메서드를 선언 하는 멤버와 연결 됩니다. 메서드를 호출 하는 멤버와 연결 되지 않습니다.

 코드 메트릭이 무명 메서드를 처리 하는 방법에 대 한 자세한 내용은 [무명 메서드 및 코드 분석](../code-quality/anonymous-methods-and-code-analysis.md)을 참조 하세요.

## <a name="generated-code"></a>생성된 코드
 일부 소프트웨어 도구와 컴파일러는 프로젝트에 추가 되는 코드를 생성 하며 프로젝트 개발자가 보거나 변경 하지 않아야 합니다. 대부분의 코드 메트릭은 메트릭 값을 계산할 때 생성 된 코드를 무시 합니다. 이렇게 하면 개발자가 보고 변경할 수 있는 항목을 반영 하는 메트릭 값을 사용할 수 있습니다.

 Windows forms에 대해 생성 된 코드는 개발자가 보고 변경할 수 있는 코드 이므로 무시 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
