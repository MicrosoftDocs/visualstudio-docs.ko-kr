---
title: VSPackage 개발용 Devenv 명령줄 스위치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185272"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 개발을 위한 Devenv 명령줄 스위치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 개발자가 Visual Studio IDE (통합 개발 환경)를 시작 하는 파일인 devenv.exe를 실행할 때 명령줄에서 작업을 자동화할 수 있도록 합니다.  
  
 작업은 다음과 같습니다.  
  
- 미리 디자인 된 구성의 응용 프로그램을 IDE 외부에서 배포 합니다.  
  
- 미리 설정 된 빌드 설정이 나 디버그 구성을 사용 하 여 프로젝트를 자동으로 빌드합니다.  
  
- Ide 외부에서 특정 구성으로 IDE를 로드 합니다. 또한 시작 시 IDE를 사용자 지정할 수 있습니다.  
  
## <a name="guidelines-for-switches"></a>스위치에 대 한 지침  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 설명서에서는 사용자 수준 devenv 명령줄 스위치에 대해 설명 합니다. 자세한 내용은 [Devenv Command Line 스위치](../ide/reference/devenv-command-line-switches.md)를 참조 하세요. 또한 Devenv는 VSPackage 개발, 배포 및 디버깅에 유용한 추가 명령줄 스위치를 지원 합니다.  
  
|명령줄 스위치|설명|  
|--------------------------|-----------------|  
|/safemode|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]안전 모드에서를 시작 하 고 기본 IDE 및 서비스만 로드 합니다. /Svera 스위치는가 시작 될 때 모든 타사 Vspackage 로드를 방지 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하므로 안정적인 실행을 보장 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
|/resetskippkgs|문제가 있는 Vspackage 로드를 방지 하려는 사용자가 추가 하는 모든 건너뛰기 로드 옵션을 지운 다음를 시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다. SkipLoading 태그가 있으면 VSPackage 로드를 사용할 수 없습니다. 태그를 지우면 VSPackage을 다시 로드할 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
|/rootsuffix|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]대체 위치를 사용 하 여를 시작 합니다. 다음 명령은 설치 관리자에서 만든 바로 가기로 실행 됩니다 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .<br /><br /> devenv/rootsuffix exp<br /><br /> 이 경우 exp는 특정 접미사를 사용 하는 위치 (예: 10.0이 아닌 10.0 Exp)를 식별 합니다. 실험적 인스턴스를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 사용 하면 코드를 작성 하는 데 사용 하는 인스턴스와 별도로 VSPackage을 디버그할 수 있습니다.<br /><br /> 이 스위치는 VSRegEx.exe을 사용 하 여 만든 위치를 식별 하는 모든 문자열을 사용할 수 있습니다. 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.|  
|/시작|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]일반적으로 시작 화면을 표시 한 다음 주 IDE를 표시 하기 전에 메시지 상자를 표시 합니다. 메시지 상자를 사용 하 여 시작 화면을 검토 하 고 VSPackage 제품 아이콘을 확인할 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [명령줄 스위치 추가](../extensibility/adding-command-line-switches.md)   
 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)
