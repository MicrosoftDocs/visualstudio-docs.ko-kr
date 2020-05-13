---
title: Visual Studio 자습서 6단계에서 Python, Git 작업
titleSuffix: ''
description: Visual Studio의 Python에 대한 핵심 연습의 6단계로, Visual Studio의 Git 관련 기능을 설명합니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72289710"
---
# <a name="step-6-work-with-git"></a>6단계: Git 작업

**이전 단계: [패키지 설치 및 Python 환경 관리](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio는 GitHub 및 Azure Repos 등의 서비스에서 로컬 Git 리포지토리 및 원격 리포지토리와의 직접 통합을 제공합니다. 통합은 리포지토리 복제, 변경 내용 커밋 및 분기 관리를 포함합니다.

이 아티클에서는 기존 프로젝트에서 로컬 Git 리포지터리를 만들고 Visual Studio의 Git 관련 기능 중 일부에 익숙해지기 위한 기본적인 개요를 제공합니다.

1. [이전 단계](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)의 프로젝트와 같은 Visual Studio에서 열린 프로젝트를 사용하여 솔루션을 마우스 오른쪽 단추로 클릭하고 **소스 제어에 솔루션 추가**를 선택합니다. Visual Studio에서는 프로젝트 코드를 포함하는 로컬 Git 리포지토리를 만듭니다.

1. Visual Studio가 Git 리포지토리에서 프로젝트가 관리되고 있는지 검색하는 경우 Git 관련 컨트롤은 Visual Studio 창의 오른쪽 아래 모서리에 나타납니다. 컨트롤은 보류 중인 커밋, 변경 내용, 리포지토리의 이름 및 분기를 표시합니다. 추가 정보를 보려면 마우스로 컨트롤을 가리킵니다.

    ![추가 정보는 Visual Studio 창에서 Git 컨트롤을 마우스로 가리킬 때 표시됩니다.](media/working-with-git-01.png)

1. 새 리포지토리를 만들거나 Git 컨트롤 중 하나를 선택할 때 Visual Studio는 **팀 탐색기** 창을 엽니다. 언제든지 **보기** > **팀 탐색기** 메뉴 명령을 사용하여 창을 열 수 있습니다. 창에는 **팀 탐색기** 헤더의 드롭다운을 사용하여 전환할 수 있는 세 개의 기본 창이 있습니다. 게시 작업을 제공하는 **동기화** 창은 **푸시** 컨트롤(위쪽 화살표 아이콘)을 선택한 경우에도 나타납니다.

    ![로컬 리포지토리를 만든 후 Visual Studio의 팀 탐색기](media/working-with-git-02.png)

1. **변경 내용**(또는 연필 아이콘을 포함한 Git 컨트롤)을 선택하여 커밋되지 않은 변경 내용을 검토하고 필요한 경우 커밋합니다.

    ![커밋되지 않은 변경 내용을 보여 주는 Visual Studio의 팀 탐색기](media/working-with-git-03.png)

    **변경** 목록에서 파일을 두 번 클릭하여 해당 파일에 대한 차이 보기를 엽니다.

    ![파일 변경 내용에 대한 차이 보기](media/working-with-git-05.png)

1. **분기**(또는 분기 이름을 포함한 Git 컨트롤)를 선택하여 분기를 검사하고 병합을 수행하고 작업을 다시 지정합니다.

    ![분기를 보여 주는 Visual Studio의 팀 탐색기](media/working-with-git-04.png)

1. 리포지토리 이름(이전 이미지에서 **CosineWave**)을 포함한 Git 컨트롤을 선택하면 **팀 탐색기**는 다른 리포지토리로 신속하고 완전하게 전환할 수 있는 **연결** 인터페이스를 보여 줍니다.

1. 로컬 저장소를 사용하는 경우 커밋된 변경 내용은 리포지토리로 직접 이동합니다. 원격 리포지토리에 연결된 경우 **팀 탐색기**에서 드롭다운 헤더를 선택하고 **동기화**를 선택하여 **동기화** 섹션으로 전환한 다음, 표시되는 **풀** 및 **페치** 명령으로 작업합니다.

## <a name="go-deeper"></a>자세히 알아보기

원격 Git 리포지토리에서 프로젝트를 만드는 짧은 연습은 [빠른 시작: Visual Studio에서 Python 코드의 리포지토리 복제](quickstart-03-python-in-visual-studio-project-from-repository.md)를 참조하세요.

병합 충돌 처리, 끌어오기 요청으로 코드 검토, 기준 주소 다시 지정, 분기 간에 변경 내용 cherry-pick 등을 포함하는 훨씬 더 포괄적인 자습서는 [Git 및 Azure Repos 시작하기](/azure/devops/repos/git/gitquickstart)를 참조하세요.

## <a name="tutorial-review"></a>자습서 검토

Visual Studio의 Python에 대한 이 자습서 완료를 축하합니다. 이 자습서에서는 다음 방법을 학습했습니다.

- 프로젝트를 만들고 프로젝트의 내용을 봅니다.
- 코드 편집기를 사용하고 프로젝트를 실행합니다.
- **대화형** 창을 사용하여 새 코드를 개발하고 해당 코드를 편집기에 쉽게 복사합니다.
- Visual Studio 디버거에서 완성된 프로그램을 실행합니다.
- 패키지를 설치하고 Python 환경을 관리합니다.
- Git 리포지토리에서 코드로 작업합니다.

여기에서 다음 문서를 포함하여 개념 및 방법 가이드를 살펴봅니다.

- [Python용 C++ 확장 만들기](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [프로파일링](profiling-python-code-in-visual-studio.md)
- [유닛 테스트](unit-testing-python-in-visual-studio.md)
