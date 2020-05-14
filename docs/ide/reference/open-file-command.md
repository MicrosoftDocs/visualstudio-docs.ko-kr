---
title: 파일 열기 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e29e3182a19c9f3a667d41725327110b415fd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591517"
---
# <a name="open-file-command"></a>파일 열기 명령

기존 파일을 열고 편집기를 지정할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>인수

`filename`

필수 사항입니다. 열려는 파일의 전체 또는 부분 경로와 파일 이름입니다. 공백을 포함한 경로는 따옴표로 묶어야 합니다.

## <a name="switches"></a>스위치

/e:`editorname`

(선택 사항) 파일이 열리는 편집기의 이름입니다. 편집기 이름을 제공하지 않고 인수를 지정한 경우 **연결 프로그램** 대화 상자가 나타납니다.

/e:`editorname` 인수 구문은 연결 프로그램 대화 상자에 따옴표로 묶여 나타나는 편집기 이름을 사용합니다.

예를 들어 소스 코드 편집기에서 파일을 열려면 /e:`editorname` 인수에 다음과 같이 입력합니다.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>설명

경로를 입력하여 자동 완성에서 올바른 경로와 파일 이름을 찾으려고 합니다.

## <a name="example"></a>예제

이 예제에서는 소스 코드 편집기에서 스타일 파일을 "Test1.css"를 엽니다.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [직접 실행 창](../../ide/reference/immediate-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
