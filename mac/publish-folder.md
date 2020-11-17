---
title: 폴더에 게시
description: Mac용 Visual Studio를 사용하여 폴더에 웹 애플리케이션을 게시하는 방법입니다.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 640cdf8b9c31bad42f8c5664f3cef44c558e2a3a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493415"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Mac용 Visual Studio를 사용하여 폴더에 게시

게시 도구를 사용하여 .NET Core 콘솔 또는 ASP.NET Core 앱을 폴더에 게시할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

- .NET Core가 사용하도록 설정된 상태로 설치된 [Mac용 Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019).
- .NET Core 콘솔 또는 ASP.NET Core 프로젝트. 아직 프로젝트가 없는 경우 [새 프로젝트를 만들 수 있습니다](./create-new-projects.md).

## <a name="publish-to-folder"></a>폴더에 게시

Mac용 Visual Studio를 사용하면 게시 도구를 통해 .NET Core 프로젝트를 폴더에 게시할 수 있습니다. 폴더에 게시한 후 파일을 다른 환경으로 전송할 수 있습니다. 폴더에 게시하려면 다음 단계를 따르세요.

 1. 솔루션 창에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시** 를 선택합니다.

    ![게시 상황에 맞는 메뉴](media/publish-context-menu.png)

 2. 이전에 이 프로젝트를 게시한 적이 있다면 메뉴에 게시 프로필이 표시됩니다. 해당 게시 프로필을 선택하여 게시 프로세스를 시작하세요.

 3. 이 프로젝트를 폴더에 처음으로 게시하려면 **폴더에 게시** 를 선택합니다.

    ![폴더에 게시 상황에 맞는 메뉴](media/publish-to-folder-context-menu.png)

 4. **폴더에 게시** 대화 상자가 나타납니다. 이 대화 상자에서 프로젝트를 게시할 폴더를 사용자 지정할 수 있습니다. **찾아보기** 단추를 사용하여 이 작업을 수행하거나 경로를 붙여넣을 수 있습니다.

 5. **게시** 를 클릭하면 몇 가지 작업이 수행됩니다. 먼저 게시 프로필이 생성됩니다. 게시 프로필은 게시 프로세스 중에 프로젝트로 가져온 MSBuild 파일입니다. 여기에는 게시 프로세스 중에 사용되는 속성이 포함됩니다. 이러한 파일은 `Properties/PublishProfiles`에 저장되며 확장명이 `.pubxml`입니다. 다음으로, 게시 프로세스가 시작됩니다. Mac용 Visual Studio의 상태 표시줄을 보고 진행 상태를 모니터링할 수 있습니다.

    ![게시 상태의 IDE 상태 표시줄](media/publish-to-folder-status-bar.png)

 6. 게시가 성공적으로 완료되면 Finder 창에 게시 폴더가 열립니다. 이제 게시 프로필이 생성되었으므로 게시 상황에 맞는 메뉴에 표시됩니다.

    ![폴더 프로필의 게시 상황에 맞는 메뉴](media/publish-context-menu-with-folder-profile.png)

 7. 동일한 설정을 사용하여 프로젝트를 다시 게시하려면 게시 상황에 맞는 메뉴에서 프로필을 클릭하면 됩니다.

## <a name="customize-publish-options"></a>게시 옵션 사용자 지정

게시 상황에 맞는 메뉴에 표시되는 게시 프로필의 이름을 변경하려면 게시 프로필 파일의 이름을 변경하세요. 파일의 확장명(`.pubxml`)은 변경하지 않도록 하세요.

게시 폴더 경로를 변경하려면 게시 프로필을 열고 `publishUrl` 값을 편집합니다.

사용되는 빌드 구성을 변경하려면 게시 프로필의 `LastUsedBuildConfiguration` 속성을 변경합니다.