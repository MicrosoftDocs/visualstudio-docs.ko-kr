---
title: codespace와 함께 Visual Studio 사용(미리 보기)
description: Windows 개발을 위해 GitHub Codespaces에서 Visual Studio IDE를 사용하는 방법을 알아봅니다.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c3a2e14236c2d24bc9650fab81150cc295826844
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006256"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>codespace와 함께 Visual Studio를 사용하는 방법(미리 보기)

Visual Studio는 GitHub Codespaces에서 개발하는 작업을 적극적으로 지원합니다. codespace를 만들어 이에 연결하고, 원격 호스팅 환경의 프로젝트에서 Visual Studio의 전체 기능이 작동하도록 할 수 있습니다. 소스 코드 및 도구가 codespace에 있고 컴파일 및 디버깅이 클라우드에서 발생하는 경우에도 로컬에서 작업하는 것처럼 개발 환경을 충돌 없이 신속하게 이용할 수 있습니다. Visual Studio 2019 미리 보기 내에서 codespace를 사용할 수 있습니다([제한된 퍼블릭 베타에 등록](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> 이 문서에서는 Visual Studio를 사용하여 GitHub Codespaces에 연결하는 방법을 구체적으로 설명합니다. [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) 또는 [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) 설명서에서 다른 클라이언트를 사용하여 codespace에 연결하는 방법을 알아볼 수 있습니다.

> [!NOTE]
> [Visual Studio 2019 미리 보기](https://aka.ms/vspreview)가 아직 설치되지 않은 경우 [visualstudio.microsoft.com](https://aka.ms/vspreview)에서 다운로드할 수 있습니다.

## <a name="enable-connect-to-github-codespaces"></a>GitHub Codespaces에 연결 사용

Visual Studio 2019 미리 보기를 사용하여 GitHub Codespaces에 연결하는 기능은 기본적으로 사용되지 않으므로 먼저 미리 보기 기능 옵션을 사용하도록 설정해야 합니다.

1. Visual Studio 2019 미리 보기에서 **도구** > **옵션** 메뉴 항목을 사용하여 옵션 대화 상자를 엽니다.

2. **환경**에서 **미리 보기 기능**을 선택하고 **GitHub Codespaces에 연결** 미리 보기 기능을 선택합니다.

   ![GitHub Codespaces에 연결 미리 보기 기능 확인](media/connect-to-github-codespaces-preview-feature.png)

3. 해당 기능을 사용하려면 Visual Studio를 다시 시작해야 합니다.

## <a name="create-a-codespace"></a>codespace 만들기

codespace가 아직 없는 경우 Visual Studio에서 만들 수 있습니다.

1. Visual Studio를 시작하면 시작 창의 “시작” 아래에 **codespace에 연결** 단추가 표시됩니다.

   ![codespace에 연결이 있는 Visual Studio 시작 창](media/visual-studio-start-window.png)

2. **codespace에 연결**을 선택하면 GitHub에 로그인하라는 메시지가 표시됩니다. 아직 없는 경우 GitHub 계정을 만들 수도 있습니다.

   ![Visual Studio GitHub에 로그인](media/visual-studio-sign-in-to-github.png)

   **GitHub에 로그인**을 선택한 후 온라인 GitHub 로그인 워크플로를 따릅니다.

3. codespace를 만든 적이 없으면 만들라는 메시지가 표시됩니다.

   “codespace 세부 정보”에서 **리포지토리 URL**을 제공해야 합니다. GitHub Codespaces는 생성 시 지정된 리포지토리를 codespace에 복제합니다.

   드롭다운을 통해 **인스턴스 유형** 및 **다음 시간 후 일시 중단** 시간 제한을 수정할 수도 있습니다. codespace 세부 정보를 설정한 후 **만들기 및 연결** 단추를 선택합니다.

   ![Visual Studio codespace 세부 정보](media/visual-studio-codespace-details.png)

   GitHub Codespaces는 codespace 준비를 시작하고 codespace가 준비된 후 Visual Studio를 엽니다.

   codespace 이름이 메뉴 모음의 원격 표시기에 표시됩니다.

   ![eShopOnWeb 리포지토리 codespace에 연결된 Visual Studio](media/visual-studio-eshoponweb-codespace.png)

4. 로컬에서 작업하는 것처럼 Visual Studio 사용을 시작합니다. 시도할 작업:

   * 소스 코드를 찾아봅니다.
   * 솔루션 파일을 선택하고 솔루션을 빌드합니다(**Ctrl+Shift+B**).
   * 소스 파일에 중단점을 설정하고 **F5** 키를 눌러 디버거에서 애플리케이션을 시작합니다.
   * 변경하고 리포지토리에 커밋합니다.   

> [!NOTE]
> 이번에는 GitHub [Codespaces 포털](https://github.com/codespaces)을 통해 Visual Studio용 GitHub Codespaces를 만들 수 없습니다. 만들려면 Visual Studio를 사용해야 합니다.

## <a name="connect-to-a-codespace"></a>codespace에 연결

codespace를 만든 후 Visual Studio에서 직접 codespace를 열 수 있습니다.

1. Visual Studio를 시작하면 시작 창의 “시작” 아래에 **codespace에 연결** 단추가 표시됩니다.

   ![codespace에 연결이 있는 Visual Studio 시작 창](media/visual-studio-start-window.png)

   Visual Studio에 이미 있는 경우 **파일** ** > codespace에 연결** 메뉴 항목을 사용할 수 있습니다.

   ![Visual Studio 파일 codespace에 연결 메뉴 항목](media/visual-studio-file-connect-to-codespace.png)

2. **codespace에 연결**을 선택합니다. 아직 로그인하지 않은 경우 GitHub에 로그인하라는 메시지가 표시됩니다.

3. 그런 다음, 오른쪽 패널에 있는 세부 정보와 함께 모든 GitHub codespace를 볼 수 있습니다.

   ![사용 가능한 GitHub codespace 및 세부 정보를 표시하는 Visual Studio](media/visual-studio-connect-codespace.png)

   Azure DevOps 리포지토리를 복제한 모든 codespace는 GitHub의 Codespaces 페이지가 아닌 Visual Studio에서만 볼 수 있습니다.

4. codespace를 선택하고 **연결** 단추를 선택합니다. codespace가 일시 중단된 경우 다시 시작되고 해당 codespace에 연결된 Visual Studio가 열립니다.

   codespace 이름이 메뉴 모음의 원격 표시기에 표시됩니다.

   ![eShopOnWeb 리포지토리 codespace에 연결된 Visual Studio](media/visual-studio-eshoponweb-codespace.png)

5. 로컬에서 작업하는 것처럼 Visual Studio 사용을 시작합니다. 시도할 작업:

   * 소스 코드를 찾아봅니다.
   * 솔루션 파일을 선택하고 솔루션을 빌드합니다(**Ctrl+Shift+B**).
   * 소스 파일에 중단점을 설정하고 **F5** 키를 눌러 디버거에서 애플리케이션을 시작합니다.
   * 변경하고 리포지토리에 커밋합니다.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>추가 정보

* [GitHub Codespaces란?](codespaces-overview.md)
* [codespace를 사용자 지정하는 방법](customize-codespaces.md)
* [지원되는 Visual Studio 기능](supported-features-codespaces.md)
