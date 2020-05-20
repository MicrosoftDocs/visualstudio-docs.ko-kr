---
title: 프로젝트 및 솔루션 속성 관리
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591309"
---
# <a name="manage-project-and-solution-properties"></a>프로젝트 및 솔루션 속성 관리

프로젝트에는 컴파일, 디버깅, 테스트 및 배포의 다양한 측면을 제어하는 속성이 있습니다. 일부 속성은 모든 프로젝트 형식 간에 공통적으로 적용되고 일부 속성은 특정 언어 또는 플랫폼에 고유합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하거나 메뉴 모음의 검색 상자에 **속성**을 입력하고 결과에서 **속성 창**을 선택하여 프로젝트 속성에 액세스합니다.

![프로젝트 상황에 맞는 메뉴](../ide/media/vs2015_proj_prop_menu.gif)

.NET 프로젝트는 프로젝트 트리 자체에도 속성 노드가 있을 수 있습니다.

![솔루션 탐색기 트리의 속성 노드](../ide/media/vs2015_props_se.png)

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [솔루션 및 프로젝트 속성 관리(Mac용 Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)를 참조하세요.

## <a name="project-properties"></a>프로젝트 속성

프로젝트 속성은 그룹별로 구성되고, 그룹마다 고유의 속성 페이지가 있습니다. 이러한 페이지는 언어 및 프로젝트 종류에 따라 달라질 수 있습니다.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic 및 F# 프로젝트

C#, Visual Basic 및 F# 프로젝트에서는 속성이 **프로젝트 디자이너**에 공개됩니다. 다음 그림에서는 C# WPF 프로젝트에 대한 **빌드** 속성 페이지를 보여 줍니다.

![Visual Studio 프로젝트 디자이너](../ide/media/vs2015_proppage_build.png)

**프로젝트 디자이너**의 각 속성 페이지에 대한 자세한 내용은 [프로젝트 속성 참조](../ide/reference/project-properties-reference.md)를 참조하세요.

> [!TIP]
> 솔루션에는 몇 가지 속성이 있으며 프로젝트 항목도 마찬가지입니다. 이러한 속성은 **프로젝트 디자이너**가 아니라 [속성 창](../ide/reference/properties-window.md)에서 액세스합니다.

### <a name="c-and-javascript-projects"></a>C++ 및 JavaScript 프로젝트

C++ 및 JavaScript 프로젝트에는 프로젝트 속성을 관리하기 위한 다른 사용자 인터페이스가 있습니다. 이 그림에서는 C++ 프로젝트 속성 페이지를 보여줍니다(JavaScript 페이지도 유사함):

![Visual C&#43;&#43; 프로젝트 속성](../ide/media/vs2015_projprops_cpp.png)

C++ 프로젝트 속성에 대한 자세한 내용은 [프로젝트 속성 작업 (C++)](/cpp/build/working-with-project-properties)을 참조하세요. JavaScript 속성에 대한 자세한 내용은 [속성 페이지, JavaScript](../ide/reference/property-pages-javascript.md)를 참조하세요.

## <a name="solution-properties"></a>솔루션 속성

솔루션에 대한 속성에 액세스하려면 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. 대화 상자에서 **디버그** 또는 **릴리스** 빌드에 대한 프로젝트 구성을 설정하고, **F5** 키를 누를 때 시작 프로젝트여야 하는 프로젝트를 선택하고, 코드 분석 옵션을 설정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)
- [솔루션 및 프로젝트 속성 관리(Mac용 Visual Studio)](/visualstudio/mac/managing-solutions-and-project-properties)
