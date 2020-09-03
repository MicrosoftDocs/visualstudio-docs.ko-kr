---
title: 기존 코드로 AI 프로젝트를 만듭니다.
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 8c0909259291bc5d2db2c4a9c8b87b1a0321d362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371718"
---
# <a name="create-an-ai-project-from-existing-code"></a>기존 코드로 AI 프로젝트를 만듭니다.

[Visual Studio Tools for AI를 설치](installation.md)하면 Visual Studio 프로젝트에 기존 Python 코드를 쉽게 가져올 수 있습니다.

> [!Important]
> 여기에 설명된 프로세스는 원래 원본 파일을 이동하거나 복사하지 않습니다. 복사본으로 작업하려면 먼저 폴더를 복제합니다.

1. Visual Studio를 시작하고 **파일 > 새로 만들기 > 프로젝트**를 선택합니다.

2. **새 프로젝트** 대화 상자에서 "**AI 도구**"를 검색하고 "**기존 Python 코드에서**" 템플릿을 선택하고 프로젝트의 이름 및 위치를 지정하고 **확인**을 선택합니다.

   ![기존 코드의 새 프로젝트, 1단계](media/create-project-existing/new-ai-project.png)

3. 마법사가 나타나면 기존 코드에 대한 경고, 파일 형식에 대한 필터를 설정하고 프로젝트에 필요한 모든 검색 경로를 지정한 후 **확인**을 선택합니다. 검색 경로를 모르는 경우 필드를 비워 둡니다.

   ![기존 코드의 새 프로젝트, 2단계](media/create-project-existing/azurebatch-newproject.png)

   기존 코드가 Azure Machine Learning 프로젝트의 일부인 경우 중요한 Azure Machine Learning 구성 정보(예: 실험 계정, 작업 영역, 사용할 컴퓨팅 컨텍스트 등)를 성공적으로 전환하도록 **Azure Machine Learning 폴더임**을 선택합니다.

4. 시작 파일을 설정하려면 **솔루션 탐색기**에서 파일을 찾고 마우스 오른쪽 단추로 클릭한 다음, **시작 파일로 설정**을 선택합니다.

5. **Ctrl**+**F5**를 누르거나 **디버그 > 디버깅하지 않고 시작**을 선택하여 프로그램을 실행합니다.

> [!div class="nextstepaction"]
> [자습서: Visual Studio에서 Python 작업](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>참고 항목

- [기존 Python 환경 수동 식별](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
