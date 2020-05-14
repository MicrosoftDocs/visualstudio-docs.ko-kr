---
title: VS패키지 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703930"
---
# <a name="vspackage-registration"></a>VSPackage 등록
VSPackage는 설치되어 있고 로드해야 한다는 것을 알려야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 이 프로세스는 레지스트리에 정보를 작성하여 수행됩니다. 이는 설치 관리자의 일반적인 작업입니다.

> [!NOTE]
> 자체 등록을 사용하는 VSPackage 개발 중에 허용되는 방법입니다. 그러나 [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] 파트너는 설정의 일부로 자체 등록을 사용하여 제품을 배송할 수 없습니다.

 Windows 설치 관리자 패키지의 레지스트리 항목은 일반적으로 레지스트리 테이블에서 이루어집니다. 레지스트리 테이블에서 파일 확장자를 등록할 수도 있습니다. 그러나 Windows Installer는 프로그래밍 방식 식별자(ProgId), 클래스, 확장 및 동사 테이블을 통해 기본 제공 지원을 제공합니다. 자세한 내용은 [데이터베이스 테이블을](/windows/desktop/Msi/database-tables)참조하십시오.

 레지스트리 항목이 선택한 나란히 전략에 적합한 구성 요소와 연결되어 있는지 확인합니다. 예를 들어 공유 파일에 대한 레지스트리 항목은 해당 파일의 Windows 설치 관리자 구성 요소와 연결되어야 합니다. 마찬가지로 버전별 파일에 대한 레지스트리 항목은 해당 파일의 구성 요소와 연결되어야 합니다. 그렇지 않으면 한 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage를 설치하거나 제거하면 다른 버전에서 VSPackage가 파손될 수 있습니다. 자세한 내용은 [여러 버전의 Visual Studio 를 참조하세요.](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

> [!NOTE]
> 등록을 관리하는 가장 쉬운 방법은 개발자 등록과 설치 시간 등록 모두에 동일한 파일에 동일한 데이터를 사용하는 것입니다. 예를 들어 일부 설치 관리자 개발 도구는 빌드 시 .reg 형식의 파일을 사용할 수 있습니다. 개발자가 일상적인 개발 및 디버깅을 위해 .reg 파일을 유지 관리하는 경우 동일한 파일을 설치 관리자에 자동으로 포함할 수 있습니다. 등록 데이터를 자동으로 공유할 수 없는 경우 설치 관리자의 등록 데이터 복사본이 최신인지 확인해야 합니다.

## <a name="registering-unmanaged-vspackages"></a>관리되지 않는 VS 패키지 등록
 관리되지 않는 VSPackage(Visual Studio 패키지 템플릿에서 생성된 패키지 포함)는 ATL 스타일 .rgs 파일을 사용하여 등록 정보를 저장합니다. .rgs 파일 형식은 ATL에만 해당되며 일반적으로 설치 작성 도구에서 있는 것처럼 사용할 수 없습니다. VSPackage 설치 관리자에 대한 등록 정보는 별도로 유지 관리해야 합니다. 예를 들어 개발자는 .rgs 파일 변경 내용과 동기화된 .reg 형식으로 파일을 유지할 수 있습니다. .reg 파일은 개발 작업을 위해 RegEdit와 병합하거나 설치 관리자가 사용할 수 있습니다.

## <a name="registering-managed-vspackages"></a>관리되는 VS패키지 등록
 RegPkg 도구는 관리되는 VSPackage의 등록 특성을 읽고 레지스트리에 직접 정보를 작성하거나 설치 관리자가 사용할 수 있는 .reg 형식 파일을 작성할 수 있습니다.

> [!NOTE]
> RegPkg 도구는 재배포할 수 없으며 사용자의 시스템에 VSPackage를 등록하는 데 사용할 수 없습니다.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>설치 시 VSPackage가 자체 등록하지 않아야 하는 이유
 VSPackage 설치 관리자는 자체 등록에 의존해서는 안 됩니다. 언뜻 보기에 VSPackage의 레지스트리 값을 VSPackage 자체에만 유지하는 것이 좋습니다. 개발자가 일상적인 작업 및 테스트에 사용할 수 있는 레지스트리 값이 필요하다는 점을 감안할 때 설치 관리자에서 레지스트리 데이터의 별도 복사본을 유지 관리하지 않는 것이 좋습니다. 설치 관리자는 VSPackage 자체를 사용하여 레지스트리 값을 작성할 수 있습니다.

 이론적으로는 좋지만 자체 등록에는 VSPackage 설치에 적합하지 않은 몇 가지 결함이 있습니다.

- 설치, 제거, 설치 롤백 및 제거 롤백을 올바르게 지원하려면 RegPkg을 호출하여 자체 등록하는 모든 관리되는 VSPackage에 대해 네 가지 사용자 지정 작업을 작성해야 합니다.

- 나란히 지원하려면 지원되는 모든 버전에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]대해 RegSvr32 또는 RegPkg을 호출하는 네 가지 사용자 지정 작업을 작성해야 할 수 있습니다.

- 자체 등록된 모듈이 있는 설치는 다른 기능이나 응용 프로그램에서 자체 등록된 키를 사용하는지 알 수 없기 때문에 안전하게 롤백할 수 없습니다.

- 자체 등록된 DLL은 때때로 존재하지 않거나 잘못된 버전인 보조 DLL에 연결됩니다. 반면 Windows 설치 관리자는 시스템의 현재 상태에 종속되지 않고 레지스트리 테이블을 사용하여 DLL을 등록할 수 있습니다.

- 구성 요소가 모두 원본에서 실행으로 지정되고 SelfReg 테이블에 나열된 경우 자체 등록 코드는 형식 라이브러리와 같은 네트워크 리소스에 대한 액세스를 거부할 수 있습니다. 이로 인해 관리 설치 중에 구성 요소 설치가 실패할 수 있습니다.

## <a name="see-also"></a>참조
- [윈도우 설치 프로그램](/windows/desktop/Msi/windows-installer-portal)
- [관리되는 패키지 등록](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
