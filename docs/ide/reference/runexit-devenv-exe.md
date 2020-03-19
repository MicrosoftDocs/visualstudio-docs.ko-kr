---
title: -RunExit(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18ca581c5a8a7f631138e8b3eacff02a031e0931
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593605"
---
# <a name="runexit-devenvexe"></a>/RunExit(devenv.exe)

지정된 프로젝트 또는 솔루션을 컴파일 및 실행한 다음 IDE(통합 개발 환경)을 닫습니다.

## <a name="syntax"></a>구문

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>인수

- *SolutionName*

  솔루션 파일의 전체 경로 및 이름입니다.

- *ProjectName*

  프로젝트 파일의 전체 경로 및 이름입니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

활성 솔루션 구성에 대해 지정된 설정에 따라 지정된 프로젝트 또는 솔루션을 컴파일하고 실행합니다. 이 스위치는 프로젝트 또는 솔루션을 실행하는 동안 IDE를 최소화합니다. 또한 프로젝트 또는 솔루션 실행을 완료한 후에 IDE를 닫습니다.

- 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

- 오류를 포함한 요약 정보는 **명령** 창 또는 `/Out` 스위치로 지정된 로그 파일에 표시할 수 있습니다.

## <a name="example"></a>예제

이 예제에서는 활성 배포 구성을 사용하여 최소화된 IDE에서 `MySolution` 솔루션을 실행한 다음 IDE를 닫습니다.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Run(devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
