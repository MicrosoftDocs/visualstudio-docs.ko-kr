---
title: -ProjectConfig(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8bb4b2860d40828a96e25ec6e6c73d947dd60c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567660"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

`/Project` 인수에서 명명된 프로젝트를 빌드, 정리, 다시 빌드 또는배포할 때 프로젝트 빌드 구성을 적용하도록 지정합니다.

## <a name="syntax"></a>구문

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>인수

- *SolutionName*

  필수 사항입니다. 솔루션 파일의 전체 경로 및 이름입니다.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  필수 사항입니다. 프로젝트를 [빌드](build-devenv-exe.md), [정리](clean-devenv-exe.md), [배포](deploy-devenv-exe.md) 또는 [다시 빌드](rebuild-devenv-exe.md)합니다.

- *SolnConfigName*

  (선택 사항) *SolutionName*에서 명명된 솔루션에 적용되는 솔루션 구성의 이름입니다(예: `Debug` 또는 `Release`). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다. 이 인수가 지정되지 않거나 빈 문자열(`""`)인 경우에는 솔루션의 활성 구성이 사용됩니다.

- `/Project` *ProjName*

  (선택 사항) 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. 프로젝트의 표시 이름 또는 *SolutionName* 폴더에서 프로젝트 파일까지 상대 경로를 입력할 수 있습니다. 프로젝트 파일의 전체 경로와 이름을 입력할 수도 있습니다.

- `/ProjectConfig` *ProjConfigName*

  (선택 사항) 명명된 `/Project`에 적용할 프로젝트의 빌드 구성 이름입니다(예: `Debug` 또는 `Release`). 둘 이상의 솔루션 플랫폼을 사용할 수 있는 경우 플랫폼(예: `Debug|Win32`)도 지정해야 합니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

`/ProjectConfig` 스위치는 `/Build`, /`Clean`, `/Deploy` 또는 `/Rebuild` 명령의 일부로 `/Project` 스위치와 함께 사용해야 합니다.

공백을 포함하는 문자열은 큰따옴표로 묶습니다.

오류를 포함한 빌드에 대한 요약 정보는 명령 창에 표시되거나 `/Out` 스위치로 지정된 로그 파일에 표시될 수 있습니다.

## <a name="example"></a>예제

다음 명령은 `MySolution` 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `CSharpWinApp` 프로젝트를 빌드합니다.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
