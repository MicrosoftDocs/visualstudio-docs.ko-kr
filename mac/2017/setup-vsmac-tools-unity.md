---
title: Mac용 Visual Studio Tools for Unity 설정
description: Mac용 Visual Studio에서 사용할 Unity 도구 설정 및 설치
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: 1ea23f701f251476693108b51da570fbcbaa7756
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950431"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Mac용 Visual Studio Tools for Unity 설정

이 섹션에서는 Mac용 Visual Studio Tools for Unity의 사용을 시작하는 방법을 설명합니다.

## <a name="install-visual-studio-for-mac"></a>Mac용 Visual Studio 설치

### <a name="unity-bundled-installation"></a>Unity Bundled 설치

Unity 2018.1부터 Mac용 Visual Studio는 기본 Unity용 C# IDE(integrated development environment)이며, Unity 다운로드 도우미와 Unity Hub 설치 도구에 포함되어 있습니다. [store.unity.com](https://store.unity.com/)에서 Unity를 다운로드하세요.

설치하는 동안 Unity와 함께 설치할 구성 요소 목록에서 Mac용 Visual Studio를 선택했는지 확인합니다.

#### <a name="unity-hub"></a>Unity Hub

![unity hub 설치](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity 다운로드 도우미

![unity 다운로드 도우미 설치](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac용 Visual Studio 업데이트 확인

Unity 설치에 포함되는 Mac용 Visual Studio의 버전은 최신 버전이 아닐 수 있습니다. 최신 도구 및 기능에 액세스할 수 있도록 업데이트를 확인하는 것이 좋습니다.

* [Mac용 Visual Studio 업데이트](update.md)

### <a name="manual-installation"></a>수동 설치

Unity 5.6.1 이상이 이미 설치되어 있지만 Mac용 Visual Studio가 없는 경우, Mac용 Visual Studio를 수동으로 설치할 수 있습니다. Mac용 Visual Studio는 무료 Community 버전을 포함한 모든 버전에서 Mac용 Visual Studio Tools for Unity가 번들로 제공됩니다.

* [visualstudio.microsoft.com](https://visualstudio.microsoft.com/)에서 Mac용 Visual Studio를 다운로드합니다.
* Mac용 Visual Studio 설치 프로세스에서 Mac용 Visual Studio Tools for Unity가 자동으로 설치됩니다.
* 설치에 관한 추가 도움을 받으려면 [설치 가이드](/visualstudio/mac/installation/?view=vsmac-2017)의 단계를 따릅니다.

> [!NOTE]
> Mac용 Visual Studio Tools for Unity를 사용하려면 Unity 버전 5.6.1 이상이 필요합니다. Visual Studio Tools for Unity가 사용 중인 Unity 버전에서 사용 가능한지 확인하려면 Unity 메뉴에서 **Unity 정보**를 선택하고 대화 상자의 왼쪽 아래에 “Microsoft Visual Studio Tools for Unity enabled”(Microsoft Visual Studio Tools for Unity 사용 가능) 텍스트가 있는지 확인하세요.
>
> ![Unity 정보](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Mac용 Visual Studio Tools for Unity 확장이 사용 가능한지 확인

Mac용 Visual Studio Tools for Unity 확장은 기본적으로 사용 가능하지만, 이를 확인하고 설치된 버전 번호를 확인할 수 있습니다.

1. Visual Studio 메뉴에서 **확장...** 을 선택합니다.

   ![확장 선택](media/setup-vsmac-tools-unity-image1.png)

2. [게임 개발] 섹션을 확장하고 [Mac용 Visual Studio Tools for Unity] 항목을 확인합니다.

   ![Unity 항목 보기](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Mac용 Visual Studio를 사용하도록 Unity 구성

Unity 2018.1부터 Visual Studio는 Unity의 기본 외부 스크립트 편집기여야 합니다. 이를 확인하거나 외부 스크립트 편집기를 Visual Studio로 변경할 수 있습니다.

1. Unity 메뉴에서 **기본 설정...** 을 선택합니다.

   ![기본 설정 선택](media/setup-vsmac-tools-unity-image4.png)

2. 기본 설정 대화 상자에서 **외부 도구** 탭을 선택합니다.

3. 외부 스크립트 편집기 드롭다운 목록에서 **Visual Studio**가 있을 경우 이를 선택하고, 그렇지 않을 경우 **찾아보기...** 를 선택합니다.

   ![Visual Studio 선택](media/setup-vsmac-tools-unity-image5.png)

4. **찾아보기...** 를 선택한 경우 애플리케이션 디렉터리로 이동하여 Visual Studio를 선택하고 **열기**를 클릭합니다.

   ![열기 선택](media/setup-vsmac-tools-unity-image6.png)

5. Visual Studio가 **외부 스크립트 편집기** 목록에서 선택되면 [기본 설정] 대화 상자를 닫아 구성 프로세스를 완료합니다.