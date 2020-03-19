---
title: 샘플 R 프로젝트
description: R 및 Visual Studio를 시작하기 위한 샘플 컬렉션의 인덱스입니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: ef3316d929b00203815918a656568f75571e954e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843815"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio용 R 도구 샘플 프로젝트

이 샘플 컬렉션을 통해 R, RTVS(Visual Studio용 R 도구) 및 Microsoft Machine Learning Server 사용을 시작할 수 있습니다.

1. [샘플 zip 파일](https://github.com/Microsoft/RTVS-docs/archive/master.zip)을 다운로드하고 선택한 폴더로 추출합니다.
1. `examples/Examples.sln`를 열어 프로젝트의 두 폴더를 표시합니다.

    - *R 개요*에서는 R을 처음 사용하는 사람에게 적당한 소개를 제공합니다.
    - *MRS 및 Machine Learning*에서는 기계 학습에 R 및 Microsoft Machine Learning Server를 사용하는 방법의 예제를 제공합니다.

## <a name="a-first-look-at-r"></a>R 개요

이 샘플에서는 두 소스 파일에 있는 포괄적인 주석을 통해 R을 자세히 소개합니다. 최상의 경험을 얻으려면 파일의 맨 위에 커서를 놓고 Ctrl+Enter를 눌러 코드를 한 줄씩 **R 대화형** 창으로 보냅니다. 패키지를 설치하는 줄은 완료하는 데 1~2분이 걸릴 수 있습니다.

- `1-Getting Started with R.R`에서는 패키지 사용, 데이터 로드 및 분석, 그리기를 포함한 많은 R 기본 사항을 설명합니다.

    ![1-Getting Started with R.R 샘플의 예제 출력](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R`에서는 눈에 띄는 플롯 및 간단한 구문용으로 알려진 ggplot2 그래픽 패키지를 소개합니다. 이 예제에서는 Fiji의 지진 데이터를 시각화합니다.

    ![2-Introduction to ggplot2.R 샘플의 예제 출력](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server 및 Machine Learning

이 예제 컬렉션에서는 R을 사용하여 기계 학습 모델을 만드는 방법과 [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)를 활용하는 방법을 보여 줍니다.

모든 예제와 마찬가지로 파일을 열고 맨 위에 커서를 놓은 다음, **Ctrl**+**Enter**를 사용하여 한 줄씩 단계별로 코드를 실행합니다. 각 폴더의 markdown 파일에도 추가 정보가 포함되어 있습니다.

- `Benchmarks`는 많은 집약적인 병렬 선형 대수 계산을 실행하여 Microsoft R Open 및 Intel MKL(Math Kernel Library) 사용을 통해 얻을 수 있는 성능 향상을 보여 줍니다. 시뮬레이션 데이터를 사용하여 벤치마크는 특히 한 스레드와 두 스레드의 행렬 계산을 비교합니다.

    ![벤치마크 플롯 예제](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`에서는 Microsoft ML Server를 사용하여 기록 데이터 집합을 기반으로 자전거 대여에 대한 수요 예측 모델을 만듭니다.

- `Data_Exploration`에는 다음 세 개의 스크립트가 포함됩니다.

  - `Import Data from URL.R`에서는 URL로 식별되는 데이터 파일을 R에 로드하는 방법을 보여 줍니다.
  - `Import Data from URL to xdf.R`에서는 URL로 식별되는 데이터 파일을 Microsoft ML Server에 xdf로 로드하는 방법을 보여 줍니다.
  - `Using ggplot2.R`는 대화형 3차원 그리기를 포함하여 ggplot2 기능의 더 다양한 둘러보기를 제공하는 `A First Look at R/2-Introduction to ggplot2.R` 샘플의 확장입니다.

      ![ggplot2.R 사용 예제 출력](media/samples-3d-interactive.png)

- `Datasets`에는 다른 샘플에서 사용되는 세 개의 *.csv* 파일이 포함됩니다.
- `Flight_Delays_Prediction_with_R` 및 `Flight_Delays_Prediction_with_MRS`는 R, 기계 학습 및 기록 정시 성능/날씨 데이터를 사용하여 항공 지연을 예측하는 방법을 보여 줍니다.
- `Machine learning`에는 항공 지연, 주택 가격 및 자전거 임대를 예측하기 위한 세 가지 학습용 샘플이 포함되어 있습니다. 세 샘플은 모두, 실제 문제에 대한 R과 Microsoft ML Server의 애플리케이션을 보여 줍니다. 이러한 항목은 여러 가지 인기 있는 기계 학습 모델을 사용하고 [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) 작업 영역을 통해 Azure 웹 서비스로 배포하는 방법을 보여 줍니다.

- `R_MRO_MRS_Comparison`은 R, Microsoft R Open 및 Microsoft ML Server의 명령, 구문, 생성 및 성능에 대한 유사점과 차이점을 보여 주는 6개 부분 비교입니다.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Microsoft R Open 및 Microsoft ML Server가 특별한 점은 무엇인가요?

Microsoft의 R 배포인 [Microsoft R Open](https://mran.revolutionanalytics.com/download/)은 [CRAN R](https://cran.r-project.org/)와 다음과 같은 중요한 두 가지가 다릅니다.

1. [Intel Math Kernel Library](https://software.intel.com/intel-mkl)와 함께 사용될 경우 [계산 성능 향상](https://mran.revolutionanalytics.com/rro/#intelmkl1). 라이브러리는 Microsoft R Open과 함께 사용하도록 Microsoft에서 무료 다운로드로 제공됩니다.

1. [재현 가능한 R 도구 키트](https://mran.revolutionanalytics.com/rro/#reproducibility)는 R 프로그램을 빌드하는 데 사용한 라이브러리가 작업을 재현할 다른 사용자에게 항상 제공되도록 합니다.

[MLS(Microsoft ML Server)](/machine-learning-server/what-is-machine-learning-server)는 추가 데이터를 더 빠르게 처리할 수 있도록 하는 R의 확장입니다. 이 확장은 R에 두 가지 강력한 기능을 제공합니다.

1. RAM 제한이 없는 더 큰 데이터 집합. ML Server는 Hadoop 클러스터, 데이터베이스 및 데이터 웨어하우스를 포함한 다양한 소스의 메모리 부족 데이터를 처리할 수 있습니다.

1. 병렬, 다중 코어 처리. MLS는 사용 가능한 모든 계산 리소스에 걸쳐 계산을 효율적으로 분배할 수 있습니다. 개인 워크스테이션 또는 원격 클러스터에서 MLS는 더 빠르게 답변을 얻습니다.

다음 비교는 MKL이 있는 MLS 및 MRO의 특정 매트릭스 계산에 관련된 계산 성능이 MKL이 없는 R 및 MRO보다 크게 향상됨을 보여 줍니다. 시뮬레이트된 데이터는 다음 계산에서 사용됩니다.

![MKL이 있는 MLS/MRO 및 MKL이 없는 R/MRO 비교](media/samples-speed-comparison.png)

R과 MRO/MLS의 기술적인 비교를 위해 항목에서 [Lixun Zhang의 자세한 설명](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html)을 확인하세요.

다음 그림은 15분 이상의 항공 지연을 예측하는 로지스틱 회귀 모델을 작성하는 데 사용되는 경과된 시간(초)을 비교합니다.  적은 수의 행을 늘릴 때 CRAN R에 사용되는 경과된 시간은 대폭 증가하지만 MLS는 2배 정도씩만 증가합니다. 이 벤치마크에 대한 자세한 내용은 *벤치마크/rxGlm_benchmark.R*을 참조하세요.

![rxGlm 벤치마크](media/samples-rxGLM-benchmark.png)
