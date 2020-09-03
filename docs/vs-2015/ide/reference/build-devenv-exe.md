---
title: -Build(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660990"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정된 솔루션 구성 파일을 사용하여 솔루션을 빌드합니다.

## <a name="syntax"></a>구문

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>인수
 `SolutionName` 필수입니다. 솔루션 파일의 전체 경로 및 이름입니다.

 `SolnConfigName` 필수입니다. `SolutionName`으로 명명된 솔루션을 빌드하는 데 사용할 솔루션 구성의 이름입니다.

 /project `ProjName` 선택 사항입니다. 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. `SolutionName` 폴더에서 프로젝트 파일, 프로젝트의 표시 이름 또는 프로젝트 파일의 전체 경로와 이름까지의 상대 경로를 입력할 수 있습니다.

 /projectconfig `ProjConfigName` 선택 사항입니다. `/project` 빌드 시 사용할 프로젝트 빌드 구성 이름입니다.

## <a name="remarks"></a>설명
 이 스위치는 IDE(통합 개발 환경)내에서 **솔루션 빌드** 메뉴 명령과 동일한 기능을 수행합니다.

 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

 오류를 포함한 빌드에 대한 요약 정보는 **명령** 창 또는 `/out` 스위치로 지정된 로그 파일에 표시할 수 있습니다.

 이 명령은 마지막 빌드 이후 변경된 프로젝트만을 빌드합니다. 솔루션에서 모든 프로젝트를 빌드하려면 [/Rebuild(devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)를 사용합니다.

## <a name="example"></a>예
 이 예제에서는 `MySolution`의 `Debug` 솔루션 구성 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `CSharpConsoleApp` 프로젝트를 빌드합니다.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>관련 항목
 [Visual Studio Devenv에서 프로젝트 및 솔루션 빌드 및 정리](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
