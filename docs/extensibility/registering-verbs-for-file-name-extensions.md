---
title: 파일 이름 확장자를 위한 동사 등록 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701529"
---
# <a name="register-verbs-for-file-name-extensions"></a>파일 이름 확장명에 대한 동사 등록
일반적으로 응용 프로그램과 파일 이름 확장자를 연결하면 사용자가 파일을 두 번 클릭할 때 발생하는 기본 설정 작업이 있습니다. 이 기본 설정 작업은 작업에 해당하는 동사(예: open)에 연결됩니다.

 프로게이터에 있는 셸 키를 사용하여 프로그마틱 식별자(ProgID)와 연결된 동사를 등록할 수 **HKEY_CLASSES_ROOT.\셸.\{** 자세한 내용은 [파일 형식을](/windows/desktop/shell/fa-file-types)참조하십시오.

## <a name="register-standard-verbs"></a>표준 동사 등록
 운영 체제는 다음과 같은 표준 동사를 인식합니다.

- 열기

- 편집

- 재생

- Print

- 미리 보기

  가능하면 표준 동사를 등록합니다. 가장 일반적인 선택은 열기 동사입니다. 파일을 열고 파일을 편집하는 사이에 명확한 차이가있는 경우에만 동사 편집을 사용합니다. 예를 들어 *.htm* 파일을 열면 브라우저에 표시되지만 *.htm* 파일을 편집하면 HTML 편집기가 시작됩니다. 표준 동사는 운영 체제 로캘로 지역화됩니다.

> [!NOTE]
> 표준 동사를 등록할 때 열기 키의 기본값을 설정하지 마십시오. 기본값에는 메뉴의 표시 문자열이 포함되어 있습니다. 운영 체제는 표준 동사에 대해 이 문자열을 제공합니다.

 사용자가 파일을 열 때의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 새 인스턴스를 시작 하려면 프로젝트 파일을 등록 해야 합니다. 다음 예제에서는 프로젝트에 대한 표준 동사 등록을 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 보여 줍니다.

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

 의 기존 인스턴스에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]파일을 열려면 DDEEXEC 키를 등록합니다. 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* 파일에 대한 표준 동사 등록을 보여 줍니다.

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
 기본 동사는 사용자가 Windows 탐색기에서 파일을 두 번 클릭할 때 실행되는 작업입니다. 기본 동사는 **HKEY_CLASSES_ROOT\\*progid*\Shell** 키의 기본값으로 지정된 동사입니다. 값을 지정하지 않으면 기본 동사는 **HKEY_CLASSES_ROOT\\*progid*\Shell** 키 목록에 지정된 첫 번째 동사입니다.

> [!NOTE]
> 병렬 배포에서 확장에 대한 기본 동사를 변경하려는 경우 설치 및 제거에 미치는 영향을 고려하십시오. 설치 하는 동안 원래 기본값을 덮어 씁쓸합니다.

## <a name="see-also"></a>참조
- [나란히 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md)
