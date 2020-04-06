---
title: 비주얼 스튜디오 SDK 설치 | 마이크로 소프트 문서
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710340"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK 설치

비주얼 스튜디오 SDK(소프트웨어 개발 키트)는 Visual Studio 설정에서 선택 사양입니다. 나중에 VS SDK를 설치할 수도 있습니다.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>비주얼 스튜디오 설치의 일부로 Visual Studio SDK 설치

Visual Studio 설치에 VS SDK를 포함하려면 다른 도구 **집합**아래에 **Visual Studio 확장 개발** 워크로드를 설치합니다. 이 워크로드는 Visual Studio SDK와 필요한 필수 구성 조건을 설치합니다. **요약** 보기에서 구성요소를 선택하거나 선택 취소하여 설치를 추가로 조정할 수 있습니다.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>비주얼 스튜디오 설치 후 비주얼 스튜디오 SDK 설치

Visual Studio 설치를 완료한 후 Visual Studio SDK를 설치하려면 Visual Studio 설치 관리자를 다시 실행하고 **Visual Studio 확장 개발** 워크로드를 선택합니다.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK 설치

VS SDK를 먼저 설치하지 않고 확장성 프로젝트를 사용하여 솔루션을 열면 **누락된 기능 설치** 대화 상자에서 **Visual Studio 확장 개발** 워크로드를 설치하라는 메시지가 표시됩니다.

![확장 개발 설치](../extensibility/media/install-extension-development.png "확장 개발 설치")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK 설치

다른 Visual Studio 워크로드 또는 구성 요소와 마찬가지로 명령줄에서 **Visual Studio 확장 개발** 워크로드(ID: Microsoft.VisualStudio.VisualStudio.VisualStudioExtension)를 설치할 수도 있습니다. 명령줄 매개 변수 사용을 사용하여 Visual [Studio를 설치하여](../install/use-command-line-parameters-to-install-visual-studio.md) 적절한 명령줄 스위치에 대한 자세한 내용과 워크로드 또는 구성 요소 식별자 결정에 대한 일반적인 지침을 참조하십시오.

설치된 버전의 Visual Studio와 일치하는 Visual Studio 설치 관리자를 사용해야 합니다. 예를 들어 컴퓨터에 Visual Studio Enterprise가 설치되어 있는 경우 Visual Studio 엔터프라이즈 설치*관리자(vs_enterprise.exe)를*실행해야 합니다.
