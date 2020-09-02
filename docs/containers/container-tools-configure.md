---
title: Visual Studio Container Tools 구성
description: Docker 컨테이너 작업을 위해 Visual Studio에서 사용할 수 있는 도구를 구성합니다.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: d2b3e2821e7697ad53b10a7148c22140aa1a07af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283218"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Visual Studio Container Tools 구성 방법

Visual Studio 설정을 사용하면 Docker 컨테이너 작업 시 성능과 리소스 사용량에 영향을 주는 설정을 포함하여 Visual Studio에서 Docker 컨테이너를 사용하는 방식의 몇 가지 측면을 제어할 수 있습니다.

## <a name="container-tools-settings"></a>컨테이너 도구 설정

주 메뉴에서 **도구 > 옵션**을 선택하고, **컨테이너 도구 > 설정**을 확장합니다. 그러면 컨테이너 도구 설정이 표시됩니다.

::: moniker range="vs-2017"

![Visual Studio Container Tools 옵션: 프로젝트 로드 시 필요한 Docker 이미지를 자동으로 끌어오기, 백그라운드에서 자동으로 컨테이너 시작, 솔루션이 닫히면 자동으로 컨테이너 종료, 신뢰할 수 있는 SSL 인증서에는 메시지를 표시하지 않기](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

컨테이너 도구 **일반** 설정:

![Visual Studio Container Tools 옵션: 필요한 경우 Docker Desktop 설치, ASP.NET Core SSL 인증서 신뢰](./media/configure-container-tools/tools-options-1.png)

컨테이너 도구 **단일 프로젝트** 및 **Docker Compose** 설정:

![Visual Studio Container Tools 옵션: 프로젝트를 닫을 때 컨테이너 종료, 프로젝트를 열 때 필요한 Docker 이미지 풀하기, 프로젝트를 열 때 컨테이너 실행](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

다음 표는 이러한 옵션을 설정하는 방법을 결정하는 데 도움이 될 수 있습니다.

::: moniker range="vs-2017"
| 이름 | 기본 설정 | 적용 대상 | 설명 |
| -----|:---------------:|:----------:| ----------- |
| 프로젝트 로드 시 필요한 Docker 이미지를 자동으로 끌어오기 | 켜기 | Docker Compose | 프로젝트를 로드할 때 성능을 향상하기 위해 Visual Studio는 백그라운드에서 Docker 끌어오기 작업을 수행합니다. 이렇게 하면 코드를 실행할 준비가 되었을 때 이미지가 이미 다운로드되어 있거나 다운로드 중입니다. 단순히 프로젝트를 로드하고 코드를 검색하려는 경우에는 불필요한 컨테이너 이미지를 다운로드하지 않도록 이 기능을 끄면 됩니다. |
| 백그라운드에서 자동으로 컨테이너 시작 | 켜기 | Docker Compose | 마찬가지로 성능을 향상하기 위해 Visual Studio는 개발자가 컨테이너를 빌드하고 실행할 때 볼륨 탑재가 완료된 컨테이너를 만듭니다. 컨테이너를 만드는 시기를 제어하려면 이 기능을 끕니다. |
| 솔루션이 닫히면 자동으로 컨테이너 종료 | 켜기 | Docker Compose | 솔루션을 닫거나 Visual Studio를 닫은 후에도 솔루션의 컨테이너를 계속 실행하려면 이 기능을 끕니다. |
| 신뢰할 수 있는 localhost SSL 인증서에는 메시지를 표시하지 않기 | 끄기 | ASP.NET Core 2.1 프로젝트 | localhost SSL 인증서를 신뢰할 수 없는 경우 이 확인란을 선택하지 않으면 프로젝트를 실행할 때마다 Visual Studio가 메시지를 표시합니다. |
::: moniker-end

::: moniker range=">=vs-2019"

다음 표에서는 **일반** 설정에 대해 설명합니다.

| 이름 | 기본 설정 | 적용 대상 | 설명 |
| -----|:---------------:|:----------:| ----------- |
| 필요한 경우 Docker Desktop 설치 | 메시지 표시 | 단일 프로젝트, Docker Compose | Docker Desktop이 설치되어 있지 않은 경우 메시지를 표시할지 여부를 선택합니다. |
| ASP.NET Core SSL 인증서 신뢰 | 메시지 표시 | ASP.NET Core 2.x 프로젝트 | **메시지 표시**로 설정된 경우, localhost SSL 인증서를 신뢰할 수 없으면 프로젝트를 실행할 때마다 Visual Studio에서 메시지가 표시됩니다. |

다음 표에서는 **단일 프로젝트** 및 **Docker Compose** 설정에 대해 설명합니다.

| 이름 | 기본 설정 | 적용 대상 | 설명 |
| -----|:---------------:|:----------:| ----------- |
| 프로젝트를 열 때 필요한 Docker 이미지 풀하기 | True | 단일 프로젝트, Docker Compose | 프로젝트를 로드할 때 성능을 향상하기 위해 Visual Studio는 백그라운드에서 Docker 끌어오기 작업을 수행합니다. 이렇게 하면 코드를 실행할 준비가 되었을 때 이미지가 이미 다운로드되어 있거나 다운로드 중입니다. 프로젝트를 로드하고 코드를 검색하기만 하는 경우에는 불필요한 컨테이너 이미지를 다운로드하지 않도록 **False**로 설정할 수 있습니다. |
| 프로젝트를 열 때 컨테이너 실행 | True | 단일 프로젝트, Docker Compose | 마찬가지로 성능 향상을 위해, Visual Studio는 준비된 상태에서 컨테이너를 빌드하고 실행할 수 있도록 컨테이너를 미리 만듭니다. 컨테이너를 만드는 시기를 제어하려면 **False**로 설정합니다. |
| 프로젝트를 닫을 때 컨테이너 중지 | True | 단일 프로젝트 및 Docker Compose | 솔루션을 닫거나 Visual Studio를 닫은 후에도 솔루션의 컨테이너를 계속 실행하려면 **False**로 설정합니다. |

::: moniker-end
> [!WARNING]
> localhost SSL 인증서를 신뢰할 수 없고, 메시지를 표시하지 않는 확인란을 선택한 경우 런타임에 앱 또는 서비스에서 HTTPS 웹 요청이 실패할 수 있습니다. 이 경우 **메시지 표시 안 함** 확인란을 선택 취소하고, 프롬프트에서 신뢰를 표시합니다.

## <a name="next-steps"></a>다음 단계

[개요](overview.md)에서 Visual Studio의 컨테이너 작업에 대해 자세히 알아봅니다.