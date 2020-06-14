---
title: Azure Batch AI에서 모델을 학습하는 작업 제출
description: 학습 모델 클라우드
keywords: ai, visual studio, 학습 모델, 클라우드
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 083b2cb191d627ced936ead6a90b363970a9e7e0
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638767"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Azure Batch AI에서 AI 모델 학습

Batch AI는 데이터 과학자와 AI 연구자들이 GPU 지원이 적용된 VM을 포함하여 Azure Virtual Machines 클러스터에서 AI 및 기타 기계 학습 모델을 교육시킬 수 있게 하는 관리되는 서비스입니다. 작업 요구 사항, 입력 확인 및 출력 저장 위치를 설명하면 Batch AI가 나머지를 처리합니다. [Azure Batch AI에 대한 자세한 정보](/azure/batch-ai/overview)

Visual Studio Tools for AI에 통합되므로 Azure에서 동적으로 학습 모델을 확장할 수 있습ㄴ디ㅏ.  [Visual Studio Tools for AI](installation.md)가 설치되면 Azure Machine Learning 샘플 갤러리에서 미리 만들어진 방법을 사용하여 새 Python 프로젝트를 쉽게 만들 수 있습니다.

1. Visual Studio를 실행합니다. **AI 도구** 메뉴를 열고 **클러스터 선택**을 선택하여 **서버 탐색기**를 엽니다.

    ![클러스터 선택기](media/train-model/select-cluster.png)

2. **AI 도구**를 확장합니다. 사용자가 보유한 모든 Batch AI 리소스가 자동 검색되어 서버 탐색기에 표시됩니다.

    ![샘플 갤러리](media/train-model/batchai.png)

3. **보기 > 팀 탐색기...** 를 선택하여 GitHub 또는 Azure DevOps에 연결하거나 리포지토리를 복제할 수 있는 **팀 탐색기** 창을 엽니다.

    ![Azure DevOps, GitHub를 표시하고 리포지토리를 복제하는 팀 탐색기 창](media/train-model/team-explorer-devops.png)

4. **로컬 Git 리포지토리** 아래의 URL 필드에 `https://github.com/Microsoft/samples-for-ai`를 입력하고, 복제된 파일에 대한 폴더를 입력하고, **복제**를 선택합니다.

    > [!Tip]
    > 팀 탐색기에서 지정하는 폴더는 복제된 파일을 받을 특정 폴더입니다. `git clone` 명령과 달리 팀 탐색기에서 복제본을 만드는 것은 리포지토리의 이름으로 하위 폴더를 자동으로 만들지 않습니다.

5. 복제가 완료되면 클릭 **파일 > 솔루션 열기 > 프로젝트 / 솔루션**을 클릭합니다.

    ![샘플 갤러리](media/train-model/open-solution.png)

6. 리포지토리를 복제한 디렉터리에서 **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln**을 엽니다.

    ![샘플 갤러리](media/train-model/tensorflowexamples.png)

7. MNIST 프로젝트를 **시작 프로젝트**로 설정

    ![샘플 갤러리](media/train-model/mnist-startup.png)

8. <strong>**MNIST 프로젝트**를 마우스 오른쪽 단추로 클릭하고 **작업 제출**</strong>

    ![샘플 갤러리](media/train-model/submit-job.png)
9. **Azure Batch AI** 클러스터를 선택한 다음 **가져오기**를 클릭합니다. `AzureBatchAI_TF_MNIST.json` 파일을 선택하여 사용할 Docker Image 같은 일부 기본 값을 신속하게 입력합니다. 그런 다음 **제출**을 클릭합니다.

    ![샘플 갤러리](media/train-model/submit-batch.png)
