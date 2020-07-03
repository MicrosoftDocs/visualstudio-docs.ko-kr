---
title: Visual Studio SDK 설치 | Microsoft Docs
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905541"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK 설치

Visual studio SDK (소프트웨어 개발 키트)는 Visual Studio 설치 프로그램의 선택적 기능입니다. VS SDK는 나중에 설치할 수도 있습니다.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual studio 설치의 일부로 Visual Studio SDK 설치

Visual Studio 설치에 VS SDK를 포함 하려면 **다른 도구 집합**아래에 **visual studio 확장 개발** 워크 로드를 설치 합니다. 이 작업을 통해 Visual Studio SDK 및 필수 구성 요소가 설치 됩니다. **요약** 뷰에서 구성 요소를 선택 하거나 선택을 취소 하 여 설치를 추가로 튜닝할 수 있습니다.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio를 설치한 후 Visual Studio SDK 설치

Visual studio 설치를 완료 한 후 Visual Studio SDK를 설치 하려면 visual studio 설치 관리자를 다시 실행 하 고 **Visual studio 확장 개발** 워크 로드를 선택 합니다.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK 설치

VS SDK를 먼저 설치 하지 않고 확장성 프로젝트를 사용 하 여 솔루션을 여는 경우 **Visual Studio 확장 개발** 워크 로드를 설치 하려면 **누락 된 기능 설치** 대화 상자가 표시 됩니다.

![확장 개발 설치](../extensibility/media/install-extension-development.png "확장 개발 설치")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK를 설치 합니다.

Visual Studio 워크 로드 또는 구성 요소와 마찬가지로 명령줄에서 **Visual studio 확장 개발** 워크 로드 (ID: VisualStudio. VisualStudioExtension)를 설치할 수도 있습니다. 적절 한 명령줄 스위치에 대 한 자세한 내용 및 워크 로드 또는 구성 요소 식별자 확인에 대 한 일반적인 지침은 [명령줄 매개 변수를 사용 하 여 Visual Studio 설치를](../install/use-command-line-parameters-to-install-visual-studio.md) 참조 하세요.

Visual Studio의 설치 된 버전과 일치 하는 Visual Studio 설치 관리자를 사용 해야 합니다. 예를 들어 컴퓨터에 Visual Studio Enterprise 설치 되어 있으면 Visual Studio Enterprise 설치 관리자 (*vs_enterprise.exe*)를 실행 해야 합니다.
