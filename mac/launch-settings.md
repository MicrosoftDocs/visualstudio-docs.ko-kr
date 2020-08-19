---
title: launchSettings.json 지원
description: 이 문서에서는 Mac용 Visual Studio의 launchSettings.json 지원에 대해 설명합니다.
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247928"
---
# <a name="launchsettingsjson"></a>launchSettings.json

ASP.NET Core 프로젝트를 개발하는 경우, launchSettings.json 파일 내용을 사용자 지정하여 개발 시나리오에서 프로젝트가 시작되는 방식을 구성할 수 있습니다. Mac용 Visual Studio에서 프로젝트 옵션 UI를 사용하거나 직접 편집하여 이 파일을 업데이트할 수 있습니다. 이 파일은 Windows에서 Visual Studio를 실행할 때 또는 `dotnet`을 사용하는 명령줄에서 사용할 수 있는 것과 동일한 구성 파일입니다. 이 파일은 프로젝트의 속성 폴더 아래에 저장됩니다.

자세한 내용은 [ASP.NET Core에서 여러 환경 사용](/aspnet/core/fundamentals/environments)을 참조하세요. 이 문서에서는 Mac용 Visual Studio에서 이 파일을 업데이트하는 방법을 설명합니다.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mac용 Visual Studio를 사용하여 시작 구성 업데이트

Mac용 Visual Studio에서 launchSettings.json 파일을 직접 편집하거나, 프로젝트 옵션을 사용하여 편집할 수 있습니다. 프로젝트 옵션을 표시하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **옵션**을 선택합니다.

![“옵션”이 선택된 프로젝트 바로 가기 메뉴](media/vsmac-ctx-proj-options.png)

**실행** > **구성** > **기본값**을 선택합니다.

![프로젝트 옵션의 "실행", "구성" 및 "기본값"](media/vsmac-run-config-default.png)

여기에서 주로 다음 두 가지를 구성합니다.

- 환경 변수
- 프로젝트의 앱 URL

## <a name="configure-environment-variables"></a>환경 변수 구성

그리드를 사용하여 환경 변수의 값을 지정할 수 있습니다. 이러한 환경 변수는 Mac용 Visual Studio 내에서 애플리케이션을 시작할 때 설정됩니다. ASP.NET Core 애플리케이션을 개발할 때는 특별한 `ASPNETCORE_ENVIRONMENT` 환경 변수에 유의해야 합니다. 자세한 내용은 [ASP.NET Core에서 여러 환경 사용](/aspnet/core/fundamentals/environments)을 참조하세요.


## <a name="configure-the-start-url"></a>시작 URL 구성

애플리케이션이 시작될 때 표시하는 URL을 구성하려면 **ASP.NET Core** 탭으로 이동합니다.

![프로젝트 옵션의 애플리케이션 URL](media/vsmac-run-config-default-aspnetcore.png)

여기서 애플리케이션이 시작될 때 수신 대기하는 URL을 지정할 수 있습니다.
