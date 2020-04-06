---
title: 윈도우 설치 프로그램을 가진 VSPackage 설치 | 마이크로 소프트 문서
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
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707456"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows Installer를 사용하여 VSPackage 설치
VSPackage를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합하려면 단순히 사용자의 컴퓨터에 파일을 복사하는 것 이상이 필요합니다. VSPackage의 설치 프로그램은 VSPackage 및 해당 종속 파일을 설치하고 에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]등록하고 통합해야 합니다. VSPackage는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시작 화면 및 대화 상자에 아이콘을 표시하는 것과 같은 통합 기능을 활용할 수 있습니다.

 Microsoft Windows 설치 관리자 파일은 VSPackage를 배포하는 데 권장되는 방법입니다. 사용하기 쉬운 Windows Installer 패키지는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 지원하는 모든 Windows 운영 체제에서 실행할 수 있습니다. 자세한 내용은 [Windows 설치 관리자](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)를 참조하십시오.

## <a name="in-this-section"></a>섹션 내용
- [Windows Installer 기본 사항](../../extensibility/internals/windows-installer-basics.md)

 Windows 설치 관리자에 대한 개요를 제공합니다.

- [VSPackage 설치 시나리오](../../extensibility/internals/vspackage-setup-scenarios.md)

 VSPackage 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Windows Installer 패키지 작성](../../extensibility/internals/authoring-a-windows-installer-package.md)

 VSPackage를 올바르게 설치하고 통합하기 위해 설치 프로그램이 따르는 일반적인 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]단계에 대한 개요를 제공합니다.

- [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)

 VSPackage 요구 사항이 충족되지 않는 경우 설치 관리자가 해당 구성 요소를 검색하고 해당 구성 요소를 검색하고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 취소하는 방법을 설명합니다.

- [구성 요소 관리](../../extensibility/internals/component-management.md)

 이전 제품 버전의 무결성을 유지할 설치 관리자를 개발하는 방법에 대해 설명합니다.

- [VSPackage용 설치 디렉터리 선택](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 VS패키지 를 찾는 옵션을 요약합니다.

- [VSPackage 등록](../../extensibility/internals/vspackage-registration.md)

 설치 시 VSPackage를 등록하는 방법과 자체 등록이 나쁜 생각인 이유에 대해 설명합니다.

- [프로젝트 형식 배포](../../extensibility/internals/deploying-project-types.md)

 관리 코드 프로젝트 형식에 새 프로젝트 형식 집계를 사용하는 방법에 대해 설명합니다.

- [방법: 설치 관리자에 대한 레지스트리 정보 생성](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 RegPkg.exe를 사용하여 관리되는 VSPackage에 대한 등록 매니페스트를 생성하는 방법을 설명합니다.

- [설치 후 실행해야 하는 명령](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 설치 후 명령을 실행하여 VSPackage를 에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]통합하는 방법을 설명합니다.

- [Windows Installer를 사용하여 VSPackage 제거](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 사용자가 VSPackage를 제거할 때 설치 프로그램이 수행해야 하는 단계를 설명합니다.
