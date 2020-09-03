---
title: 파일 이름 확장명에 대 한 동사를 등록 하는 중 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701529"
---
# <a name="register-verbs-for-file-name-extensions"></a>파일 이름 확장명에 대 한 동사 등록
일반적으로 응용 프로그램과 파일 이름 확장명을 연결 하는 경우 사용자가 파일을 두 번 클릭할 때 발생 하는 기본 작업이 있습니다. 이 기본 작업은 작업에 해당 하는 열기와 같은 동사에 연결 됩니다.

 **HKEY_CLASSES_ROOT \{ progid} \shell**에 있는 셸 키를 사용 하 여 확장 프로그램에 대 한 progid (프로그래밍 식별자)와 연결 된 동사를 등록할 수 있습니다. 자세한 내용은 [파일 형식](/windows/desktop/shell/fa-file-types)을 참조 하세요.

## <a name="register-standard-verbs"></a>표준 동사 등록
 운영 체제는 다음 표준 동사를 인식 합니다.

- 열기

- 편집

- 재생

- 인쇄

- 미리 보기

  가능 하면 표준 동사를 등록 합니다. 가장 일반적인 선택은 Open 동사입니다. 파일 열기와 파일 편집 사이에 명백한 차이가 있는 경우에만 편집 동사를 사용 합니다. 예를 들어 *.htm* 파일을 열면 브라우저가 브라우저에 표시 되는 반면 *.htm* 파일을 편집 하면 HTML 편집기가 시작 됩니다. 표준 동사는 운영 체제 로캘로 지역화 됩니다.

> [!NOTE]
> 표준 동사를 등록할 때 열기 키에 대 한 기본값을 설정 하지 마세요. 기본값은 메뉴의 표시 문자열을 포함 합니다. 운영 체제는 표준 동사에 대해이 문자열을 제공 합니다.

 사용자가 파일을 열 때의 새 인스턴스를 시작 하려면 프로젝트 파일을 등록 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 다음 예제에서는 프로젝트의 표준 동사 등록을 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 기존 인스턴스에서 파일을 열려면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DDEEXEC 키를 등록 합니다. 다음 예제에서는 .cs 파일의 표준 동사 등록을 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* .

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>기본 동사 설정
 기본 동사는 사용자가 Windows 탐색기에서 파일을 두 번 클릭할 때 실행 되는 동작입니다. 기본 동사는 **HKEY_CLASSES_ROOT \\ *progid*\shell** 키에 대 한 기본값으로 지정 된 동사입니다. 값을 지정 하지 않으면 기본 동사는 **HKEY_CLASSES_ROOT \\ *progid*\shell** 키 목록에 지정 된 첫 번째 동사입니다.

> [!NOTE]
> Side-by-side 배포에서 확장에 대 한 기본 동사를 변경 하려는 경우 설치 및 제거에 대 한 영향을 고려해 야 합니다. 설치 하는 동안 원래 기본값을 덮어씁니다.

## <a name="see-also"></a>추가 정보
- [Side-by-side 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md)
