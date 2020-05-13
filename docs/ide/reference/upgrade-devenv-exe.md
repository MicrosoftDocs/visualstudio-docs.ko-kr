---
title: -Upgrade(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596426"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

솔루션 파일 및 모든 프로젝트 파일이나 지정한 프로젝트 파일을 이러한 파일의 현재 Visual Studio 형식으로 업데이트합니다.

## <a name="syntax"></a>구문

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>인수

- *SolutionFile*

  전체 솔루션 및 해당 프로젝트를 업그레이드할 경우 필요합니다. 솔루션 파일의 경로 및 이름입니다. 솔루션 파일의 이름만 입력하거나 솔루션 파일의 전체 경로와 이름을 입력할 수 있습니다. 명명된 폴더 또는 파일이 아직 없으면 만들어집니다.

- *ProjectFile*

  단일 프로젝트를 업그레이드할 경우 필요합니다. 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. 프로젝트 파일의 이름만 입력하거나 프로젝트 파일의 전체 경로와 이름을 입력할 수 있습니다. 명명된 폴더 또는 파일이 아직 없으면 만들어집니다.

- `/Out` *OutputFilename*

  (선택 사항) 도구의 출력을 보낼 파일의 이름입니다. 파일이 이미 있는 경우 출력은 파일의 끝에 추가됩니다.

## <a name="remarks"></a>설명

백업은 자동으로 만들어지고 현재 디렉터리에 생성된 Backup 디렉터리로 복사됩니다.

소스 제어 솔루션 또는 프로젝트는 업그레이드하기 전에 체크 아웃해야 합니다.

`/Upgrade` 스위치를 사용하면 Visual Studio가 열리지 않습니다. 솔루션 또는 프로젝트의 개발 언어에 대한 업그레이드 보고서에서 업그레이드 결과를 확인할 수 없습니다. 오류 또는 사용 정보가 반환되지 않습니다. Visual Studio에서 프로젝트를 업그레이드하는 방법에 대한 자세한 내용은 [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)를 참조하세요.

## <a name="example"></a>예제

이 예제에서는 “MyProject.sln”이라는 솔루션 파일을 업그레이드합니다.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
