---
title: Windows Installer를 사용 하 여 Vspackage 설치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a7ace9203cd8f21a9e9ab5dc525bf604aeff678
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012206"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows Installer를 사용하여 VSPackage 설치
VSPackage를에 통합 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하려면 사용자의 컴퓨터에 파일을 복사 하는 것 외에 더 많은 작업이 필요 합니다. VSPackage의 설치 관리자가 VSPackage와 종속 파일을 설치 하 고에 등록 하 여 통합 해야 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . VSPackage는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시작 화면 및 정보 대화 상자에 아이콘을 표시 하는 등의 통합 기능을 활용할 수 있습니다.

 Microsoft Windows Installer 파일은 Vspackage를 배포 하는 데 권장 되는 방법입니다. 사용 하기 쉬운 Windows Installer 패키지는에서 지원 되는 모든 Windows 운영 체제에서 실행할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 자세한 내용은 [Windows Installer](/previous-versions/2kt85ked(v=vs.120))를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
- [Windows Installer 기본 사항](../../extensibility/internals/windows-installer-basics.md)

 Windows Installer에 대 한 개요를 제공 합니다.

- [VSPackage 설치 시나리오](../../extensibility/internals/vspackage-setup-scenarios.md)

 Vspackage 및의 병렬 설치를 지원할 수 있는 여러 가지 방법을 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Windows Installer 패키지 작성](../../extensibility/internals/authoring-a-windows-installer-package.md)

 설치 관리자가 Vspackage을 올바르게 설치 하 고 통합 하기 위해 수행 하는 일반적인 단계에 대 한 개요를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

- [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)

 설치 관리자가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 요구 사항이 충족 되지 않은 경우 설치 프로그램에서 해당 구성 요소를 검색 하 고 설치를 취소 하는 방법을 설명 합니다.

- [구성 요소 관리](../../extensibility/internals/component-management.md)

 이전 제품 버전의 무결성을 유지 하는 설치 관리자를 개발 하는 방법을 설명 합니다.

- [VSPackage용 설치 디렉터리 선택](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Vspackage를 찾기 위한 옵션을 요약 합니다.

- [VSPackage 등록](../../extensibility/internals/vspackage-registration.md)

 설치 시 Vspackage를 등록 하는 방법과 자체 등록이 잘못 된 이유를 설명 합니다.

- [프로젝트 형식 배포](../../extensibility/internals/deploying-project-types.md)

 관리 코드 프로젝트 형식에 새 프로젝트 형식 집계를 사용 하는 방법을 설명 합니다.

- [방법: 설치 관리자에 대한 레지스트리 정보 생성](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 RegPkg.exe를 사용 하 여 관리 되는 VSPackage 등록 매니페스트를 생성 하는 방법을 설명 합니다.

- [설치 후 실행해야 하는 명령](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 설치 후 명령을 실행 하 여 Vspackage를에 통합 하는 방법을 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Windows Installer를 사용하여 VSPackage 제거](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 사용자가 VSPackage를 제거 하는 경우 설치 관리자가 수행 해야 하는 단계를 설명 합니다.