---
title: Visual Studio 자습서 0단계에서 Python 설치
titleSuffix: ''
description: Visual Studio의 Python 작업에 대한 핵심 연습의 0단계(설치 필수 구성 요소)입니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 96c067d4c55a5df4d9343e60360142466e8f218f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431298"
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio에서 Python 지원 설치

> [!Note]
> Python 지원은 현재 Windows용 Visual Studio에서만 사용할 수 있으며, [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial)를 통해 Mac 및 Linux에서 사용할 수 있습니다.

1. Windows용 최신 Visual Studio 설치 관리자를 다운로드하고 실행합니다(Python 지원은 릴리스 15.2 이상에 있음). Visual Studio가 이미 설치되어 있는 경우 Visual Studio 설치 관리자를 실행하고 2단계로 이동합니다.

    > [!div class="nextstepaction"]
    > [Visual Studio Community 설치](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > 커뮤니티 에디션은 개인 개발자, 교실 학습, 학술 연구 및 오픈 소스 개발용입니다. 다른 용도의 경우 [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) 또는 [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)를 설치합니다.

1. 설치 관리자는 특정 개발 영역에 대한 관련 옵션의 그룹인 워크로드 목록을 제공합니다. Python의 경우 **Python 개발** 워크로드를 선택하고 **설치**를 선택합니다.

    ![Visual Studio 설치 관리자의 Python 개발 작업](media/installation-python-workload.png)

1. Python 지원을 신속하게 테스트하려면 Visual Studio를 시작하고 **Alt**+**I**를 눌러 **Python 대화형** 창을 연 다음, `2+2`를 입력합니다. **4** 출력이 표시되지 않으면 수행한 단계를 다시 확인합니다.

    ![대화형 창을 통해 Python 테스트](media/installation-interactive-test.png)

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [1단계: Python 프로젝트 만들기](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>참고 항목

- [기존 Python 인터프리터 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 및 이전 버전에서 Python 지원 설치](installing-python-support-in-visual-studio.md)
- [설치 위치](installing-python-support-in-visual-studio.md#install-locations)
