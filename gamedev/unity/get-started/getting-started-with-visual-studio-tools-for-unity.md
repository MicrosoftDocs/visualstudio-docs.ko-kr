---
title: Visual Studio Tools for Unity 시작 | Microsoft 문서
description: Unity 개발을 위해 Visual Studio를 설치 하 고 설정 하는 방법에 대해 알아봅니다.
ms.custom: ''
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: e05a94ecf9cf690f46299684c82f2b3961a783c8
ms.sourcegitcommit: 585547ea7363ab1b6bb9d41f6d008cbe478d1a3b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98912570"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Visual Studio 및 Unity 시작

> [!NOTE]
> 이 가이드에서는 Unity 허브 프로그램을 사용 하 여 Unity를 이미 설치 했다고 가정 합니다. Unity를 처음 접하는 경우 unity에서 [Unity Essentials learning 경로](https://learn.unity.com/pathway/unity-essentials) 를 학습 하 고 완료 하는 것이 좋습니다.

## <a name="install-unity-support-for-visual-studio"></a>Visual Studio에 대 한 Unity 지원 설치

Visual Studio Tools for Unity은 c # 등을 작성 하 고 디버깅 하는 기능을 제공 하는 무료 확장입니다. 확장 프로그램에 포함 된 내용에 대 한 전체 목록은 [Unity 용 도구 개요](./visual-studio-tools-for-unity.md) 를 참조 하세요.

:::zone pivot="windows"

> [!NOTE]
> 이 설치 가이드는 Visual Studio 용입니다. Visual Studio Code 사용 하는 경우 [VS Code 설명서를 사용 하 여 Unity 개발](https://code.visualstudio.com/docs/other/unity)을 참조 하세요.

1. [Visual Studio 설치 관리자를 다운로드](/visualstudio/docs/install/install-visual-studio.md)하거나 이미 설치 되어 있는 경우 실행 합니다.
2. 원하는 Visual Studio 버전에 대해 **수정**(이미 설치된 경우) 또는 **설치**(새 설치의 경우)를 클릭합니다.
3. **작업** 탭에서 **게임** 섹션으로 스크롤하고 Unity 워크 로드 **를 사용 하 여 게임 개발** 을 선택 합니다.

    ![설치 관리자에서 Unity를 사용한 게임 개발 작업 상자](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> 이 설치 가이드는 Mac용 Visual Studio에 대 한 것입니다. Visual Studio Code 사용 하는 경우 [VS Code 설명서를 사용 하 여 Unity 개발](https://code.visualstudio.com/docs/other/unity)을 참조 하세요.

Unity 용 도구는 Mac용 Visual Studio 설치에 포함 되어 있으며 별도의 설치 단계가 필요 하지 않습니다. **Mac용 Visual Studio > Extensions > 게임 개발** 메뉴에서이를 확인할 수 있습니다. **Unity 용 Mac용 Visual Studio 도구** 를 사용 하도록 설정 해야 합니다.

![Unity를 사용 하도록 설정 된 Mac용 Visual Studio 도구를 보여 주는 확장 관리자 보기](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>업데이트 확인

최신 버그 수정, 기능 및 Unity 지원이 있도록 Visual Studio 및 Mac용 Visual Studio 업데이트를 유지 하는 것이 좋습니다. Unity 버전의 업데이트는 필요 하지 않습니다.

:::zone pivot="windows"

1. **도움말 > 업데이트 확인** 메뉴를 클릭 합니다.

    ![Visual Studio 2019의 업데이트 확인 메뉴](../media/vs/check-for-updates.png)

2. 업데이트를 사용할 수 있는 경우 Visual Studio 설치 관리자 새 버전이 표시 됩니다. **업데이트** 단추를 클릭합니다.

:::zone-end
:::zone pivot="macos"

1. **Mac용 Visual Studio > 업데이트 확인** ... 메뉴를 클릭 하 여 **Visual Studio 업데이트** 대화 상자를 엽니다.
2. 업데이트를 사용할 수 있는 경우 **설치** 단추를 클릭 합니다.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Visual Studio를 사용 하도록 Unity 구성

기본적으로 Unity는 Visual Studio를 사용 하거나 스크립트 편집기로 Mac용 Visual Studio을 사용 하도록 이미 구성 되어 있어야 합니다. 이를 확인 하거나 Unity 편집기에서 외부 스크립트 편집기를 특정 버전의 Visual Studio로 변경할 수 있습니다.

:::zone pivot="windows"

1. Unity 편집기에서 **> 기본 설정 편집** 메뉴를 선택 합니다.
2. 왼쪽에서 **외부 도구** 탭을 선택 합니다.
3. **외부 스크립트 편집기** 드롭다운 목록에서 Visual Studio의 여러 설치를 선택 하는 방법을 제공 합니다. 드롭다운 목록에서 **찾아보기 ...** 를 클릭 하 여 목록에 없는 버전을 추가할 수도 있습니다.

    ![Windows에서 Unity 편집기의 외부 도구 기본 설정 메뉴](../media/vs/preferences-external-tools.png)

4. **찾아보기...** 를 선택한 경우 Visual Studio 설치 디렉터리 내부의 **Common7/IDE** 디렉터리로 이동하고 **devenv.exe** 를 선택합니다. 그런 다음 **열기** 를 클릭 합니다.
5. **외부 스크립트 편집기** 목록에서 Visual Studio를 선택한 후 **편집기 연결** 확인란이 선택되어 있는지 확인합니다.
6. **기본 설정** 대화 상자를 닫아 구성 프로세스를 완료합니다.

:::zone-end
:::zone pivot="macos"

1. Unity 편집기에서 **unity > 기본 설정** 메뉴 .를 선택 합니다.
2. 왼쪽에서 **외부 도구** 탭을 선택 합니다.
3. **외부 스크립트 편집기** 드롭다운 목록에서 Visual Studio의 여러 설치를 선택 하는 방법을 제공 합니다. 드롭다운 목록에서 **찾아보기 ...** 를 클릭 하 여 목록에 없는 버전을 추가할 수도 있습니다.

    ![MacOS에서 Unity 편집기의 외부 도구 기본 설정 메뉴](../media/vsm/preferences-external-tools.png)

4. **기본 설정** 대화 상자를 닫아 구성 프로세스를 완료합니다.

:::zone-end

## <a name="next-steps"></a>다음 단계

 Visual Studio에서 Unity 프로젝트를 사용 하 여 작업 하 고 디버그 하는 방법을 알아보려면 [Visual Studio Tools for Unity 사용](using-visual-studio-tools-for-unity.md)을 참조 하세요.
