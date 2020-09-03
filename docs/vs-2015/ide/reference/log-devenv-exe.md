---
title: -Log(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666835"
---
# <a name="log-devenvexe"></a>/Log(devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

문제 해결을 위해 모든 작업을 로그 파일에 기록합니다. 이 파일은 `devenv /log`를 한 번 이상 호출한 후 나타납니다. 기본적으로 로그 파일의 위치는 다음과 같습니다.

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 여기서 *Version*은 Visual Studio 버전입니다. 그러나 다른 경로 및 파일 이름을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>설명
 이 스위치는 다른 모든 스위치 뒤에서 명령 줄 끝에 나타나야 합니다.

 /log 스위치로 호출한 Visual Studio의 모든 인스턴스에 대해 로그가 작성됩니다. 스위치 없이 호출한 Visual Studio의 인스턴스에 대해서는 로그가 작성되지 않습니다.

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
