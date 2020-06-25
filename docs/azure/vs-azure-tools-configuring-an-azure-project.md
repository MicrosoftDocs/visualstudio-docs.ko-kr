---
title: Azure 클라우드 서비스 프로젝트 구성
description: 프로젝트의 요구 사항에 따라 Visual Studio에서 Azure 클라우드 서비스 프로젝트를 구성하는 방법을 알아보세요.
author: ghogen
manager: jillfra
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 1776aebbe827295cbc7902f72417bc57e03a4196
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280637"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Visual Studio에서 Azure 클라우드 서비스 프로젝트 구성
프로젝트 요구 사항에 따라 Azure 클라우드 서비스 프로젝트를 구성할 수 있습니다. 다음 범주에 대해 프로젝트 속성을 설정할 수 있습니다.

- **Azure에 클라우드 서비스 게시** - Azure에 배포된 기존 클라우드 서비스가 실수로 삭제되지 않도록 속성을 설정할 수 있습니다.
- **로컬 컴퓨터에서 클라우드 서비스 실행 또는 디버깅** - 사용할 서비스 구성을 선택하고 Azure Storage 에뮬레이터를 시작할 것인지를 선택할 수 있습니다.
- **생성된 클라우드 서비스 패키지 유효성 검사** - 클라우드 서비스 패키지가 문제 없이 배포되도록 모든 경고를 오류로 처리할 수 있습니다.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Azure 클라우드 서비스 프로젝트 구성 단계
1. Visual Studio에서 클라우드 서비스 프로젝트 열기 또는 만들기

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

1. 프로젝트 속성 페이지에서 **개발** 탭을 선택합니다.

    ![프로젝트 속성 메뉴](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. **기존 배포를 삭제하기 전 알림**을 **True**로 설정합니다. 이 설정을 사용하면 Azure에서 기존 배포를 실수로 삭제되는 일이 없도록 방지할 수 있습니다.

1. 클라우드 서비스를 로컬로 실행 또는 디버그할 때 사용할 서비스 구성을 지정하려면 원하는 **서비스 구성**을 선택합니다. 역할에 대한 서비스 구성을 수정하는 방법에 대한 자세한 내용은 [Visual Studio를 사용하여 Azure 클라우드 서비스에 대한 역할을 구성하는 방법](./vs-azure-tools-configure-roles-for-cloud-service.md)을 참조하세요.

1. 클라우드 서비스를 로컬로 실행 또는 디버그할 경우 Azure Storage 에뮬레이터를 시작하려면 **Azure Storage 에뮬레이터 시작**을 **True**로 설정합니다.

1. 패키지 유효성 검사 오류가 있을 경우 게시하지 않도록 하려면 **경고를 오류로 처리**를 **True**로 설정합니다.

1. 웹 역할이 IIS Express에서 로컬로 시작될 때마다 동일한 포트를 사용하도록 하려면 **웹 프로젝트 포트 사용**을 **True**로 설정합니다.

1. Visual Studio의 도구 모음에서 **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계
- [여러 서비스 구성을 사용하여 Azure 프로젝트 구성](vs-azure-tools-multiple-services-project-configurations.md)
