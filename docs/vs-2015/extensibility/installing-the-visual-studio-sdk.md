---
title: Visual Studio SDK 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843426"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual studio 설치의 일부로 Visual Studio SDK 설치  
 Visual Studio 설치에 필요한 것을 포함 하려면 사용자 지정 설치를 수행 해야 합니다.  
  
> [!NOTE]
> 설치 실행 파일에서 Visual Studio SDK를 **Visual Studio 확장성 도구**이라고 합니다.  
  
1. Visual Studio 2015 설치를 시작 합니다. Express를 제외한 모든 버전의 Visual Studio를 설치할 수 있습니다.  
  
2. 첫 번째 화면에서 **기본값**이 아닌 **사용자 지정**을 선택 합니다. **다음**을 클릭합니다.  
  
3. 사용자 지정 기능의 트리 뷰가 표시 됩니다. **일반 도구**를 엽니다. **Visual Studio 확장성 도구** 표시 되어야 합니다.  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. **Visual Studio 확장성 도구** 를 확인 하 고 **다음** 을 클릭 한 후 설치를 계속 합니다.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio를 설치한 후 Visual Studio SDK 설치  
 Visual Studio 설치를 완료 한 후 Visual Studio SDK를 설치 하기로 결정 한 경우 다음 절차를 수행 해야 합니다.  
  
1. **제어판/프로그램/프로그램/기능**으로 이동 하 여 **Visual Studio 2015**을 찾습니다. Express를 제외 하 고 Visual Studio 2015의 모든 버전에 대해 Visual Studio SDK를 설치할 수 있습니다.  
  
2. **Visual Studio 2015**을 마우스 오른쪽 단추로 클릭 한 다음 **변경**을 클릭 합니다. 설치 페이지가 표시 됩니다.  
  
3. 위의 Visual studio SDK를 설치 **하는 과정** 에서와 동일한 절차를 수행 합니다.  
  
4. **Visual Studio 확장성 도구** 링크를 클릭 하 여 VISUAL Studio SDK를 설치 합니다.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK 설치  
 서 수를 먼저 설치 하지 않고 확장성 프로젝트를 사용 하 여 솔루션을 여는 경우 솔루션 탐색기 위에 강조 표시 된 정보 표시줄이 표시 됩니다. 다음과 유사해야 합니다.  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK 설치  
 Visual Studio 설치 관리자와 함께 **/InstallSelectableItems** 스위치를 사용 하 여 명령줄에서 고 지 수를 설치할 수 있습니다. 설치 관리자에서 명령줄 매개 변수를 사용 하는 방법에 대 한 자세한 내용은 [Visual Studio 2015 설치](../install/install-visual-studio-2015.md)를 참조 하세요.  
  
 Visual Studio 2015 Community installer를 사용 하 여 다음을 설치 하는 방법은 다음과 같습니다.  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Visual Studio의 설치된 버전과 일치하는 Visual Studio 설치 프로그램을 사용해야 합니다. 예를 들어 컴퓨터에 Visual Studio Enterprise가 설치되어 있는 경우 Visual Studio Enterprise 설치 프로그램(vs_enterprise.exe)을 실행해야 합니다.
