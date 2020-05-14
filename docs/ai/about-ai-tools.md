---
title: Visual Studio용 AI 도구
titleSuffix: ''
description: Visual Studio용 AI 도구 개요
keywords: AI, Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: f696f5c2696ef15c133c9011b4235bf6714742e7
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638560"
---
# <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

Visual Studio Tools for AI는 딥 러닝/AI 솔루션을 빌드, 테스트 및 배포하기 위한 확장 기능입니다. 데이터 준비 및 모델 교육 작업을 다른 컴퓨팅 대상에 투명하게 제출하는 것을 포함하지만 이에 국한되지 않는 강력한 실험 기능을 위해 Azure Machine Learning과 원활하게 통합됩니다. 또한 사용자 지정 메트릭 및 실행 기록 추적을 지원하므로 데이터 과학 재현 가능성과 감사가 가능합니다. 엔터프라이즈 지원 협업을 통해 다른 사람들과 프로젝트를 안전하게 수행할 수 있습니다.

[CNTK(Microsoft Cognitive Toolkit)](/cognitive-toolkit/), [Google TensorFlow](https://www.tensorflow.org) 또는 기타 딥 러닝 프레임워크를 사용하여 딥 러닝을 시작합니다.

## <a name="develop-debug-and-deploy-deep-learning-models-and-ai-solutions"></a>딥 러닝 모델 및 AI 솔루션 개발, 디버그 및 배포
Visual Studio의 생산성 기능을 사용하여 현재의 AI 혁신을 가속화합니다. 구문 강조 표시, IntelliSense 및 텍스트 자동 서식 지정과 같이 기본 제공되는 코드 편집기 기능을 사용하세요. 지역 변수 및 모델에 대한 단계별 디버깅을 사용하여 로컬 환경에서 딥 러닝 애플리케이션을 대화형으로 테스트할 수 있습니다.

![딥 러닝 IDE](media/about/ide.png)

## <a name="get-started-quickly-with-the-azure-machine-learning-sample-gallery"></a>Azure Machine Learning 샘플 갤러리를 통해 빠르게 시작
Visual Studio Tools for AI는 Azure Machine Learning과 통합되어 CNTK, TensorFlow, MMLSpark 등을 사용하여 샘플 실험 갤러리를 쉽게 탐색할 수 있습니다.

![샘플 탐색기](media/about/gallery.png)

[샘플 갤러리에서 프로젝트를 만드는 방법에 대한 자세한 정보](create-project-gallery.md)

## <a name="scale-out-deep-learning-model-training-andor-inferencing-to-the-cloud"></a>딥 러닝 모델 학습 및/또는 클라우드로 유추 학습 확장
이 확장을 사용하면 로컬 컴퓨터에서 모델을 쉽게 학습하거나 Azure Machine Learning과의 통합을 사용하여 클라우드에 작업을 제출할 수 있습니다. Spark 클러스터, Azure GPU 가상 머신 등 다양한 컴퓨팅 대상에 작업을 제출할 수 있습니다.

![작업 제출](media/about/submitjobs.png)

[클라우드에서 모델을 학습하는 방법에 대한 자세한 정보](tensorflow-vm.md)

## <a name="supported-operating-systems"></a>지원되는 운영 체제
이 확장은 현재 Windows 64비트 운영 체제를 지원합니다.

## <a name="support"></a>지원
이 확장에 대한 지원은 [GitHub 문제 추적](https://github.com/Microsoft/vs-tools-for-ai/issues)에 제공됩니다. 버그 보고서, 기능 제안을 제출하거나 토론에 참여할 수 있습니다.
