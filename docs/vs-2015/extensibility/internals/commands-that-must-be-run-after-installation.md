---
title: 설치 후 실행 해야 하는 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842142"
---
# <a name="commands-that-must-be-run-after-installation"></a>설치 후 실행해야 하는 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

.Msi 파일을 통해 확장을 배포 하는 경우 `devenv /setup` Visual Studio에서 확장을 검색 하기 위해 설치의 일부로를 실행 해야 합니다.  
  
> [!NOTE]
> 이 항목의 정보는 Visual Studio 2008 이전 버전에서 DevEnv를 찾는 데 적용 됩니다. 이후 버전의 Visual Studio에서 DevEnv를 검색 하는 방법에 대 한 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)을 참조 하세요.  
  
## <a name="finding-devenvexe"></a>devenv.exe 찾기  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]RegLocator 테이블 및 AppSearch 테이블을 사용 하 여 레지스트리 값을 속성으로 저장 하는 레지스트리 값에서 각 버전의 devenv.exe를 찾을 수 있습니다. 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)을 참조 하세요.  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>여러 버전의 Visual Studio에서 devenv.exe를 찾는 RegLocator 테이블 행  
  
|Signature_|Root|키|이름|유형|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|환경 경로|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|환경 경로|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|환경 경로|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|환경 경로|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>해당 RegLocator 테이블 행에 대 한 AppSearch 테이블 행  
  
|속성|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 예를 들어, Visual Studio 설치 관리자는 설치 관리자가 실행 해야 하는 실행 파일의 전체 경로를 **C:\VS2008\Common7\IDE\devenv.exe** **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** 의 레지스트리 값을 기록 합니다.  
  
 **참고** RegLocator 유형 열이 2 이기 때문에 서명 테이블에서 추가 버전 정보를 지정할 필요가 없습니다.  
  
## <a name="running-devenvexe"></a>실행 중인 devenv.exe  
 설치 관리자에서 AppSearch 표준 작업이 실행 된 후 AppSearch 테이블의 각 속성에는 해당 버전의 Visual Studio에 대 한 devenv.exe 파일을 가리키는 값이 있습니다. 지정 된 레지스트리 값이 없는 경우 (해당 버전의 Visual Studio가 설치 되지 않은 경우) 지정 된 속성이 null로 설정 됩니다.  
  
 Windows Installer는 속성이 사용자 지정 동작 유형 50을 가리키는 실행 파일의 실행을 지원 합니다. 사용자 지정 작업에는를에 통합 하기 전에 VSPackage가 성공적으로 설치 되었는지 확인 하기 위해 스크립트 내 실행 옵션인 msidbCustomActionTypeInScript (1024) 및 msidbCustomActionTypeCommit (512)가 포함 되어야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 자세한 내용은 CustomAction 테이블 및 사용자 지정 작업-스크립트 실행 옵션을 참조 하세요.  
  
 유형 50의 사용자 지정 작업은 실행 파일을 포함 하는 속성을 원본 열의 값으로 지정 하 고 대상 열에 명령줄 인수를 지정 합니다.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>devenv.exe 실행할 테이블 행 CustomAction  
  
|작업|유형|원본|대상|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 설치 하는 동안 실행 되도록 예약 하려면 사용자 지정 작업을 InstallExecuteSequence 테이블에 작성 해야 합니다. 조건 열의 각 행에 해당 하는 속성을 사용 하 여 해당 버전의 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 가 시스템에 설치 되지 않은 경우 사용자 지정 작업이 실행 되지 않도록 합니다.  
  
> [!NOTE]
> `Null` 속성 `False` 은 조건에 사용 되는 경우로 평가 됩니다.  
  
 각 사용자 지정 동작에 대 한 Sequence 열의 값은 Windows Installer 패키지의 다른 시퀀스 값에 따라 달라 집니다. 시퀀스 값은 devenv.exe 사용자 지정 작업이 InstallFinalize 표준 동작 직전에 최대한 가깝게 실행 되도록 하기 위한 것입니다.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>devenv.exe 사용자 지정 작업을 예약 하는 InstallExecuteSequence 테이블  
  
|작업|조건|순서|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer를 사용하여 VSPackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
