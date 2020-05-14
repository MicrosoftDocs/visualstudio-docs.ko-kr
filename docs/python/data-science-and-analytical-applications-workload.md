---
title: 데이터 과학 및 분석 애플리케이션 워크로드
description: 이 Visual Studio 워크로드는 Python, F# 및 Anaconda를 비롯한 해당 런타임 배포를 함께 제공합니다. (R도 Visual Studio 2017에만 포함되어 있습니다.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154888"
---
# <a name="install-data-science-support-in-visual-studio"></a>Visual Studio에서 데이터 과학 지원 설치

Visual Studio 설치 관리자를 통해 선택하고 설치한 데이터 과학 및 분석 애플리케이션 워크로드는 여러 언어 및 해당 런타임 분포와 함께 제공합니다.

::: moniker range="vs-2017"
- [Python 및 Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET 프레임워크로 F#](/dotnet/fsharp/)
- [R 및 Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET 프레임워크로 F#](/dotnet/fsharp/)
::: moniker-end

![Visual Studio 설치 관리자의 데이터 과학 및 분석 애플리케이션 워크로드](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python 및 R은 데이터 과학에 사용되는 두 가지 기본 스크립팅 언어입니다. 두 언어는 배우기 쉬우며 풍부한 패키지의 에코시스템에서 지원됩니다. 이러한 패키지는 데이터 취득, 정리, 모델 학습, 배포 및 그리기와 같은 다양한 범위의 시나리오를 해결합니다. 또한 F#은 다양한 데이터 처리 작업에 적합한 강력한 기능 우선 .NET 언어입니다.
::: moniker-end

::: moniker range="vs-2019"
Python은 데이터 과학에 사용되는 기본 스크립팅 언어입니다. Python은 배우기 쉬우며 풍부한 패키지의 에코시스템에서 지원됩니다. 이러한 패키지는 데이터 취득, 정리, 모델 학습, 배포 및 그리기와 같은 다양한 범위의 시나리오를 해결합니다. 또한 F#은 다양한 데이터 처리 작업에 적합한 강력한 기능 우선 .NET 언어입니다. (R 언어의 경우 [Azure Notebooks](https://notebooks.azure.com)를 권장합니다.)
::: moniker-end

<!--Note link on the image because this one is large -->
[![R, Python 및 F#을 사용한 Visual Studio의 스크린샷](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>워크로드 옵션

기본적으로 워크로드는 Visual Studio 설치 관리자의 작업에 대한 요약 섹션에서 수정할 수 있는 다음 옵션을 설치합니다.

::: moniker range="vs-2019"
- F# 데스크톱 언어 지원
- Python:
  - Python 언어 지원
  - Python 웹 지원
::: moniker-end

::: moniker range="vs-2017"
- F# 언어 지원
- Python:
  - Python 언어 지원
  - [Anaconda3 64비트](https://www.continuum.io)는 광범위한 데이터 과학 라이브러리 및 Python 인터프리터를 포함하는 Python 배포판입니다.
  - Python 웹 지원
  - Cookiecutter 템플릿 지원
- R:
  - R 언어 지원
  - R 개발 도구에 대한 런타임 지원
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)(단일 노드 또는 클러스터에서 더 빠른 계산을 위해 ScaleR 라이브러리를 사용하는 Microsoft의 완전히 호환되는, 커뮤니티 지원 R 인터프리터입니다. [CRAN](https://cran.r-project.org/)에서 R을 사용할 수도 있습니다.)
::: moniker-end

## <a name="sql-server-integration"></a>SQL Server 통합

::: moniker range="vs-2017"
SQL Server는 Python과 R 모두를 사용하여 SQL Server 내에서 고급 분석을 직접 수행할 수 있도록 지원합니다. R 지원은 Server 2016 이상과 함께 제공됩니다. Python 지원은 SQL Server 2017 CTP 2.0 이상에서 사용할 수 있습니다.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server는 Python을 사용하여 SQL Server 내에서 직접 고급 분석을 수행할 수 있도록 지원합니다. Python 지원은 SQL Server 2017 CTP 2.0 이상에서 사용할 수 있습니다.
::: moniker-end

데이터가 이미 있는 코드를 실행하여 다음과 같은 장점을 활용할 수 있습니다.

- **데이터 이동의 제거**: 데이터베이스에서 애플리케이션 또는 모델로 데이터를 이동하는 대신 데이터베이스에서 애플리케이션을 빌드할 수 있습니다. 이 기능은 보안의 장벽, 규정 준수, 거버넌스, 무결성 및 방대한 양의 데이터 이동과 관련된 호스트의 비슷한 문제를 제거합니다. 또한 클라이언트 머신의 메모리에 맞출 수 없는 데이터 세트를 사용할 수 있습니다.

- **간편한 배포**: 모델의 준비가 완료되면 프로덕션에 배포하기 위해 T-SQL 스크립트에 포함하기만 하면 됩니다. 어떠한 언어로 작성된 모든 SQL 클라이언트 애플리케이션은 저장된 프로시저 호출을 통해 모델 및 인텔리전스를 활용할 수 있습니다. 특정 언어 통합이 필요하지 않습니다.

- **엔터프라이즈급 성능 및 확장성**: RevoScale 패키지의 고성능 확장 가능 API를 사용하여 메모리 내 테이블 및 열 저장소 인덱스와 같은 SQL Server의 고급 기능을 사용할 수 있습니다. 데이터 이동의 제거는 데이터가 확대되거나 애플리케이션의 성능을 향상시키기 원하므로 클라이언트 메모리 제약 조건을 방지하는 것을 의미하기도 합니다.

- **강력한 확장성**: SQL Server에서 최신 오픈 소스 패키지를 설치하고 실행하여 SQL Server에서 엄청난 양의 데이터에 대한 딥 러닝 및 AI 애플리케이션을 빌드할 수 있습니다. SQL Server에 패키지를 설치하는 것은 로컬 컴퓨터에 패키지를 설치하는 것만큼 간단합니다.

- **추가 비용 없는 광범위한 가용성**: 언어 통합은 Express 버전을 포함하여 SQL Server 2017 이상의 모든 버전에서 사용할 수 있습니다.

SQL Server 통합을 모두 활용하려면 Visual Studio 설치 관리자를 사용하여 **SQL Server Data Tools** 옵션으로 **데이터 스토리지 및 처리** 워크로드를 설치합니다. 두 번째 옵션은 SQL IntelliSense, 구문 강조 표시 및 배포를 활성화합니다.

![데이터 스토리지 및 처리 워크로드](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![데이터 스토리지 및 처리 워크로드 옵션](media/workload/data-storage-workload-options.png)

추가 정보

::: moniker range="vs-2017"
- [SQL Server 및 R 사용](../rtvs/integrating-sql-server-with-r.md)
- [SQL Server 2016에서 R을 사용하여 데이터베이스 내 고급 분석(블로그)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [SQL Server 2017의 Python: 향상된 데이터베이스 내 기계 학습(블로그)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>추가 서비스 및 SDK

데이터 과학 및 분석 애플리케이션 워크로드에 있는 것 외에도 Azure Notebooks 서비스 및 Python용 Azure SDK도 데이터 과학에 유용합니다.

Python용 Azure SDK를 사용하면 Windows, Mac 및 Linux에서 실행되는 애플리케이션에서 Microsoft Azure 서비스를 쉽게 사용하고 관리할 수 있습니다. 자세한 내용은 [Python용 Azure SDK](/azure/python/)를 참조하세요.

Azure Notebooks(현재 미리 보기 상태)는 Microsoft Azure의 클라우드에서 실행되는 Jupyter 노트북에 대한 무료 온라인 액세스를 제공합니다. 서비스는 시작하기 위해 Python, R 및 F#에서 샘플 전자 필기장을 포함합니다. [notebooks.azure.com](https://notebooks.azure.com/)을 방문해 보세요.

<!--Note link on the image because this one is large -->
[![R 샘플에 대한 소개가 있는 Azure Notebooks의 스크린샷](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
