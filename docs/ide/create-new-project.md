---
title: 새 프로젝트 만들기
description: Visual Studio에서 새 프로젝트를 만드는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcbf39be441ba8237520fcc56ceec7946d688901
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846911"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio에서 새 프로젝트 만들기

이 문서에서는 Visual Studio에서 새 프로젝트를 빠르게 만드는 방법을 보여 줍니다.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>새 프로젝트 대화 상자 열기

Visual Studio 2017에서 새 프로젝트를 만드는 여러 방법이 있습니다. 시작 페이지에서 **프로젝트 템플릿 검색** 상자에 프로젝트 템플릿의 이름을 입력하거나 **새 프로젝트 만들기** 링크를 선택하여 **새 프로젝트** 대화 상자를 엽니다. 시작 페이지 외에도 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하거나 도구 모음에서 **새 프로젝트** 단추를 클릭할 수도 있습니다.

![파일 > 새로 만들기 > 프로젝트 옵션이 선택된 Visual Studio의 메뉴 모음 스크린샷](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>템플릿 형식 선택

**새 프로젝트** 대화 상자에서 사용 가능한 프로젝트 템플릿은 **템플릿** 범주 아래에 목록으로 나타납니다. 템플릿은 Visual C#, JavaScript 및 Azure Data Lake 등의 프로그래밍 언어 및 프로젝트 형식으로 구성되어 있습니다.

![설치된 템플릿 목록을 보여 주는 새 프로젝트 대화 상자의 스크린샷](./media/vside-newproject-templates-list.png)

> [!NOTE]
> 표시되는 사용 가능한 언어 및 프로젝트 템플릿 목록은 실행 중인 Visual Studio의 버전 및 설치된 워크로드에 따라 다릅니다. 추가 워크로드를 설치하는 방법에 대해 자세히 알아 보려면 [작업과 구성 요소를 추가하거나 제거하여 Visual Studio 수정](../install/modify-visual-studio.md)을 참조하세요.

언어 이름 옆에 있는 삼각형을 클릭한 다음, 프로젝트 범주(예: Windows 데스크톱)를 선택하여 사용할 프로그래밍 언어에 대한 템플릿 목록을 표시합니다.

다음 이미지에서는 Visual C# .NET Core 프로젝트에 사용할 수 있는 프로젝트 템플릿을 보여줍니다.

![선택할 수 있는 프로젝트 템플릿을 나열하는 새 프로젝트 대화 상자의 스크린샷](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>프로젝트 구성

**이름** 상자에 새 프로젝트의 이름을 입력합니다. 프로젝트를 컴퓨터의 기본 위치에 저장하거나 **찾아보기** 단추를 클릭하여 다른 위치를 찾을 수 있습니다. **소스 제어에 추가** 를 선택하여 솔루션 이름을 선택하거나 새 프로젝트를 Git 리포지토리에 추가할 수도 있습니다.

**확인** 을 클릭하여 솔루션 및 프로젝트를 만듭니다.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>새 프로젝트 만들기 페이지 열기

Visual Studio 2019에서 새 프로젝트를 만드는 여러 방법이 있습니다. Visual Studio를 처음 열면 시작 창에 나타나고, 여기에서 **새 프로젝트 만들기** 를 선택할 수 있습니다.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 시작 창의 ‘새 프로젝트 만들기’ 대화 상자 스크린샷":::

Visual Studio 개발 환경이 이미 열려 있는 경우 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 새 프로젝트를 만들 수 있습니다. 도구 모음에서 **새 프로젝트** 단추를 클릭하거나 **Ctrl**+**Shift**+**N** 을 누를 수도 있습니다.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Visual Studio 2019의 새 프로젝트 단추 스크린샷":::

## <a name="select-a-template-type"></a>템플릿 형식 선택

**새 프로젝트를 만들기** 페이지에서 최근에 선택한 템플릿 목록이 왼쪽에 표시됩니다. 템플릿이 *가장 최근에 사용* 한 기준으로 정렬됩니다.

최근에 사용한 템플릿에서 선택하지 않는 경우, 사용 가능한 모든 프로젝트 템플릿을 **언어**(예: C# 또는 C++), **플랫폼**(예: Windows 또는 Azure) 및 **프로젝트 형식**(예: 데스크톱 또는 웹)으로 필터링할 수 있습니다. 검색 상자에 검색 텍스트를 입력하여 템플릿(예: **asp.net**)을 추가로 필터링할 수도 있습니다.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Visual Studio 2019의 프로젝트 템플릿 필터 스크린샷":::

각 템플릿 아래에 나타나는 태그는 세 개의 드롭다운 필터(언어, 플랫폼 및 프로젝트 형식)에 해당합니다.

> [!TIP]
> 찾고 있는 템플릿이 보이지 않으면 Visual Studio용 워크로드가 누락되었을 수 있습니다. 추가 워크로드(예: **Azure 개발** 또는 **.NET을 사용한 모바일 개발**)를 설치하려면 **추가 도구 및 기능 설치** 링크를 클릭하여 Visual Studio 설치 관리자를 엽니다. 여기에서 설치할 워크로드를 선택한 다음, **수정** 을 선택합니다. 그 후 추가 프로젝트 템플릿을 선택할 수 있게 됩니다.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Visual Studio 2019의 ‘추가 도구 및 기능 설치’ 링크 스크린샷":::

템플릿을 선택한 후, **다음** 을 클릭합니다.

## <a name="configure-your-project"></a>프로젝트 구성

**새 프로젝트 구성** 페이지에는 프로젝트 및 솔루션 이름을 지정하고, 디스크 위치를 선택하고, 프레임워크 버전(선택한 템플릿에 해당하는 경우)을 선택하는 옵션이 있습니다.

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019의 ‘새 프로젝트 구성’ 페이지 스크린샷":::

> [!NOTE]
> Visual Studio에서 프로젝트 또는 솔루션을 이미 열어 둔 상태에서 새 프로젝트를 만든 경우 추가 구성 옵션을 사용할 수 있습니다. 새 솔루션을 만들거나 이미 열려 있는 솔루션에 새 프로젝트를 추가하도록 선택할 수 있습니다.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Visual Studio 2019의 ‘새 솔루션 만들기’ 또는 ‘솔루션에 추가’ 대화 상자 스크린샷":::

**만들기** 를 클릭하여 새 프로젝트를 만듭니다.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>추가 프로젝트를 솔루션에 추가

추가 프로젝트를 솔루션에 추가하려면 **솔루션 탐색기** 에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트** 를 선택합니다.

> [!TIP]
> 처음부터 프로젝트 및 솔루션을 만들고 단계별 지침 및 샘플 코드를 사용하여 완료하는 예제는 [프로젝트 및 솔루션 소개](../get-started/tutorial-projects-solutions.md)를 참조하세요.

## <a name="see-also"></a>추가 정보

- [프로젝트 및 솔루션 소개](../get-started/tutorial-projects-solutions.md)
- [솔루션 및 프로젝트 작업](creating-solutions-and-projects.md)
- [프로젝트 및 솔루션 속성 관리](managing-project-and-solution-properties.md)
- [프로젝트 만들기(Mac용 Visual Studio)](/visualstudio/mac/create-new-projects)