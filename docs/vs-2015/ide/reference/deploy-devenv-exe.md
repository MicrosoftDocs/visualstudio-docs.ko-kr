---
title: -Deploy(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660780"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

빌드 또는 다시 빌드 후 솔루션을 배포합니다. 관리 코드 프로젝트에만 적용됩니다.

## <a name="syntax"></a>구문

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>인수
 `SolnConfigName` 필수입니다. `SolutionName`으로 명명된 솔루션을 빌드하는 데 사용할 솔루션 구성의 이름입니다.

 `SolutionName` 필수입니다. 솔루션 파일의 전체 경로 및 이름입니다.

 /project `ProjName` 선택 사항입니다. 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. `SolutionName` 폴더에서 프로젝트 파일, 프로젝트의 표시 이름 또는 프로젝트 파일의 전체 경로와 이름까지의 상대 경로를 입력할 수 있습니다.

 /projectconfig `ProjConfigName` 선택 사항입니다. `/project` 빌드 시 사용할 프로젝트 빌드 구성 이름입니다.

## <a name="remarks"></a>설명
 지정된 프로젝트는 배포 프로젝트여야 합니다. 지정된 프로젝트가 배포 프로젝트가 아닌 경우, 빌드된 프로젝트가 배포되도록 전달되면 오류로 인해 실패합니다.

 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

 오류를 포함한 빌드에 대한 요약 정보는 **명령** 창 또는 `/out` 스위치로 지정된 로그 파일에 표시할 수 있습니다.

## <a name="example"></a>예
 이 예제에서는 `MySolution`의 `Release` 솔루션 구성 내에 있는 `Release` 프로젝트 빌드 구성을 사용하여 `CSharpConsoleApp` 프로젝트를 배포합니다.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [/project (devenv.exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
