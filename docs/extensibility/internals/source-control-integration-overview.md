---
title: 소스 제어 통합 개요 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705119"
---
# <a name="source-control-integration-overview"></a>소스 제어 통합 개요
이 섹션에서는 Visual Studio 소스 제어에 통합 하는 두 가지 방법을 비교 합니다. 소스 제어 솔루션을 제공 하 고 새 소스 제어 기능을 강조 표시 하는 소스 제어 플러그 인 및 VSPackage입니다. Visual Studio에서는 소스 제어 Vspackage 및 소스 제어 플러그 인과 자동 솔루션 기반 전환 사이를 수동으로 전환할 수 있습니다.

## <a name="source-control-integration"></a>소스 제어 통합
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서는 두 가지 유형의 원본 제어 통합 옵션을 지원 합니다. 모든 버전의에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 플러그 인 api (이전에는 MSSCCI api 라고도 함)를 기반으로 플러그 인을 통합할 수 있습니다 .이는 Visual Studio 소스 제어 UI (사용자 인터페이스)를 사용 하는 동안 기본 소스 제어 기능을 제공 합니다. 반면, 소스 제어 VSPackage는 소스 제어 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 모델에서 높은 수준의 복잡성과 자율성을 요구 하는 소스 제어 통합에 적합 한 새로운 딥 통합 경로를 제공 합니다.

 ![소스 제어 개요](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>소스 제어 플러그 인
 모든 버전의 Visual Studio에서는 소스 제어 플러그 인 API 사양 버전 1.2을 통합 경로로 지원 합니다. 소스 제어 플러그 인 구현자는 소스 제어 플러그 인 [만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)에 설명 된 대로 소스 제어 통합 및 등록에 대 한 소스 제어 플러그 인 API 함수를 구현 하는 DLL을 작성 합니다. 이 방법에서 IDE (통합 개발 환경)는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 체크 인, 체크 아웃, 도구/옵션 속성 페이지, 도구 모음 및 소스 제어 문자 모양과 같은 대화 상자에 UI를 사용 합니다. 소스 제어 플러그 인 API를 엄격 하 게 준수 하는 것은 Visual Studio 및 사용자에 게 문제가 없는 환경으로 쉽게 통합할 수 있습니다. 즉, 소스 제어 플러그 인은 API에 자세히 설명 된 대부분의 함수 및 콜백을 구현 해야 합니다.

 소스 제어 플러그 인 API를 사용 하 여 소스 제어 플러그 인을 구현 하려면 다음 단계를 수행 합니다.

1. [소스 제어 플러그](../../extensibility/source-control-plug-ins.md)인에 지정 된 함수를 구현 하는 DLL을 만듭니다.

2. 적절 한 레지스트리 항목을 만들어 DLL을 등록 합니다 ( [방법: 소스 제어 플러그 인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)에 설명).

3. 도우미 UI를 만들고 소스 제어 어댑터 패키지 (소스 제어 플러그 인을 통해 소스 제어 기능을 처리 하는 Visual Studio 구성 요소)에서 메시지가 표시 될 때 표시

   소스 제어 명령에 대 한 응답으로 Visual Studio IDE는 기본 작업에 대 한 표준 UI를 제공 하 고 소스 제어 플러그 인 API에 정의 된 함수를 통해 소스 제어 플러그 인에 정보를 전달 합니다. 고급 옵션의 경우 소스 제어 플러그 인을 호출 하 여 소스 제어 프로젝트를 검색 하는 등의 고유한 UI를 제공할 수 있습니다. 즉, 소스 제어를 처리할 때 사용자에 게 두 가지 스타일의 UI가 표시 될 수 있습니다. Visual Studio에서 제공 하는 UI와 소스 제어 플러그 인에서 표시 하는 ui입니다. 이는 고급 소스 제어 작업에서 가장 두드러지게 나타납니다.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그 인을 구현할 때의 단점

- 고급 기능의 경우 사용자에 게 두 가지 다른 스타일의 인터페이스가 표시 되어 혼동을 줄 수 있습니다.

- 소스 제어 플러그 인은 소스 제어 플러그 인 API에서 암시 하는 소스 제어 모델로 한정 됩니다.

- 소스 제어 플러그 인 API는 일부 원본 제어 시나리오에 대해 너무 제한적일 수 있습니다.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그 인을 구현할 경우의 이점

- Visual Studio는 모든 기본 소스 제어 작업에 대 한 모든 UI를 제공 하므로 소스 제어 플러그 인에서 잠재적으로 복잡 한 UI를 구현할 필요가 없습니다.

- 엄격한 API로 인해 소스 제어 플러그 인은 외부 소스 제어 프로그램과 쉽게 상호 작용 하 여 더 광범위 한 기능을 제공할 수 있습니다. Visual Studio는 소스 제어 기능을 수행 하는 방법에 대해 설명 하지 않으며 소스 제어 플러그 인 API에 따라 수행 됩니다.

- 소스 제어 VSPackage 원본 제어 플러그 인을 구현 하는 것이 더 쉽습니다.

## <a name="source-control-vspackage"></a>소스 제어 VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 소스 제어 기능을 완벽 하 게 제어 하 고 Visual Studio에서 제공 하는 소스 제어 사용자 인터페이스의 전체 대체를 사용 하 여 Visual Studio에 긴밀 하 게 통합할 수 있습니다. 소스 제어 VSPackage은 Visual Studio에 등록 되며 소스 제어 기능을 제공 합니다. 여러 소스 제어 Vspackage을 Visual Studio에 등록할 수 있지만 한 번에 하나씩만 활성화할 수 있습니다. 소스 제어 VSPackage는 활성화 된 상태에서 Visual Studio의 소스 제어 기능 및 모양에 대 한 모든 권한을 가집니다. 시스템에 등록 될 수 있는 다른 모든 소스 제어 Vspackage는 비활성화 되어 UI를 전혀 표시 하지 않습니다.

 소스 제어 VSPackage를 구현 하려면 "모두 또는 없음" 전략이 필요 합니다. 소스 제어 VSPackage의 작성자는 전체 소스 제어 기능을 포함 하는 여러 소스 제어 인터페이스 및 새 UI 요소 (대화 상자, 메뉴 및 도구 모음)를 구현 하는 데 상당한 노력을 투자 해야 합니다. 자세한 내용은 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md) 를 참조 하세요.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>소스 제어 VSPackage 구현에 대 한 단점

- VSPackage는 Visual Studio와 성공적으로 통합 하기 위해 여러 개의 복합 인터페이스를 구현 해야 합니다.

- VSPackage는 소스 제어에 필요한 모든 UI를 제공 해야 합니다. Visual Studio는이 영역에 대 한 지원을 제공 하지 않습니다.

- 소스 제어 VSPackage은 Visual Studio에 연결 되 고 독립 실행형 프로그램으로 작동할 수 없으므로 소스 제어 프로그램의 외부 버전과 기능을 쉽게 공유할 수 없습니다.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>소스 제어 VSPackage을 구현 하는 이점

- VSPackage에는 소스 제어 UI 및 기능에 대 한 모든 권한이 있으므로 사용자에 게 소스 제어를 위한 원활한 인터페이스가 제공 됩니다.

- VSPackage은 특정 소스 제어 모델로 한정 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어](../../extensibility/internals/source-control.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [소스 제어의 새로운 기능](../../extensibility/internals/what-s-new-in-source-control.md)
