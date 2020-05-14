---
title: 현재 프로세스 설정
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3440c66d79fef3eac3744681870c9ce1ed0e97b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593553"
---
# <a name="set-current-process"></a>현재 프로세스 설정
디버거에서 지정한 프로세스를 활성 프로세스로 설정합니다.

## <a name="syntax"></a>구문

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>인수
`index`

필수 사항입니다. 프로세스의 인덱스입니다.

## <a name="remarks"></a>설명
디버그하는 동안 여러 프로세스에 연결할 수 있지만 한 번에 프로세스 하나만 디버거에서 활성화됩니다. `SetCurrentProcess` 명령을 사용하여 활성 프로세스를 설정할 수 있습니다.

## <a name="example"></a>예제

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
