---
title: Visual Studio 설치 관리자 프로젝트 및 .NET Core 3.1
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c35e6a12262083d09575b51f6c9f918ba30a27b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88714400"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Visual Studio 설치 관리자 프로젝트 확장 및 .NET Core 3.1

응용 프로그램을 MSI로 패키징하는 것은 Visual Studio 설치 관리자 프로젝트 확장을 사용 하 여 수행 하는 경우가 많습니다.

[Visual Studio 설치 관리자 프로젝트](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects) 에서 확장을 다운로드할 수 있습니다.

## <a name="update-for-net-core"></a>.NET Core에 대 한 업데이트
.NET Core에는 게시를 위한 두 가지 모델이 있습니다.

- 프레임 워크 종속 배포

- 자체 포함 응용 프로그램은 런타임을 포함 합니다.

이러한 배포 전략에 대해 자세히 알아보려면 [.Net Core 응용 프로그램 게시 개요](https://docs.microsoft.com/dotnet/core/deploying/)를 참조 하세요.

### <a name="workflow-changes-for-net-core-31"></a>.NET Core 3.1에 대 한 워크플로 변경

1. **기본 출력** 대신 **항목 게시** 를 선택 하 여 .net Core 3.1 프로젝트에 대 한 올바른 출력을 가져옵니다.  이 대화 상자를 표시 하려면 **Add**  >  프로젝트의 상황에 맞는 메뉴에서**프로젝트 출력** 추가 ...를 선택 합니다.

    ![프로젝트 출력 그룹 추가 대화 상자의 게시 항목 출력 그룹](../deployment/media/installer-projects-net-core-publish-items-output.png "게시 항목 선택")

2. 자체 포함 된 설치 관리자를 만들려면 올바른 속성이 설정 된 게시 프로필의 상대 경로를 사용 하 여 설치 프로젝트의 **게시 항목** 노드에서 **PublishProfilePath** 속성을 설정 합니다.

    ![게시 항목 프로젝트 출력 항목에 게시 프로필 설정](../deployment/media/installer-projects-net-core-publish-profile.png "게시 프로필 설정")

### <a name="prerequisites-for-net-core-31"></a>.NET Core 3.1에 대 한 필수 구성 요소

설치 관리자에서 프레임 워크 종속 .NET Core 3.1 앱에 필요한 런타임을 설치할 수 있도록 하려면 [필수 구성 요소](../deployment/application-deployment-prerequisites.md)를 사용 하 여이 작업을 수행할 수 있습니다.  설치 관리자 프로젝트의 속성 대화 상자에서 **필수 구성 요소 ...** 대화 상자를 열면 다음 항목이 표시 됩니다.

![필수 구성 요소 대화 상자의 .NET Core 항목](../deployment/media/installer-projects-net-core-prerequisites.png ".NET Core 필수 조건")

WPF/WinForms 응용 프로그램에 대해 .net **Core runtime** ... 옵션을 선택 하 여 콘솔 응용 **프로그램을 선택** 해야 합니다.

>[!NOTE]
>이러한 항목은 Visual Studio 2019 업데이트 7 릴리스부터 제공 됩니다.

## <a name="see-also"></a>추가 정보

- [필수 조건 대화 상자](../ide/reference/prerequisites-dialog-box.md)
- [응용 프로그램 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)
