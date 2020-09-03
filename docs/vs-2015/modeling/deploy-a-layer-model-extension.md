---
title: 레이어 모델 확장 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669871"
---
# <a name="deploy-a-layer-model-extension"></a>레이어 모델 확장 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 다른 사용자는 Visual Studio를 사용하여 만든 레이어 모델링 확장을 설치할 수 있습니다.

## <a name="installing-your-extension"></a>확장 설치
 확장은 다른 컴퓨터에 설치할 수 있는 VSIX 파일로 컴파일됩니다. 개발 컴퓨터에 설치하여 Visual Studio의 기본 인스턴스에서 확장을 사용할 수 있게 만들 수도 있습니다.

#### <a name="to-install-the-extension"></a>확장을 설치하려면

1. **소스 .vsix .manifest**를 포함 하는 프로젝트의 파일 탐색기에서 **bin \\ \\ ***을 엽니다.

2. 확장명을 설치 하려는 컴퓨터에 ** \* .vsix** 파일을 복사 합니다.

3. 대상 컴퓨터에서 Windows 탐색기를 통해 *.vsix 파일을 두 번 클릭합니다.

    VSIX 설치 관리자가 열립니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

2. 확장의 이름을 클릭 한 다음 **제거**를 클릭 합니다.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation Build 서버에 확장 설치
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 서버에는 일반적으로 Visual Studio가 설치 되어 있지 않으므로 두 번 클릭 하 여 VSIX를 설치할 수 없습니다. [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 설치에는 VSIX 확장 실행을 허용하는 일부 구성 요소가 포함되어 있지만 수동으로 확장을 설치해야 합니다.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>[!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 서버에 레이어 확장을 설치하려면

1. 개발 컴퓨터의 **.vsix** 파일을 컴퓨터로 복사 합니다. [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]

     VSIX 파일을 다음 위치 중 하나에 배치합니다.

    - 모든 사용자 및 서비스에 대해 설치하려면

         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft

    - [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]를 실행하는 네트워크 서비스에 대해서만 설치하려면

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [version] \Extensions\Microsoft

    - 특정 사용자로 대화형 모드에서 실행되도록 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]를 구성한 경우 해당 사용자에 대해서만 설치할 수 있습니다.

         %LocalAppData%\Microsoft\VisualStudio \\ [version] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData%는 일반적으로 *DriveName*: Users*UserName*AppDataLocal입니다.

2. 각 VSIX 파일을 동일한 위치의 폴더로 확장합니다.

    1. **.Vsix** 에서 **.zip**으로 파일 이름 확장명을 변경 합니다.

    2. .zip 파일의 내용을 폴더로 추출합니다.

    3. .zip 파일을 삭제합니다.

3. [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]를 다시 시작합니다.
