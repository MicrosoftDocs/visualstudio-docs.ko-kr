---
title: -Command(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 434b2ad0f2a6ca4d84c6d82bf9a1a85876a4d975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570403"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Visual Studio IDE를 시작한 후 지정된 명령을 실행합니다.

## <a name="syntax"></a>구문

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>인수

*CommandName*

필수 요소. Visual Studio 명령 또는 해당 별칭의 전체 이름으로, 큰따옴표로 묶습니다. 명령 및 별칭 구문에 대한 자세한 내용은 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)을 참조하세요.

## <a name="remarks"></a>설명

시작이 완료된 후 IDE는 명명된 명령을 실행합니다.

::: moniker range="vs-2017"

이 스위치를 사용하면 시작 시 IDE가 시작 페이지를 표시하지 않습니다.

::: moniker-end

추가 기능이 명령을 표시할 경우에는 이 스위치를 사용하여 명령줄에서 추가 기능을 시작할 수 있습니다. 자세한 내용은 [방법: 추가 기능 관리자를 사용하여 추가 기능 제어](/previous-versions/xwdatdwh(v=vs.140))를 참조하세요.

## <a name="example"></a>예제

첫 번째 예제에서는 Visual Studio를 시작하고 Open Favorite Files(즐겨찾기 파일 열기) 매크로를 자동으로 실행합니다.

두 번째 예제에서는 IDE 내에서 웹 브라우징 탭을 열고 Microsoft Docs 사이트로 이동합니다.

세 번째 예제에서는 `some_file.cs`라는 새 파일을 만들고 코드 편집기에서 엽니다.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>참조

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [명령 창](command-window.md)
