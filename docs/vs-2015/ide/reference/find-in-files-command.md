---
title: 파일에서 찾기 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651033"
---
# <a name="find-in-files-command"></a>파일에서 찾기 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**찾기 및 바꾸기** 창의 **파일에서 바꾸기** 탭에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다.

## <a name="syntax"></a>구문

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>인수
 `findwhat` 필수입니다. 일치하는 텍스트입니다.

## <a name="switches"></a>스위치
 /case 또는 /c 선택 사항입니다. 대문자와 소문자가 `findwhat` 인수에서 지정된 항목과 정확하게 일치하는 경우에만 일치합니다.

 /ext: `extensions` 선택 사항입니다. 검색할 파일의 파일 확장명을 지정합니다. 지정하지 않으면 이전 확장명이 사용됩니다(이전에 입력한 경우).

 /lookin: `searchpath` 선택 사항입니다. 검색할 디렉터리입니다. 파일에 공백이 있는 경우 전체 경로를 따옴표로 묶습니다.

 /names 또는 /n 선택 사항입니다. 일치 항목을 포함하는 파일 이름의 목록을 표시합니다.

 /options 또는 /t 선택 사항입니다. 현재 찾기 옵션 설정의 목록을 표시하고 검색을 수행하지 않습니다.

 /regex 또는 /r 선택 사항입니다. 리터럴 문자가 아닌 텍스트의 패턴을 나타내는 표기법으로 `findwhat` 인수에서 미리 정의된 특수 문자를 사용합니다. 정규식 문자의 전체 목록은 [정규식](../../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

 /reset 또는 /e 선택 사항입니다. 해당 기본 설정에 찾기 옵션을 반환하고 검색을 수행하지 않습니다.

 /stop 선택 사항입니다. 검색 작업이 진행 중인 경우 현재 검색 작업을 중단합니다. `/stop`이 지정된 경우 검색은 다른 모든 인수를 무시합니다. 예를 들어 현재 검색을 중지하려면 다음을 입력합니다.

```
>Edit.FindinFiles /stop
```

 /sub 또는 /s 선택 사항입니다. /lookin:`searchpath` 인수에서 지정된 디렉터리 내의 하위 폴더를 검색합니다.

 /text2 또는 /2 선택 사항입니다. 찾기 결과 2 창에 검색의 결과를 표시합니다.

 /wild 또는 /l 선택 사항입니다. `findwhat` 인수에서 미리 정의된 특수 문자를 문자 또는 문자 시퀀스를 나타내는 표기법으로 사용합니다.

 /word 또는 /w 선택 사항입니다. 전체 단어만을 검색합니다.

## <a name="example"></a>예
 이 예제에서는 "내 Visual Studio 프로젝트" 폴더에 있는 모든 .cls 파일에서 btnCancel을 검색하고 찾기 결과 2 창에서 일치 항목 정보를 표시합니다.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>관련 항목
 [파일에서 찾기](../../ide/find-in-files.md) [명령 창](../../ide/reference/command-window.md) [찾기/명령 상자](../../ide/find-command-box.md) [visual studio](../../ide/reference/visual-studio-commands.md) 명령 [visual studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
