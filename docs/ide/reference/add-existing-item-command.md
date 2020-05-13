---
title: 기존 항목 추가 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585706"
---
# <a name="add-existing-item-command"></a>기존 항목 추가 명령
현재 솔루션에 기존 파일을 추가하고 엽니다.

## <a name="syntax"></a>구문

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>인수
`filename`\
필수 사항입니다. 현재 솔루션에 추가할 항목의 전체 경로 및 파일 이름(확장명 포함)입니다. 파일 경로 또는 파일 이름은 공백을 포함하며 전체 경로를 따옴표로 묶습니다.

## <a name="switches"></a>스위치
/e: `editorname`\
(선택 사항) 파일이 열리는 편집기의 이름입니다. 편집기 이름을 제공하지 않고 인수를 지정한 경우 **연결 프로그램** 대화 상자가 나타납니다.

/e:`editorname` 인수 구문은 **연결 프로그램 대화 상자**에 따옴표로 묶여 나타나는 순서대로 편집기 이름을 사용합니다. 예를 들어 소스 코드 편집기에서 스타일시트를 열려면 /e:`editorname` 인수에 대해 다음과 같이 입력합니다.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>설명
입력 시 자동 완성에서 올바른 경로와 파일 이름을 찾으려고 합니다.

## <a name="example"></a>예제
이 예제에서는 Form1.frm 파일을 현재 솔루션에 추가합니다.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
