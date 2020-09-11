---
title: Windows Installer를 사용 하 여 VSPackage 제거 | Microsoft Docs
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
ms.openlocfilehash: 6cdf9023512f4225e2a8edcadcf589cb61547e24
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011816"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer를 사용하여 VSPackage 제거
대부분의 경우에는 VSPackage를 설치 하기 위해 수행 하는 작업을 "실행 취소" 하 여 VSPackage를 제거할 수 Windows Installer. [설치 후 실행 해야 하는 명령](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 에서 설명한 사용자 지정 작업은 제거 후에도 실행 해야 합니다. devenv.exe 호출은 설치 및 제거에 대해 모두 InstallFinalize 표준 작업 바로 전에 발생 하므로 CustomAction 및 InstallExecuteSequence 테이블 항목은 두 경우 모두 제공 됩니다.

> [!NOTE]
> `devenv /setup`MSI 패키지를 제거한 후를 실행 합니다.

 일반적으로 Windows Installer 패키지에 사용자 지정 작업을 추가 하는 경우 제거 및 롤백 중에 이러한 작업을 처리 해야 합니다. 예를 들어 사용자 지정 작업을 추가 하 여 VSPackage를 직접 등록 하는 경우 등록을 취소 하는 사용자 지정 작업을 추가 해야 합니다.

> [!NOTE]
> 사용자가 VSPackage를 설치한 다음 통합 된 버전의를 제거할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 종속성과 함께 코드를 실행 하는 사용자 지정 작업을 제거 하 여 해당 시나리오에서 VSPackage의 제거가 작동 하는지 확인할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>제거 시 시작 조건 처리
 LaunchConditions 표준 작업은 조건이 충족 되지 않을 경우 오류 메시지를 표시 하기 위해 Launchconditions 테이블의 행을 읽습니다. 일반적으로 시작 조건은 시스템 요구 사항이 충족 되었는지 확인 하는 데 사용 되기 때문에, 일반적으로를 제거 하는 동안 `NOT Installed` launchconditions 테이블의 launchconditions 행에 조건을 추가 하 여 시작 조건을 건너뛸 수 있습니다.

 대안은 `OR Installed` 제거 중에 중요 하지 않은 시작 조건을 추가 하는 것입니다. 이렇게 하면 제거 하는 동안 조건이 항상 true가 되므로 시작 조건 오류 메시지가 표시 되지 않습니다.

> [!NOTE]
> `Installed` VSPackage가 시스템에 이미 설치 되어 있음을 감지 하면 속성 Windows Installer 설정 됩니다.

## <a name="see-also"></a>참고 항목
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)