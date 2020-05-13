---
title: 프로젝트 열기 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565814"
---
# <a name="open-project-command"></a>프로젝트 열기 명령

기존 프로젝트 또는 솔루션을 엽니다.

## <a name="syntax"></a>구문

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>인수

`filename`

필수 사항입니다. 열려는 프로젝트 또는 솔루션의 전체 경로와 파일 이름입니다.

> [!NOTE]
> `filename` 인수 구문에서 공백을 포함하는 경로에는 따옴표를 사용해야 합니다.

## <a name="remarks"></a>설명

입력 시 자동 완성에서 올바른 경로와 파일 이름을 찾으려고 합니다.

디버깅 중에는 이 명령을 사용할 수 없습니다.

## <a name="example"></a>예제

다음 예제에서는 Visual Basic 프로젝트 **Test1**을 엽니다.

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
