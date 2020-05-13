---
title: 새 프로젝트 및 솔루션 만들기
description: 이 문서에서는 Mac용 Visual Studio에서 프로젝트와 솔루션을 만드는 방법을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75678899"
---
# <a name="create-a-new-project"></a>새 프로젝트 만들기

## <a name="opening-the-project-creation-dialog"></a>프로젝트 만들기 대화 상자 열기

Mac용 Visual Studio에서 새 프로젝트를 만드는 여러 방법이 있습니다. Mac용 Visual Studio를 처음 열면 시작 창이 표시됩니다. 여기에서 **새로 만들기**를 선택하면 프로젝트 만들기 화면으로 이동합니다.

> [!TIP]
> 또한 시작 창에서 최근 프로젝트 및 솔루션을 열고 검색할 수도 있습니다. 메뉴 모음으로 이동하여 **파일 > 최근 솔루션**을 선택하여 최근 프로젝트를 열 수도 있습니다.

![새 프로젝트 만들기가 표시된 시작 창](media/first-run-project.png)

솔루션이 로드된 상태로 Mac용 Visual Studio가 이미 열려 있는 경우 메뉴 모음으로 이동한 후 **파일> 새 솔루션**을 선택하여 새 솔루션을 만들 수 있습니다. 이러한 방식으로 새 솔루션을 만들면 이미 로드된 솔루션은 닫힙니다.

## <a name="creating-a-new-project-from-a-template"></a>템플릿으로 새 프로젝트 만들기

**새 프로젝트** 대화 상자는 기본적으로 *가장 최근에 사용한* 템플릿을 기준으로 정렬된 사용자가 최근에 사용한 템플릿을 보여줍니다.

최근 템플릿을 사용하지 않으려면 대화 상자 왼쪽에 있는 범주에서 선택할 수 있습니다. 각 범주에는 사용자가 선택할 수 있는 여러 프로젝트 템플릿이 있습니다. 프로젝트 형식을 클릭하면 화면 오른쪽에서 설명을 볼 수 있습니다.

![새 프로젝트 화면](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>새 프로젝트 구성

프로젝트 템플릿을 선택하면 다음 화면들이 나타나 프로젝트를 설정하는 데 필요한 구성 단계를 안내하며, 프로젝트 형식에 따라 다를 수 있습니다.

모든 프로젝트에는 파일을 저장할 위치와 함께, 새 프로젝트가 필요합니다. 해당 프로젝트를 기존 솔루션에 추가하는 것이 아니라 새 솔루션의 일부인 경우, 솔루션 이름도 필요합니다.

필요에 따라 이 단계에서 Git 원본 제어 옵션도 구성할 수 있습니다. 다음 이미지는 .NET Core 프로젝트의 최종 구성 단계의 예입니다.

![새 프로젝트 구성](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>추가 프로젝트를 솔루션에 추가

Solution Pad에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 프로젝트 추가** 또는 **추가 > 기존 프로젝트 추가** 중에서 선택하여 솔루션에 추가 프로젝트를 추가할 수 있습니다.

새 프로젝트를 추가하면 [새 프로젝트 구성](#configuring-your-new-project)에 표시된 대로 프로젝트 만들기가 진행됩니다.

기존 프로젝트를 추가하도록 선택하면 컴퓨터에서 기존 프로젝트를 찾아 솔루션에 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [솔루션 및 프로젝트 만들기(Windows의 Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
