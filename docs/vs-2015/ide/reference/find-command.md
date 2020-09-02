---
title: 찾기 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657676"
---
# <a name="find-command"></a>찾기 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**찾기 및 바꾸기** 창의 **파일에서 바꾸기** 탭에서 사용할 수 있는 옵션의 하위 집합을 사용하여 파일을 검색합니다.

## <a name="syntax"></a>구문

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>인수
 `findwhat` 필수입니다. 일치하는 텍스트입니다.

## <a name="switches"></a>스위치
 /case 또는 /c 선택 사항입니다. 대문자와 소문자가 `findwhat` 인수에서 지정된 항목과 정확하게 일치하는 경우에만 일치합니다.

 /doc 또는 /d 선택 사항입니다. 현재 문서만을 검색합니다. 사용 가능한 검색 범위(`/doc`, `/proc`, `/open` 또는 `/sel`) 중 하나만 지정합니다.

 /markall 또는 /m 선택 사항입니다. 현재 문서 내에서 검색 일치 항목을 포함하는 각 줄에 그래픽을 배치합니다.

 /open 또는 /o 선택 사항입니다. 열려 있는 모든 문서가 하나의 문서인 것처럼 검색합니다. 사용 가능한 검색 범위(`/doc`, `/proc`, `/open` 또는 `/sel`) 중 하나만 지정합니다.

 /options 또는 /t 선택 사항입니다. 현재 찾기 옵션 설정의 목록을 표시하고 검색을 수행하지 않습니다.

 /proc 또는 /p 선택 사항입니다. 현재 프로시저만을 검색합니다. 사용 가능한 검색 범위(`/doc`, `/proc`, `/open` 또는 `/sel`) 중 하나만 지정합니다.

 /reset 또는 /e 선택 사항입니다. 해당 기본 설정에 찾기 옵션을 반환하고 검색을 수행하지 않습니다.

 /sel 또는 /s 선택 사항입니다. 현재 선택 영역만을 검색합니다. 사용 가능한 검색 범위(`/doc`, `/proc`, `/open` 또는 `/sel`) 중 하나만 지정합니다.

 /up 또는 /u 선택 사항입니다. 파일의 현재 위치에서 파일의 시작 부분으로 검색합니다. 기본적으로 검색은 파일의 현재 위치에서 시작하여 파일의 끝으로 검색합니다.

 /regex 또는 /r 선택 사항입니다. 리터럴 문자가 아닌 텍스트의 패턴을 나타내는 표기법으로 `findwhat` 인수에서 미리 정의된 특수 문자를 사용합니다. 정규식 문자의 전체 목록은 [정규식](../../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

 /wild 또는 /l 선택 사항입니다. `findwhat` 인수에서 미리 정의된 특수 문자를 문자 또는 문자 시퀀스를 나타내는 표기법으로 사용합니다.

 /word 또는 /w 선택 사항입니다. 전체 단어만을 검색합니다.

## <a name="example"></a>예
 이 예제에서는 코드의 현재 선택된 섹션에서 "somestring"이라는 단어에 대해 대/소문자 구분 검색을 수행합니다.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>관련 항목
 [명령 창](../../ide/reference/command-window.md) [찾기/명령 상자](../../ide/find-command-box.md) Visual [Studio](../../ide/reference/visual-studio-commands.md) 명령 [visual studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
