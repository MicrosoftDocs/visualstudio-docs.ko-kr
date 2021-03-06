---
title: -DoNotLoadProjects(devenv.exe)
description: DoNotLoadProjects devenv 명령줄 스위치를 사용하여 프로젝트를 로드하지 않고 지정된 솔루션을 여는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907595"
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

필수 요소. 열려는 솔루션의 전체 경로 및 이름입니다.

## <a name="example"></a>예제

예제에서는 프로젝트를 로드하지 않고 MySln.sln 솔루션을 엽니다.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>참고 항목

- [Visual Studio의 필터링된 솔루션](../filtered-solutions.md)
- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
