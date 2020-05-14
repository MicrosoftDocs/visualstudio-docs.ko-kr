---
title: -DoNotLoadProjects(devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569857"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects(devenv.exe)

**Visual Studio 2019 버전 16.1의 새로운 기능**

프로젝트를 로드하지 않고 지정된 솔루션을 엽니다. 자세한 내용은 [Visual Studio의 필터링된 솔루션](../filtered-solutions.md)을 참조하세요.

## <a name="syntax"></a>구문

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>인수

*SolutionName*

필수 사항입니다. 열려는 솔루션의 전체 경로 및 이름입니다.

## <a name="example"></a>예제

예제에서는 프로젝트를 로드하지 않고 MySln.sln 솔루션을 엽니다.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>참고 항목

- [Visual Studio의 필터링된 솔루션](../filtered-solutions.md)
- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
