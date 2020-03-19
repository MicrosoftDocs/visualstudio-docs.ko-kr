---
title: 템플릿으로 AI 프로젝트 만들기
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0b537d80b8db9150c6804aff2ee3de0e6c879bb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62546728"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Visual Studio의 템플릿에서 AI 프로젝트 만들기

[AI에 Visual Studio Tools를 설치](installation.md)하면 다양한 템플릿을 사용하여 새 AI 프로젝트를 쉽게 만들 수 있습니다.

1. Visual Studio를 시작합니다.

2. **파일 > 새로 만들기 > 프로젝트**(Ctrl+Shift+N)를 선택합니다. **새 프로젝트** 대화 상자에서 "**AI 도구**"를 검색하고, 원하는 템플릿을 선택합니다. 템플릿을 선택하면 템플릿이 제공하는 것의 간단한 설명이 표시됩니다.

    ![Python 템플릿이 있는 VS2017 새 프로젝트 대화 상자](media/create-project/new-ai-project.png)

3. 이 빠른 시작의 경우 "**TensorFlow 애플리케이션**" 템플릿을 선택하고, 프로젝트에 이름(예: "MNIST") 및 위치를 지정하고, **확인**을 선택합니다.

4. Visual Studio는 템플릿에 설명된 대로 다른 파일과 함께 프로젝트 파일(디스크의 `.pyproj` 파일)을 만듭니다. "TensorFlow 애플리케이션" 템플릿을 사용하여 프로젝트는 프로젝트와 같은 이름이 지정된 하나의 파일만을 포함합니다. 파일은 기본적으로 Visual Studio 편집기에서 열립니다.

    ![Python 애플리케이션 템플릿을 사용하는 경우의 결과 프로젝트](media/create-project/new-tensorflowapp.png)

5. 코드가 이미 TensorFlow, numpy, sys 등을 비롯한 여러 라이브러리를 가져옵니다. 또한 입력 학습 데이터, 출력 모델 및 로그 파일의 위치를 쉽게 전환할 수 있기 위해 몇 가지 입력 인수를 갖는 애플리케이션을 준비하기 시작합니다. 이러한 매개 변수는 여러 컴퓨팅 컨텍스트에 작업을 제출하는 경우에 유용합니다(예: Azure 파일 공유가 아닌 로컬 개발 상자의 다른 디렉터리).

6. 프로젝트에는 이러한 입력 매개 변수에 명령줄 인수를 자동으로 전달하여 앱을 디버그하기 쉽도록 하기 위해 만든 몇 가지 속성이 있습니다. 프로젝트를 **마우스 오른쪽 단추로 클릭**하고 **속성**을 선택합니다.

    ![속성](media/create-project/project-properties.png)

7. **디버그** 탭을 클릭하여 스크립트 인수가 자동으로 추가되었는지 확인합니다. 필요에 따라 입력 데이터의 위치 및 출력을 저장할 위치로 변경할 수 있습니다.

    ![속성](media/create-project//project-properties_1.png)

8. Ctrl+F5 키를 누르거나 메뉴에서 **디버그 > 디버깅하지 않고 시작**을 선택하여 프로그램을 실행합니다. 결과는 콘솔 창에 표시됩니다.
