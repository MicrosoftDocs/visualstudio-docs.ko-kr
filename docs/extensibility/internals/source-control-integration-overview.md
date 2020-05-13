---
title: 소스 제어 통합 개요 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705119"
---
# <a name="source-control-integration-overview"></a>소스 제어 통합 개요
이 섹션에서는 Visual Studio 소스 제어에 통합하는 두 가지 방법을 비교합니다. 소스 제어 플러그인 및 VSPackage는 소스 제어 솔루션을 제공하고 새 소스 제어 기능을 강조 강조 합니다. Visual Studio를 사용하면 소스 제어 VSPackage 및 소스 제어 플러그인과 자동 솔루션 기반 스위칭 간에 수동으로 전환할 수 있습니다.

## <a name="source-control-integration"></a>소스 제어 통합
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]소스 제어 통합 옵션의 두 가지 유형을 지원합니다. 모든 버전에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Visual Studio 소스 제어 사용자 인터페이스(UI)를 사용하는 동안 기본 소스 제어 기능을 제공하는 소스 제어 플러그인 API(이전에는 MSSCCI API라고도 함)를 기반으로 플러그인을 통합할 수 있습니다. 반면 소스 제어 VSPackage는 소스 제어 모델에서 높은 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 수준의 정교함과 자율성을 요구하는 소스 제어 통합에 적합한 새로운 심층 통합 경로를 제공합니다.

 ![소스 제어 개요](../../extensibility/internals/media/sourcectnrloverview.gif "소스트턴오버뷰")

## <a name="source-control-plug-in"></a>소스 제어 플러그인
 Visual Studio의 모든 버전은 통합 경로로 소스 제어 플러그인 API 사양 버전 1.2를 지원합니다. 소스 제어 플러그인 구현자는 소스 제어 플러그인 [만들기에](../../extensibility/internals/creating-a-source-control-plug-in.md)설명된 대로 소스 제어 통합 및 등록을 위해 소스 제어 플러그인 API 기능을 구현하는 DLL을 작성합니다. 이 방법에서 IDE(통합 개발 환경)는 UI를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 체크 인, 체크 아웃, 도구/옵션 속성 페이지, 도구 모음 및 소스 제어 글리프와 같은 대화 상자에 사용합니다. 소스 제어 플러그인 API를 엄격하게 준수하여 Visual Studio에 쉽게 통합하고 사용자에게 문제 없는 환경을 제공합니다. 즉, 소스 제어 플러그인은 API에 자세히 설명된 대부분의 함수와 콜백을 구현해야 합니다.

 소스 제어 플러그인 API를 사용하여 소스 제어 플러그인을 구현하려면 다음 단계를 따르십시오.

1. [소스 제어 플러그인에](../../extensibility/source-control-plug-ins.md)지정된 함수를 구현하는 DLL을 만듭니다.

2. 적절한 레지스트리 항목을 만들어 DLL을 [등록합니다(방법: 소스 제어 플러그인 설치).](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. 도우미 UI를 만들고 소스 제어 어댑터 패키지(소스 제어 플러그인을 통해 소스 제어 기능을 처리하는 Visual Studio 구성 요소)에 의해 메시지가 표시될 때 표시됩니다.

   소스 제어 명령에 대한 응답으로 Visual Studio IDE는 기본 작업에 대한 표준 UI를 제공한 다음 소스 제어 플러그인 API에 정의된 기능을 통해 소스 제어 플러그인에 정보를 전달합니다. 고급 옵션의 경우 소스 제어 플러그인을 호출하여 소스 제어 프로젝트 검색과 같은 자체 UI를 표시할 수 있습니다. 즉, 사용자에게 소스 제어를 처리할 때 두 가지 다른 스타일의 UI가 표시될 수 있습니다: Visual Studio에서 제공하는 UI와 소스 제어 플러그인이 제공하는 UI. 이는 고급 소스 제어 작업에서 가장 두드러지않습니다.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그인 구현의 단점

- 고급 기능의 경우 사용자는 두 가지 인터페이스 스타일을 볼 수 있으며 혼동이 발생할 수 있습니다.

- 소스 제어 플러그인은 소스 제어 플러그인 API에서 내포한 소스 제어 모델에 국한됩니다.

- 소스 제어 플러그인 API는 일부 소스 제어 시나리오에 너무 제한적일 수 있습니다.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그인 구현의 장점

- Visual Studio는 소스 제어 플러그인이 잠재적으로 복잡한 UI를 구현할 필요가 없도록 모든 기본 소스 제어 작업에 모든 UI를 제공합니다.

- 엄격한 API로 인해 소스 제어 플러그인은 외부 소스 제어 프로그램과 쉽게 상호 작용하여 보다 광범위한 기능을 제공할 수 있습니다. Visual Studio는 소스 제어 기능이 수행되는 방법을 너무 신경 쓰지 않고 소스 제어 플러그인 API에 따라 수행되는 것만 신경 쓰지 않습니다.

- 소스 제어 VSPackage보다 소스 제어 플러그인을 구현하는 것이 더 쉽습니다.

## <a name="source-control-vspackage"></a>소스 제어 VS패키지
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]소스 제어 기능을 완벽하게 제어하고 Visual Studio에서 제공하는 소스 제어 사용자 인터페이스를 완전히 교체하여 Visual Studio에 심층통합할 수 있습니다. 소스 제어 VSPackage는 Visual Studio에 등록되어 있으며 소스 제어 기능을 제공합니다. 여러 소스 제어 VSPackage를 Visual Studio에 등록할 수 있지만 한 번에 하나만 활성화할 수 있습니다. 소스 제어 VSPackage는 활성화되어 있는 동안 Visual Studio에서 소스 제어 기능 및 모양을 완전히 제어할 수 있습니다. 시스템에 등록될 수 있는 다른 모든 소스 제어 VSPackage는 비활성 상태이며 UI를 전혀 표시하지 않습니다.

 소스 제어 VSPackage를 구현하려면 "전부 또는 전혀" 전략이 필요합니다. 소스 제어 VSPackage를 작성하는 사람은 전체 소스 제어 기능을 다루기 위해 여러 소스 제어 인터페이스와 새로운 UI 요소(대화 상자, 메뉴 및 도구 모음)를 구현하는 데 상당한 노력을 기울여야 합니다. 자세한 내용은 [소스 제어 VSPackage 만들기를](../../extensibility/internals/creating-a-source-control-vspackage.md) 참조하십시오.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>소스 제어 VS패키지 구현의 단점

- VSPackage는 Visual Studio와 성공적으로 통합하려면 여러 가지 복잡한 인터페이스를 구현해야 합니다.

- VSPackage는 소스 제어에 필요한 모든 UI를 제공해야 합니다. 비주얼 스튜디오는이 지역에 도움을 제공하지 않습니다.

- 소스 제어 VSPackage는 Visual Studio와 밀접하게 연결되어 있으며 독립 실행형 프로그램으로 작동할 수 없으므로 소스 제어 프로그램의 외부 버전과 기능을 쉽게 공유할 수 없습니다.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>소스 제어 VS패키지 구현의 장점

- VSPackage는 소스 제어 UI 및 기능을 완벽하게 제어하므로 사용자에게 소스 제어를 위한 원활한 인터페이스가 제공됩니다.

- VSPackage는 특정 소스 제어 모델에 국한되지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어](../../extensibility/internals/source-control.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [소스 제어의 새로운 기능](../../extensibility/internals/what-s-new-in-source-control.md)
