---
title: -Build(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595763"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

지정된 솔루션 구성 파일을 사용하여 솔루션 또는 프로젝트를 빌드합니다.

## <a name="syntax"></a>구문

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>인수

- *SolutionName*

  필수 사항입니다. 솔루션 파일의 전체 경로 및 이름입니다.

- *SolnConfigName*

  (선택 사항) `Debug`SolutionName`Release`에서 명명된 솔루션을 빌드하는 데 사용할 솔루션 구성의 이름입니다(예: *또는*). 여러 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼을 지정해야 합니다(예: `Debug|Win32`). 이 인수가 지정되지 않거나 빈 문자열(`""`)인 경우에는 솔루션의 활성 구성이 사용됩니다.

- `/Project` *ProjName*

  (선택 사항) 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. *SolutionName* 폴더에서 프로젝트 파일, 프로젝트의 표시 이름 또는 프로젝트 파일의 전체 경로와 이름까지의 상대 경로를 입력할 수 있습니다.

- `/ProjectConfig` *ProjConfigName*

  (선택 사항) 명명된 프로젝트를 빌드할 때 사용할 프로젝트 빌드 구성 이름입니다(예: `Debug` 또는 `Release`). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 스위치가 지정되면 *SolnConfigName* 인수를 재정의합니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

- `/Build` 스위치는 IDE(통합 개발 환경) 내에서 **솔루션 빌드** 메뉴 명령과 동일한 기능을 수행합니다.

- 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

- 오류를 포함한 빌드에 대한 요약 정보는 명령 창에 표시되거나 `/Out` 스위치로 지정된 로그 파일에 표시될 수 있습니다.

- `/Build` 스위치는 마지막 빌드 이후 변경된 프로젝트만을 빌드합니다. 솔루션에서 모든 프로젝트를 빌드하려면 대신 [/rebuild](../../ide/reference/rebuild-devenv-exe.md)를 사용합니다.

- **잘못된 프로젝트 구성**이라는 오류 메시지가 표시되면 솔루션 플랫폼 또는 프로젝트 플랫폼(예: `Debug|Win32`)을 지정했는지 확인합니다.

## <a name="example"></a>예제

다음 명령은 `CSharpWinApp` 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `MySolution` 프로젝트를 빌드합니다.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>참고 항목

- [프로젝트 및 솔루션 빌드 및 정리](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
