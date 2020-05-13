---
title: 간략한 조사식 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f6382a79884bf8c3891a3a191b594bf183efb62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565632"
---
# <a name="quick-watch-command"></a>간략한 조사식 명령
[간략한 조사식](../../debugger/watch-and-quickwatch-windows.md) 창의 식 필드에 선택하거나 지정한 텍스트를 표시합니다. 이 대화 상자를 사용하여 디버거에서 인식되는 변수 또는 식의 현재 값이나 레지스터의 콘텐츠를 계산할 수 있습니다. 또한 비const 변수 값 또는 레지스터 콘텐츠를 변경할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>인수

`text`\
(선택 사항) **간략한 조사식** 대화 상자에 추가할 텍스트입니다.

## <a name="remarks"></a>설명

`text`가 생략되면 커서에서 현재 선택된 텍스트 또는 단어가 조사식 창에 추가됩니다.

## <a name="example"></a>예제

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 조사식 및 간략한 조사식 창을 사용하여 변수에 대한 조사식 설정](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
