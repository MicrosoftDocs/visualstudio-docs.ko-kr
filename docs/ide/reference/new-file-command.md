---
title: 새 파일 명령
description: 새 파일 명령 및 새 파일을 만들어 여는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a75678e8f29a282deef6f3d443a6e1c96d3edd7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967269"
---
# <a name="new-file-command"></a>새 파일 명령
새 파일을 만들고 엽니다. 파일은 기타 파일 폴더 아래에 나타납니다.

## <a name="syntax"></a>구문

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>인수
`filename`

선택 사항입니다. 파일의 이름입니다. 이름을 제공하지 않으면 기본 이름이 제공됩니다. 템플릿 이름이 나열되지 않으면 텍스트 파일이 만들어집니다.

## <a name="switches"></a>스위치
/t:`templatename`\
선택 사항입니다. 만들 파일의 형식을 지정합니다.

/t:`templatename` 인수 구문은 새 파일 대화 상자에 있는 정보를 미러링합니다. 뒤에 백슬래시(`\`)가 오는 범주 이름 및 템플릿 이름을 입력하고 전체 문자열을 따옴표로 묶습니다.

예를 들어 새 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 원본 파일을 만들려면 /t:`templatename` 인수에 대해 다음과 같이 입력합니다.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

위의 예제에서는 C++ 파일 템플릿이 **새 파일** 대화 상자의 Visual C++ 범주 아래에 있는지 나타냅니다.

/e:`editorname`\
선택 사항입니다. 파일이 열리는 편집기의 이름입니다. 편집기 이름을 제공하지 않고 인수를 지정한 경우 **연결 프로그램** 대화 상자가 나타납니다.

/e:`editorname` 인수 구문은 연결 프로그램 대화 상자에 따옴표로 묶여 나타나는 편집기 이름을 사용합니다.

예를 들어 소스 코드 편집기에서 파일을 열려면 /e:`editorname` 인수에 다음과 같이 입력합니다.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>예제
이 예제에서는 “test1.htm”이라는 새 웹 페이지를 만들고 소스 코드 편집기에서 엽니다.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>추가 정보

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [직접 실행 창](../../ide/reference/immediate-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
