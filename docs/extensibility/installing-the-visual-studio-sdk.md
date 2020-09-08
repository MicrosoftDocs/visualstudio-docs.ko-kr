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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905541"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK 설치

Visual Studio SDK(소프트웨어 개발 키트)는 Visual Studio 설치 프로그램의 선택적 기능입니다. VS SDK는 나중에 설치할 수도 있습니다.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio 설치의 일부로 Visual Studio SDK 설치

Visual Studio 설치에 VS SDK를 포함하려면 **기타 도구 세트**에 **Visual Studio 확장 개발** 워크로드를 설치합니다. 이 워크로드를 통해 Visual Studio SDK 및 필수 구성 요소가 설치됩니다. **요약** 뷰에서 구성 요소를 선택하거나 선택을 취소하여 설치를 추가로 조정할 수 있습니다.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio 설치 후 Visual Studio SDK 설치

Visual Studio 설치를 완료한 후 Visual Studio SDK를 설치하려면 Visual Studio 설치 프로그램을 다시 실행하고 **Visual Studio 확장 개발** 워크로드를 선택합니다.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK 설치

VS SDK를 먼저 설치하지 않고 확장성 프로젝트를 사용하여 솔루션을 여는 경우 **Visual Studio 확장 개발** 워크로드를 설치하는 **누락된 기능 설치** 대화 상자가 표시됩니다.

![확장 개발 설치](../extensibility/media/install-extension-development.png "확장 개발 설치")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK 설치

Visual Studio 워크로드 또는 구성 요소와 마찬가지로 **Visual Studio 확장 개발** 워크로드(ID: Microsoft.VisualStudio.Workload.VisualStudioExtension)를 명령줄에서 설치할 수 있습니다. 적절한 명령줄 스위치에 대한 자세한 내용과 워크로드 또는 구성 요소 식별자 확인에 대한 일반 지침은 [명령줄 매개 변수를 사용한 Visual Studio 설치](../install/use-command-line-parameters-to-install-visual-studio.md)를 참조하세요.

Visual Studio의 설치된 버전과 일치하는 Visual Studio 설치 프로그램을 사용해야 합니다. 예를 들어 컴퓨터에 Visual Studio Enterprise가 설치되어 있는 경우 Visual Studio Enterprise 설치 프로그램(*vs_enterprise.exe*)을 실행해야 합니다.
