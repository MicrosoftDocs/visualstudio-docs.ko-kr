---
title: Dotfuscator Community 설치
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 보호, community edition, 난독 처리, .NET, 무료, Visual Studio 2017, Visual Studio 2019, Visual Studio, 설치
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Visual Studio에 포함된 Dotfuscator Community 무료 복사본을 설치하는 방법을 알아봅니다.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: bb659976126713a11594ad1b4aeb536510744c38
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596816"
---
# <a name="install-dotfuscator-community"></a>Dotfuscator Community 설치

Dotfuscator Community는 Visual Studio의 선택적 구성 요소입니다.
이 지침에서는 설치 방법을 설명합니다.

> [!NOTE]
> Visual Studio 릴리스와 함께 제공된 Dotfuscator Community 버전 외에도 PreEmptive Solutions에서는 웹 사이트에 정기적으로 업데이트된 버전을 제공합니다.
> **최신 버전**을 Visual Studio에서 설치하지 않고 직접 다운로드하려면 **[여기를 클릭하여 Dotfuscator 다운로드 페이지로 이동][download]** 합니다.

## <a name="within-visual-studio"></a>Visual Studio 내에서

::: moniker range="vs-2019"

Visual Studio IDE에서 Dotfuscator Community를 설치할 수 있습니다.

1. **검색 상자**(Ctrl+Q)에 `dotfuscator`을 입력합니다. <br/> <br/> ![검색 상자](media/install_in_vs19_12.png) <br/> <br/>

2. 표시되는 검색 결과에서 ‘구성 요소’ 제목 아래에 있는 **PreEmptive Protection - Dotfuscator 설치**를 선택합니다. 
   * ‘메뉴’ 제목 아래에 **PreEmptive Protection - Dotfuscator Community**가 대신 표시되면 Dotfuscator Community가 이미 설치되어 있습니다.  해당 옵션을 선택하여 [시작][get-started]합니다.

3. Dotfuscator Community를 설치하도록 미리 구성된 Visual Studio 설치 관리자 창이 시작됩니다.
   > [!NOTE]
   > 계속하려면 관리자 자격 증명을 제공해야 할 수 있습니다.

4. [Visual Studio 설치 관리자] 창에서 *설치*를 클릭합니다. <br/> <br/> ![설치 클릭](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Visual Studio IDE에서 Dotfuscator Community를 설치할 수 있습니다.

1. **빠른 실행**(Ctrl+Q) 검색 창에서 `dotfuscator`를 입력합니다. <br/> <br/> ![빠른 실행](media/install_from_vs_12.png) <br/> <br/>

2. 표시된 빠른 실행 결과 중 *설치* 제목 아래에서 **PreEmptive Protection - Dotfuscator(개별 구성 요소)** 를 선택합니다.
   * *메뉴* 제목 아래에서 **도구 - PreEmptive Protection - Dotfuscator**를 확인하면 Dotfuscator CE가 이미 설치되어 있습니다. 해당 옵션을 선택하여 [시작][get-started]합니다.

3. Dotfuscator CE를 설치하도록 미리 구성된 Visual Studio 설치 관리자 창이 시작됩니다.
   > [!NOTE]
   > 계속하려면 관리자 자격 증명을 제공해야 할 수 있습니다.

4. [Visual Studio 설치 관리자] 창에서 *설치*를 클릭합니다. <br/> <br/> ![설치 클릭](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

설치가 완료되면 [Dotfuscator Community 사용을 시작][get-started]할 수 있습니다.

## <a name="during-visual-studio-installation"></a>Visual Studio를 설치하는 동안

Visual Studio를 아직 설치하지 않은 경우 [Visual Studio 웹 사이트][vs-install]에서 설치 관리자를 다운로드할 수 있습니다.
설치 관리자를 실행하면 선택된 Visual Studio 버전에 대한 설치 옵션이 표시됩니다.

::: moniker range="vs-2019"

![설치 옵션](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![설치 옵션](media/install_ui_17.png)

::: moniker-end

Dotfuscator Community를 Visual Studio의 개별 구성 요소로 설치할 수 있습니다.

1. **개별 구성 요소** 탭을 선택합니다.
2. *코드 도구*에서 *PreEmptive Protection - Dotfuscator* 항목을 선택합니다.<br/> <br/> ![개별 구성 요소](media/install_individually_12.png) <br/> <br/>
3. *요약* 패널에서 *개별 구성 요소* 섹션 아래에 *PreEmptive Protection - Dotfuscator*가 표시됩니다. <br/> <br/> ![요약 창](media/install_individually_3.png) <br/> <br/>
4. 환경에 맞게 추가 설치 설정을 구성합니다.
5. Visual Studio를 설치할 준비가 되면 *설치* 단추를 클릭합니다.

설치가 완료되면 Dotfuscator Community 사용을 시작할 수 있습니다. 자세한 내용은 [전체 Dotfuscator Community 사용자 가이드의 시작하기][get-started] 페이지를 참조하세요.

## <a name="see-also"></a>참조

[전체 Dotfuscator Community 사용자 가이드의 이 항목](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
