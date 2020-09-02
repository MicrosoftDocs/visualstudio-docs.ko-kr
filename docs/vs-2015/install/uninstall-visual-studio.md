---
title: Visual Studio 2015 제거 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546904"
---
# <a name="uninstall-visual-studio"></a>Visual Studio 제거
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대한 최신 설명서는 [Visual Studio 제거](/visualstudio/install/uninstall-visual-studio)를 참조하세요.

이 페이지에서는 개발자를 위한 통합 생산성 도구 제품군의 이전 버전인 Visual Studio 2015를 제거하는 과정을 안내합니다.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>“표준” 제거 방법을 사용하여 Visual Studio 제거

1. **제어판**의 **프로그램 및 기능** 페이지에서 제거할 제품 버전을 선택한 다음, **변경**을 선택합니다.

2. 설치 마법사에서 **제거**, **예**를 차례로 선택한 다음, 마법사의 나머지 지시를 따릅니다.

   이 표준 또는 기본 방법은 Visual Studio를 처음 설치할 때 함께 설치된 일부 항목을 원래 설치된 대로 둡니다(예: Microsoft .NET Framework, Microsoft Visual C++ 재배포 가능 패키지, Microsoft SQL Server 등).   다른 많은 애플리케이션에서 이 항목을 사용하므로 해당 항목을 설치된 대로 둡니다. 그러나 이 항목도 제거하려면 **프로그램 및 기능**에서 해당 항목을 선택한 다음, 각각 개별적으로 제거합니다.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Visual Studio 및 기타 관련된 모든 파일을 제거합니다(거의 모든 것 제거).

1. Visual Studio .exe 파일(예: “vs_enterprise.exe”)을 찾습니다.

    > [!NOTE]
    > 파일은 “%ProgramData%\Package Cache”의 하위 폴더에 있습니다(예: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe).

2. /uninstall /force 명령줄 매개 변수를 사용하여 .exe 파일을 실행합니다.

     예를 들어 ```vs_enterprise.exe /uninstall /force```를 실행하면 Visual Studio 및 기본 설치에 함께 설치된 대부분의 핵심 구성 요소가 제거됩니다. 그러나 Visual Studio 추가 기능 및 확장과 함께 설치될 수 있는 일부 추가 콘텐츠(예: Visual Studio 업데이트 및 기타 선택적 구성 요소)는 제거되지 않습니다.

    > [!TIP]
    > 또는 “**전체 제거 프로그램**” 도구를 사용하여 Visual Studio 또는 Visual Studio 업데이트와 함께 설치되었을 수 있는 모든 것을 제거할 수 있습니다. 즉, Visual Studio 2013 이상의 모든 버전을 제거할 수 있습니다. 자세한 내용은 GitHub에서 [Visual Studio 제거 도구](https://github.com/Microsoft/VisualStudioUninstaller/releases)를 참조하세요.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Visual Studio를 자동 또는 수동 모드에서 제거(소스에서 제거)

1. Visual Studio가 설치된 컴퓨터에서 Windows 명령 프롬프트를 엽니다.

2. 다음 매개 변수를 입력합니다.

     *DVDRoot* \\<설치 파일 \> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Visual Studio의 이전 버전 또는 릴리스로 롤백

1. 이 항목에 나열된 방법을 사용하여 Visual Studio를 제거합니다.

   > [!WARNING]
   > Visual Studio의 현재 릴리스(또는 Visual Studio 업데이트)를 제거한 후 이전 릴리스 설치하면 예상대로 작동하지 않을 수 있습니다.
   >
   > 결과는 설치한 Visual Studio의 버전 또는 릴리스, 설치된 해당 구성 요소의 버전, Visual Studio 또는 해당 구성 요소에 종속성이 있을 수 있는 설치된 제품, 마지막으로 설치하거나 다시 설치하려는 초기 Visual Studio 버전에 따라 달라집니다.  이와 같은 모든 변수로 인해 표준 제거를 통해서는 이전 Visual Studio 버전 또는 릴리스에서 작동하지 않는 구성 요소가 남겨질 수 있습니다.
   >
   > 따라서 최상의 결과를 얻으려면 [Visual Studio 제거 도구](https://github.com/Microsoft/VisualStudioUninstaller/releases)를 사용하는 것이 좋습니다.

2. 사용하려는 초기 버전의 Visual Studio를 설치하거나 다시 설치합니다.

   이전 버전의 Visual Studio를 설치한 경우에도 설치 프로그램에서는 사용 가능한 최신 버전이나 릴리스를 사용하려고 시도합니다. 자세한 내용은 [방법: Visual Studio의 특정 릴리스 설치](../install/how-to-install-a-specific-release-of-visual-studio.md) 항목을 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio 설치](https://msdn.microsoft.com/library/e2h7fzkw.aspx)