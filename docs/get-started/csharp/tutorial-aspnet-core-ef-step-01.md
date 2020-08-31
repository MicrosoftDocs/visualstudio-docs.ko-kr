---
title: Entity Framework 및 Visual Studio 2019를 사용하는 ASP.NET Core 웹앱
titleSuffix: ''
description: ASP.NET Core 웹앱을 만들기 전에 첫 번째 단계에서는 이 동영상 자습서 및 단계별 지침을 통해 Visual Studio 2019를 설치하는 방법을 알아봅니다.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f6d069bfa462b8aa75fc9247c08b3662c4a445fd
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801804"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>자습서: Visual Studio 2019와 함께 Entity Framework를 사용하여 첫 번째 ASP.NET Core 앱 만들기

이 자습서에서는 데이터를 사용하는 ASP.NET Core 웹앱을 만들고 Azure에 배포합니다. 이 자습서는 다음 단계로 구성됩니다.

- [1단계: Visual Studio 2019 설치](#step-1-install-visual-studio-2019)
- [2단계: 첫 번째 ASP.NET Core 웹앱 만들기](tutorial-aspnet-core-ef-step-02.md)
- [3단계: Entity Framework를 사용하여 데이터 작업](tutorial-aspnet-core-ef-step-03.md)
- [4단계: ASP.NET Core 앱에서 웹 API 표시](tutorial-aspnet-core-ef-step-04.md)
- [5단계: Azure에 ASP.NET Core 앱 배포](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>1단계: Visual Studio 2019 설치

이 동영상 자습서 및 단계별 지침을 통해 Visual Studio 2019를 설치하는 방법을 알아봅니다. Visual Studio를 이미 설치한 경우 [2단계: 첫 번째 ASP.NET Core 웹앱 만들기](tutorial-aspnet-core-ef-step-02.md)로 건너뜁니다.

_이 비디오를 보고 따라서 Visual Studio를 설치하고 첫 번째 ASP.NET Core 앱을 만듭니다._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>설치 관리자 다운로드

[visualstudio.com](https://visualstudio.com)으로 이동하여 설치 관리자를 찾습니다. Visual Studio 2019 링크를 찾고 클릭하여 다운로드를 시작합니다. Visual Studio의 무료 버전을 보려면 Visual Studio Community를 선택합니다.

## <a name="start-the-installer"></a>설치 관리자 시작

다운로드가 완료되면 **실행**을 클릭하여 설치 관리자를 시작합니다.

![Visual Studio 2019 설치 관리자](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>워크로드 선택

Visual Studio를 여러 종류의 개발에 사용할 수 있으며, 워크로드를 사용하여 빌드하려는 앱 종류에 필요한 모든 것을 쉽게 다운로드할 수 있습니다. 지금은 **ASP.NET 및 웹 개발** 및 **.NET Core 플랫폼 간 개발** 워크로드를 선택합니다. 나중에 설치 관리자를 다시 시작하여 추가 워크로드 및 구성 요소를 설치할 수 있습니다.

![Visual Studio 2019 워크로드 선택](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>설치

**설치**를 클릭하고 설치 관리자가 Visual Studio를 다운로드하여 설치하도록 합니다.

## <a name="run-visual-studio-for-the-first-time"></a>Visual Studio 첫 번째 실행

설치 관리자가 완료되면 Visual Studio가 자동으로 시작됩니다. 몇 가지 유용한 기능이 연결되어 있어 로그인할지 묻는 메시지가 표시되지만, 지금은 나중에 로그인하도록 선택할 수 있습니다. 다음으로 테마 및 개발 설정을 선택할 수 있습니다. 이 설정을 선택하면 첫 번째 프로젝트를 시작할 준비가 된 것입니다. **새 프로젝트 만들기**를 클릭한 다음, **ASP.NET Core 웹 애플리케이션**을 선택합니다.

![Visual Studio 2019 새 ASP.NET Core 웹 애플리케이션 프로젝트 만들기](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>ASP.NET Core 프로젝트 형식 살펴보기

프로젝트 이름 및 위치를 선택한 다음, **만들기**를 선택할 수 있습니다. 이제 ASP.NET Core 애플리케이션에 사용할 템플릿을 선택합니다. 다음 옵션 중에서 선택할 수 있습니다.

- 비어 있음. 처음부터 시작할 수 있는 빈 프로젝트 템플릿입니다.
- API. 웹 API에 가장 적합합니다.
- 웹 애플리케이션. Razor Pages를 사용하여 빌드된 표준 ASP.NET Core 웹 애플리케이션입니다.
- 웹 애플리케이션(Model-View-Controller) Model-View-Controller 패턴을 사용하는 표준 ASP.NET Core 웹 애플리케이션입니다.
- Angular.
- React.js.
- React.js / Redux.
- Razor 클래스 라이브러리. 프로젝트 간에 Razor 자산을 공유하는 데 사용됩니다.

대부분의 프로젝트 템플릿에서는 상자를 선택하여 Docker 지원을 사용하도록 설정할 수 있습니다. [인증 변경] 단추를 클릭하여 인증 지원을 추가할 수도 있습니다. 여기서 다음 옵션을 선택할 수 있습니다.

- 인증 없음.
- 개별 사용자 계정. 이 항목은 로컬 또는 Azure 기반 데이터베이스에 저장됩니다.
- 회사 또는 학교 계정. 이 옵션은 인증에 Active Directory, Azure AD 또는 Microsoft 365를 사용합니다.
- Windows 인증. 인트라넷 애플리케이션에 적합합니다.

인증 없음과 함께 표준 웹 애플리케이션 템플릿을 선택하고 **만들기**를 클릭합니다.

![Visual Studio 2019 ASP.NET Core 프로젝트 옵션 선택](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>다음 단계

다음 동영상에서는 첫 번째 ASP.NET Core 프로젝트에 대해 자세히 알아보겠습니다.

[자습서: 첫 번째 ASP.NET Core 웹앱 만들기](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>참조

- [자습서: C# 및 ASP.NET Core 시작](tutorial-aspnet-core.md) 동영상 연습이 없는 더 자세한 자습서
