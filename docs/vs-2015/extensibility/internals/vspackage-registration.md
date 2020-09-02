---
title: VSPackage 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685280"
---
# <a name="vspackage-registration"></a>VSPackage 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설치 되어 있고 로드 되어야 한다는 것을 알려 주어 야 합니다. 이 프로세스는 레지스트리에서 정보를 작성 하 여 수행 됩니다. 이는 설치 관리자의 일반적인 작업입니다.  
  
> [!NOTE]
> VSPackage를 개발 하는 동안 자체 등록을 사용 하는 것이 허용 되는 방법입니다. 그러나 [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] 파트너는 설치의 일부로 자체 등록을 사용 하 여 제품을 출시할 수 없습니다.  
  
 Windows Installer 패키지의 레지스트리 항목은 일반적으로 레지스트리 테이블에 만들어집니다. 레지스트리 테이블에 파일 확장명을 등록할 수도 있습니다. 그러나 Windows Installer는 ProgId (프로그래밍 식별자), 클래스, 확장 및 동사 테이블을 통해 기본 제공 되는 지원을 제공 합니다. 자세한 내용은 [데이터베이스 테이블](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)을 참조 하세요.  
  
 선택한 side-by-side 전략에 적합 한 구성 요소와 레지스트리 항목이 연결 되어 있어야 합니다. 예를 들어 공유 파일에 대 한 레지스트리 항목은 해당 파일의 Windows Installer 구성 요소와 연결 되어야 합니다. 마찬가지로 버전별 파일의 레지스트리 항목도 해당 파일의 구성 요소와 연결 되어야 합니다. 그렇지 않으면 한 버전의에 대 한 VSPackage를 설치 하거나 제거 하면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다른 버전의 VSPackage이 중단 될 수 있습니다. 자세한 내용은 [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md) 을 참조 하세요.  
  
> [!NOTE]
> 등록을 관리 하는 가장 쉬운 방법은 동일한 파일에서 개발자 등록 및 설치 시간 등록에 동일한 데이터를 사용 하는 것입니다. 예를 들어 일부 설치 관리자 개발 도구는 빌드할 때 .reg 형식으로 파일을 사용할 수 있습니다. 개발자가 자신의 일상 개발 및 디버깅을 위해 .reg 파일을 유지 관리 하는 경우 동일한 파일이 설치 관리자에 자동으로 포함 될 수 있습니다. 등록 데이터를 자동으로 공유할 수 없는 경우 등록 데이터의 설치 관리자가 최신 복사본 인지 확인 해야 합니다.  
  
## <a name="registering-unmanaged-vspackages"></a>관리 되지 않는 Vspackage 등록  
 관리 되지 않는 Vspackage (Visual Studio 패키지 템플릿에서 생성 된 파일 포함)는 ATL 스타일의 .rgs 파일을 사용 하 여 등록 정보를 저장 합니다. .Rgs 파일 형식은 ATL에만 적용 되며 일반적으로 설치 제작 도구를 사용 하 여 그대로 사용할 수 없습니다. VSPackage 설치 관리자에 대 한 등록 정보는 별도로 유지 관리 해야 합니다. 예를 들어 개발자는 파일의 .reg 형식을 .rgs 파일 변경 내용과 동기화 된 상태로 유지할 수 있습니다. .Reg 파일은 개발 작업을 위해 RegEdit와 병합 하거나 설치 관리자에서 사용할 수 있습니다.  
  
## <a name="registering-managed-vspackages"></a>관리 되는 Vspackage 등록  
 RegPkg 도구는 관리 되는 VSPackage에서 등록 특성을 읽고 레지스트리에 직접 정보를 쓰거나 설치 관리자에서 사용할 수 있는 .reg 형식 파일을 작성할 수 있습니다.  
  
> [!NOTE]
> RegPkg 도구는 재배포할 수 없으며 사용자 시스템에 VSPackage을 등록 하는 데 사용할 수 없습니다.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>설치 시 Vspackage에서 자체 등록 하지 않아야 하는 이유  
 VSPackage 설치 관리자는 자체 등록을 사용 하면 안 됩니다. 언뜻 보기에는 VSPackage의 레지스트리 값을 VSPackage 자체에 유지 하는 것이 좋습니다. 개발자가 일상적인 작업 및 테스트에 사용할 수 있는 레지스트리 값을 필요로 하는 경우 설치 관리자에서 레지스트리 데이터의 개별 복사본을 유지 관리 하지 않는 것이 좋습니다. 설치 관리자는 VSPackage 자체를 사용 하 여 레지스트리 값을 쓸 수 있습니다.  
  
 이론적으로는 유용 하지만, 자체 등록에는 VSPackage 설치에 적합 하지 않은 여러 가지 결함이 있습니다.  
  
- 설치, 제거, 설치 롤백 및 제거 롤백을 올바르게 지원 하려면 RegPkg를 호출 하 여 자체 등록 하는 모든 관리 되는 VSPackage에 대해 네 가지 사용자 지정 작업을 작성 해야 합니다.  
  
- Side-by-side 지원을 사용 하려면 지원 되는 모든 버전에 대해 RegSvr32 또는 RegPkg를 호출 하는 네 가지 사용자 지정 작업을 작성 해야 할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- 자체 등록 된 모듈을 사용 하는 설치는 다른 기능 또는 응용 프로그램에서 사용 되는지 여부를 알려주는 방법이 없으므로 안전 하 게 롤백할 수 없습니다.  
  
- 자체 등록 Dll이 존재 하지 않거나 잘못 된 버전인 보조 Dll로 연결 되는 경우가 있습니다. 반면, Windows Installer는 시스템의 현재 상태에 대 한 종속성 없이 레지스트리 테이블을 사용 하 여 Dll을 등록할 수 있습니다.  
  
- 구성 요소가 원본에서 실행으로 지정 되 고 SelfReg 테이블에 나열 되는 경우에는 형식 라이브러리와 같은 네트워크 리소스에 대 한 자동 등록 코드의 액세스가 거부 될 수 있습니다. 이로 인해 관리를 설치 하는 동안 구성 요소 설치가 실패할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [관리 패키지 등록](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
