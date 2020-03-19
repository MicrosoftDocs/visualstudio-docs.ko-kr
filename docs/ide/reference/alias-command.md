---
title: 별칭 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596907"
---
# <a name="alias-command"></a>별칭 명령
전체 명령에 대한 새 별칭, 전체 명령 및 인수에 대한 새 별칭, 또 다른 별칭을 만듭니다.

> [!TIP]
> 인수 없이 `>alias`를 입력하면 별칭의 최신 목록과 해당 정의가 표시됩니다.

## <a name="syntax"></a>구문

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>인수
`aliasname`\
(선택 사항) 새 별칭에 대한 이름입니다. `aliasname`에 대해 제공된 값이 없으면 현재 별칭 목록과 해당 정의가 나타납니다.

`aliasstring`\
(선택 사항) 전체 명령 이름 또는 기존 별칭과 별칭으로 만들려는 매개 변수입니다. `aliasstring`에 대해 제공되는 값이 없으면 지정된 별칭에 대한 별칭 이름 및 별칭 문자열이 표시됩니다.

## <a name="switches"></a>스위치
/delete, /del 또는 /d\
(선택 사항) 지정된 별칭을 삭제하여 자동 완성에서 제거합니다.

/reset\
(선택 사항) 미리 정의된 별칭 목록을 원래 설정으로 다시 설정합니다. 즉, 미리 정의된 모든 별칭을 복원하고 모든 사용자 정의 별칭을 제거합니다.

## <a name="remarks"></a>설명
별칭은 명령을 나타내므로 명령줄 시작 부분에 있어야 합니다.

이 명령을 실행할 때는 별명 뒤가 아닌 명령 바로 다음에 스위치를 포함해야 합니다. 그렇지 않으면 스위치 자체가 별명 문자열의 일부로 포함됩니다.

`/reset` 스위치는 별칭을 복원하기 전에 확인을 요청합니다. `/reset`의 약식은 없습니다.

## <a name="examples"></a>예
이 예제에서는 Edit.MakeUpperCase 전체 명령에 대해 `upper`라는 새 별칭을 만듭니다.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

이 예제에서는 별칭 `upper`를 삭제합니다.

```cmd
>Tools.alias /delete upper
```

이 예제에서는 모든 최신 별칭 및 정의 목록을 표시합니다.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
