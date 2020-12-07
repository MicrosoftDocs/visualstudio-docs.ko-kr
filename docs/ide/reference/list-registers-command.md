---
title: 레지스터 목록 표시 명령
description: 레지스터 목록 표시 명령에 대해 알아보고, 선택된 레지스터의 값을 등록하고 표시할 레지스터의 목록을 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5459ded60ea90ae00a3f943f829065a82548d160
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305301"
---
# <a name="list-registers-command"></a>레지스터 목록 표시 명령
선택된 레지스터의 값을 등록하고 표시할 레지스터의 목록을 수정합니다.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>스위치
/Display [{`register`&#124;`registerGroup`}...]

지정된 `register` 또는 `registerGroup`의 값을 표시합니다. `register` 또는 `registerGroup`를 지정하지 않은 경우 레지스터의 기본 목록이 표시됩니다. 스위치를 지정하지 않은 경우 동작은 동일합니다. 다음은 그 예입니다. 

`Debug.ListRegisters /Display eax`

위의 식은 아래의 식과 동일합니다.

`Debug.ListRegisters eax`

/List

목록에서 레지스터 그룹을 모두 표시합니다.

/Watch [{`register`&#124;`registerGroup`}...]

하나 이상의 `register` 또는 `registerGroup` 값을 목록에 추가합니다.

/Unwatch [{`register`&#124;`registerGroup`}...]

하나 이상의 `register` 또는 `registerGroup` 값을 목록에서 제거합니다.

## <a name="remarks"></a>설명
별칭 `r`을 `Debug.ListRegisters` 대신 사용할 수 있습니다.

## <a name="example"></a>예제
이 예제에서는 `Debug.ListRegisters` 별칭 `r`을 사용하여 `Flags` 레지스터 그룹의 값을 표시합니다.

```cmd
r /Display Flags
```

## <a name="see-also"></a>추가 정보

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [디버깅 기본 사항: 레지스터 창](../../debugger/debugging-basics-registers-window.md)
- [방법: 레지스터 창 사용](../../debugger/how-to-use-the-registers-window.md)
