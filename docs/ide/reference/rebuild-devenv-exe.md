---
title: -Rebuild(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76fe4bcf3441163604d93e9264ed6f78fcf0224b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565619"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

지정된 솔루션 구성을 정리하고 빌드합니다.

## <a name="syntax"></a>구문

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>인수

- *SolutionName*

  필수 사항입니다. 솔루션 파일의 전체 경로 및 이름입니다.

- *SolnConfigName*

  (선택 사항) `Debug`SolutionName`Release`에서 명명된 솔루션을 다시 빌드하는 데 사용할 솔루션 구성의 이름입니다(예: *또는*). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 인수가 지정되지 않거나 빈 문자열(`""`)인 경우에는 솔루션의 활성 구성이 사용됩니다.

- `/Project` *ProjName*

  (선택 사항) 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. 프로젝트의 표시 이름 또는 *SolutionName* 폴더에서 프로젝트 파일까지 상대 경로를 입력할 수 있습니다. 프로젝트 파일의 전체 경로와 이름을 입력할 수도 있습니다.

- `/ProjectConfig` *ProjConfigName*

  (선택 사항) 명명된 `Debug`를 다시 빌드할 때 사용할 프로젝트의 빌드 구성 이름입니다(예: `Release` 또는 `/Project`). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 스위치가 지정되면 *SolnConfigName* 인수를 재정의합니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

- 이 스위치는 IDE 내에서 **솔루션 다시 빌드** 메뉴 명령과 동일한 기능을 수행합니다.

- 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

- 정리 및 빌드에 대한 오류를 포함한 요약 정보는 **명령** 창 또는 [/Out](out-devenv-exe.md) 스위치로 지정된 로그 파일에 표시될 수 있습니다.

## <a name="example"></a>예제

이 예제에서는 `CSharpWinApp` 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `MySolution` 프로젝트를 정리 침 다시 빌드합니다.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
