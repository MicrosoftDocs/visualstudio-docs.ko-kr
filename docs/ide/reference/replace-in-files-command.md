---
title: 파일에서 바꾸기 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565476"
---
# <a name="replace-in-files-command"></a>파일에서 바꾸기 명령
**찾기 및 바꾸기** 창의 **파일에서 바꾸기**에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일의 텍스트를 바꿉니다.

## <a name="syntax"></a>구문

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>인수
`findwhat`

필수 사항입니다. 일치하는 텍스트입니다.

`replacewith`

필수 사항입니다. 일치된 텍스트를 대체할 텍스트입니다.

## <a name="switches"></a>스위치
/all 또는 /a

(선택 사항) 검색 텍스트의 모든 항목을 대체 텍스트로 바꿉니다.

/case 또는 /c

(선택 사항) 대문자와 소문자가 `findwhat` 인수에서 지정된 항목과 정확하게 일치하는 경우에만 일치합니다.

/ext: `extensions`

(선택 사항) 검색할 파일의 파일 확장명을 지정합니다.

/keep 또는 /k

(선택 사항) 모든 수정된 파일이 열려 있도록 지정합니다.

/lookin: `searchpath`

(선택 사항) 검색할 디렉터리입니다. 파일에 공백이 있는 경우 전체 경로를 따옴표로 묶습니다.

/options 또는 /t

(선택 사항) 현재 찾기 옵션 설정의 목록을 표시하고 검색을 수행하지 않습니다.

/regex 또는 /r

(선택 사항) 리터럴 문자가 아닌 텍스트의 패턴을 나타내는 표기법으로 `findwhat` 인수에서 미리 정의된 특수 문자를 사용합니다. 정규식 문자의 전체 목록은 [정규식](../../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

/reset 또는 /e

(선택 사항) 해당 기본 설정에 찾기 옵션을 반환하고 검색을 수행하지 않습니다.

/stop

(선택 사항) 검색 작업이 진행 중인 경우 현재 검색 작업을 중단합니다. `/stop`이 지정된 경우 대체는 다른 모든 인수를 무시합니다. 예를 들어 현재 대체를 중지하려면 다음을 입력합니다.

```
>Edit.ReplaceinFiles /stop
```

/sub 또는 /s

(선택 사항) /lookin:`searchpath` 인수에서 지정된 디렉터리 내의 하위 폴더를 검색합니다.

/text2 또는 /2

(선택 사항) **찾기 결과 2** 창에 대체의 결과를 표시합니다.

/wild 또는 /l

(선택 사항) `findwhat` 인수에서 미리 정의된 특수 문자를 문자 또는 문자 시퀀스를 나타내는 표기법으로 사용합니다.

/word 또는 /w

(선택 사항) 단어 단위로 검색합니다.

## <a name="example"></a>예제
이 예제에서는 `btnCancel`을 검색하고, "내 Visual Studio 프로젝트" 폴더에 있는 모든 .cls 파일에서 `btnReset`으로 바꾸고, **찾기 결과 2** 창에서 대체 정보를 표시합니다.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>참고 항목

- [텍스트 찾기 및 바꾸기](../../ide/finding-and-replacing-text.md)
- [파일에서 바꾸기](../../ide/replace-in-files.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
