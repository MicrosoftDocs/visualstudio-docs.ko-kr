---
title: 파일 이름 확장명에 대한 동사 등록 | Microsoft Docs
description: Shell 키를 사용하여 파일 이름 확장명에 대한 프로그래밍 식별자와 연결된 동사를 등록하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c223dea7e265d8d040d502c99ded09380e89690f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901229"
---
# <a name="register-verbs-for-file-name-extensions"></a>파일 이름 확장명에 대한 동사 등록
일반적으로 애플리케이션과 파일 이름 확장명을 연결하면 사용자가 파일을 두 번 클릭할 때 발생하는 기본 동작이 있습니다. 이 기본 설정 작업은 작업에 해당하는 동사(예: 열기)에 연결됩니다.

 HKEY_CLASSES_ROOT **\{ progid}\shell에** 있는 셸 키를 사용하여 확장에 대한 ProgID(프로그래밍 식별자)와 연결된 동사를 등록할 수 있습니다. 자세한 내용은 [파일 형식을 참조하세요.](/windows/desktop/shell/fa-file-types)

## <a name="register-standard-verbs"></a>표준 동사 등록
 운영 체제는 다음 표준 동사를 인식합니다.

- 열기

- 편집

- 재생

- 인쇄

- 미리 보기

  가능하면 표준 동사를 등록합니다. 가장 일반적인 선택은 Open 동사입니다. 파일을 여는 것과 파일을 편집하는 것 사이에 명확한 차이가 있는 경우에만 편집 동사를 사용합니다. 예를 들어 *.htm* 파일을 열면 브라우저에 표시되는 반면 *.htm* 파일을 편집하면 HTML 편집기가 시작됩니다. 표준 동사는 운영 체제 로케일을 통해 지역화됩니다.

> [!NOTE]
> 표준 동사를 등록할 때는 Open 키의 기본값을 설정하지 마십시오. 기본값은 메뉴의 표시 문자열을 포함합니다. 운영 체제는 표준 동사에 이 문자열을 제공합니다.

 사용자가 파일을 열 때 의 새 인스턴스를 시작하려면 프로젝트 파일을 등록해야 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 다음 예제에서는 프로젝트에 대한 표준 동사 등록을 보여 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 줍니다.

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

 기존 인스턴스에서 파일을 열려면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DDEEXEC 키를 등록합니다. 다음 예제에서는 .cs 파일에 대한 표준 동사 등록을 보여 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *줍니다.*

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
 기본 동사는 사용자가 Windows 탐색기 파일을 두 번 클릭할 때 실행되는 동작입니다. 기본 동사는 **HKEY_CLASSES_ROOT \\ *progid*\Shell** 키의 기본값으로 지정된 동사입니다. 값을 지정하지 않으면 기본 동사는 **HKEY_CLASSES_ROOT \\ *progid*\Shell** 키 목록에 지정된 첫 번째 동사입니다.

> [!NOTE]
> side-by-side 배포에서 확장의 기본 동사를 변경하려는 경우 설치 및 제거에 미치는 영향을 고려합니다. 설치하는 동안 원래 기본값을 덮어씁니다.

## <a name="see-also"></a>참조
- [side-by-side 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md)
