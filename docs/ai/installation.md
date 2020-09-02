---
title: AI 도구 설치
description: Visual Studio용 AI 도구를 설치하는 방법을 설명합니다.
keywords: AI, Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ffa8c7634c0d97dd24ff69814ae73ad5ff12928b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800205"
---
# <a name="installation"></a>설치

Visual Studio Tools for AI는 64비트 운영 체제에 설치할 수 있습니다.

## <a name="install-visual-studio-tools-for-ai"></a>Visual Studio Tools for AI 설치

이 확장 프로그램은 Visual Studio 2015 및 Visual Studio 2017, Community Edition 이상에서 작동합니다.

[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017) 또는 Visual Studio 내에서 도구를 다운로드할 수 있습니다.

1. **도구** > **확장 및 업데이트**를 선택합니다.

   ![Visual Studio의 확장 및 업데이트 메뉴](media/installation/extensions.png)

2. **확장 및 업데이트** 대화 상자의 왼쪽에서 **온라인**을 선택합니다.
3. 오른쪽 위에 있는 검색 상자에 “AI 도구”를 입력합니다.
4. 결과에서 **Visual Studio Tools for AI**를 선택합니다.
5. **다운로드**를 선택합니다.

## <a name="prepare-your-local-machine"></a>로컬 머신 준비
로컬 컴퓨터에서 심층 학습 모델을 교육하기 전에 해당하는 필수 구성 요소가 설치되어 있는지 확인합니다. 여기에는 NVIDIA GPU용 최신 드라이버 및 라이브러리가 있는지 확인하는 작업도 포함됩니다(해당하는 경우). Python 및 Python 라이브러리(예: NumPy, SciPy 등)와, 프로젝트에서 사용하려는 적합한 심층 학습 프레임워크(예: Microsoft CNTK(Cognitive Toolkit), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch, Chainer 등)를 설치했는지도 확인합니다.

> [!NOTE]
> 다음 하위 섹션의 소프트웨어 소개는 해당 홈 페이지에서 발췌한 것입니다.

### <a name="nvidia-gpu-driver"></a>NVIDIA GPU 드라이버

심층 학습 프레임워크는 NVIDIA GPU를 활용하여 컴퓨터가 신속 정확하게 학습하고 진정한 인공 지능을 향해 확장해 나갈 수 있게 합니다. 컴퓨터에 NVIDIA GPU 카드가 있으면 [NVIDIA 드라이버 다운로드](https://www.nvidia.com/Download/index.aspx)를 참조하거나 운영 체제 업데이트를 시도하여 최신 드라이버를 설치합니다.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone)는 NVIDIA가 개발한 병렬 컴퓨팅 플랫폼 및 프로그래밍 모델입니다. GPU 기능을 활용하여 컴퓨팅 성능을 획기적으로 증대할 수 있습니다. 현재 심층 학습 프레임워크에서는 CUDA Toolkit 8.0이 필요합니다.

CUDA를 설치하려면

- 이 [사이트](https://developer.nvidia.com/cuda-80-ga2-download-archive)를 방문하여 CUDA를 다운로드하고 설치합니다.
- CUDA 런타임 라이브러리를 설치한 다음 CUDA 이진 경로를 %PATH% 또는 $Path 환경 변수에 추가합니다.
- Windows에서 기본적으로 이 경로는 "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin"입니다.

![Windows에 CUDA 설치](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn)(CUDA Deep Neural Network) 라이브러리는 NVIDIA가 제공하는 심층 신경망용 GPU 가속 원시 라이브러리입니다. 최신 심층 학습 프레임워크에서는 cuDNN v6가 필요합니다.

cuDNN을 설치하려면:

- [NVIDIA 개발자](https://developer.nvidia.com/rdp/cudnn-download)를 방문하여 최신 패키지를 다운로드 및 설치합니다.
- cuDNN 바이너리가 포함된 디렉터리를 %PATH% 또는 $Path 환경 변수에 추가합니다.
- Windows에서 cudnn64_6.dll을 "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin"에 복사할 수 있습니다.

> [!NOTE]
> CNTK 2.0 및 TensorFlow 1.2.1 같은 이전 심층 학습 프레임워크에는 cuDNN v5.1이 필요합니다. 그러나 여러 cuDNN 버전을 함께 설치할 수 있습니다.

### <a name="python"></a>Python

Python은 심층 학습 애플리케이션의 기본 프로그래밍 언어입니다. **64비트** Python 배포가 필요하며 최상의 호환성을 위해 [Python 3.5.4](https://www.python.org/downloads/release/python-354/)를 사용하는 것이 좋습니다.

### <a name="to-install-python-on-windows"></a>Windows에 Python을 설치하려면

- Python 시작 관리자는 사용자 본인 전용으로 설치하고 Python을 %PATH% 환경 변수에 추가합니다.
- Python으로 작성된 소프트웨어 패키지를 설치 및 관리하는 패키지 관리 시스템인 pip를 설치합니다.

심층 학습 프레임워크는 자체 설치에 pip를 사용합니다.

![Windows에 Python 설치](media/installation/install_python_win.png)

이제 Python 3.5가 제대로 설치되었는지 확인하고 터미널에서 다음 명령을 실행하여 pip를 최신 버전으로 업그레이드합니다.

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Visual Studio의 Python

Python은 확장을 통해 Visual Studio에서 완전히 지원됩니다.
자세한 내용은 [Python for Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) 설치를 참조하세요.

### <a name="numpy-and-scipy"></a>NumPy 및 SciPy

- **NumPy**는 작은 다차원 배열 처리를 위한 대규모 속도 저하 없이 임의 레코드의 대형 다차원 배열을 효율적으로 조작하도록 설계된 범용 배열 처리 패키지입니다.

- **SciPy("싸이파이"로 읽음)** 는 NumPy 기반의 수학, 과학, 공학용 오픈 소스 소프트웨어입니다. 버전 1.0.0부터 SciPy에는 Windows용으로 미리 작성된 공식 휠 패키지가 있습니다.

NumPy 및 SciPy를 설치하려면 터미널에서 다음 명령을 실행합니다.

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> 위의 명령은 기존 구형 또는 비공식(예: http://www.lfd.uci.edu/~gohlke/pythonlibs/ 에서 제공하는 Windows용 타사 패키지) NumPy 및 SciPy를 최신 공식 버전으로 업그레이드합니다.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft CNTK(Cognitive Toolkit)

[Microsoft Cognitive Toolkit](https://cntk.ai)는 지시된 그래프를 통해 일련의 계산 단계로 신경망을 설명하는 통합 심층 학습 도구 키트입니다. CNTK은 Python 및 BrainScript 프로그래밍 언어를 모두 지원합니다.

> [!NOTE]
> CNTK는 현재 macOS를 지원하지 않습니다.

CNTK Python 패키지를 설치하려면 [CNTK를 설치하는 방법](/cognitive-toolkit/Setup-CNTK-on-your-machine)을 참조하세요.

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/)는 데이터 흐름 그래프를 사용한 수치 계산용 오픈 소스 소프트웨어 라이브러리입니다. 자세한 설치는 [여기](https://www.tensorflow.org/install/)를 참조하세요.

> [!NOTE]
> 버전 1.2부터 TensorFlow는 macOS에 GPU 지원을 제공하지 않습니다.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/)는 가벼운 모듈 방식의 확장성 있는 심층 학습 프레임워크입니다. 원래 Caffe를 바탕으로 구축된 Caffe2는 수식, 속도 및 모듈 방식을 목표로 설계되었습니다.

현재 미리 작성된 Caffe2 python 휠 패키지는 제공되지 않습니다.

소스 코드를 통해 빌드하려면 [여기](https://caffe2.ai/docs/getting-started.html)를 방문하세요.

### <a name="mxnet"></a>MXNet

[Apache MXNet(인큐베이팅)](https://mxnet.incubator.apache.org/)은 효율성과 유연성을 위해 설계된 심층 학습 프레임워크입니다. 이를 통해 [기호 및 명령적 프로그래밍](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts)을 **혼합**하여 효율성과 생산성을 극대화할 수 있습니다.

MXNet을 설치하려면 터미널에서 다음 명령을 실행합니다.

- GPU 사용

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- GPU 사용 안 함

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/)는 Python으로 작성된 고급 신경망 API로, CNTK, TensorFlow, 또는 Theano 위에서 실행할 수 있습니다. 신속한 실험 구현에 초점을 맞추어 개발되었습니다. 가능한 최소한의 지연을 통해 결과를 얻도록 하는 것이 훌륭한 연구를 위한 핵심이 됩니다.

Keras를 설치하려면 터미널에서 다음 명령을 실행합니다.

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/)는 다차원 배열이 관련되어 잇는 수학식을 효율적으로 정의, 최적화 및 평가할 수 있게 하는 Python 라이브러리입니다.

Theano를 설치하려면 터미널에서 다음 명령을 실행합니다.

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/)는 두 고급 기능을 제공하는 Python 패키지입니다.

- 강력한 GPU 가속화를 통해 numpy처럼 텐서 계산
- 테이프 기반 오토그래드 시스템을 바탕으로 구축된 심층 신경망

PyTorch를 설치하려면 터미널에서 다음 명령을 실행합니다.

- **Windows**

  아직 공식 휠 패키지가 없습니다. [Anaconda](https://anaconda.org/pytorch/repo?type=all) 또는 [캘리포니아 대학교](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch)에서 타사 패키지를 다운로드할 수 있습니다.

  - 홈 디렉터리(예: *C:\Users\test\pytorch*)에 압축을 풉니다.
  - *C:\Users\test\pytorch\Lib\site-packages*를 %PYTHONPATH% 환경 변수에 추가합니다.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > macOS 이진은 CUDA를 지원하지 않습니다. CUDA가 필요하면 원본에서 설치합니다.

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > 이 단일 패키지는 GPU 및 CPU를 모두 지원합니다.

마지막으로, 비 Windows에 torchvision을 설치합니다.

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/)는 유연성을 목표로 하는 Python 기반 심층 학습 프레임워크입니다. 여기서는 신경망을 빌드하고 학습하는 데 사용되는 개체 지향 고급 API 뿐만 아니라 실행별 정의 방법(동적 계산 그래프라고도 함)을 기준으로 하는 자동 차별화 API를 제공합니다.

CUDA 지원을 사용하려면 [CuPy](https://github.com/cupy/cupy)를 설치합니다.

```bash
pip3.5 install cupy
```

> [!NOTE]
> Windows의 경우 CUDA 8.0을 통한 CuPy를 컴파일하려면 2015 버전의 [Visual Studio](https://visualstudio.microsoft.com/) 또는 [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)가 필요합니다.

Chainer를 설치하려면 터미널에서 다음 명령을 실행합니다.

```bash
pip3.5 install chainer==3.0.0
```
