---
title: -Clean(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac184f25d79a47814fee52b99bce1cddce247fc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570468"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

모든 중간 파일 및 출력 디렉터리를 정리합니다.

## <a name="syntax"></a>구문

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>인수

- *SolutionName*

  필수 사항입니다. 솔루션 파일의 전체 경로 및 이름입니다.

- *Config*

  (선택 사항) `Debug`SolutionName`Release`에서 명명된 솔루션의 매개자 파일을 정리하는 구성입니다(예: *또는*). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 인수가 지정되지 않거나 빈 문자열(`""`)인 경우에는 솔루션의 활성 구성이 사용됩니다.

- `/Project` *ProjName*

  (선택 사항) 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. 프로젝트의 표시 이름 또는 *SolutionName* 폴더에서 프로젝트 파일까지 상대 경로를 입력할 수 있습니다. 프로젝트 파일의 전체 경로와 이름을 입력할 수도 있습니다.

- `/ProjectConfig` *ProjConfigName*

  (선택 사항) 명명된 `Debug`를 정리할 때 사용할 프로젝트의 빌드 구성 이름입니다(예: `Release` 또는 `/Project`). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 스위치가 지정되면 *Config* 인수를 재정의합니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

이 스위치는 IDE 내에서 **솔루션 정리** 메뉴 명령과 동일한 기능을 수행합니다.

공백을 포함하는 문자열은 큰따옴표로 묶습니다.

정리 및 빌드 시 오류를 포함한 요약 정보는 **명령** 창 또는 [/Out](out-devenv-exe.md) 스위치로 지정된 로그 파일에 표시될 수 있습니다.

`/Project` 스위치가 지정되지 않으면 *FileName*이 프로젝트 파일로 지정된 경우에도 솔루션의 모든 프로젝트에서 정리 작업이 수행됩니다.

## <a name="example"></a>예제

첫 번째 예제는 솔루션 파일에 지정된 기본 구성을 사용하여 `MySolution` 솔루션을 정리합니다.

두 번째 예제에서는 `CSharpWinApp` 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `MySolution` 프로젝트를 정리합니다.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
