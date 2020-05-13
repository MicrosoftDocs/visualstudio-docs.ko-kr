---
title: -NoSplash(devenv.exe)
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1e8118faa743398271fb282a2603aab5fcd76b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950655"
---
# <a name="nosplash-devenvexe"></a>/NoSplash(devenv.exe)

시작 화면이 표시되지 않도록 합니다.

## <a name="syntax"></a>구문

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>인수

- *File1*

  (선택 사항) Visual Studio의 기존 인스턴스에서 열 파일입니다. Visual Studio의 인스턴스가 없으면 간소화된 창 레이아웃으로 새 인스턴스가 만들어지고 *File1*이 새 인스턴스에서 열립니다.

- *FileN*

  (선택 사항) Visual Studio의 기존 인스턴스에서 열 1개 이상의 추가 파일입니다.

## <a name="remarks"></a>설명

이 스위치는 시작 화면을 숨깁니다. 이 스위치를 벗어나면 시작 화면이 표시됩니다. 시작 화면을 추가로 검토하려면(예: VSPackage 제품 아이콘 확인) [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) 스위치를 사용합니다.

`/NoSplash` 스위치는 [/Run](run-devenv-exe.md) 또는 [/DebugExe](debugexe-devenv-exe.md) 같은 다른 스위치와 결합할 수 있습니다.

## <a name="example"></a>예제

세 가지 예제는 모두 시작 화면을 표시하지 않고 IDE를 엽니다. 두 번째 예제도 지정된 솔루션을 컴파일하고 빌드된 실행 파일을 실행합니다. 세 번째 예제는 IDE에서 디버그할 지정된 실행 파일을 엽니다.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [VSPackage 개발을 위한 Devenv 명령줄 스위치](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
