---
title: Visual Studio Tools for Unity 시작 | Microsoft 문서
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 32766fdf69136f3882186bbcad08aaf83d2e573e
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815749"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity 시작

## <a name="install-visual-studio"></a>Visual Studio 설치

### <a name="unity-bundled-installation"></a>Unity 번들 설치

Unity 2018.1부터 Visual Studio는 기본 Unity용 C# 스크립트 편집기이며, Unity 다운로드 도우미와 Unity Hub 설치 도구에 포함되어 있습니다.

- [store.unity.com](https://store.unity.com/)에서 Unity를 다운로드하세요.

설치하는 동안 Unity와 함께 설치할 구성 요소 목록에서 Visual Studio를 선택했는지 확인합니다.

#### <a name="unity-hub"></a>Unity Hub

:::moniker range="vs-2017"
![unity hub 설치](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![unity hub 설치](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Unity 다운로드 도우미

![unity 다운로드 도우미 설치](media/vs-2017/vstu-download-assistant.png)

Unity 설치에 포함되는 Visual Studio의 버전은 최신 버전이 아닐 수 있습니다. Visual Studio 2017을 설치하라는 메시지가 표시되면 최신 버전의 Visual Studio를 직접 설치하는 것이 좋습니다.
:::moniker-end

### <a name="manual-installation"></a>수동 설치

Visual Studio가 이미 설치되어 있거나 수동으로 설치하려는 경우에는 Visual Studio 설치 관리자를 실행합니다.

1. [Visual Studio 설치 관리자를 다운로드](../install/install-visual-studio.md)하거나 이미 설치된 경우에는 설치 관리자를 엽니다.

1. 원하는 Visual Studio 버전에 대해 **수정**(이미 설치된 경우) 또는 **설치**(새 설치의 경우)를 클릭합니다.

1. **워크로드** 탭에서 **모바일 및 게임** 섹션으로 스크롤하고 **Unity를 사용한 게임 개발** 워크로드를 선택합니다.

   :::moniker range="vs-2017"
   ![Unity 워크로드](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Unity 워크로드](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. 설치 관리자 창의 오른쪽 아래 모서리에 있는 **수정**(이미 설치된 경우) 또는 **설치**(새 설치의 경우)를 클릭합니다.


#### <a name="check-for-updates-to-visual-studio"></a>Visual Studio 업데이트 확인

최신 도구 및 기능에 액세스할 수 있도록 Visual Studio 내에서 업데이트를 확인하는 것이 좋습니다. 업데이트 시 Unity 프로젝트는 중단되지 않습니다.

- [Visual Studio 업데이트](../install/update-visual-studio.md)


## <a name="configure-unity-for-use-with-visual-studio"></a>Visual Studio를 사용하도록 Unity 구성

Unity 2018.1부터 Visual Studio는 Unity의 기본 외부 스크립트 편집기여야 합니다. 이를 확인하거나 외부 스크립트 편집기를 특정 Visual Studio 버전으로 변경할 수 있습니다.

1. **편집** 메뉴에서 **기본 설정**을 선택합니다.

   :::moniker range="vs-2017"
   ![기본 설정 선택](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![기본 설정 선택](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. 기본 설정 대화 상자에서 **외부 도구** 탭을 선택합니다.

3. 외부 스크립트 편집기 드롭다운 목록에서 원하는 **Visual Studio** 버전이 있을 경우 이를 선택하고, 그렇지 않을 경우 **찾아보기...** 를 선택합니다.

   :::moniker range="vs-2017"
   ![Visual Studio 선택](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Visual Studio 선택](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end


4. **찾아보기...** 를 선택한 경우 Visual Studio 설치 디렉터리 내부의 **Common7/IDE** 디렉터리로 이동하고 **devenv.exe**를 선택합니다. 그런 다음, **열기**를 클릭합니다.

   :::moniker range="vs-2017"
   ![열기 선택](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![열기 선택](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. **외부 스크립트 편집기** 목록에서 Visual Studio를 선택한 후 **편집기 연결** 확인란이 선택되어 있는지 확인합니다.

6. **기본 설정** 대화 상자를 닫아 구성 프로세스를 완료합니다.

## <a name="support-for-older-versions"></a>이전 버전 지원

Visual Studio Marketplace에서 Visual Studio Tools for Unity를 다운로드하고 설치합니다. 사용 중인 Visual Studio 버전에 맞는 패키지를 설치해야 합니다.

- Visual Studio 2015 Community, Visual Studio 2015 Professional 또는 Visual Studio 2015 Enterprise의 경우:

   [Visual Studio 2015 Tools for Unity 다운로드](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity에는 Unity 5.2 이상과 함께 Visual Studio Community, Professional, Premium 또는 Enterprise와 같이 확장을 지원하는 Visual Studio 버전이 필요합니다. Visual Studio Tools for Unity가 사용 중인 Unity 설치에서 사용 가능한지 확인하려면 **도움말** 메뉴에서 **Unity 정보**를 선택하고 대화 상자의 왼쪽 아래에 “Microsoft Visual Studio Tools for Unity enabled”(Microsoft Visual Studio Tools for Unity 사용 가능) 텍스트가 있는지 확인하세요.
> ![Unity 정보](media/vs-2019/vstu-about-unity.png)


## <a name="next-steps"></a>다음 단계

 Visual Studio에서 Unity 프로젝트를 작업하고 디버그하는 방법을 알아보려면 [Visual Studio Tools for Unity 사용](../cross-platform/using-visual-studio-tools-for-unity.md)을 참조하세요.
