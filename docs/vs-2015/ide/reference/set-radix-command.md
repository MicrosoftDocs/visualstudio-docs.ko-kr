---
title: 기수 설정 명령 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665413"
---
# <a name="set-radix-command"></a>기수 설정 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

정수 값을 표시하는 데 사용할 숫자 기준을 설정하거나 반환합니다.

## <a name="syntax"></a>구문

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>인수
 `10` 또는 또는 또는 `16` `hex` `dec` 옵션입니다. 10진수(10 또는 dec) 또는 16진수(16 또는 hex)를 나타냅니다. 인수를 생략하면 현재 기수 값이 반환됩니다.

## <a name="example"></a>예
 이 예제에서는 16진수 형식의 정수 값을 표시하도록 환경을 설정합니다.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>관련 항목
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md) [명령 창](../../ide/reference/command-window.md) [찾기/명령 상자](../../ide/find-command-box.md) [visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
