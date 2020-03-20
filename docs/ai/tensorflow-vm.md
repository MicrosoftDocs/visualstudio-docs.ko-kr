---
title: 클라우드에서 TensorFlow 모델 실행
description: Azure 딥 러닝 VM에서 TensorFlow 모델을 실행합니다.
keywords: AI, Visual Studio, 딥 러닝 가상 머신
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 9cb06220c99abb86c24808f6831cf98280133f2e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75915834"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>클라우드에서 TensorFlow 모델 학습

이 자습서에서는 Azure [심층 학습](http://yann.lecun.com/exdb/mnist/) 가상 머신에서 [MNIST 데이터 세트](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)를 사용하여 TensorFlow 모델을 학습합니다.

MNIST 데이터베이스에는 60,000개의 학습 예제 집합과 직접 작성한 10,000개의 테스트 예제 집합이 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
시작하기 전에 다음을 설치하고 구성했는지 확인합니다.

### <a name="setup-azure-deep-learning-virtual-machine"></a>Azure 딥 러닝 가상 머신 설치

> [!NOTE]
> **OS 유형**을 Linux로 설정하세요.

딥 러닝 가상 머신을 설정하기 위한 지침은 [여기](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm)에 있습니다.

### <a name="remove-comment-in-parens"></a>괄호 안에 있는 주석 제거

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>샘플 코드 다운로드

TensorFlow, CNTK, Theano 등에서 심층 학습을 시작하는 샘플이 포함된 이 [GitHub 리포지토리](https://github.com/Microsoft/samples-for-ai)를 다운로드합니다.

## <a name="open-project"></a>프로젝트 열기

- Visual Studio를 시작하고 **파일 > 열기 > 프로젝트/솔루션**을 차례로 선택합니다.

- 다운로드한 샘플 리포지토리에서 **Tensorflow Examples** 폴더를 선택하고 **TensorflowExamples.sln** 파일을 엽니다.

   ![프로젝트 열기](media/tensorflow-local/open-project.png)

   ![솔루션 열기](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Azure 원격 VM 추가

[서버 탐색기]의 AI 도구 노드 아래에서 **원격 컴퓨터** 노드를 마우스 오른쪽 단추로 클릭하고 "추가..."를 선택합니다. 원격 컴퓨터 표시 이름, IP 호스트, SSH 포트, 사용자 이름 및 암호/키 파일을 입력합니다.

![새 원격 컴퓨터 추가](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Azure VM에 작업 제출
**솔루션 탐색기**에서 MNIST 프로젝트를 마우스 오른쪽 단추로 클릭하고 **작업 제출**을 선택합니다.

![원격 컴퓨터에 작업 제출](media/tensorflow-vm/job-submission.png)

제출 창에서 다음을 수행합니다.

- **사용할 클러스터** 목록에서 작업을 제출할 원격 컴퓨터("rm:" 접두사 사용)를 선택합니다.

- **작업 이름**을 입력합니다.

- **제출**을 클릭합니다.

## <a name="check-status-of-job"></a>작업 상태 확인
작업의 상태 및 세부 정보를 보려면 **서버 탐색기**에서 작업을 제출한 가상 머신을 펼칩니다. **작업**을 두 번 클릭합니다.

![작업 브라우저](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>리소스 정리

나중에 사용하려면 VM을 중지합니다. 이 자습서를 완료하면 다음 명령을 실행하여 리소스를 정리합니다.

```azurecli-interactive
az group delete --name myResourceGroup
```
