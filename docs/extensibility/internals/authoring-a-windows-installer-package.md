---
title: Windows 설치 관리자 패키지 작성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710034"
---
# <a name="author-a-windows-installer-package"></a>Windows 설치 관리자 패키지 작성
데이터는 Windows 설치 관리자 모델을 구동합니다. 예를 들어 파일을 복사하고 레지스트리 항목을 작성하는 절차 스크립트를 작성하는 대신 파일 및 레지스트리 데이터가 포함된 데이터베이스 테이블의 행과 열을 작성합니다.

## <a name="database-entries"></a>데이터베이스 항목
VSPackage를 설치하려면 Windows 설치 관리자 패키지에 다음 작업을 수행하려면 데이터베이스 항목이 포함되어야 합니다.

- 시스템을 검색하여 VSPackage 지원 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버전을 찾습니다(AppSearch, CompLocator, RegLocator, DrLocator 및 서명을 포함하는 Windows 설치 관리자 테이블 사용).

- 지원되는 버전이 설치되지 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 않았거나 VSPackage의 다른 시스템 요구 사항이 충족되지 않는 경우(LaunchCondition 테이블 사용) 설치를 취소합니다.

- 디렉터리, 구성 요소 및 파일 테이블을 사용하여 VSPackage 및 종속 파일을 설치합니다.

- 레지스트리 테이블을 사용하여 VSPackage에 대한 적절한 정보를 레지스트리에 추가합니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Devenv.exe /setup을** 호출하여 VSPackage를 통합합니다(사용자 지정 작업 테이블 사용).

자세한 내용은 [Windows 설치 관리자](/windows/desktop/Msi/windows-installer-portal)를 참조하십시오.

## <a name="setup-tools"></a>설정 도구
다양한 타사 설치 도구는 Windows 설치 관리자 패키지에 대한 개발 환경을 제공합니다. 다음과 같은 무료 도구를 사용할 수 있습니다.

- 설치쉴드 리미티드 에디션

   Visual Studio **새 프로젝트** 대화 상자를 통해 제한된 버전의 InstallShield를 얻을 수 있습니다. **다른 프로젝트 유형을** 확장한 다음 설정 및 **배포를**선택합니다. 설치 쉴드 템플릿을 선택합니다.

- 윈도우 설치 프로그램 XML 도구 세트

   Windows 설치 관리자 XML(WiX) 도구 집합은 XML 원본 파일에서 Windows 설치 관리자 패키지를 빌드합니다. WiX 도구 집합은 Microsoft 오픈 소스 프로젝트입니다. [Wix 도구 집합에서](https://sourceforge.net/projects/wix/)소스 코드 및 실행 도구를 다운로드할 수 있습니다.

   을 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]통합되는 상용 제품에 대한 경우 [Visual Studio 마켓플레이스를](https://marketplace.visualstudio.com/)참조하십시오.

## <a name="see-also"></a>참조
- [윈도우 설치 관리자와 VS패키지 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
