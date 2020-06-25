---
title: IntelliTrace로 게시된 Azure 클라우드 서비스 디버그
description: Visual Studio 및 IntelliTrace를 사용하여 클라우드 서비스를 디버그하는 방법을 알아봅니다.
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: how-to
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: 1e4de25f3d1b00459128b89bc5559f55cec8f077
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280598"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio 및 IntelliTrace를 사용하여 게시된 Azure 클라우드 서비스 디버깅
IntelliTrace를 사용하여 Azure에서 실행할 때 역할 인스턴스에 대한 광범위한 정보를 기록할 수 있습니다. 문제의 원인을 찾아야 하는 경우 Azure에서 실행 중인 것처럼 Visual Studio에서 코드를 단계별로 실행하는 데 IntelliTrace 로그를 사용할 수 있습니다. 실제로 Azure에서 Azure 애플리케이션을 클라우드 서비스로 실행 중일 때 IntelliTrace는 키 코드 실행 및 환경 데이터를 기록하여 Visual Studio에서 기록된 데이터를 재생할 수 있습니다.

Visual Studio Enterprise가 설치되어 있으며 Azure 애플리케이션 대상 .NET Framework 4 이상 버전이 있는 경우 IntelliTrace를 사용할 수 있습니다. IntelliTrace는 Azure 역할에 대한 정보를 수집합니다. 이러한 역할에 대한 가상 머신은 항상 64비트 운영 체제를 실행합니다.

또는 [원격 디버깅](vs-azure-tools-debugging-cloud-services-overview.md) 을 사용 하 여 Azure에서 실행 되는 클라우드 서비스에 직접 연결할 수 있습니다.

> [!IMPORTANT]
> IntelliTrace는 디버그 시나리오 전용이며 프로덕션 배포용으로 사용할 수 없습니다.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>IntelliTrace에 대한 Azure 애플리케이션 구성
Azure 애플리케이션에 IntelliTrace를 사용하려면 Visual Studio Azure 프로젝트에서 애플리케이션을 만들고 게시해야 합니다. Azure에 게시하기 전에 Azure 애플리케이션에 대한 IntelliTrace를 구성해야 합니다. IntelliTrace를 구성하지 않고 애플리케이션을 게시하는 경우 프로젝트를 다시 게시해야 합니다. 자세한 내용은 [Visual Studio를 사용하여 Azure Cloud Services 게시](vs-azure-tools-publishing-a-cloud-service.md)를 참조하세요.

1. Azure 응용 프로그램을 배포할 준비가 되면 프로젝트 빌드 대상이 **디버그**로 설정되었는지 확인합니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **게시**를 선택합니다.

1. **Azure 애플리케이션 게시** 대화 상자에서 Azure 구독을 선택하고 **다음**을 선택합니다.

1. **설정** 페이지에서 **고급 설정** 탭을 선택합니다.

1. IntelliTrace 로그가 클라우드에 게시될 때 애플리케이션에서 해당 로그를 수집하려면 **IntelliTrace 사용** 옵션을 설정합니다.

1. 기본 IntelliTrace 구성을 사용자 지정하려면 **IntelliTrace 사용** 옆의 **설정**을 선택합니다.

    ![IntelliTrace 설정 링크](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. **IntelliTrace 설정** 대화 상자에서 기록할 이벤트, 호출 정보를 수집할지 여부, 로그를 수집할 모듈 및 프로세스, 기록에 할당할 공간의 크기를 지정할 수 있습니다. IntelliTrace에 대한 자세한 내용은 [IntelliTrace로 디버깅](../debugger/intellitrace.md)을 참조하세요.

    ![IntelliTrace 설정](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace 로그는 IntelliTrace 설정에 지정된 최대 크기(기본 크기는 250MB)의 순환 로그 파일입니다. IntelliTrace 로그는 가상 머신의 파일 시스템에 있는 파일에 수집됩니다. 로그를 요청하는 경우 스냅샷이 해당 시점에 수행되며 로컬 컴퓨터에 다운로드됩니다.

Azure 클라우드 서비스를 Azure에 게시한 후 다음 그림에 표시된 것처럼 **서버 탐색기**의 Azure 노드에서 IntelliTrace가 활성화되었는지를 확인할 수 있습니다.

![서버 탐색기 - IntelliTrace 사용](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>역할 인스턴스에 대한 IntelliTrace 로그 다운로드
Visual Studio를 사용하면 다음 단계를 통해 역할 인스턴스에 대한 IntelliTrace 로그를 다운로드할 수 있습니다.

1. **서버 탐색기**에서 **Cloud Services** 노드를 확장하고 로그를 다운로드할 역할 인스턴스를 찾습니다.

1. 역할 인스턴스를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **IntelliTrace 로그 보기**를 선택합니다.

    ![IntelliTrace 로그 보기 메뉴 옵션](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace 로그는 로컬 컴퓨터의 디렉터리에 있는 파일에 다운로드됩니다. IntelliTrace 로그를 요청할 때마다 새 스냅샷이 생성됩니다. 로그가 다운로드되는 경우 Visual Studio는 **Azure 활동 로그** 창에서 작업의 진행률을 표시합니다. 다음 그림에 표시된 것과 같이 작업에 대한 품목을 확장하여 자세한 사항을 볼 수 있습니다.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace 로그를 다운로드하는 동안 Visual Studio에서 작업을 계속할 수 있습니다. 로그 다운로드가 완료되면 Visual Studio에서 열립니다.

> [!NOTE]
> IntelliTrace 로그는 프레임워크가 생성하고 이후에 처리하는 예외를 포함할 수 있습니다. 내부 프레임워크 코드는 안전하게 무시할 수 있도록 역할을 시작할 때의 일반적인 한 부분으로 이러한 예외를 생성합니다.
>
>

## <a name="next-steps"></a>다음 단계
- [Azure Cloud Services 디버깅 옵션](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio를 사용하여 클라우드 서비스 게시](vs-azure-tools-publishing-a-cloud-service.md)