---
title: -Clean(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 043e9373f242523b7925a9ae775be6789f7cfc20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660880"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 중간 파일 및 출력 디렉터리를 정리합니다.

## <a name="syntax"></a>구문

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>인수
 `FileName` 필수입니다. 솔루션 파일 또는 프로젝트 파일의 전체 경로 및 이름입니다.

 /project `ProjName` 선택 사항입니다. 솔루션 내에 있는 프로젝트 파일의 경로와 이름입니다. `SolutionName` 폴더에서 프로젝트 파일, 프로젝트의 표시 이름 또는 프로젝트 파일의 전체 경로와 이름까지의 상대 경로를 입력할 수 있습니다.

 /projectconfig `ProjConfigName` 선택 사항입니다. `/project` 정리 시 사용할 프로젝트 빌드 구성 이름입니다.

## <a name="remarks"></a>설명
 이 스위치는 IDE(통합 개발 환경)내에서 **솔루션 정리** 메뉴 명령과 동일한 기능을 수행합니다.

 공백을 포함하는 문자열은 큰따옴표로 묶습니다.

 오류를 포함한 정리 및 빌드에 대한 요약 정보는 **명령** 창 또는 `/out` 스위치로 지정된 로그 파일에 표시할 수 있습니다.

## <a name="example"></a>예
 첫 번째 예제는 솔루션 파일에 지정된 기본 구성을 사용하여 `MySolution` 솔루션을 정리합니다.

 두 번째 예제에서는 `MySolution`의 `Debug` 솔루션 구성 내에 있는 `Debug` 프로젝트 빌드 구성을 사용하여 `CSharpConsoleApp` 프로젝트를 정리합니다.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
