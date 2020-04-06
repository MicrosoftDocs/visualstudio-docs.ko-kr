---
title: 윈도우 설치 프로그램을 통해 VS패키지 제거 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704273"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer를 사용하여 VSPackage 제거
대부분의 경우, 윈도우 설치 프로그램은 단지 "취소"하여 VSPackage를 제거 할 수 있습니다 당신의 VSPackage를 설치. [설치 후 실행해야 하는 명령에서](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 설명하는 사용자 지정 작업은 제거 한 후에도 실행되어야 합니다. devenv.exe에 대한 호출은 설치 및 제거에 대한 설치 종료 표준 작업 직전에 발생하므로 CustomAction 및 InstallExecuteSequence 테이블 항목은 두 경우 모두 를 제공합니다.

> [!NOTE]
> MSI 패키지를 제거한 후 실행합니다. `devenv /setup`

 일반적으로 Windows Installer 패키지에 사용자 지정 작업을 추가하는 경우 제거 및 롤백 중에 해당 작업을 처리해야 합니다. 예를 들어 VSPackage를 자체 등록하기 위해 사용자 지정 작업을 추가하는 경우 사용자 지정 작업을 추가하여 등록을 취소해야 합니다.

> [!NOTE]
> 사용자가 VSPackage를 설치한 다음 통합된 버전을 제거할 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 종속된 코드를 실행하는 사용자 지정 작업을 제거하여 해당 시나리오에서 VSPackage의 제거가 작동하는지 확인할 수 있습니다.

## <a name="handling-launch-conditions-at-uninstall-time"></a>제거 시 실행 조건 처리
 LaunchConditions 표준 작업은 조건이 충족되지 않는 경우 오류 메시지를 표시하는 LaunchConditions 테이블의 행을 읽습니다. 일반적으로 시스템 요구 사항을 충족하는데 시작 조건이 사용되기 때문에 LaunchConditions 테이블의 LaunchConditions `NOT Installed`행에 조건을 추가하여 제거 하는 동안 시작 조건을 건너뛸 수 있습니다.

 다른 방법은 제거 `OR Installed` 하는 동안 중요 하지 않은 시작 조건에 추가 하는 것입니다. 이렇게 하면 제거 하는 동안 조건이 항상 true 되므로 시작 조건 오류 메시지가 표시 되지 않습니다.

> [!NOTE]
> `Installed`는 VSPackage가 시스템에 이미 설치되었음을 감지하면 Windows Installer가 설정하는 속성입니다.

## <a name="see-also"></a>참조
- [윈도우 설치 프로그램](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)
