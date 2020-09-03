---
title: '방법: Visual C++ 프로젝트를 Visual Studio 2015로 업그레이드 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 23461fb1927cfcbf738d2dbcb82e3977b3be265a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278734"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>방법: Visual C++ 프로젝트를 Visual Studio 2015로 업그레이드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017에 대한 최신 설명서는 [Visual C++ 포팅 및 업그레이드 가이드](/cpp/porting/visual-cpp-porting-and-upgrading-guide)를 참조하세요.

이전 버전의 Visual Studio에서 만든 Visual C++ 프로젝트를 처음 열면 프로젝트를 업데이트해야 한다는 메시지가 표시될 수 있습니다. 최신 버전의 Visual C++ 컴파일러와 라이브러리로 업그레이드할 것인지 묻는 메시지가 나타납니다. 업그레이드하는 방법은 프로젝트를 만드는 데 사용한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전에 따라 달라집니다.

 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 을 사용하여 [!INCLUDE[win8](../includes/win8-md.md)] 에서 만든 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]프로젝트를 열거나 편집, 빌드할 수 있지만 새 [!INCLUDE[win8](../includes/win8-md.md)] 프로젝트를 만들려면 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]를 사용해야 합니다. [!INCLUDE[win81](../includes/win81-md.md)] 프로젝트를 만들려면 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]을 사용해야 합니다.

 Windows 10 프로젝트를 만들려면 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]를 사용해야 합니다.

 프로젝트를 업데이트하라는 메시지가 나타나지 않으면 프로젝트를 업그레이드할 필요가 없습니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이전의 [!INCLUDE[vs2010](../includes/vs2010-md.md)]버전에서 프로젝트(.vcproj)를 만든 경우 해당 프로젝트를 업데이트해야 합니다.

- [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)],  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]또는 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 에서 프로젝트(.vcxproj)를 만든 경우 두 가지 옵션이 있습니다.

  - 업데이트를 건너뛸 수 있습니다. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 또는 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]의 Visual C++ 도구에 대한 액세스 권한이 있을 경우 프로젝트를 변경하지 않고 로드합니다. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]가 있는 동일한 컴퓨터에서 프로젝트를 만드는 데 사용한 버전의 Visual Studio를 설치하여 이 액세스 권한을 제공할 수 있습니다. 자세한 내용은 [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md)를 참조하세요.

  - 이 항목의 뒷부분에서 설명하는 사항을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 변경하도록 허용하여 프로젝트를 업데이트할 수 있습니다. 솔루션에 Visual C++ 프로젝트가 두 개 이상 있을 경우 이를 모두 업데이트해야 합니다.

    > [!NOTE]
    > 프롬프트 메시지가 처음 나타날 때 업데이트를 거부할 경우 **프로젝트** 메뉴에서 **VC++ 프로젝트 업데이트** 를 선택하여 나중에 프로젝트를 업데이트할 수 있습니다. 명령이 나타나지 않으면 업데이트할 필요가 없습니다.

## <a name="upgrading-a-visual-c-project"></a>Visual C++ 프로젝트 업그레이드
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 에서 프로젝트를 자동으로 업데이트하도록 허용할 경우 다음과 같이 변경됩니다.

- [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 컴파일러 및 라이브러리(PlatformToolset = VisualStudio v140)를 사용하도록 프로젝트를 변경합니다.

- [!INCLUDE[cppcli](../includes/cppcli-md.md)] 프로젝트의 경우 TargetFrameworkVersion을 .NET Framework 4.5.2로 변경합니다.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>사용자 지정 플랫폼 도구 집합 계속 사용
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]에서 사용자 지정 플랫폼 도구 집합으로 계속 작업하려면 해당 도구 집합이 %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\(x86 컴퓨터) 또는 %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\(x64 컴퓨터)에 있어야 합니다. 사용자 지정 플랫폼 도구 집합을 만드는 방법에 대한 자세한 내용은 Visual C++ 팀 블로그에서 [C++ 네이티브 멀티 타기팅](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) 을 참조하세요.

## <a name="see-also"></a>관련 항목
 [Visual C++ 포팅 및 업그레이드 가이드](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [Visual Studio 프로젝트 포팅, 마이그레이션 및 업그레이드](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
