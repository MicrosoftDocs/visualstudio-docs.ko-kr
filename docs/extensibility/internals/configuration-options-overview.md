---
title: 구성 옵션 개요 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709405"
---
# <a name="configuration-options-overview"></a>구성 옵션 개요
in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트는 빌드, 디버깅, 실행 및/또는 배포할 수 있는 여러 구성을 지원할 수 있습니다. 구성은 명명된 속성 집합(일반적으로 컴파일러 스위치 및 파일 위치)으로 설명된 빌드 유형입니다. 기본적으로 새 솔루션에는 *디버그* 및 *릴리스의*두 가지 구성이 포함되어 있습니다. 이러한 구성은 기본 설정을 사용하여 적용하거나 특정 솔루션 및/또는 프로젝트 요구 사항을 충족하도록 수정할 수 있습니다. 일부 패키지는 ActiveX 편집기 또는 내부 구성 요소로 두 가지 방법으로 빌드할 수 있습니다. 그러나 프로젝트는 여러 구성을 지원할 필요가 없습니다. 사용 가능한 구성이 하나만 있는 경우 해당 구성은 모든 솔루션 구성에 매핑됩니다.

 구성은 일반적으로 구성 이름(예: *디버그* 또는 *릴리스)과*플랫폼 설정의 두 부분으로 구성됩니다. 구성의 플랫폼 이름은 API 집합 또는 운영 체제 플랫폼과 같이 구성이 대상으로 하는 환경을 식별합니다. 사용자가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 플랫폼을 만들 수 없습니다. 프로젝트 VSPackage가 허용하는 선택 중에서 선택해야 합니다. 사용자가 VSPackage를 설치하면 패키지 개발 중에 생성된 배달 플랫폼에 패키지 작성자가 설정한 기준에 따라 원하는 플랫폼 이름을 표시할 수 있습니다. 그런 다음 속성 페이지가 인스턴스화될 때 VSPackage를 통해 사용할 수 있는 플랫폼 목록에서 선택할 수 있습니다.

 모든 프로젝트가 플랫폼 개념을 지원하지는 않으므로 플랫폼 이름은 선택 사항입니다. 구성에 플랫폼 이름이 없는 경우 **문자열 N/A가** UI에 표시됩니다.

 각 솔루션에는 고유한 구성 집합이 있으며 그 중 하나만 한 번에 활성화할 수 있습니다. 솔루션 구성은 각 프로젝트에서 하나 이하의 구성 집합입니다. "더 이상" 규정은 솔루션을 솔루션 구성에서 프로젝트를 제외하는 옵션 때문입니다. 사용자는 사용자 지정 솔루션 구성을 직접 만들 수 있습니다.

 다음 표에서는 프로젝트에 대한 일반적인 구성 설정을 보여 줍니다. 행은 구성 이름과 플랫폼 이름이 있는 열로 레이블이 지정됩니다.

|구성 이름|플랫폼: Win32|플랫폼: Win64|
|------------------------|----------------------|----------------------|
|*디버그*|\<> Win32 설정 디버그|\<> Win64 설정 디버그|
|*릴리스*|\<릴리스 Win32 설정>|\<Win64 설정> 릴리스|
|*마이콘피그*|해당 없음|\<마이콘피그 Win64 설정>|

> [!NOTE]
> 대상으로 하는 프로젝트가 Win32를 지원하지 않는 한 Win32 플랫폼을 제외하는 *MyConfig* 솔루션 구성을 만들 수 없습니다.

 솔루션의 활성 구성을 변경하면 해당 솔루션에 빌드, 실행, 디버깅 또는 배포되는 프로젝트 구성 집합이 선택됩니다. 예를 들어 활성 솔루션 구성을 *Release에서* *디버그로*변경하면 해당 솔루션 내의 모든 프로젝트가 솔루션의 디버그 구성에 표시된 프로젝트 구성으로 자동으로 빌드됩니다. 사용자가 환경의 구성 관리자를 수동으로 변경하지 않는 한 프로젝트의 구성은 *디버그라고도* 합니다.

 각 프로젝트에 대해 저장된 솔루션 구성 속성에는 프로젝트 이름, 프로젝트 구성 이름, 빌드 또는 배포 여부를 나타내는 플래그 및 플랫폼 이름이 포함됩니다. 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조하십시오.

 사용자는 계층 구조(솔루션 탐색기)에서 솔루션을 선택하고 속성 페이지를 열어 솔루션 구성 매개 변수를 보고 설정할 수 있습니다. 마찬가지로 솔루션 탐색기에서 프로젝트를 선택하고 해당 프로젝트의 속성 페이지를 열어 프로젝트 구성 매개 변수를 보고 설정할 수 있습니다.

 사용자는 릴리스 구성 설정을 사용하여 하나의 프로젝트를 빌드할 수도 있고 필요한 경우 디버그 구성 설정을 사용하여 나머지 모든 프로젝트를 빌드할 수도 있습니다. 자세한 내용은 [건물을 위한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-building.md)참조하십시오.

 다음 다이어그램에서는 솔루션 및 프로젝트 구성을 지원하는 인터페이스가 구현되는 방법을 보여 줍니다.

 ![구성 인터페이스 그래픽](../../extensibility/internals/media/vsconfiginterfaces.gif "대Config인터페이스") 구성 인터페이스

 이전 다이어그램과 관련된 몇 가지 참고 사항:

- `IDispatch`은 구성 개체에서 선택 사항으로 표시됩니다. 특히 찾아보기 개체에 구성 인터페이스를 두는 것은 선택 사항입니다.

- `IVsDebuggableProjectCfg`구성 개체에서 선택 사항으로 표시되지만 디버깅 지원에 필요합니다.

- `IVsProjectCfg2`구성 개체에서 선택 사항으로 표시되지만 출력 그룹화 지원에 필요합니다.

- Config 공급자 개체는 선택적 개체로 표시되지만 옵션은 구현할 위치입니다. 프로젝트 개체 또는 별도의 개체에 개체를 구현할 수 있습니다.

- `IVsCfgProvider2`플랫폼 지원 및 구성 편집에 필요합니다. `IVsCfgProvider`해당 기능을 구현하지 않으면 충분합니다.

- 다이어그램에 별도의 개체로 표시된 이러한 개체 중 일부는 특정 설계 요구 사항에 따라 실용적인 동일한 클래스로 결합할 수 있습니다. 그러나 이 섹션의 다른 항목에서는 다이어그램에 제시된 시나리오에 따라 해당 개체와 연결된 개체 및 인터페이스에 대해 설명합니다.

- 특정 개체는 별도로 구현됩니다. 예를 들어 프로젝트 및 솔루션 빌드는 빌드에 대한 구성을 설명하는 개체와 별도로 빌드 수명과 는 별도로 빌드 를 관리하는 별도의 스레드및 개체에서 발생합니다.

  이전 다이어그램의 구성 개체 인터페이스 및 구성 공급자 개체 인터페이스에 대한 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)를 참조하십시오. 또한 [빌드용 프로젝트 구성은](../../extensibility/internals/project-configuration-for-building.md) 구성 빌더 및 빌드 종속성 개체 인터페이스에 대한 자세한 정보를 제공하며, [배포관리를 위한 프로젝트 구성은](../../extensibility/internals/project-configuration-for-managing-deployment.md) 구성 배포자 및 배포 종속성 개체에 연결된 인터페이스를 추가로 설명합니다. 마지막으로 [출력을 위한 프로젝트 구성은](../../extensibility/internals/project-configuration-for-output.md) 출력 그룹 및 출력 개체 인터페이스와 속성 페이지를 사용하여 구성 종속 속성을 보고 설정하는 방법을 설명합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [건물을 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)
