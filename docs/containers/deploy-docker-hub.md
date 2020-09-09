---
title: Docker Hub에 ASP.NET Core Docker 컨테이너 배포 | Microsoft Docs
description: Visual Studio Container Tools를 사용하여 Docker Hub에 ASP.NET Core 웹앱을 배포하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2a6db2771525010d73fdeeea12ff4aebd99a1bd2
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485140"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub에 배포

Docker Hub는 이미지 리포지토리를 위한 편리한 호스팅 서비스를 제공합니다. 수동으로 Visual Studio에서 Docker Hub로 쉽게 배포할 수 있습니다.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker 계정 및 Docker Hub 리포지토리 만들기

Docker 계정이 아직 없는 경우 [가입](https://hub.docker.com/signup)합니다.

Docker Hub 리포지토리가 없는 경우 [Docker Hub](https://hub.docker.com/)에서 새로 만듭니다.

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Docker Hub에 단일 프로젝트용 이미지 게시

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **게시...** 를 선택합니다. 배포 옵션을 표시하는 화면이 나타납니다.

   ![배포 옵션 스크린샷](media/container-tools/vs-2019/docker-container-registry.png)

1. **Docker 컨테이너 레지스트리**를 선택한 다음 **Docker Hub**를 선택합니다.

   ![게시 대화 상자 - Docker Hub 선택 스크린샷](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Docker 자격 증명을 입력합니다.

   ![Docker Hub 대화 상자 스크린샷](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. 조직에 속하지 않는 사용자 고유의 리포지토리에 연결하는 경우에는 **개인 리포지토리에 게시** 확인란을 선택된 상태로 둡니다. 조직이 리포지토리를 소유하고 있는 경우, 확인란의 선택을 취소하고 조직 이름을 입력합니다. 연결 중인 리포지토리에 대한 액세스 권한이 있는 Docker 계정의 Docker 사용자 이름과 암호를 입력하고 **저장**을 선택합니다.  

   Visual Studio에서 사용자 이미지를 Docker Hub에 배포하려고 합니다.  작업이 성공하면 리포지토리 이미지의 URL, 이미지 태그, 리포지토리 및 빌드 구성(예: **릴리스**)이 포함된 **게시** 화면이 나타납니다.

   ![게시 화면 스크린샷](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. 언제든지 이 페이지에서 **게시** 단추를 클릭하여 이미지를 업데이트할 수 있습니다.  또는 URL 아래에 있는 링크를 사용하여 프로필을 수정하거나 제거할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Azure Container Registry에 배포](hosting-web-apps-in-docker.md) 단계에 따라 [Azure Container Registry](/azure/container-registry/)에 게시합니다.

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)를 사용하여 CI/CD(연속 통합 및 지속적인 업데이트)를 설정합니다.

## <a name="see-also"></a>참조

[Azure App Service에 배포](deploy-app-service.md)
[Visual Studio Container Tools](./index.yml).