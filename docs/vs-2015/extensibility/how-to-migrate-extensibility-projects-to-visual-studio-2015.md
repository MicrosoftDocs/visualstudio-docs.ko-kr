---
title: '방법: 확장성 프로젝트를 Visual Studio 2015로 마이그레이션 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915977"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>방법: Visual Studio 2015로 확장성 프로젝트 마이그레이션
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장을 업그레이드 하는 방법은 다음과 같습니다.  
  
> [!IMPORTANT]
> 이전 버전의 Visual Studio에 대 한 확장 솔루션 버전을 유지 하려는 경우 업그레이드 하기 전에 복사본을 만들어야 합니다. 업그레이드 된 버전을 이전 상태로 되돌리는 것은 어려울 수 있습니다.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>확장성 솔루션을 업그레이드 하려면  
  
1. 업그레이드 하려는 복사본을 사용 하 여 새 버전에서 엽니다. 업그레이드는 되돌릴 수 없다는 것이 좋습니다.  
  
2. 업그레이드가 완료 되 면 외부 프로그램의 경로를 devenv.exe 새 버전으로 변경 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다. **디버그** 탭에서 **시작 외부 프로그램** 을 기준으로 텍스트 상자를 찾고 devenv.exe의 경로를 Visual Studio 2015 경로로 변경 합니다 .이는 다음과 같습니다.  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3. Microsoft.VisualStudio.Shell.14.0.dll에 대 한 참조를 추가 합니다. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **추가/참조**를 선택 합니다. **확장** 탭을 선택 하 고 VisualStudio를 확인 합니다. **14.0**.  
  
4. 솔루션을 빌드합니다. 빌드된 파일은 다음에 배포 됩니다.  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions \\<Author 이름 \> \\<프로젝트 이름 \> \\<프로젝트 버전 \> \\ **입니다.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>확장성 프로젝트를 NuGet VS SDK 참조 어셈블리로 업데이트 하려면  
  
1. 프로젝트에 필요한 VS SDK 참조 어셈블리를 확인 합니다.  **솔루션 탐색기**에서 프로젝트의 **참조** 노드를 확장 하 고 프로젝트 참조 목록을 검토 합니다.  VS SDK 참조 어셈블리에는 이름에 **VisualStudio** 접두사가 있습니다 (예: VisualStudio 14.0).  
  
2. VS SDK 참조 어셈블리를 선택 하 여 프로젝트에서 제거 하 고 마우스 오른쪽 단추를 클릭 한 다음 **제거**합니다.  
  
3. VS SDK 참조 어셈블리의 NuGet 버전을 추가 합니다.  **솔루션 탐색기 참조** 노드에 있지만 **NuGet 패키지 관리 ...** 를 엽니다. 대화 상자에서 추가합니다.  이 대화 상자에 대 한 자세한 내용을 보려면 [대화 상자를 사용 하 여 NuGet 패키지 관리](/nuget/consume-packages/install-use-packages-visual-studio)를 참조 하세요. VS SDK 참조 어셈블리는 [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)에 의해 [nuget.org](https://www.nuget.org/) 에 게시 됩니다.  
  
4. **Nuget.org** 를 **패키지 원본**으로 사용 하 여 원하는 참조 어셈블리 (예: VisualStudio. 14.0)와 일치 하는 nuget 패키지 이름을 검색 하 고 프로젝트에 설치 합니다.  NuGet은 초기 어셈블리의 종속성을 충족 하기 위해 여러 참조 어셈블리를 추가할 수 있습니다.  
  
     원하는 경우 VS SDK [메타 패키지](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)를 설치 하 여 모든 vs sdk 참조 어셈블리를 한 번에 추가할 수 있습니다.  
  
5. 또한 NuGet 버전의 VS SDK 빌드 도구를 사용 하 여로 전환할 수 있습니다. 이 NuGet 패키지는 [Microsoft.](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) 사용자의 프로젝트에 추가 되 고 나면 VS SDK가 설치 되지 않은 컴퓨터에서 확장성 프로젝트를 빌드할 수 있도록 필요한 도구와 대상 파일이 포함 됩니다.  
  
> [!NOTE]
> NuGet 참조 어셈블리 및 도구를 사용 하도록 기존 확장성 프로젝트를 업데이트 하지 않아도 됩니다.  VS SDK와 함께 설치 된 참조 어셈블리 및 도구를 사용 하 여 계속 빌드할 수 있습니다.
