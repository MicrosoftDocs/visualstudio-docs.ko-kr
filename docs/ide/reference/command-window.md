---
title: 명령 창
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb855cbed67bffc5ff2fb63b1785c577dd9fea25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570351"
---
# <a name="command-window"></a>명령 창
**명령** 창은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE(통합 개발 환경)에서 직접 명령 또는 별칭을 실행하는 데 사용됩니다. 메뉴 명령 및 메뉴에 나타나지 않는 명령을 둘 다 실행할 수 있습니다. **명령** 창을 표시하려면 **보기** 메뉴에서 **다른 창**을 선택하고 **명령 창**을 선택합니다.

## <a name="displaying-the-values-of-variables"></a>변수 값 표시
`varA` 변수의 값을 확인하려면 [인쇄 명령](../../ide/reference/print-command.md)을 사용합니다.

```cmd
>Debug.Print varA
```

물음표(?)는 `Debug.Print`에 사용되는 별칭이므로 이 명령은 다음과 같이 기록될 수도 있습니다.

```cmd
>? varA
```

이 명령의 두 버전은 모두 `varA` 변수의 값을 반환합니다.

## <a name="entering-commands"></a>명령 입력
보다 큼 기호(`>`)는 명령 창의 왼쪽 가장자리에 새 줄 프롬프트로 표시됩니다. 위쪽 화살표 및 아래쪽 화살표 키를 사용해서 이전에 실행된 명령을 스크롤합니다.

|Task|해결 방법|예제|
|----------|--------------|-------------|
|식을 계산합니다.|식 앞에 물음표(`?`)를 추가합니다.|`? myvar`|
|직접 실행 창으로 전환합니다.|`immed`를 보다 큼 기호(>) 없이 창에 입력합니다.|`immed`|
|직접 실행 창에서 명령 창으로 다시 전환합니다.|창에 `cmd`를 입력합니다.|`>cmd`|

명령 모드에서는 다음 바로 가기를 사용하여 탐색할 수 있습니다.

|작업|커서 위치|키 바인딩|
|------------| - |----------------|
|이전에 입력된 명령의 목록을 순환합니다.|입력 줄|위쪽 화살표 및 아래쪽 화살표|
|창을 위로 스크롤합니다.|명령 창 콘텐츠|Ctrl+위쪽 화살표|
|창을 아래로 스크롤합니다.|명령 창 콘텐츠|아래쪽 화살표 또는 CTRL+아래쪽 화살표|

> [!TIP]
> 명령으로 스크롤하고, 명령의 전부 또는 일부를 강조 표시하고 나서, Enter 키를 눌러 이전 명령의 전부 또는 일부를 입력 줄로 복사할 수 있습니다.

## <a name="mark-mode"></a>표시 모드
**명령** 창에서 이전 줄을 클릭하면 자동으로 표시 모드로 전환됩니다. 이 모드에서는 텍스트 편집기를 사용하는 것처럼 이전 명령의 텍스트를 선택, 편집 및 복사하고 현재 줄에 붙여넣을 수 있습니다.

## <a name="the-equals--sign"></a>같음(=) 기호
`EvaluateStatement` 명령을 입력하는 데 사용되는 창에서는 같음 기호(=)를 비교 연산자 또는 대입 연산자로 해석할지 결정합니다.

**명령** 창에서 같음 기호(=)는 비교 연산자로 해석됩니다. **명령** 창에서는 대입 연산자를 사용할 수 없습니다. 따라서 예를 들면 `varA` 및 `varB` 변수 값이 다른 경우 `>Debug.EvaluateStatement(varA=varB)` 명령은 `False` 값을 반환합니다.

이와 달리 **직접 실행** 창에서는 같음 기호(=)가 대입 연산자로 해석됩니다. 예를 들어, `>Debug.EvaluateStatement(varA=varB)` 명령은 `varA` 변수에 `varB` 변수 값을 할당합니다.

## <a name="parameters-switches-and-values"></a>매개 변수, 스위치 및 값
일부 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령에는 필수 및 선택적 인수, 스위치 및 값이 있습니다. 해당 명령을 처리할 때 특정 규칙이 적용됩니다. 용어를 설명하는 다양한 명령의 예는 다음과 같습니다.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

이 예제에서는 다음이 적용됩니다.

- `Edit.ReplaceInFiles`는 명령입니다.

- `/case` 및 `/pattern:regex`는 스위치입니다(앞에 슬래시[/] 문자가 추가됨).

- `regex`는 `/pattern` 스위치의 값이고, `/case` 스위치에는 값이 없습니다.

- `var[1-3]+` 및 `oldpar`은 매개 변수입니다.

    > [!NOTE]
    > 공백이 포함된 명령, 매개 변수, 스위치 또는 값에는 양쪽에 큰따옴표가 있어야 합니다.

스위치 및 매개 변수의 위치는 명령줄에서 자유롭게 서로 바꿀 수 있습니다. 단, 스위치와 매개 변수가 특정 순서로 사용되어야 하는 [셸](../../ide/reference/shell-command.md) 명령은 예외입니다.

명령이 지원하는 거의 모든 스위치에는 짧은(단일 문자) 형식 및 긴 형식이 있습니다. 여러 개의 짧은 형식 스위치를 그룹으로 결합할 수 있습니다. 예를 들어 `/p /g /m`은 대신 `/pgm`으로 표현될 수 있습니다.

짧은 형식 스위치를 그룹으로 결합하고 값을 지정하면 해당 값이 모든 스위치에 적용됩니다. 예를 들어 `/pgm:123`은 `/p:123 /g:123 /m:123`과 같습니다. 그룹에 있는 스위치가 값을 허용하지 않으면 오류가 발생합니다.

## <a name="escape-characters"></a>이스케이프 문자
명령줄의 캐럿(^) 문자는 캐럿 바로 뒤의 문자가 제어 문자가 아닌 문자 그대로 해석된다는 것을 의미합니다. 이스케이프 문자는 매개 변수 또는 스위치 값에 곧은 큰따옴표("), 공백, 선행 슬래시, 캐럿 등 또는 리터럴 문자를 포함하기 위해 사용할 수 있습니다(스위치 이름 제외). 예를 들면 다음과 같습니다.

```cmd
>Edit.Find ^^t /regex
```

캐럿은 따옴표 내부에 있든 외부에 있든 기능이 동일합니다. 캐럿이 줄에서 마지막 문자인 경우 무시됩니다. 여기 표시된 예제는 “^t” 패턴을 검색하는 방법을 보여 줍니다.

## <a name="use-quotes-for-path-names-with-spaces"></a>공백이 있는 경로 이름에 따옴표 사용
예를 들어 경로에 공백이 포함된 파일을 열려면 공백이 포함된 경로 또는 경로 세그먼트 주위에 큰따옴표를 넣어야 합니다(예: **C:\\"Program Files"** 또는 **"C:\Program Files"** ).

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
