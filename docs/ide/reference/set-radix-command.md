---
title: 기수 설정 명령
description: 기수 설정 명령에 대해 알아보고 정수 값을 표시하는 데 사용할 숫자 기준을 설정하거나 반환하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957688"
---
# <a name="set-radix-command"></a>기수 설정 명령
정수 값을 표시하는 데 사용할 숫자 기준을 설정하거나 반환합니다.

## <a name="syntax"></a>구문

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>인수
`10`, `16`, `hex` 또는 `dec`

선택 사항입니다. 10진수(10 또는 dec) 또는 16진수(16 또는 hex)를 나타냅니다. 인수를 생략하면 현재 기수 값이 반환됩니다.

## <a name="example"></a>예
이 예제에서는 16진수 형식의 정수 값을 표시하도록 환경을 설정합니다.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)