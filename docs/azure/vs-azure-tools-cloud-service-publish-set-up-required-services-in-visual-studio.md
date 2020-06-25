---
title: 클라우드 서비스 게시 또는 배포 준비
description: 클라우드 및 스토리지 계정 서비스를 설정하고 Azure 애플리케이션을 구성하는 절차에 대해 알아봅니다.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 5cd458cca0a0b387ce816f2e7f5dde8153e08410
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280806"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Visual Studio에서 클라우드 서비스 게시 또는 배포 준비

클라우드 서비스 프로젝트를 게시하려면 이 문서에서 설명한 대로 다음 서비스를 설정해야 합니다.

* Azure 환경에서 역할을 실행하는 **클라우드 서비스**
* Blob, 큐 및 Table service에 대한 액세스를 제공하는 **스토리지 계정** .

## <a name="create-a-cloud-service"></a>클라우드 서비스 만들기

Azure 환경에서 역할을 실행하는 클라우드 서비스 다음 섹션에서 설명한 대로 Visual Studio 또는 [Azure Portal](https://portal.azure.com/)을 통해 클라우드 서비스를 만들 수 있습니다.

### <a name="create-a-cloud-service-from-visual-studio"></a>Visual Studio에서 클라우드 서비스 만들기

1. 이전에 만든 클라우드 서비스 프로젝트에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. 필요에 따라 Azure 구독과 연결된 Microsoft 또는 조직 계정으로 로그인하고, **다음**을 선택하여 **설정** 페이지로 이동합니다.
1. **클라우드 서비스 및 스토리지 계정 만들기** 대화 상자가 표시됩니다. 그렇지 않으면 **클라우드 서비스** 목록에서 **새로 만들기**를 선택합니다.
1. 대/소문자를 구분하지 않는 클라우드 서비스 이름을 입력합니다. 이 이름은 URL의 일부이며 고유해야 합니다. 또한 [지역] 또는 [선호도 그룹]을 선택하고 [복제] 옵션을 선택합니다.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Azure Portal을 통해 클라우드 서비스 만들기

1. [Azure Portal](https://portal.azure.com/)에 로그인합니다.
1. 페이지의 왼쪽에서 **Cloud Services(클래식)** 를 선택합니다.
1. **+ 추가**를 선택한 다음, 필요한 정보(DNS 이름, 구독, 리소스 그룹 및 위치)를 제공합니다. 나중에 Visual Studio에서 동일한 작업을 수행하므로 이 시점에서 패키지를 업로드할 필요가 없습니다.
1. **만들기**를 선택하여 프로세스를 완료합니다.

## <a name="create-a-storage-account"></a>스토리지 계정 만들기

스토리지 계정은 Blob, 큐 및 Table service에 대한 액세스를 제공합니다. Visual Studio 또는 [Azure Portal](https://portal.azure.com/)을 통해 스토리지 계정을 만들 수 있습니다.

### <a name="create-a-storage-account-from-visual-studio"></a>Visual Studio에서 스토리지 계정 만들기

1. 이전에 만든 클라우드 서비스 프로젝트가 있는 **솔루션 탐색기**에서 역할 프로젝트 내의 **연결된 서비스** 노드를 찾고, 마우스 오른쪽 단추로 클릭하고, **연결된 서비스 추가**를 선택합니다. (Visual Studio 2015에서는 **스토리지** 노드를 마우스 오른쪽 단추로 클릭하고 **스토리지 계정 만들기**를 선택합니다.)
1. **연결된 서비스** 목록에서 **Azure Storage가 있는 클라우드 스토리지**를 선택합니다.
1. Azure Storage 대화 상자가 표시되면 **+ 새 스토리지 계정 만들기**를 선택합니다. 그러면 구독, 계정 이름, 가격 책정 계층, 리소스 그룹 및 위치를 지정하는 대화 상자가 표시됩니다.
1. 완료되면 **만들기**를 선택합니다. 새 스토리지 계정이 구독에서 사용 가능한 스토리지 계정 목록에 표시됩니다.
1. 해당 계정을 선택하고 **추가**를 선택합니다.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Azure Portal을 통해 스토리지 계정 만들기

1. [Azure Portal](https://portal.azure.com/)에 로그인합니다.
1. 왼쪽 위에서 **+ 새로 만들기**를 선택합니다.
1. &quot;Azure Marketplace&quot; 아래에서 **스토리지**를 선택한 다음, 오른쪽에서 **스토리지 계정 - Blob,파일, 테이블, 큐**를 선택합니다.
1. 필요한 정보(이름, 배포 모델 등)를 제공합니다.
1. **만들기**를 선택하여 프로세스를 완료합니다.

## <a name="configure-your-app-to-use-the-storage-account"></a>스토리지 계정을 사용하도록 앱 구성

스토리지 계정을 만든 후 Visual Studio에서 해당 계정에 연결하면 URL 및 액세스 키를 포함하여 프로젝트에 대한 서비스 구성이 자동으로 업데이트됩니다.

**연결된 서비스 추가**를 사용하여 Visual Studio에서 클라우드 서비스를 만든 경우 `ServiceConfiguration.Cloud.cscfg`와 `ServiceConfiguration.Local.cscfg`를 열어 연결을 확인할 수 있습니다.

Azure Portal을 통해 클라우드 서비스를 만든 경우 [Visual Studio에서 스토리지 계정 만들기](#create-a-storage-account-from-visual-studio)와 동일한 단계를 수행하지만 새 계정을 만드는 대신 기존 계정을 선택합니다. 그런 다음 Visual Studio에서 구성을 업데이트합니다.

설정을 수동으로 구성하려면 클라우드 서비스 프로젝트에서 해당 역할에 대한 Visual Studio의 속성 페이지를 사용합니다(역할을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택함). 자세한 내용은 [스토리지 계정에 연결 문자열 구성](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account)을 참조하세요.

### <a name="about-access-keys"></a>액세스 키 정보

Azure Portal에는 각 Azure Storage 서비스의 리소스에 액세스하는 데 사용할 수 있는 URL과 계정에 대한 기본 및 보조 액세스 키가 표시됩니다. 이러한 키를 사용하여 스토리지 서비스에 대해 수행된 요청을 인증합니다.

보조 액세스 키는 기본 액세스 키로서 스토리지 계정에 대한 동일한 액세스를 제공하며 기본 액세스 키가 손상되는 경우 백업으로 생성됩니다. 또한 정기적으로 액세스 키를 다시 생성하는 것이 좋습니다. 기본 키를 다시 생성하는 동안 보조 키를 사용하기 위한 연결 문자열 설정을 수정한 다음, 보조 키를 다시 생성하는 동안 기본 키를 다시 생성하기 위해 문자열 설정을 수정할 수 있습니다.

## <a name="next-steps"></a>다음 단계

Visual Studio에서 Azure에 앱을 게시하는 방법에 대한 자세한 내용은 [Azure Tools를 사용하여 클라우드 서비스 게시](vs-azure-tools-publishing-a-cloud-service.md)를 참조하세요.
