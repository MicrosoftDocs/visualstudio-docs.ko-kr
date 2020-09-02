---
title: 제공 된 서비스 (소스 제어 VSPackage) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705402"
---
# <a name="services-provided-source-control-vspackage"></a>제공된 서비스(소스 제어 VSPackage)
서비스는 Vspackage와 Visual Studio IDE (통합 개발 환경) 및 설치 된 Vspackage 사이에서 기능을 공유 하는 기본 메커니즘입니다. Visual Studio IDE에서 서비스 및 해당 중요도에 대 한 자세한 설명은[서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)을 참조 하세요.

## <a name="the-source-control-service"></a>소스 제어 서비스
 Visual Studio는 두 가지 계층의 서비스, 즉 IDE 수준 서비스와 패키지 수준 서비스를 제공 합니다. Visual Studio IDE는 기본적으로 IDE 수준 서비스를 제공 합니다. 원본 제어 패키지는 이러한 서비스 중 일부를 사용 합니다. VSPackage 원본 제어 패키지는 자체의 전용 소스 제어 서비스를 제공 하 여 소스 제어 기능을 공유 합니다. 소스 제어 패키지는 Visual Studio IDE에서 사용할 수 있는 계약 형식으로 구현 되는 소스 제어 관련 인터페이스 집합을 캡슐화 합니다.

## <a name="see-also"></a>추가 정보
- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
