---
title: -UseEnv(devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596398"
---
# <a name="useenv-devenvexe"></a>/UseEnv(devenv.exe)

Visual Studio를 시작하고 컴파일을 위해 특정 환경 변수를 로드합니다.

> [!NOTE]
> **C++ 워크로드로 데스크톱 개발**을 사용하여 이 스위치를 설치합니다.

## <a name="syntax"></a>구문

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>인수

- *SolutionName*

  솔루션 파일의 전체 경로 및 이름입니다.

- *ProjectName*

  프로젝트 파일의 전체 경로 및 이름입니다.

## <a name="remarks"></a>설명

이 스위치는 **VC++ 디렉터리**의 프로젝트 속성에서 Visual Studio IDE에 영향을 줍니다. `/UseEnv` 스위치를 지정하면 **VC++ 디렉터리** 노드는 PATH, INCLUDE, LIBPATH 및 LIB 환경 변수의 값을 표시합니다. **소스 디렉터리** 및 **제외 디렉터리**의 값도 표시합니다. 스위치를 지정하지 않으면 노드는 환경 변수를 다음 5개의 디렉터리 값으로 바꿉니다. **실행 파일 디렉터리**, **포함 디렉터리**, **참조 디렉터리**, **라이브러리 디렉터리** 및 **라이브러리 WinRT 디렉터리**.

> [!TIP]
> C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하여 프로젝트 속성에 액세스합니다. **속성 페이지** 대화 상자에서 **구성 속성**, **VC++ 디렉터리**를 차례로 선택합니다.

이 스위치로 프로젝트 이름을 지정하면 프로젝트의 부모 솔루션 내에 있는 모든 프로젝트의 환경 변수가 표시됩니다.

## <a name="example"></a>예제

다음 예제에서는 Visual Studio를 시작하고 환경 변수를 `MySolution` 솔루션의 속성 페이지에 로드합니다.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>참조

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [VC++ 디렉터리 속성 페이지(Windows)](/cpp/build/reference/vcpp-directories-property-page)
