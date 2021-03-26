---
title: 설치 후 실행 해야 하는 명령 | Microsoft Docs
description: Visual Studio에서 .msi 파일을 통해 배포 된 확장 설치의 일부로 실행 해야 하는 명령에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef557c0c679fad0dff25a51a8529270e4bd7ced2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057145"
---
# <a name="commands-that-must-be-run-after-installation"></a>설치 후 실행 해야 하는 명령
*.Msi* 파일을 통해 확장을 배포 하는 경우 Visual Studio에서 확장을 검색 하기 위해 설치의 일부로 **devenv/설치 프로그램** 을 실행 해야 합니다.

> [!NOTE]
> 이 항목의 정보는 Visual Studio 2008 및 이전 버전과의 *devenv.exe* 찾기에 적용 됩니다. 이후 버전의 Visual Studio에서 *devenv.exe* 을 검색 하는 방법에 대 한 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)을 참조 하세요.

## <a name="find-devenvexe"></a>devenv.exe 찾기
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Reglocator 테이블 및 appsearch 테이블을 사용 하 여 레지스트리 값을 속성으로 저장 하는 레지스트리 값에서 각 버전의devenv.exe를 찾을 수 있습니다. 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)을 참조 하세요.

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>여러 버전의 Visual Studio에서 devenv.exe를 찾는 RegLocator 테이블 행

|서명|Root|키|이름|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|환경 경로|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|환경 경로|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|환경 경로|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|환경 경로|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>해당 RegLocator 테이블 행에 대 한 AppSearch 테이블 행

|속성|서명|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 예를 들어, Visual Studio 설치 관리자는 설치 관리자가 실행 해야 하는 실행 파일의 전체 경로를 *C:\VS2008\Common7\IDE\devenv.exe* **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** 레지스트리 값을 기록 합니다.

> [!NOTE]
> RegLocator 테이블의 유형 열이 2 이기 때문에 서명 테이블에서 추가 버전 정보를 지정할 필요가 없습니다.

## <a name="run-devenvexe"></a>devenv.exe 실행
 설치 관리자에서 AppSearch 표준 작업이 실행 된 후 AppSearch 테이블의 각 속성에는 해당 버전의 Visual Studio에 대 한 *devenv.exe* 파일을 가리키는 값이 있습니다. 지정 된 레지스트리 값이 없는 경우 (해당 버전의 Visual Studio가 설치 되지 않은 경우) 지정 된 속성이 null로 설정 됩니다.

 Windows Installer는 속성이 사용자 지정 동작 유형 50을 가리키는 실행 파일의 실행을 지원 합니다. 사용자 지정 작업에는 `msidbCustomActionTypeInScript` `msidbCustomActionTypeCommit` VSPackage를에 통합 하기 전에 성공적으로 설치 되었는지 확인 하기 위해 스크립트 내 실행 옵션 (1024) 및 (512)이 포함 되어야 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 자세한 내용은 [CustomAction 테이블](/windows/desktop/msi/customaction-table) 및 [사용자 지정 작업-스크립트 실행 옵션](/windows/desktop/msi/custom-action-in-script-execution-options)을 참조 하세요.

 유형 50의 사용자 지정 작업은 실행 파일을 포함 하는 속성을 원본 열의 값으로 지정 하 고 대상 열에 명령줄 인수를 지정 합니다.

### <a name="customaction-table-rows-to-run-devenvexe"></a>devenv.exe 실행할 테이블 행 CustomAction

|작업|형식|원본|대상|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 설치 하는 동안 실행 되도록 예약 하려면 사용자 지정 작업을 InstallExecuteSequence 테이블에 작성 해야 합니다. 조건 열의 각 행에 해당 하는 속성을 사용 하 여 해당 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 가 시스템에 설치 되지 않은 경우 사용자 지정 작업이 실행 되지 않도록 합니다.

> [!NOTE]
> 조건에 사용 되는 경우 Null 값 속성이로 평가 `False` 됩니다.

 각 사용자 지정 동작에 대 한 Sequence 열의 값은 Windows Installer 패키지의 다른 시퀀스 값에 따라 달라 집니다. 시퀀스 값은 *devenv.exe* 사용자 지정 작업이 InstallFinalize 표준 동작 직전에 최대한 가깝게 실행 되도록 하기 위한 것입니다.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>devenv.exe 사용자 지정 작업을 예약 하는 InstallExecuteSequence 테이블

|작업|조건|시퀀스|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>참조
- [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
