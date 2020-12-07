---
title: -Log(devenv.exe)
description: Log devenv 명령줄 스위치를 사용하여 문제 해결을 위해 모든 작업을 로그 파일에 기록하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040578"
---
# <a name="log-devenvexe"></a>/Log(devenv.exe)

문제 해결을 위해 모든 작업을 로그 파일에 기록합니다. 이 파일은 `devenv /log`를 한 번 이상 호출한 후 나타납니다. 기본적으로 로그 파일은 다음 위치에 있습니다.

**%APPDATA%\\Microsoft\\VisualStudio\\** \<Version\> **\\ActivityLog.xml**

여기서 \<Version\>은 Visual Studio 버전입니다. 그러나 다른 경로 및 파일 이름을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>인수

- *NameOfLogFile*

  필수 사항입니다. 저장할 로그 파일의 전체 경로 및 이름입니다.

## <a name="remarks"></a>설명

이 스위치는 다른 모든 스위치 뒤에서 명령 줄 끝에 나타나야 합니다.

`/Log` 스위치를 사용하여 연 Visual Studio의 모든 인스턴스에 대한 로그만 작성됩니다.

## <a name="example"></a>예제

이 예제는 사용자 홈 디렉터리에 있는 `MyVSLog.xml` 파일에 로깅을 전달합니다.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
