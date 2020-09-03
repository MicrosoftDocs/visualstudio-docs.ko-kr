---
title: -Upgrade(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657906"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

솔루션 파일 및 모든 프로젝트 파일이나 지정한 프로젝트 파일을 이러한 파일의 현재 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 형식으로 업데이트합니다.

## <a name="syntax"></a>구문

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>인수
 `SolutionFile`전체 솔루션 및 해당 프로젝트를 업그레이드할 경우 필요합니다. 솔루션 파일의 경로 및 이름입니다. 솔루션 파일의 이름만 입력하거나 솔루션 파일의 전체 경로와 이름을 입력할 수 있습니다. 이름이 지정된 폴더나 파일이 아직 없으면 새로 만들어집니다.

 `ProjectFile`단일 프로젝트를 업그레이드할 경우 필요합니다. 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. 프로젝트 파일의 이름만 입력하거나 프로젝트 파일의 전체 경로와 이름을 입력할 수 있습니다. 이름이 지정된 폴더나 파일이 아직 없으면 새로 만들어집니다.

## <a name="remarks"></a>설명
 백업은 자동으로 만들어지고 현재 디렉터리에 생성된 Backup 디렉터리로 복사됩니다.

 소스 제어 솔루션 또는 프로젝트는 업그레이드하기 전에 체크 아웃해야 합니다.

 `/upgrade` 스위치를 사용해도 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]가 시작되지 않습니다. 솔루션 또는 프로젝트의 개발 언어에 대한 업그레이드 보고서에서 업그레이드 결과를 확인할 수 없습니다. 오류 또는 사용 정보가 반환되지 않습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 프로젝트를 업그레이드하는 방법에 대한 자세한 내용은 [방법: 실패한 Visual Studio 프로젝트 업그레이드 문제 해결](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)을 참조하세요.

## <a name="example"></a>예
 이 예제에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 솔루션에 대한 기본 폴더에서 “MyProject.sln”이라는 솔루션 파일을 업그레이드합니다.

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>관련 항목
 [방법: 실패 한 Visual Studio 프로젝트 업그레이드에 대 한 문제 해결](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
