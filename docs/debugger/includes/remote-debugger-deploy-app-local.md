---
title: 로컬 폴더에 배포
description: 로컬 폴더에 앱 배포
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89325827"
---
1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **게시**(Web Forms의 경우 **웹앱 게시**)를 선택합니다.

    게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새 프로필**을 클릭합니다.

1. **게시** 대화 상자에서 **폴더**를 선택하고 **찾아보기**를 클릭하여 새 폴더 **C:\Publish**를 만듭니다.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Web Forms 앱의 경우 게시 대화 상자에서 **사용자 지정**을 선택하고 프로필 이름을 입력한 다음, **확인**을 선택합니다.

1. 드롭다운 목록에서 **프로필 만들기**를 클릭합니다(**게시**가 기본값).

1. **게시** 대화 상자에서 **설정** 링크를 클릭한 다음, **설정** 탭을 선택합니다.

1. 구성을 **디버그**로 설정하고 **게시 전에 모든 기존 파일 삭제**를 선택한 후 **저장**을 클릭합니다.

    > [!NOTE]
    > 릴리스 빌드를 사용하는 경우 게시할 때 web.config 파일에서 디버깅을 사용하지 않도록 설정합니다.

1. **게시**를 클릭합니다.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    애플리케이션은 프로젝트의 **디버그** 구성을 로컬 폴더에 게시합니다. 진행률이 출력 창에 표시됩니다.

1. Visual Studio 컴퓨터의 ASP.NET 프로젝트 디렉터리를 Windows Server 컴퓨터에서 ASP.NET에 대해 구성된 로컬 디렉터리(이 예에서는 **C:\Publish**)에 복사합니다. 이 자습서에서는 수동으로 복사하는 것을 가정하고 설명하지만 PowerShell, Xcopy 또는 Robocopy 같은 다른 도구를 사용할 수도 있습니다.

    > [!CAUTION]
    > 코드를 변경하거나 다시 빌드해야 하는 경우 다시 게시하고 이 단계를 반복해야 합니다. 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.    이렇게 하지 않으면 프로세스를 디버그하려고 할 때 Visual Studio에서 `cannot find or open the PDB file` 경고가 표시됩니다.

1. Windows Server에서 브라우저에서 앱을 열어 앱을 제대로 실행할 수 있는지 확인합니다.

    앱이 제대로 실행되지 않는다면 서버에 설치된 ASP.NET 버전과 Visual Studio 머신의 버전이 일치하지 않을 수 있습니다. 또는 IIS 또는 웹 사이트 구성에 문제가 있을 수도 있습니다. 이전 단계를 다시 확인합니다.
