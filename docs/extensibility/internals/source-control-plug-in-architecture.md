---
title: 소스 제어 플러그인 아키텍처 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705102"
---
# <a name="source-control-plug-in-architecture"></a>소스 제어 플러그 인 아키텍처
소스 제어 플러그인을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구현하고 연결하여 IDE(통합 개발 환경)에 소스 제어 지원을 추가할 수 있습니다. IDE는 잘 정의된 소스 제어 플러그인 API를 통해 소스 제어 플러그인에 연결합니다. IDE는 도구 모음 및 메뉴 명령으로 구성된 사용자 인터페이스(UI)를 제공하여 소스 제어 시스템의 버전 제어 기능을 노출합니다. 소스 제어 플러그인은 소스 제어 기능을 구현합니다.

## <a name="source-control-plug-in-resources"></a>소스 제어 플러그인 리소스
 소스 제어 플러그인은 버전 관리 응용 프로그램을 만들고 IDE에 연결하는 데 도움이 되는 리소스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공합니다. 소스 제어 플러그인에는 IDE에 통합될 수 있도록 소스 제어 플러그인에서 구현해야 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API 사양이 포함되어 있습니다. 또한 소스 제어 플러그인 API를 준수하는 필수 함수의 구현을 보여주는 스켈레톤 소스 제어 플러그인을 구현하는 코드 샘플(C++로 작성)도 포함되어 있습니다.

 소스 제어 플러그인 API 사양을 사용하면 소스 제어 플러그인 API에 따라 구현된 필수 기능 집합을 사용하여 소스 제어 DLL을 만드는 경우 원하는 소스 제어 시스템을 활용할 수 있습니다.

## <a name="components"></a>구성 요소
 다이어그램의 소스 제어 어댑터 패키지는 소스 제어 작업에 대한 사용자의 요청을 소스 제어 플러그인에서 지원하는 함수 호출로 변환하는 IDE의 구성 요소입니다. 이렇게 하려면 IDE와 소스 제어 플러그인에는 IDE와 플러그인 간에 정보를 주고받는 효과적인 대화 상자가 있어야 합니다. 이 대화 상자가 열리려면 둘 다 같은 언어를 사용해야 합니다. 이 문서에 설명된 소스 제어 플러그인 API는 이 교환의 일반적인 어휘입니다.

 ![소스 코드 제어 아키텍처 다이어그램](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") VS와 소스 제어 플러그인 간의 상호 작용을 보여주는 아키텍처 다이어그램

 아키텍처 다이어그램에 표시된 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 셸과 같이 다이어그램에서 VS 셸로 레이블이 지정된 셸은 사용자의 작업 프로젝트 및 편집기 및 솔루션 탐색기와 같은 관련 구성 요소를 호스트합니다. 소스 제어 어댑터 패키지는 IDE와 소스 제어 플러그인 간의 상호 작용을 처리합니다. 소스 제어 어댑터 패키지는 자체 소스 제어 UI를 제공합니다. 소스 제어 작업의 범위를 시작하고 정의하기 위해 사용자가 상호 작용하는 최상위 UI입니다.

 소스 제어 플러그인에는 그림과 같이 두 부분으로 구성될 수 있는 자체 UI가 있을 수 있습니다. "공급업체 UI"라는 레이블이 붙은 상자는 소스 제어 플러그인 작성자로서 사용자가 제공하는 사용자 지정 사용자 인터페이스 요소를 나타냅니다. 사용자가 고급 소스 제어 작업을 호출할 때 소스 제어 플러그인에 의해 직접 표시됩니다. "도우미 UI"라는 레이블이 붙은 상자는 IDE를 통해 간접적으로 호출되는 소스 제어 플러그인 UI 기능 집합입니다. 소스 제어 플러그인은 IDE에서 제공하는 특수 콜백 기능을 통해 UI 관련 메시지를 IDE에 전달합니다. 도우미 UI는 고급 **단추를** 사용하여 IDE와 보다 원활하게 통합되므로 보다 통합된 최종 사용자 환경을 제공합니다.

 소스 제어 플러그인은 셸을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 변경할 수 없으므로 소스 제어 어댑터 패키지 또는 IDE에서 제공하는 소스 제어 UI를 변경할 수 없습니다. 최종 사용자를 위한 통합 된 경험에 기여 하는 다양 한 소스 제어 플러그인 API 함수의 구현을 통해 제공 하는 유연성을 최대한 활용 해야 합니다. 소스 제어 플러그인 API 설명서의 참조 섹션에는 일부 고급 소스 제어 플러그인 기능에 대한 정보가 포함되어 있습니다. 이러한 기능을 사용하려면 소스 제어 플러그인은 초기화 하는 동안 IDE에 고급 기능을 선언 해야 하 고 각 기능에 대 한 특정 고급 기능을 구현 해야 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
- [용어](../../extensibility/source-control-plug-in-glossary.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
