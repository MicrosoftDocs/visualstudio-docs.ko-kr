---
title: 직접 실행 창
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b21cdb9136abe1e960e5b74bbf09e7d1694519d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568960"
---
# <a name="immediate-window"></a>직접 실행 창

**직접 실행** 창을 사용하여 식을 디버깅 및 계산하고, 명령문을 실행하고, 변수 값을 인쇄합니다. **직접 실행** 창에서는 현재 선택한 프로젝트를 빌드하고 사용하여 식을 계산합니다.

**직접 실행** 창을 표시하려면 편집할 프로젝트를 연 다음, **디버그** > **Windows** > **직접 실행**을 열거나 **Ctrl**+**Alt**+**I**를 누릅니다. **명령** 창에 **Debug.Immediate**를 입력할 수도 있습니다.

**직접 실행** 창은 IntelliSense를 지원합니다.

## <a name="display-the-values-of-variables"></a>변수 값 표시

**직접 실행** 창은 애플리케이션을 디버깅할 때 특히 유용합니다. 예를 들어, `varA` 변수의 값을 확인하려면 [인쇄 명령](../../ide/reference/print-command.md)을 사용할 수 있습니다.

```cmd
>Debug.Print varA
```

물음표(?)는 `Debug.Print`에 사용되는 별칭이므로 이 명령은 다음과 같이 기록될 수도 있습니다.

```cmd
? varA
```

이 명령의 두 버전은 모두 `varA` 변수의 값을 반환합니다.

> [!TIP]
> **즉시 실행** 창에서 Visual Studio 명령을 실행하려면 명령 앞에 보다 큼 기호(>)를 추가해야 합니다. 여러 개의 명령을 입력하려면 [명령 창](command-window.md)으로 전환합니다.

## <a name="design-time-expression-evaluation"></a>디자인 타임 식 계산

**직접 실행** 창을 사용하여 디자인 타임에 함수 또는 서브루틴을 실행할 수 있습니다.

### <a name="execute-a-function-at-design-time"></a>디자인 타임에 함수 실행

1. 다음 코드를 Visual Basic 콘솔 앱에 복사합니다.

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. **디버그** 메뉴에서 **Windows** > **직접 실행**을 선택합니다.

3. **직접 실행 창**에 `?MyFunction(2)`을 입력하고 **Enter** 키를 누릅니다.

    **직접 실행** 창이 `MyFunction`을 실행하고 `4`를 표시합니다.

함수 또는 서브루틴에 중단점이 포함된 경우 Visual Studio는 적절한 지점에서 실행을 중단합니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. 자세한 내용은 [연습: 디자인 타임에 디버깅](../../debugger/walkthrough-debugging-at-design-time.md)을 참조하세요.

Office용 Visual Studio Tools 프로젝트, 웹 프로젝트, 스마트 디바이스 프로젝트 및 SQL 프로젝트를 포함하여 실행 환경을 시작해야 하는 프로젝트 형식에서 디자인 타임 식 계산을 사용할 수 없습니다.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>다중 프로젝트 솔루션에서 디자인 타임 식 계산

디자인 타임 식 계산에 대한 컨텍스트를 설정할 때 Visual Studio는 솔루션 탐색기에서 현재 선택된 프로젝트를 참조합니다. 솔루션 탐색기에서 선택된 프로젝트가 없는 경우 Visual Studio는 시작 프로젝트에 대해 함수를 평가하려고 합니다. 현재 컨텍스트에서 함수를 계산할 수 없는 경우 오류 메시지를 받게 됩니다. 솔루션을 위해 시작 프로젝트가 아닌 프로젝트에서 함수를 계산하려고 하는데 오류를 받은 경우 솔루션 탐색기에서 프로젝트를 선택하고 계산을 다시 시도하세요.

## <a name="enter-commands"></a>명령 입력

**즉시 실행** 창에서 Visual Studio 명령을 실행할 경우 보다 큼 기호(>)를 입력하세요. **위쪽 화살표** 및 **아래쪽 화살표** 키를 사용하여 이전에 사용한 명령을 스크롤합니다.

|작업|솔루션|예제|
|----------|--------------|-------------|
|식을 계산합니다.|식 앞에 물음표(?)를 추가합니다.|`? a+b`|
|직접 실행 모드(단일 명령 실행)에 있는 동안 명령 모드를 일시적으로 입력합니다.|앞에 보다 큼 기호(>)를 추가하여 명령을 입력합니다.|`>alias`|
|명령 창으로 전환합니다.|앞에 보다 큼 기호(>)를 추가하여 창에 `cmd`를 입력합니다.|`>cmd`|
|직접 실행 창으로 다시 전환합니다.|`immed`를 보다 큼 기호(>) 없이 창에 입력합니다.|`immed`|

## <a name="mark-mode"></a>표시 모드

**즉시 실행** 창에서 이전 줄을 클릭하면 자동으로 표시 모드로 전환됩니다. 이 모드에서는 텍스트 편집기를 사용하는 것처럼 이전 명령의 텍스트를 선택, 편집 및 복사하고 현재 줄에 붙여넣을 수 있습니다.

## <a name="examples"></a>예

다음 예제에서는 Visual Basic 프로젝트의 **직접 실행** 창에서 네 개의 식과 그 결과를 보여줍니다.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>첫째 예외 알림

일반 설정 구성에서 첫째 예외 알림이 **즉시 실행** 창에 표시됩니다.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>직접 실행 창에서 첫째 예외 알림 전환

1. **보기** 메뉴에서 **기타 창**을 클릭하고 **출력**을 클릭합니다.

2. **출력** 창의 텍스트 영역을 마우스 오른쪽 단추로 클릭한 다음, **예외 메시지**를 선택 또는 선택 취소합니다.

## <a name="see-also"></a>참조

- [디버거로 코드 탐색](../../debugger/navigating-through-code-with-the-debugger.md)
- [명령 창](../../ide/reference/command-window.md)
- [디버거 소개](../../debugger/debugger-feature-tour.md)
- [연습: 디자인 타임에 디버깅](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio에서 정규식 사용](../../ide/using-regular-expressions-in-visual-studio.md)
