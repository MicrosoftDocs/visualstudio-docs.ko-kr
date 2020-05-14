---
title: 프로젝트 및 솔루션, 옵션 대화 상자
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567647"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>옵션 대화 상자: 프로젝트 및 솔루션 \> 일반

이 페이지를 사용하여 프로젝트 및 솔루션과 관련된 Visual Studio의 동작을 정의할 수 있습니다. 이러한 옵션에 액세스하려면 **도구** > **옵션**을 선택하고 **프로젝트 및 솔루션**을 확장한 후 **일반**을 클릭합니다.

**일반** 페이지에서는 다음 옵션을 사용할 수 있습니다.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>오류로 인해 빌드가 종료될 때 항상 오류 목록 표시

프로젝트 빌드가 실패하는 경우에만 빌드 완료 시 **오류 목록** 창을 엽니다. 빌드 프로세스 중 발생하는 오류가 표시됩니다. 이 옵션을 선택 취소하면 오류는 계속 발생하지만 빌드 완료 시 창이 열리지 않습니다. 기본적으로 이 옵션은 사용하도록 설정됩니다.

## <a name="track-active-item-in-solution-explorer"></a>솔루션 탐색기에서 활성화된 항목 추적

이 옵션을 선택하면 **솔루션 탐색기**가 자동으로 열리고 활성 항목이 선택됩니다. 선택한 항목은 프로젝트 또는 솔루션에서 다른 파일로 작업하거나 디자이너에서 다른 구성 요소로 작업하면 변경됩니다. 이 옵션을 선택 취소해도 **솔루션 탐색기**의 선택 항목이 자동으로 변경되지는 않습니다. 기본적으로 이 옵션은 사용하도록 설정됩니다.

## <a name="show-advanced-build-configurations"></a>고급 빌드 구성 표시

이 옵션을 선택하면 빌드 구성 옵션이 **프로젝트 속성 페이지** 대화 상자 및 **솔루션 속성 페이지** 대화 상자에 표시됩니다. 이 옵션을 선택 취소하면 구성 디버그 및 릴리스 하나 또는 두 개를 포함하는 Visual Basic 및 C# 프로젝트의 **프로젝트 속성 페이지** 대화 상자와 **솔루션 속성 페이지** 대화 상자에 빌드 구성 옵션이 나타나지 않습니다. 프로젝트에 사용자 정의 구성이 있으면 빌드 구성 옵션이 표시됩니다.

이 옵션을 선택 취소하면 **빌드** 메뉴의 명령(예: **솔루션 빌드**, **솔루션 다시 빌드** 및 **솔루션 지우기**)이 릴리스 구성에 대해 수행되고, **디버그** 메뉴의 명령(예: **디버깅 시작** 및 **디버깅하지 않고 시작**)이 디버그 구성에 대해 수행됩니다.

## <a name="always-show-solution"></a>솔루션 항상 표시

이 옵션을 선택하면 솔루션과 솔루션에서 작동하는 모든 명령이 IDE에 항상 표시됩니다. 이 옵션을 선택 취소하면 모든 프로젝트가 독립 실행형 프로젝트로 만들어지고, 솔루션이 하나의 프로젝트만 포함하는 경우 IDE의 솔루션에서 작동하는 명령이나 솔루션 탐색기의 솔루션이 표시되지 않습니다.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>만들어질 때 새 프로젝트 저장

이 옵션을 선택하면 **새 프로젝트** 대화 상자에 프로젝트의 위치를 지정할 수 있습니다. 이 옵션을 선택 취소하면 모든 새 프로젝트가 임시 프로젝트로 만들어집니다. 임시 프로젝트로 작업할 경우에는 디스크 위치를 지정하지 않아도 프로젝트를 만들고 사용할 수 있습니다.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>프로젝트 위치를 신뢰할 수 없을 때 사용자에게 경고

완전히 신뢰할 수 없는 위치(예: UNC 경로 또는 HTTP 경로)에서 새 프로젝트를 만들거나 기존 프로젝트를 열려고 하면 메시지가 표시됩니다. 완전히 신뢰할 수 없는 위치에서 프로젝트를 만들거나 열려고 할 때마다 메시지를 표시할지 여부를 지정하려면 이 옵션을 사용합니다.

## <a name="show-output-window-when-build-starts"></a>빌드를 시작할 때 출력 창 표시

솔루션 빌드 시작 시에 IDE에 [출력 창](../../ide/reference/output-window.md)이 자동으로 표시됩니다.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>파일 이름을 바꿀 때 기호화된 이름 바꾸기 확인

이 옵션을 선택하면 Visual Studio에서 프로젝트에서 코드 요소에 대한 모든 참조 이름을 바꿀지 묻는 메시지 상자를 표시합니다.

## <a name="prompt-before-moving-files-to-a-new-location"></a>파일을 새 위치로 이동하기 전에 확인

이 옵션을 선택하면 **솔루션 탐색기**에서 작업을 통해 파일 위치를 변경하기 전에 Visual Studio에서 확인 메시지 상자를 표시합니다.

## <a name="reopen-documents-on-solution-load"></a>솔루션 로드 시 문서 다시 열기

이 옵션을 선택하면 이 솔루션이 닫힐 때 열려 있던 문서가 솔루션이 열릴 때 자동으로 열립니다.

특정 유형의 파일 또는 디자이너를 다시 열면 솔루션 로드가 지연될 수 있습니다. 솔루션의 이전 컨텍스트를 복원하지 않으려면 이 옵션을 선택 취소하여 [솔루션 로드 성능을 개선](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore)합니다.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>솔루션 로드 시 솔루션 탐색기 프로젝트 계층 구조 상태 복원

이 옵션을 선택하면 솔루션이 마지막으로 열렸을 때 노드가 확장 또는 축소되었는지 여부에 따라 솔루션 탐색기에서 노드 상태를 복원합니다. 대규모 솔루션의 솔루션 로드 시간을 줄이려면 이 옵션을 선택 취소합니다.

> [!TIP]
> 이 옵션을 사용하지 않도록 설정하면 **솔루션 탐색기** 도구 모음에서 **활성 문서와 동기화**를 선택하여 솔루션 탐색기에서 활성 문서로 쉽게 이동할 수 있습니다.
>
> ![솔루션 탐색기에서 활성 문서와 동기화](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>두 번 클릭 또는 Enter 키를 사용하여 SDK 스타일 프로젝트 파일 열기

이 옵션을 선택하고 솔루션 탐색기에서 SDK 스타일 프로젝트 노드를 두 번 클릭하거나 해당 노드를 선택한 후 **Enter** 키를 누르면 프로젝트 파일(예: \*.csproj 파일)이 편집기에서 XML로 열립니다. 이 옵션을 선택 취소하면 솔루션 탐색기에서 SDK 스타일 프로젝트 노드를 두 번 클릭하거나 해당 노드를 선택한 후 **Enter** 키를 누르면 해당 노드만 확장 또는 축소됩니다.

이 옵션을 선택하지 않고 SDK 스타일 프로젝트 파일을 편집하려면 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 파일 편집**을 선택합니다. 다른 프로젝트 형식의 경우 Visual Studio에서 프로젝트를 편집하기 전에 먼저 프로젝트를 언로드해야 합니다.

> [!TIP]
> ‘SDK 스타일 프로젝트’ 또는 [프로젝트 SDK](../../msbuild/how-to-use-project-sdk.md)에는 MSBuild 15.0에 도입된 더욱 간소화된 최신 프로젝트 파일 형식이 있습니다.  SDK 스타일 프로젝트에는 `Project` 요소에 대한 `Sdk` 특성(예: `<Project Sdk="Microsoft.NET.Sdk">`)이 포함됩니다. Visual Studio 템플릿 중 하나에서 새 .NET Core 프로젝트를 만들면 Visual Studio에서 SDK 스타일 프로젝트가 생성됩니다. 예를 들어 다음과 같습니다.

::: moniker-end

## <a name="see-also"></a>참조

- [옵션 대화 상자: 프로젝트 및 솔루션 \> 위치](projects-solutions-locations-options.md)
- [옵션 대화 상자, 프로젝트 및 솔루션, 빌드 및 실행](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [옵션 대화 상자, 프로젝트 및 솔루션, 웹 프로젝트](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
