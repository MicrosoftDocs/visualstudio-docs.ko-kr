---
title: '방법: 실패 한 프로젝트 업그레이드 문제 해결 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844444"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>방법: 실패한 Visual Studio 프로젝트 업그레이드 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

때때로 Visual Studio는 이전 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 프로젝트를 완전히 전환할 수 없습니다. 다음 섹션의 팁으로 특정 문제를 해결할 수 없는 경우 TechNet [Wiki: 개발 포털](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio)에서 자세한 정보를 찾을 수 있습니다.

## <a name="the-project-does-not-run-because-files-are-not-found"></a>파일이 없으므로 프로젝트가 실행 되지 않습니다.
 프로젝트 파일에는 F5를 누를 때 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 프로젝트를 실행하기 위해 사용하는 하드 코드된 파일이 포함되어 있습니다. 이러한 경로에는 devenv.exe 및 기타 필수 파일의 위치가 포함 될 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 업그레이드 버전에서 이러한 파일의 경로는 변경이 가능할 수 있습니다.

#### <a name="to-resolve-incorrect-file-paths"></a>잘못 된 파일 경로를 확인 하려면

1. 텍스트 편집기에서 프로젝트 파일을 엽니다.

2. 올바르지 않을 수 있는 파일 경로의 탐색, 특히 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전 번호를 포함하는 경로입니다.

3. 새 대상을 가리키도록 잘못 된 파일 경로를 수정 합니다.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>참조가 유효 하지 않기 때문에 프로젝트가 빌드되지 않습니다.
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 업그레이드 하는 경우 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]버전을 업그레이드할 수도 있습니다. 프로젝트에 최신 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전에서 중지된 참조가 포함되어 있는 경우 올바르게 해결할 수 없을 수 있습니다. 이는 특히 버전 번호를 포함 하는 참조에 사용할 수 있습니다 `Microsoft.VisualStudio.Shell.Interop.8.0` .

 코드에 잘못된 참조가 많이 있는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 멀티 타기팅 기능을 사용하여 이전 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 대상하는 하는 것이 가장 쉬운 해결 방법일 수 있습니다.

#### <a name="to-resolve-incorrect-references"></a>잘못된 참조를 해결하려면

1. 텍스트 편집기에서 프로젝트 파일을 엽니다.

2. 프로젝트 속성을 엽니다.

3. 올바른 **대상 프레임워크** 값을 선택합니다. 또는 프로젝트 파일에서 `<TargetFrameworkVersion>` 요소의 값을 직접 수정할 수 있습니다.

   프로젝트를 업그레이드된 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전에서 실행하려면 프로젝트에 대한 참조를 업데이트하고 참조를 호출하는 `Imports` 또는 `Using` 문도 업데이트해야 합니다. IDE에서 프로젝트가 로드되는 경우 **솔루션 탐색기** 또는 **참조 관리자** 대화 상자를 사용하여 참조를 업데이트할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [/Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [ASP.NET 4로 변환](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
