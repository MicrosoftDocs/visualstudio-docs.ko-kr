---
title: 지역화를 위한 리소스의 계층적 구성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645609"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>지역화를 위한 리소스의 계층적 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 지역화된 리소스(각 문화권에 적절한 문자열 및 이미지와 같은 데이터)는 별도의 파일에 저장되며 UI 문화권 설정에 따라 로드됩니다. 지역화된 리소스가 로드되는 방식을 이해하려면 이러한 리소스를 계층 구조 방식으로 구성된 것으로 생각하는 것이 좋습니다.

## <a name="kinds-of-resources-in-the-hierarchy"></a>계층 구조 내 리소스의 종류

- 계층 구조의 맨 위에는 기본 문화권에 대한 대체 리소스가 있습니다(예: 영어("en")). 이는 자체 파일이 없는 유일한 리소스이며, 주 어셈블리에 저장됩니다.

- 대체 리소스 아래에는 모든 중립 문화권에 대한 리소스가 있습니다. 중립 문화권은 언어와 연관이 있지만 국가/지역과는 연관이 없습니다. 예를 들어 프랑스("fr")는 중립 문화권입니다. 대체 리소스도 중립 문화권에 사용되지만 이는 특수한 경우입니다.

- 중립 문화권의 리소스 아래에는 특정 문화권에 대한 리소스가 있습니다. 특정 문화권은 언어 및 국가/지역과 연관이 있습니다. 예를 들어 프랑스어(캐나다)("fr-CA")는 특정 문화권입니다.

  애플리케이션에서 문자열과 같은 지역화된 리소스를 로드하려는데 찾지 못한 경우 요청한 리소스가 포함된 리소스 파일을 찾을 때까지 계층 구조 위로 이동합니다.

  리소스를 저장하는 가장 좋은 방법은 가급적 일반화하는 것입니다. 즉, 지역화된 문자열, 이미지 등을 가능하면 특정 문화권이 아니라 중립 문화권에 대한 리소스 파일에 저장합니다. 예를 들어 프랑스어(벨기에)("fr-BE") 문화권에 대한 리소스가 있고 그 바로 위의 리소스가 영어로 된 대체 리소스인 경우 다른 사람이 프랑스어(캐나다) 문화권용으로 구성된 시스템에서 사용자의 애플리케이션을 사용하려고 하면 문제가 발생할 수 있습니다. 즉, 시스템에서는 "fr-CA"에 대한 위성 어셈블리를 찾다가 못 찾은 경우 프랑스 리소스를 로드하는 대신 대체 리소스(영어)가 포함된 주 어셈블리를 로드합니다. 다음 그림에서는 이 바람직하지 않은 시나리오를 보여 줍니다.

  ![특정 리소스 전용](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")

  가능한 한 많은 리소스를 "fr" 문화권에 대한 중립 리소스 파일에 두는 권장 사례를 따를 경우 프랑스어(캐나다) 사용자는 "fr-BE" 문화권용으로 표시된 리소스를 볼 수 없지만 문자열을 프랑스어로 표시할 수는 있습니다. 다음 상황에서는 이 기본 시나리오를 보여 줍니다.

  ![NeutralSpecificResources 그래픽](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>관련 항목
 지역화 [보안 및 지역화 된 위성 어셈블리](../ide/security-and-localized-satellite-assemblies.md) [에 대 한 중립 리소스 언어](../ide/neutral-resources-languages-for-localization.md) [응용 프로그램](../ide/localizing-applications.md) [전역화 및](../ide/globalizing-and-localizing-applications.md) 지역화 응용 프로그램 지역화 [방법: Windows Forms 세계화를 위한 문화권 및 ui 문화권 설정](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [방법: ASP.NET 웹 페이지 세계화를 위한 문화권 및 ui 문화권](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0) 설정
