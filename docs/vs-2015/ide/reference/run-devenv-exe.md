---
title: -Run(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665515"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정한 프로젝트 또는 솔루션을 컴파일하고 실행합니다.

## <a name="syntax"></a>구문

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>인수
 `SolutionName` 필수입니다. 솔루션 파일의 전체 경로 및 이름입니다.

 `ProjectName` 필수입니다. 프로젝트 파일의 전체 경로 및 이름입니다.

## <a name="remarks"></a>설명
 활성 솔루션 구성에 대해 지정된 설정에 따라 지정된 프로젝트 또는 솔루션을 컴파일하고 실행합니다. 이 스위치는 IDE(통합 개발 환경)를 시작하고 프로젝트 또는 솔루션 실행이 완료된 후 활성 상태로 둡니다.

- 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

- 오류를 포함한 요약 정보는 **명령** 창 또는 `/out` 스위치로 지정된 로그 파일에 표시할 수 있습니다.

## <a name="example"></a>예
 이 예제에서는 활성 배포 구성을 사용하여 `MySolution` 솔루션을 실행합니다.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
