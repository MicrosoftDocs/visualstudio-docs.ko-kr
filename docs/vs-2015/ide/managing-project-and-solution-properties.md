---
title: 프로젝트 및 솔루션 속성 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec48aac60a8f15527c92d19a38ca9f996dcfdd6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651355"
---
# <a name="managing-project-and-solution-properties"></a>프로젝트 및 솔루션 속성 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에는 컴파일, 디버깅, 테스트 및 배포의 다양한 측면을 제어하는 속성이 있습니다. 일부 속성은 모든 프로젝트 형식 간에 공통적으로 적용되고 일부 속성은 특정 언어 또는 플랫폼에 고유합니다. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 속성을 선택하거나 메뉴 모음의 **QuickLaunch** 검색 상자에 속성을 입력하여 프로젝트 속성에 액세스합니다.

 ![프로젝트 상황에 맞는 메뉴](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")

 .NET 프로젝트는 프로젝트 트리 자체에도 속성 노드가 있습니다.

 ![솔루션 탐색기 트리의 속성 노드](../ide/media/vs2015-props-se.png "VS2015_Props_SE")

> [!TIP]
> 솔루션에는 몇 가지 속성이 있으며 프로젝트 항목도 마찬가지입니다. 이러한 속성은 **프로젝트 디자이너**가 아니라 [속성 창](../ide/reference/properties-window.md)에서 액세스합니다.

## <a name="project-properties"></a>프로젝트 속성
 프로젝트 속성은 그룹으로 구성되어 있으며, 각 그룹에 해당 속성 페이지가 있고 언어 및 프로젝트 형식마다 페이지가 다를 수 있습니다.

### <a name="c-and-visual-basic-projects"></a>C# 및 Visual Basic 프로젝트
 C# 및 Visual Basic 프로젝트에서는 속성이 **프로젝트 디자이너**에 노출됩니다. 다음 그림에서는 C# WPF 프로젝트에 대한 빌드 속성 페이지를 보여 줍니다.

 ![Visual Studio 프로젝트 디자이너](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")

 프로젝트 디자이너의 각 속성 페이지에 대한 자세한 내용은 [프로젝트 속성 참조](../ide/reference/project-properties-reference.md)를 참조하세요.

### <a name="c-and-javascript-projects"></a>C++ 및 JavaScript 프로젝트
 C++ 및 JavaScript 프로젝트에는 프로젝트 속성을 관리하기 위한 다른 사용자 인터페이스가 있습니다. 이 그림에서는 C++ 프로젝트 속성 페이지를 보여줍니다(JavaScript 페이지도 유사함):

 ![Visual C&#43;&#43; 프로젝트 속성](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")

 C++ 프로젝트 속성에 대한 자세한 내용은 [프로젝트 속성 작업](https://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd)을 참조하세요. JavaScript 속성에 대한 자세한 내용은 [속성 페이지, JavaScript](../ide/reference/property-pages-javascript.md)를 참조하세요.

## <a name="solution-properties"></a>솔루션 속성
 솔루션에 대한 속성에 액세스하려면 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. 대화 상자에서 디버그 또는 릴리스 빌드에 대한 프로젝트 구성을 설정하고, F5 키를 누를 때 시작 프로젝트여야 하는 프로젝트를 선택하고, 코드 분석 옵션을 설정할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)
