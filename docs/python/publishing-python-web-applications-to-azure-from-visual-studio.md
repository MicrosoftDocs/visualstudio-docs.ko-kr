---
title: Azure App Service에 Python 앱 게시
description: Linux용 Git 배포 및 컨테이너를 비롯하여 Azure App Service에 Python 앱을 게시하고 IIS에 배포하기 위한 옵션입니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c3c8d6c16f2f7e432b6b5e988bf63521f3dfc8c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784117"
---
# <a name="publish-to-azure-app-service"></a>Azure App Service에 게시

현재 Python은 Linux용 Azure App Service에서 지원되며, 이 문서에 설명된 대로 [Git 배포](#publish-to-app-service-on-linux-using-git-deploy) 및 [컨테이너](#publish-to-app-service-on-linux-using-containers)를 사용하여 앱을 게시할 수 있습니다.

> [!Note]
> Windows용 Azure App Service의 Python 지원은 공식적으로 사용이 중단되었습니다. 따라서 Visual Studio의 **게시** 명령은 [IIS 대상](#publish-to-iis)에 대해서만 공식적으로 지원되며, Azure App Service의 원격 디버깅은 더 이상 공식적으로 지원되지 않습니다.
>
> 그러나 Windows의 App Service용 Python 확장이 사용할 수 있지만 서비스 또는 업데이트되지 않기 때문에 [Windows의 App Service에 게시](publish-to-app-service-windows.md) 기능은 여전히 작동합니다.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Git 배포를 사용하여 Linux의 App Service에 게시

Git 배포는 Linux의 App Service를 Git 리포지토리의 특정 분기에 연결합니다. 해당 분기에 코드를 커밋하면 App Service에 자동으로 배포되며, App Service는 *requirements.txt*에 나열된 모든 종속성을 자동으로 설치합니다. 이 경우 Linux의 App Service는 Gunicorn 웹 서버를 사용하는 미리 구성된 컨테이너 이미지에서 사용자 코드를 실행합니다. 현재 이 서비스는 미리 보기로 제공되고 있으며 프로덕션 용도로는 지원되지 않습니다.

자세한 내용은 Azure 설명서의 다음 문서를 참조하세요.

- [빠른 시작: App Service에서 Python 웹앱 만들기](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json)에서는 단순 Flask 앱과 로컬 Git 리포지토리에서 배포를 사용한 Git 배포 프로세스에 대한 간단한 연습을 제공합니다.
- [Python 구성 방법](/azure/app-service/containers/how-to-configure-python)에서는 Linux의 App Service 컨테이너 특성 및 사용자 앱에 대한 Gunicorn 시작 명령을 사용자 지정하는 방법을 설명합니다.

## <a name="publish-to-app-service-on-linux-using-containers"></a>컨테이너를 사용하여 Linux의 App Service에 게시

Linux의 App Service에 미리 빌드된 컨테이너를 사용하지 않고 사용자 고유의 컨테이너를 제공할 수 있습니다. 이 옵션을 통해 사용하는 웹 서버를 선택하고 컨테이너의 동작을 사용자 지정할 수 있습니다.

컨테이너를 빌드, 관리 및 푸시하는 다음 두 가지 옵션이 있습니다.

- [Docker 컨테이너를 사용하여 Python 배포](https://code.visualstudio.com/docs/python/tutorial-deploy-containers)에 설명된 대로 Visual Studio Code 및 Docker 확장을 사용합니다. Visual Studio Code를 사용하지 않더라도, 이 문서에서는 프로덕션에서 바로 사용할 수 있는 uwsgi 및 nginx 웹 서버로 Flask 및 Django 앱에 대한 컨테이너 이미지를 빌드하는 방법에 대한 유용한 세부 정보를 제공합니다. 그런 다음, Azure CLI를 사용하여 동일한 컨테이너를 배포할 수 있습니다.

- Azure 설명서의 [사용자 지정 Docker 이미지 사용](/azure/app-service/containers/tutorial-custom-docker-image)에 설명된 대로 명령줄 및 Azure CLI를 사용합니다. 그러나 이 가이드는 일반적인 것으로, Python과 관련된 가이드는 아닙니다.

## <a name="publish-to-iis"></a>IIS에 게시

Visual Studio에서 **게시** 명령을 사용하여 Windows 가상 머신 또는 다른 IIS 가능 컴퓨터에 게시할 수 있습니다. IIS를 사용하는 경우 Python 인터프리터가 있는 위치를 IIS에 알려 주는 *web.config* 파일을 앱에서 만들거나 수정해야 합니다. 자세한 내용은 [IIS에 대한 웹앱 구성](configure-web-apps-for-iis-windows.md)을 참조하세요.
