---
title: 설치 후 실행해야 하는 명령 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709479"
---
# <a name="commands-that-must-be-run-after-installation"></a>설치 후 실행해야 하는 명령
*.msi* 파일을 통해 확장을 배포하는 경우 Visual Studio에서 확장프로그램을 검색하려면 설치의 일부로 **devenv /setup을** 실행해야 합니다.

> [!NOTE]
> 이 항목의 정보는 Visual Studio 2008 이전과 함께 *devenv.exe를* 찾는 데 적용됩니다. 이후 버전의 Visual Studio에서 *devenv.exe를* 검색하는 방법에 대한 자세한 내용은 [시스템 요구 사항 검색을](../../extensibility/internals/detecting-system-requirements.md)참조하십시오.

## <a name="find-devenvexe"></a>devenv.exe 찾기
 RegLocator 테이블 및 AppSearch 테이블을 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 값을 속성으로 저장하는 설치 프로그램이 작성하는 레지스트리 값에서 각 버전의 *devenv.exe를* 찾을 수 있습니다. 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)을 참조하십시오.

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator 테이블 행은 비주얼 스튜디오의 다른 버전에서 devenv.exe를 찾을 수

|서명|Root|키|이름|형식|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|소프트웨어\마이크로소프트\비주얼 스튜디오\7.0\설치\VS|환경 경로|2|
|RL_DevenvExe_2003|2|소프트웨어\마이크로소프트\비주얼 스튜디오\7.1\설치\VS|환경 경로|2|
|RL_DevenvExe_2005|2|소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\설치\VS|환경 경로|2|
|RL_DevenvExe_2008|2|소프트웨어\마이크로소프트\비주얼 스튜디오\9.0\설치\VS|환경 경로|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>해당 RegLocator 테이블 행에 대한 AppSearch 테이블 행

|속성|서명|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 예를 들어 Visual Studio 설치 관리자는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\설치\VS\환경경로의** 레지스트리 값을 *C:\VS2008\Common7\IDE\devenv.exe로*기록합니다.

> [!NOTE]
> RegLocator 테이블의 유형 열은 2이므로 서명 테이블에 추가 버전 정보를 지정할 필요가 없습니다.

## <a name="run-devenvexe"></a>실행 devenv.exe
 AppSearch 표준 작업이 설치 프로그램에서 실행된 후 AppSearch 테이블의 각 속성에는 해당 버전의 Visual Studio에 대한 *devenv.exe* 파일을 가리키는 값이 있습니다. 지정된 레지스트리 값이 없는 경우(해당 버전의 Visual Studio가 설치되지 않았기 때문에) 지정된 속성이 null로 설정됩니다.

 Windows Installer는 사용자 지정 작업 유형 50을 통해 속성이 가리키는 실행 가능한 실행을 지원합니다. 사용자 지정 작업에는 스크립트 `msidbCustomActionTypeInScript` `msidbCustomActionTypeCommit` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]내 실행 옵션(1024) 및 (512)이 포함되어야 합니다. 자세한 내용은 [사용자 지정 작업 테이블](/windows/desktop/msi/customaction-table) 및 사용자 지정 작업 [인스크립트 실행 옵션을](/windows/desktop/msi/custom-action-in-script-execution-options)참조하세요.

 유형 50의 사용자 지정 작업은 대상 열의 소스 열 및 명령줄 인수의 값으로 실행 할 수 있는 속성을 지정합니다.

### <a name="customaction-table-rows-to-run-devenvexe"></a>devenv.exe를 실행하는 사용자 지정 작업 테이블 행

|작업|형식|원본|대상|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/설정|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/설정|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/설정|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/설정|

 설치 하는 동안 실행을 예약 하려면 사용자 지정 작업을 설치 Execute시 테이블에 작성 해야 합니다. 조건 열의 각 행에 해당 속성을 사용하여 해당 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버전이 시스템에 설치되어 있지 않은 경우 사용자 지정 작업이 실행되지 않도록 합니다.

> [!NOTE]
> Null 값 속성은 `False` 조건에서 사용될 때 평가합니다.

 각 사용자 지정 작업에 대한 시퀀스 열 값은 Windows Installer 패키지의 다른 시퀀스 값에 따라 다릅니다. 시퀀스 값은 *devenv.exe* 사용자 지정 작업이 InstallFinalize 표준 작업 직전에 가능한 한 가깝게 실행되도록 해야 합니다.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>설치실행시퀀스 테이블은 devenv.exe 사용자 지정 작업을 예약합니다.

|작업|조건|시퀀스|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>참조
- [윈도우 설치 관리자와 VS패키지 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
