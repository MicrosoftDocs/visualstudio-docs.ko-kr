---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567842"
---
# <a name="print-command"></a>인쇄 명령

식을 계산하거나 지정된 텍스트를 표시합니다.

## <a name="syntax"></a>구문

```cmd
>Debug.Print text
```

## <a name="arguments"></a>인수

`text`

필수 사항입니다. 계산할 식 또는 표시할 텍스트입니다.

## <a name="remarks"></a>설명

이 명령에 대한 별칭으로 물음표(?)를 사용할 수 있습니다. 따라서 예를 들면

```cmd
>Debug.Print expA
```

다음과 같이 작성할 수도 있습니다.

```cmd
? expA
```

이 명령의 두 버전은 모두 `expA` 식의 현재 값을 반환합니다.

## <a name="example"></a>예제

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>참고 항목

- [문 실행 명령](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
