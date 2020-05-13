---
title: 서비스 제공(소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705402"
---
# <a name="services-provided-source-control-vspackage"></a>제공된 서비스(소스 제어 VSPackage)
서비스는 VSPackage 와 Visual Studio 통합 개발 환경(IDE) 및 설치된 VSPackage 간에 기능을 공유하는 기본 메커니즘입니다. Visual Studio IDE에서 서비스 및 서비스 중요성에 대한 자세한 설명은[서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)을 참조하십시오.

## <a name="the-source-control-service"></a>소스 제어 서비스
 Visual Studio는 IDE 수준의 서비스와 패키지 수준 서비스등 두 가지 계층의 서비스를 제공합니다. 비주얼 스튜디오 IDE는 기본적으로 IDE 수준의 서비스를 제공합니다. 소스 제어 패키지는 이러한 서비스 중 일부를 사용합니다. VSPackage로 소스 제어 패키지자체의 개인 소스 제어 서비스를 제공 하 여 소스 제어 기능을 공유 합니다. 소스 제어 패키지는 Visual Studio IDE에서 사용할 수 있는 계약 형식으로 구현된 소스 제어 관련 인터페이스 집합을 캡슐화합니다.

## <a name="see-also"></a>참조
- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
