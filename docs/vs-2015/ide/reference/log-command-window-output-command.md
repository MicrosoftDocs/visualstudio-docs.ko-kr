---
title: 명령 창 출력 로그 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666871"
---
# <a name="log-command-window-output-command"></a>명령 창 출력 로그 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**명령** 창의 모든 입력 및 출력을 파일로 복사합니다.

## <a name="syntax"></a>구문

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>인수
 `filename` 선택 사항입니다. 로그 파일의 이름입니다. 기본적으로 파일은 사용자의 프로필 폴더에 만들어집니다. 파일 이름이 이미 존재하는 경우 로그는 기존 파일의 끝에 추가됩니다. 파일이 지정되지 않은 경우 지정된 마지막 파일이 사용됩니다. 이전 파일이 없는 경우 cmdline.log라는 기본 로그 파일이 만들어집니다.

> [!TIP]
> 로그 파일이 저장되는 위치를 변경하려면 경로에 공백이 있는 경우 따옴표로 묶인 파일의 전체 경로를 입력합니다.

## <a name="switches"></a>스위치
 /on 옵션입니다. 지정된 파일에서 **명령** 창에 대한 로그를 시작하고 새 정보를 포함한 파일을 추가합니다.

 /off 선택 사항입니다. **명령** 창에 대한 로그를 중지합니다.

 /overwrite 선택 사항입니다. `filename` 인수에서 지정된 파일이 기존 파일과 일치하는 경우 파일을 덮어씁니다.

## <a name="remarks"></a>설명
 파일이 지정되지 않은 경우 기본적으로 cmdline.log 파일이 만들어집니다. 기본적으로 이 명령에 대한 별칭은 Log입니다.

## <a name="examples"></a>예제
 이 예제에서는 cmdlog라는 새 로그 파일을 만들고 명령 로그를 시작합니다.

```
>Tools.LogCommandWindowOutput cmdlog
```

 이 예제에서는 로깅 명령을 중지합니다.

```
>Tools.LogCommandWindowOutput /off
```

 이 예제에서는 이전에 사용된 로그 파일에서 명령의 로깅을 다시 시작합니다.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>관련 항목
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md) [명령 창](../../ide/reference/command-window.md) [찾기/명령 상자](../../ide/find-command-box.md) [visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
