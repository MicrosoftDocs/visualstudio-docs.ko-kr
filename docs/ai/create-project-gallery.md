---
title: 프로젝트 만들기
description: Azure Machine Learning 갤러리에서 샘플을 사용하여 프로젝트 만들기
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 4bcc1932bad5b34d9695257feb163654f6b99514
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371627"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Visual Studio의 Azure Machine Learning 갤러리에서 AI 프로젝트 만들기

Azure Machine Learning은 Visual Studio Tools for AI와 통합됩니다. Azure 가상 머신, Spark 클러스터 등과 같은 원격 컴퓨팅 대상에 기계 학습 작업을 제출할 수 있습니다. 

[Visual Studio Tools for AI](installation.md)가 설치되면 Azure Machine Learning 샘플 갤러리에서 미리 만들어진 방법을 사용하여 새 Python 프로젝트를 쉽게 만들 수 있습니다.

> [!NOTE]
> Azure Machine Learning Workbench가 설치되어 있어야 합니다. 

1. Visual Studio를 실행합니다. **AI 도구** 메뉴를 열고 **클러스터 선택**을 선택하여 **서버 탐색기**를 엽니다.

    ![클러스터 선택](media/create-project-gallery/select-cluster.png)

2. 서버 탐색기에서 **Azure Machine Learning** 노드를 마우스 오른쪽 단추로 클릭하여 Azure Machine Learning 구독에 로그인한 다음 **로그인**을 선택하여 지시를 따릅니다.

    ![login](media/create-project-gallery/azureml-login.png)

3. **AI 도구 > Azure Machine Learning 샘플 갤러리**를 차례로 선택합니다.

    ![샘플 갤러리](media/create-project-gallery/gallery.png)

4. 이 빠른 시작의 경우 "**TensorFlow를 사용하는 MNIST**" 샘플을 선택하고 **설치**를 클릭합니다. 다음을 제공합니다.

   - **리소스 그룹**: 메타데이터가 저장될 Azure 리소스 그룹입니다.
   - **계정**: Azure Machine Learning 실험 계정입니다.
   - **작업 영역**: Azure Machine Learning 작업 영역입니다.
   - **프로젝트 형식**: 기계 학습 프레임워크이며, 여기서는 **TensorFlow**를 선택합니다.
   - **솔루션에 추가**: 현재 Visual Studio 솔루션에 추가할지, 아니면 새 솔루션을 만들어 열지를 결정합니다.
   - **프로젝트 경로**: 코드를 저장할 위치입니다.
   - **프로젝트 이름**: **TensorFlowMNIST**를 입력합니다.

   ![Python 애플리케이션 템플릿을 사용하는 경우의 결과 프로젝트](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio는 샘플에 정의된 다른 파일과 함께 프로젝트 파일(디스크의 `.pyproj` 파일)을 만듭니다. "MNIST" 템플릿을 사용하면 프로젝트에 여러 파일이 포함됩니다.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. Azure Machine Learning에 작업을 제출합니다.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Docker 컨테이너 또는 로컬 컴퓨터에서 실행합니다.

    ![mnist](media/create-project-gallery/azml-local.png)
