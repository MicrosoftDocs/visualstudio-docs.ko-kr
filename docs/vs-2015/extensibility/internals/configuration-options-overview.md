---
title: 구성 옵션 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b37d93adbd2accb7a12fb176ab15aafc6914190
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841522"
---
# <a name="configuration-options-overview"></a>구성 옵션 개요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

의 프로젝트 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 빌드, 디버깅, 실행 및/또는 배포할 수 있는 여러 구성을 지원할 수 있습니다. 구성은 명명 된 속성 집합 (일반적으로 컴파일러 스위치 및 파일 위치)으로 설명 되는 빌드 형식입니다. 기본적으로 새 솔루션에는 디버그 및 릴리스의 두 가지 구성이 포함 됩니다. 이러한 구성은 기본 설정을 사용 하 여 적용 하거나 특정 솔루션 및/또는 프로젝트 요구 사항에 맞게 수정할 수 있습니다. 일부 패키지는 ActiveX 편집기 또는 내부 구성 요소와 같은 두 가지 방법으로 빌드할 수 있습니다. 그러나 프로젝트는 여러 구성을 지원할 필요가 없습니다. 하나의 구성만 사용할 수 있는 경우 해당 구성은 모든 솔루션 구성에 매핑됩니다.  
  
 구성은 일반적으로 구성 이름 (예: 디버그 또는 릴리스) 및 플랫폼 설정의 두 부분으로 구성 됩니다. 구성의 플랫폼 이름은 구성에서 대상으로 하는 환경 (예: API 집합 또는 운영 체제 플랫폼)을 식별 합니다. 사용자는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 플랫폼을 만들 수 없으며, 프로젝트 VSPackage 허용 하는 선택 항목 중에서 선택 해야 합니다. 사용자가 VSPackage를 설치 하면 패키지를 개발 하는 동안 생성 된 배달 플랫폼이 패키지 작성자가 설정한 조건에 따라 원하는 모든 플랫폼 이름을 표시할 수 있습니다. 그런 다음 사용자는 속성 페이지가 인스턴스화될 때 VSPackage를 통해 사용 가능한 플랫폼 목록에서 선택할 수 있습니다.  
  
 모든 프로젝트가 플랫폼의 개념을 지원 하지 않기 때문에 플랫폼 이름은 선택 사항입니다. 구성에 플랫폼 이름이 없는 경우 문자열 "N/A"가 UI에 표시 됩니다.  
  
 각 솔루션에는 고유한 구성 집합이 있으며 한 번에 하나씩만 활성화 될 수 있습니다. 솔루션 구성은 각 프로젝트에서 하나 이상의 구성으로 구성 된 집합입니다. "Stipulation"은 솔루션 구성에서 프로젝트를 제외 하는 옵션 때문에 발생 합니다. 사용자는 고유한 사용자 지정 솔루션 구성을 만들 수 있습니다.  
  
 다음 표에서는 프로젝트에 대 한 일반적인 구성 설정을 보여 줍니다. 행에는 구성 이름 및 플랫폼 이름으로 열이 표시 됩니다.  
  
|구성 이름|플랫폼-Win32|플랫폼-Win64|  
|------------------------|----------------------|----------------------|  
|디버그|\<Debug Win32 settings>|\<Debug Win64 settings>|  
|Release|\<Release Win32 settings>|\<Release Win64 settings>|  
|Myconfig.xml|해당 없음|\<MyConfig Win64 settings>|  
  
> [!NOTE]
> 대상으로 지정 하는 프로젝트에서 Win32를 지원 하지 않는 경우 "Win32" 플랫폼을 제외 하는 "MyConfig" 솔루션 구성을 만들 수 없습니다.  
  
 솔루션에 대 한 활성 구성을 변경 하면 해당 솔루션에 빌드, 실행, 디버깅 또는 배포 되는 프로젝트 구성 집합이 선택 됩니다. 예를 들어 활성 솔루션 구성을 릴리스에서 디버그로 변경 하는 경우 솔루션의 모든 프로젝트는 솔루션의 디버그 구성에 표시 된 프로젝트의 구성을 사용 하 여 자동으로 빌드됩니다. 사용자가 환경의 Configuration Manager를 수동으로 변경 하지 않는 한, 프로젝트의 구성도 일반적으로 Debug로 지정 됩니다.  
  
 각 프로젝트에 대해 저장 된 솔루션 구성 속성에는 프로젝트 이름, 프로젝트 구성 이름, 빌드 여부 및 배포 여부를 나타내는 플래그 및 플랫폼 이름이 포함 됩니다. 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조 하세요.  
  
 사용자는 계층 (솔루션 탐색기)에서 솔루션을 선택 하 고 속성 페이지를 열어 솔루션 구성 매개 변수를 확인 하 고 설정할 수 있습니다. 마찬가지로 솔루션 탐색기에서 프로젝트를 선택 하 고 해당 프로젝트에 대 한 속성 페이지를 열어 프로젝트 구성 매개 변수를 확인 하 고 설정할 수 있습니다.  
  
 사용자는 릴리스 구성 설정을 사용 하 여 프로젝트 하나를 빌드하고 필요한 경우 디버그 구성 설정을 사용 하는 나머지 모든 사용자를 빌드할 수도 있습니다. 자세한 내용은 [빌드하기 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)을 참조 하세요.  
  
 다음 다이어그램에서는 솔루션 및 프로젝트 구성을 지 원하는 인터페이스를 구현 하는 방법을 보여 줍니다.  
  
 ![구성 인터페이스 그래픽](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
구성 인터페이스  
  
 이전 다이어그램과 관련 된 몇 가지 참고 사항:  
  
- `IDispatch` 구성 개체에서 옵션으로 표시 됩니다. 특히 찾아보기 개체에 구성 인터페이스를 포함 하는 것이 선택 사항입니다.  
  
- `IVsDebuggableProjectCfg` 는 구성 개체에서 선택적으로 표시 되지만 디버깅 지원에 필요 합니다.  
  
- `IVsProjectCfg2` 는 구성 개체에서 선택적으로 표시 되지만 출력 그룹화 지원에 필요 합니다.  
  
- `Config Provider`개체가 선택적 개체로 표시 되었지만 옵션은이를 구현할 수 있습니다. 프로젝트 개체 또는 별도의 개체에서 개체를 구현할 수 있습니다.  
  
- `IVsCfgProvider2` 플랫폼 지원 및 구성 편집에 필요 합니다. `IVsCfgProvider` 해당 기능을 구현 하지 않는 경우에는 충분 합니다.  
  
- 다이어그램에 표시 되는 이러한 개체 중 일부는 특정 디자인 요구 사항에 따라 실용적으로 동일한 클래스로 결합 될 수 있습니다. 그러나이 섹션의 다른 항목에서 이러한 개체와 연결 된 개체 및 인터페이스는 다이어그램에 표시 된 시나리오에 따라 설명 됩니다.  
  
- 특정 개체는 개별적으로 구현 됩니다. 예를 들어 프로젝트 및 솔루션 빌드는 별도의 스레드에서 발생 하며 빌드를 관리 하는 개체는 빌드에 대 한 구성을 설명 하는 개체와 별도로 존재 합니다.  
  
  이전 다이어그램의 구성 개체 인터페이스 및 구성 공급자 개체 인터페이스에 대 한 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)를 참조 하세요. 또한 빌드를 [위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md) 에서는 구성 작성기 및 빌드 종속성 개체 인터페이스에 대 한 자세한 정보를 제공 하 고, [배포 관리를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-managing-deployment.md) 에서는 구성 배포자 및 배포 종속성 개체에 연결 된 인터페이스에 대해 자세히 설명 합니다. 마지막으로 [출력에 대 한 프로젝트 구성은](../../extensibility/internals/project-configuration-for-output.md) 출력 그룹 및 출력 개체 인터페이스를 설명 하 고 속성 페이지를 사용 하 여 구성 종속 속성을 보고 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
