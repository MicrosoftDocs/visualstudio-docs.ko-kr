---
title: -Log(devenv.exe)
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
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595464"
---
# <a name="log-devenvexe"></a>/Log(devenv.exe)

문제 해결을 위해 모든 작업을 로그 파일에 기록합니다. 이 파일은 `devenv /log`를 한 번 이상 호출한 후 나타납니다. 기본적으로 로그 파일은 다음 위치에 있습니다.

**%APPDATA%\\Microsoft\\VisualStudio\\** \<버전\> **\\ActivityLog.xml**

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
