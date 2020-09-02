---
title: 시작 페이지 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665846"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Visual Studio 시작 페이지 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 시작 페이지를 사용자 지정할 수 있는 기본 방법에는 **프로젝트 열기** 대화 상자 표시 또는 가장 최근에 로드한 솔루션 열기 등 여러 가지가 있습니다. 도구 창에서 실행되는 WPF(Windows Presentation Foundation) XAML 페이지인 사용자 지정 시작 페이지를 표시하고 Visual Studio 내부에 있는 명령을 실행할 수도 있습니다.

## <a name="customizing-the-default-start-page"></a>기본 시작 페이지 사용자 지정

1. 메뉴 모음에서 **도구**, **옵션**을 선택 합니다.

2. **환경**을 확장한 다음 **시작**을 선택합니다.

3. **시작 시** 목록에서 원하는 사용자 지정 항목을 선택합니다.

## <a name="show-a-custom-start-page"></a>사용자 지정 시작 페이지 표시

1. 사용자 지정 시작 페이지를 설치하는 방법은 다음과 같습니다.

    - [Visual Studio Marketplace](https://marketplace.visualstudio.com/), 다른 웹 사이트 또는 로컬 인트라넷의 페이지에서 설치할 수 있습니다.

        > [!NOTE]
        > 이전 버전의 Visual Studio를 대상으로 한 페이지가 필요한 경우 Visual Studio SDK를 사용하여 페이지를 업그레이드할 수 있습니다. [방법: Visual Studio 사용자 지정 시작 페이지 업그레이드](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md)를 참조하세요.

         사용자 지정 시작 페이지를 포함하는 .vsix 파일을 열거나 시작 페이지 파일을 컴퓨터의 **%USERPROFILE% \My Documents\Visual Studio 2015\StartPages** 폴더에 복사하여 붙여넣습니다.

    - Visual Studio SDK를 설치한 경우 고유의 시작 페이지를 만듭니다.

         [고유한 시작 페이지 만들기](../misc/creating-your-own-start-page.md)를 참조하세요.

2. 메뉴 모음에서 **도구**, **옵션**을 선택 합니다.

3. **환경**을 확장한 다음 **시작**을 선택합니다.

4. **시작 페이지 사용자 지정** 목록에서 원하는 페이지를 선택합니다.

> [!NOTE]
> 사용자 지정 시작 페이지에 오류가 있어 Visual Studio에 충돌이 발생하면 안전 모드에서 Visual Studio를 시작한 다음 기본 시작 페이지를 사용하도록 설정할 수 있습니다. [/SafeMode(devenv.exe)](../ide/reference/safemode-devenv-exe.md)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [고유한 시작 페이지 만들기](../misc/creating-your-own-start-page.md)
