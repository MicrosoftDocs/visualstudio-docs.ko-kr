---
title: 현재 스레드 설정 명령
description: 현재 스레드 설정 명령에 대해 알아보고 지정한 스레드를 현재 스레드로 설정하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cb58bf8751eb4299ecede18bac83770c3a7df96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957740"
---
# <a name="set-current-thread-command"></a>현재 스레드 설정 명령
지정한 스레드를 현재 스레드로 설정합니다.

## <a name="syntax"></a>구문

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>인수
`index`

필수 요소. 해당 인덱스로 스레드를 선택합니다.

## <a name="example"></a>예제

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)